---
title: Özel Bağlama Taşıma ve Kodlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 47841b23dc3259aeb233192f396397745864d7ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145170"
---
# <a name="custom-binding-transport-and-encoding"></a>Özel Bağlama Taşıma ve Kodlama
Özel bir bağlama, ayrık bağlama öğelerinin sıralı bir listesi yle tanımlanır. Bu örnek, çeşitli aktarım ve ileti kodlama öğeleriyle özel bir bağlamanın nasıl yapılandırılabildiğini gösterir.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bu örnek [Self-Host'a](../../../../docs/framework/wcf/samples/self-host.md)dayanır ve http, TCP ve NamedPipe aktarımlarını özel bağlamalarla desteklemek için üç uç noktayı yapılandırmak üzere değiştirilmiştir. İstemci yapılandırması benzer şekilde değiştirildi ve istemci kodu üç uç noktanın her biriyle iletişim kurmak için değiştirildi.  
  
 Örnek, belirli bir aktarım ve ileti kodlamasını destekleyen özel bir bağlamanın nasıl yapılandırılabildiğini gösterir. Bu, `binding` öğe için bir aktarım ve ileti kodlaması yapılandırılarak gerçekleştirilir. Bağlama öğelerinin sıralanması, özel bir bağlama tanımlamada önemlidir, çünkü her biri kanal yığınındaki bir katmanı temsil eder (bkz. [Özel Bağlamalar).](../../../../docs/framework/wcf/extending/custom-bindings.md) Bu örnek üç özel bağlamayı yapılandırır: metin kodlaması içeren bir HTTP aktarım, metin kodlaması içeren bir TCP aktarım ve ikili kodlama içeren bir NamedPipe aktarım.  
  
 Hizmet yapılandırması özel bağlamaları aşağıdaki gibi tanımlar:  
  
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
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir. İstemci üç uç noktanın her biriyle iletişim kurar ve önce HTTP, sonra TCP ve son olarak NamedPipe'a erişir. Hizmeti ve istemciyi kapatmak için her konsol penceresinde ENTER tuşuna basın.  
  
 `namedPipeTransport` Bağlama, makineden makineye işlemleri desteklemez. Yalnızca aynı makinede iletişim için kullanılır. Bu nedenle, örneği makineler arası bir senaryoda çalıştırırken, istemci kodu dosyasında aşağıdaki satırları yorumlayın:  
  
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
> Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinden emin olun.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C#, C++veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation Örneklerini Oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
