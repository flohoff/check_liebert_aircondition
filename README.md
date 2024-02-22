
Nagios/Icinga2 check for Vertiv aka Liebert DataCenter Air Condition controllers:

    $ ./check_liebert_aircondition --help
    check_liebert_aircondition [-CHt] [long options...] <some-arg>
        --host STR (or -H)       Hostname
        --community STR (or -C)  SNMP community
        --timeout INT (or -t)    Timeout
        --waterflow              Water Flow Loss
        --debug                  Debug
        --listflexentries        List flexible entries
        --perf STR...            Performance metrics

        --help                   print usage message and exit

User **--waterflow** to monitor the waterflow alarm entry.

    ./check_liebert_aircondition \
            --host 172.30.128.18 \
            --waterflow \
            --community public \
            --perf "Ext Air Sensor B Temperature|deg C" \
            --perf "Supply Air Temperature|deg C" \
            --perf "Chilled Water Inlet Temperature|deg C" \
            --perf "Chilled Water Outlet Temperature|deg C" \
            --perf "Ext Air Sensor B Humidity" \
            --perf "Fan Speed" \
            --perf "Return Air Temperature|deg C"

    LIEBERT_AIRCONDITION OK - system state: normalOperation(1) conditions present: 0 controlOperation: On(1) | 'Ext Air Sensor B Temperature'=14.3C;; 'Supply Air Temperature'=19.9C;; 'Chilled Water Inlet Temperature'=14.3C;; 'Chilled Water Outlet Temperature'=UnavailableC;; 'Ext Air Sensor B Humidity'=23.3%;; 'Fan Speed'=53%;; 'Return Air Temperature'=27.4C;;

