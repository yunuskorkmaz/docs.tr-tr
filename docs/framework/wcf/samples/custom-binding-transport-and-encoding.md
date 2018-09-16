---
title: Özel Bağlama Taşıma ve Kodlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: ee15fd37390f8bf4ca3bc287f9a3dbd5f8ebd935
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668684"
---
# <a name="custom-binding-transport-and-encoding"></a>Özel Bağlama Taşıma ve Kodlama
Özel bağlama ayrık bağlama öğelerinin sıralı bir listesi tanımlanır. Bu örnek, çeşitli taşıma ve kodlama öğeleri ileti özel bağlama yapılandırma işlemi gösterilmektedir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnek dayanır [barındırma](../../../../docs/framework/wcf/samples/self-host.md)ve özel bağlamalar HTTP, TCP ve NamedPipe taşımalar desteklemek için üç uç noktalarını yapılandırma değiştirildi. İstemci yapılandırması benzer şekilde değiştirildiği ve her biri üç uç noktaları ile iletişim kurmak için istemci kodu değiştirildi.  
  
 Örnek gösterilmektedir, belirli taşıma destekleyen özel bağlama ve ileti kodlama yapılandırmak için. Bu bir taşıma ve kodlama için bir ileti yapılandırılarak gerçekleştirilir `binding` öğesi. Bağlama öğelerinin sıralama her bir katman kanal yığınında temsil ettiği için bir özel bağlamayı tanımlamak önemlidir (bkz [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)). Bu örnek, üç özel bağlamalar yapılandırır: metin kodlama ile bir HTTP aktarımı ve bir TCP taşıması metin kodlama ile ikili kodlama ile NamedPipe aktarım.  
  
 Özel bağlamalar hizmet yapılandırmasını tanımlar gibi:  
  
```xml  
<bindings>  
    <customBinding>  
        <binding name="HttpBinding" >  
            <textMessageEncoding   
                messageVersion="Soap12Addressing10"/>  
            <httpTransport />  
        </binding>  
        <binding name="TcpBinding" >  
            <textMessageEncoding />  
            <tcpTransport />  
        </binding>  
        <binding name="NamedPipeBinding" >  
            <binaryMessageEncoding />  
            <namedPipeTransport />  
        </binding>  
    </customBinding>  
</bindings>  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol penceresinde görüntülenir. İstemci, her üç uç noktaları ile ilk HTTP daha sonra TCP ve son olarak NamedPipe erişim iletişim kurar. Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.  
  
 `namedPipeTransport` Bağlama makineden makineye işlemleri desteklemez. Yalnızca aynı makinede iletişim için kullanılır. Bu nedenle, örnek bir çapraz makine senaryosunda çalıştırırken, istemci kod dosyasında aşağıdaki satırları açıklama satırı yapın:  
  
```csharp  
CalculatorClient client = new CalculatorClient("default");  
Console.WriteLine("Communicate with named pipe endpoint.");  
// Call operations.  
DoCalculations(client);  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
```vb  
Dim client As New CalculatorClient("default")  
Console.WriteLine("Communicate with named pipe endpoint.")  
' call operations  
DoCalculations(client)  
'Closing the client gracefully closes the connection and cleans up resources  
client.Close()  
```  
  
> [!NOTE]
>  Bu örnek için yapılandırmayı yeniden üretmek için Svcutil.exe kullanma, istemci kodu eşleştirilecek istemci yapılandırmasında uç noktası adını değiştirmek emin olun.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C#, C++ veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a>Ayrıca Bkz.
