# RFM69H SX1231

Add RFM69_interruptHandler(); in interrupt handler PIN DIO0 
<br/>

Добавить RFM69_interruptHandler(); в обработчик прерываний, пин внешнего прерывания соеденить с пином DIO0 RFM69H
<br/>

Протестировано на STM32F103
<br/>


##### example receive
```
#define ENCRYPTKEY "key" //characters
#define NODEID 10 //0-255 
#define NETWORKID 0 // 0-255


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

#define ENCRYPTKEY "key" // 14 characters
#define NODEID 11 //0-255 
#define NETWORKID 0 // 0-255

typedef struct {
	uint8_t		data1; 
	uint8_t		data2; 
	uint16_t	data3;   
	uint16_t	data4;
	uint32_t	data5;
	uint32_t	data6;
} Payload; // data sizeof max 60 byte 

|        |            |

RFM69_initialize(RF69_433MHZ,NODEID,NETWORKID);
RFM69_encrypt(ENCRYPTKEY);
RFM69_promiscuous(true);

|        |            |

Payload theData;

|        |            |

RFM69_send(GATEWAYID, (const void*)(&theData), sizeof(theData),true);

````			