To get the available sensor entries use the **-flexentries** command line option. Example output
for a Liebert PDX-PCW:

	./check_liebert_aircondition --host 172.30.128.18 --community public --listflexentries
	Actual Cold Aisle Humidity                              Unavailable          % RH      
	Actual Cold Aisle Temperature                           Unavailable          deg C     
	Actual Cold Aisle Temperature                           Unavailable          deg F     
	Actual Compressor 1 Suction Pressure                    -32768               bar       
	Actual Compressor 2 Suction Pressure                    -32768               bar       
	Actual Return Air Temperature Set Point                 25.0                 deg C     
	Actual Return Air Temperature Set Point                 77.0                 deg F     
	Actual Return Humidity Set Point                        Unavailable          % RH      
	Adjusted Humidity                                       30.4                 % RH      
	Air Filter Differential Pressure                        -131.55              inWC      
	Air Filter Differential Pressure                        -32768               Pa        
	Air Temperature Control Integration Time                0                    min       
	Air Temperature Control Type                            Proportional                   
	Air Temperature Dead Band                               0.0                  deg C     
	Air Temperature Dead Band                               0.0                  deg F     
	Air Temperature Proportional Band                       14.4                 deg F     
	Air Temperature Proportional Band                       8.0                  deg C     
	Air Temperature Set Point                               25.0                 deg C     
	Air Temperature Set Point                               77.0                 deg F     
	Analog Input Reading                                    0.00                           
	Analog Input Reading                                    0.00                           
	Analog Input Reading                                    0.00                           
	Analog Input Reading                                    0.00                           
	Auto Restart Delay                                      5                    sec       
	Automatic Transfer Switch - Active Power Supply         Power Supply 1                 
	Automatic Transfer Switch - Power Supply 1 Status       OK                             
	Automatic Transfer Switch - Power Supply 2 Status       OK                             
	BMS Timeout Period                                      0                    min       
	Back Draft Control Fan Speed                            20                   %         
	CW Valve Control                                        0                              
	Calculated Next Maintenance Month                       65409                          
	Calculated Next Maintenance Year                        Unavailable                    
	Chilled Water Flow Loss Status                          Flow OK                        
	Chilled Water Flow Loss Status                          Flow OK                        
	Chilled Water Inlet Temperature                         14.3                 deg C     
	Chilled Water Inlet Temperature                         Unavailable          deg C     
	Chilled Water Outlet Temperature                        23.3                 deg C     
	Chilled Water Outlet Temperature                        Unavailable          deg C     
	Chilled Water Valve Hours                               0                    hr        
	Chilled Water Valve Hours                               8494                 hr        
	Chilled Water Valve Reset Enable                        disabled                       
	Clogged Air Filter - Event Control                      enabled                        
	Clogged Air Filter - Event Type                         Warning                        
	Cold Aisle Cascade Fan Speed Max Set Point              40                   %         
	Cold Aisle Control Enable                               disabled                       
	Cold Aisle Fan Speed Max Set Point                      80                   %         
	Cold Aisle Fan Speed Min Set Point                      30                   %         
	Cold Aisle Force Max Fan/Cooling - Ext Control          disabled                       
	Cold Aisle Humidity Calculation Method                  Highest                        
	Cold Aisle Sensor Air Temperature                       Unavailable          deg C     
	Cold Aisle Sensor Air Temperature                       Unavailable          deg C     
	Cold Aisle Sensor Air Temperature                       Unavailable          deg C     
	Cold Aisle Sensor Air Temperature                       Unavailable          deg F     
	Cold Aisle Sensor Air Temperature                       Unavailable          deg F     
	Cold Aisle Sensor Air Temperature                       Unavailable          deg F     
	Cold Aisle Sensor Humidity                              Unavailable          % RH      
	Cold Aisle Sensor Humidity                              Unavailable          % RH      
	Cold Aisle Sensor Humidity                              Unavailable          % RH      
	Cold Aisle Temperature Calculation Method               Highest                        
	Compressor Capacity Control State                       off                            
	Compressor Capacity Control State                       off                            
	Compressor Discharge Pressure                           Unavailable          bar       
	Compressor Discharge Pressure                           Unavailable          bar       
	Compressor High Head Pressure - Event Control           enabled                        
	Compressor High Head Pressure - Event Control           enabled                        
	Compressor High Head Pressure - Event Type              Alarm                          
	Compressor High Head Pressure - Event Type              Alarm                          
	Compressor Hours                                        0                    hr        
	Compressor Hours                                        0                    hr        
	Compressor Hours                                        0                    hr        
	Compressor Hours                                        0                    hr        
	Compressor Hours Threshold                              0                    hr        
	Compressor Hours Threshold                              0                    hr        
	Compressor Hours Threshold                              0                    hr        
	Compressor Hours Threshold                              0                    hr        
	Compressor Low Suction Pressure - Event Control         enabled                        
	Compressor Low Suction Pressure - Event Control         enabled                        
	Compressor Low Suction Pressure - Event Type            Alarm                          
	Compressor Low Suction Pressure - Event Type            Alarm                          
	Compressor Short Cycle - Event Control                  enabled                        
	Compressor Short Cycle - Event Control                  enabled                        
	Compressor Short Cycle - Event Type                     Warning                        
	Compressor Short Cycle - Event Type                     Warning                        
	Compressor State                                        off                            
	Compressor State                                        off                            
	Compressor Thermal Overload - Event Control             enabled                        
	Compressor Thermal Overload - Event Control             enabled                        
	Compressor Thermal Overload - Event Type                Alarm                          
	Compressor Thermal Overload - Event Type                Alarm                          
	Compressor Utilization                                  57                   %         
	Condenser Issue - Event Control                         enabled                        
	Condenser Issue - Event Control                         enabled                        
	Condenser Issue - Event Type                            Warning                        
	Condenser Issue - Event Type                            Warning                        
	Cooling Capacity                                        0.0                  kW        
	Cooling Capacity                                        0.0                  kW        
	Cooling State                                           on                             
	Customer Configurable Analog Output Value               0                    %         
	Customer Configurable Analog Output Value               0                    %         
	Customer Configurable Analog Output Value               53                   %         
	Customer Configurable Analog Output Value               57                   %         
	Customer Input 1                                        Inactive Event                 
	Customer Input 1 - Event Control                        enabled                        
	Customer Input 1 - Event Type                           Alarm                          
	Customer Input 2                                        Inactive Event                 
	Customer Input 2 - Event Control                        enabled                        
	Customer Input 2 - Event Type                           Alarm                          
	Customer Input 3 - Event Control                        enabled                        
	Customer Input 3 - Event Type                           Alarm                          
	Customer Input 4 - Event Control                        enabled                        
	Customer Input 4 - Event Type                           Alarm                          
	Dehumidification Fan Speed Min Set Point                40                   %         
	Dehumidifier Hours                                      0                    hr        
	Dehumidifier Hours Threshold                            0                    hr        
	Dehumidifier State                                      off                            
	Dehumidifier Utilization                                0                    %         
	Dew Point Dead Band                                     2.2                  deg C     
	Dew Point Dead Band                                     4.0                  deg F     
	Dew Point Over Temp Threshold                           15.0                 deg C     
	Dew Point Proportional Band                             4.4                  deg C     
	Dew Point Proportional Band                             7.9                  deg F     
	Dew Point Set Point                                     48.0                 deg F     
	Dew Point Set Point                                     8.9                  deg C     
	Dew Point Under Temp Threshold                          3.9                  deg C     
	Dig Scroll Comp Discharge Over Temp - Event Ctrl        enabled                        
	Dig Scroll Comp Discharge Over Temp - Event Ctrl        enabled                        
	Dig Scroll Comp Discharge Over Temp - Event Type        Alarm                          
	Dig Scroll Comp Discharge Over Temp - Event Type        Alarm                          
	Dig Scroll Comp Discharge Temp                          Unavailable          deg C     
	Dig Scroll Comp Discharge Temp                          Unavailable          deg C     
	Dig Scroll Comp Discharge Temp                          Unavailable          deg F     
	Dig Scroll Comp Discharge Temp                          Unavailable          deg F     
	Electric Reheat State                                   off                            
	Electric Reheater Hours                                 0                    hr        
	Electric Reheater Hours                                 0                    hr        
	Electric Reheater Hours                                 0                    hr        
	Electric Reheater Hours Threshold                       0                    hr        
	Electric Reheater Hours Threshold                       0                    hr        
	Electric Reheater Hours Threshold                       0                    hr        
	Energy Consumption                                      Unavailable          kWH       
	Ext Air Sensor A Event Control                          disabled                       
	Ext Air Sensor A High Humidity - Event Control          disabled                       
	Ext Air Sensor A High Humidity - Event Type             Warning                        
	Ext Air Sensor A Humidity                               Unavailable          % RH      
	Ext Air Sensor A Low Humidity - Event Control           disabled                       
	Ext Air Sensor A Low Humidity - Event Type              Alarm                          
	Ext Air Sensor A Over Temp - Event Control              disabled                       
	Ext Air Sensor A Over Temp - Event Type                 Warning                        
	Ext Air Sensor A Temperature                            Unavailable          deg C     
	Ext Air Sensor A Temperature                            Unavailable          deg F     
	Ext Air Sensor A Under Temp - Event Control             disabled                       
	Ext Air Sensor A Under Temp - Event Type                Alarm                          
	Ext Air Sensor B Humidity                               23.3                 % RH      
	Ext Air Sensor B Temperature                            14.3                 deg C     
	Ext Air Sensor B Temperature                            57.7                 deg F     
	Ext Air Sensor C Humidity                               Unavailable          % RH      
	Ext Air Sensor C Temperature                            Unavailable          deg C     
	Ext Air Sensor C Temperature                            Unavailable          deg F     
	Ext Compressor Lockout - Event Control                  enabled                        
	Ext Compressor Lockout - Event Type                     Warning                        
	Ext Condenser Pump High Water - Event Control           enabled                        
	Ext Condenser Pump High Water - Event Type              Warning                        
	Ext Free Cooling Lockout - Event Control                enabled                        
	Ext Free Cooling Lockout - Event Type                   Warning                        
	Ext Humidifier Lockout - Event Control                  enabled                        
	Ext Humidifier Lockout - Event Type                     Warning                        
	Ext Loss of Flow - Event Control                        enabled                        
	Ext Loss of Flow - Event Type                           Alarm                          
	Ext Over Temperature - Event Control                    enabled                        
	Ext Over Temperature - Event Type                       Alarm                          
	Ext Reheat Lockout - Event Control                      enabled                        
	Ext Reheat Lockout - Event Type                         Warning                        
	Fan Control Mode                                        Auto                           
	Fan Hours                                               8498                 hr        
	Fan Hours Exceeded - Event Control                      enabled                        
	Fan Hours Exceeded - Event Type                         Warning                        
	Fan Hours Threshold                                     0                    hr        
	Fan Issue - Event Control                               enabled                        
	Fan Speed                                               53                   %         
	Fan Speed Delta Control                                 0                              
	Fan Speed Maximum Set Point                             80                   %         
	Fan State                                               on                             
	Fluid Flow Rate                                         -32768               m3/h      
	Fluid Flow Rate                                         -32768               m3/h      
	Free Cooling Fluid Temperature                          Unavailable          deg C     
	Free Cooling Fluid Temperature                          Unavailable          deg F     
	Free Cooling Internal Control Mode                      Disabled                       
	Free Cooling Internal Temperature Delta                 4.5                  deg C     
	Free Cooling Internal Temperature Delta                 8.1                  deg F     
	Free Cooling State                                      off                            
	Free Cooling Status                                     No Support                     
	Free Cooling Valve Hours                                0                    hr        
	Free Cooling Valve Hours Threshold                      0                    hr        
	Free Cooling Valve Open Position                        0                    %         
	Heating Fan Speed Min Set Point                         50                   %         
	High Power Shutdown - Event Control                     enabled                        
	High Power Shutdown - Event Type                        Warning                        
	High Return Air Temperature Threshold                   34.0                 deg C     
	High Return Air Temperature Threshold                   93.2                 deg F     
	High Return Humidity - Event Control                    enabled                        
	High Return Humidity - Event Type                       Warning                        
	High Return Humidity Threshold                          99.0                 % RH      
	Hot Water / Hot Gas State                               off                            
	Hot Water / Hot Gas Valve Hours                         0                    hr        
	Hot Water / Hot Gas Valve Hours Threshold               0                    hr        
	Hot Water / Hot Gas Valve Open Position                 0                    %         
	Humidification Fan Speed Min Set Point                  75                   %         
	Humidifier Hours                                        0                    hr        
	Humidifier Hours Threshold                              0                    hr        
	Humidifier Issue - Event Control                        enabled                        
	Humidifier Issue - Event Type                           Alarm                          
	Humidifier State                                        off                            
	Humidifier Utilization                                  0                    %         
	Humidity Control Integration Time                       0                    min       
	Humidity Control Type                                   Relative                       
	Humidity Dead Band                                      0.0                  % RH      
	Humidity Proportional Band                              10                   % RH      
	Humidity Set Point                                      50                   % RH      
	Infrared Humidifier Flush Rate                          150                  %         
	Instantaneous Power                                     Unavailable          W         
	Low Return Air Temperature Threshold                    14.0                 deg C     
	Low Return Air Temperature Threshold                    57.2                 deg F     
	Low Return Humidity - Event Control                     enabled                        
	Low Return Humidity - Event Type                        Warning                        
	Low Return Humidity Threshold                           1.0                  % RH      
	MAN-OFF-AUTO Switch                                     2                              
	Main Fan Overload - Event Control                       enabled                        
	Main Fan Overload - Event Type                          Alarm                          
	Main Valve                                              0                              
	Maintenance Ramp                                        0                    %         
	Maintenance Tracking State                              off                            
	Master Unit Communication Lost - Event Control          enabled                        
	Master Unit Communication Lost - Event Type             Warning                        
	Minimum Chilled Water Temp Set Point                    44.6                 deg F     
	Minimum Chilled Water Temp Set Point                    7.0                  deg C     
	Minimum Chilled Water Temp Set Point Enable             disabled                       
	Outside Air Temperature                                 Unavailable          deg C     
	Outside Air Temperature                                 Unavailable          deg F     
	Power Meter Status                                      0                              
	Raw Auxiliary Air Temperature                           Unavailable          deg C     
	Raw Auxiliary Air Temperature                           Unavailable          deg F     
	Reheat Utilization                                      0                    %         
	Return Air Over Temp - Event Control                    enabled                        
	Return Air Over Temp - Event Type                       Warning                        
	Return Air Sensor Event Control                         enabled                        
	Return Air Temperature                                  27.4                 deg C     
	Return Air Temperature                                  81.3                 deg F     
	Return Air Under Temp - Event Control                   enabled                        
	Return Air Under Temp - Event Type                      Warning                        
	Return Damper Status                                    open                           
	Return Dew Point                                        47.1                 deg F     
	Return Dew Point                                        8.4                  deg C     
	Return Humidity                                         30.4                 % RH      
	Server Class                                            AIR                            
	Shutdown - Loss Of Power - Event Control                disabled                       
	Shutdown - Loss Of Power - Event Type                   Warning                        
	Smoke Detected - Event Control                          enabled                        
	Smoke Detected - Event Type                             Alarm                          
	Static Pressure Set Point                               0.10                 inWC      
	Static Pressure Set Point                               25                   Pa        
	Super Saver Call For Cooling                            0                    %         
	Supply Air Temperature                                  20.0                 deg C     
	Supply Air Temperature                                  68.0                 deg F     
	Supply Air Temperature Sensor Control                   Temp Only                      
	Supply Air Temperature Set Point                        20.0                 deg C     
	Supply Air Temperature Set Point                        68.0                 deg F     
	System Date and Time                                    2024-02-22 21:17:47            
	System Input RMS A-B                                    Unavailable          VAC       
	System Input RMS A-N                                    Unavailable          VAC       
	System Input RMS B-C                                    Unavailable          VAC       
	System Input RMS B-N                                    Unavailable          VAC       
	System Input RMS C-A                                    Unavailable          VAC       
	System Input RMS C-N                                    Unavailable          VAC       
	System Input RMS Current Phase A                        Unavailable          A AC      
	System Input RMS Current Phase B                        Unavailable          A AC      
	System Input RMS Current Phase C                        Unavailable          A AC      
	System Model Number                                     PDX-PCW                        
	System Name                                             UNIT                           
	System On/Off Control                                   on                             
	System Static Pressure                                  0                    Pa        
	System Static Pressure                                  0.00                 inWC      
	System Status                                           Normal Operation               
	Today's High Air Temperature                            27.7                 deg C     
	Today's High Air Temperature                            81.9                 deg F     
	Today's High Air Temperature Time                       11:28:46                       
	Today's High Humidity                                   30.6                 % RH      
	Today's High Humidity Time                              12:58:05                       
	Today's Low Air Temperature                             27.3                 deg C     
	Today's Low Air Temperature                             81.1                 deg F     
	Today's Low Air Temperature Time                        00:00:06                       
	Today's Low Humidity                                    28.5                 % RH      
	Today's Low Humidity Time                               06:45:24                       
	Underfloor Static Pressure Control Enable               disabled                       
	Unit Control Mode                                       Internal (Auto)                
	Unit Off Reason                                         None                           
	Unit Operating State                                    on                             
	Water Under Floor - Event Control                       enabled                        
	Water Under Floor - Event Type                          Alarm                          

