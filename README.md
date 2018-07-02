# RFM69H SX1231

Add RFM69_interruptHandler(); in interrupt handler PIN DIO0 
<br/>

Добавить RFM69_interruptHandler(); в обработчик прерываний, пин внешнего прерывания соеденить с пином DIO0 RFM69H
<br/>

Протестировано на STM32F103
<br/>


##### example

if(RFM69_receiveDone())<br/>
	{<br/>
        pdata = RFM69_receive(&len);<br/>
          for (int i = 0; i < len; i++)<br/>
            datarecive[i]=((char)pdata[i]);<br/>
	}<br/>
		
		
<br/>
			
