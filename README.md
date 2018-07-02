# RFM69H SX1231

Add RFM69_interruptHandler(); in interrupt handler PIN DIO0 
<br/>

Добавить RFM69_interruptHandler(); в обработчик прерываний, пин внешнего прерывания соеденить с пином DIO0 RFM69H
<br/>

Протестировано на STM32F103
<br/>


##### example recive
```
uint8_t* pdata;
int8_t datarecive[61];

|         |           |

RFM69_initialize(RF69_433MHZ,NODEID,NETWORKID);
RFM69_encrypt(ENCRYPTKEY);
RFM69_promiscuous(true);

|         |           |

if(RFM69_receiveDone())
	{
        pdata = RFM69_receive(&len);
          for (int i = 0; i < len; i++)
            datarecive[i]=((char)pdata[i]);
	}
```		
		
<br/>


##### example transmit
```
typedef struct {
	uint16_t        data1; 
	uint16_t		data2; 
	uint16_t       	data3;   
	uint16_t 		data4;
	uint16_t		data5;
} Payload;

|        |            |

RFM69_initialize(RF69_433MHZ,NODEID,NETWORKID);
RFM69_encrypt(ENCRYPTKEY);
RFM69_promiscuous(true);

|        |            |

Payload theData;

|        |            |

RFM69_send(GATEWAYID, (const void*)(&theData), sizeof(theData),true);

````			
