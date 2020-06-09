---
title: Özel Bağlama Taşıma ve Kodlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 3b3a0f1b52afce495ca41a426ebc9e57314d8254
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592534"
---
# <a name="custom-binding-transport-and-encoding"></a>Özel Bağlama Taşıma ve Kodlama
Özel bağlama, farklı bağlama öğelerinin sıralı bir listesi tarafından tanımlanır. Bu örnek, çeşitli taşıma ve ileti kodlama öğeleriyle özel bağlamanın nasıl yapılandırılacağını gösterir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bu örnek, [kendi kendine ana bilgisayar](self-host.md)tabanlıdır ve özel BAĞLAMALARLA http, TCP ve NamedPipe aktarımlarını desteklemek üzere üç uç nokta yapılandırmak üzere değiştirilmiştir. İstemci yapılandırması benzer şekilde değiştirilmiştir ve istemci kodu üç uç noktanın her biriyle iletişim kuracak şekilde değiştirilmiştir.  
  
 Örnek, belirli bir aktarımı ve ileti kodlamasını destekleyen bir özel bağlamanın nasıl yapılandırılacağını gösterir. Bu, bir taşıma ve öğe için ileti kodlaması yapılandırılarak gerçekleştirilir `binding` . Bağlama öğelerinin sıralaması, her biri kanal yığınındaki bir katmanı temsil ettiğinden (bkz. [Özel Bağlamalar](../extending/custom-bindings.md)) özel bir bağlama tanımlamak açısından önemlidir. Bu örnek üç özel bağlamayı yapılandırır: metin kodlamalı HTTP taşıması, metin kodlamalı bir TCP taşıması ve ikili kodlamalı bir NamedPipe taşıması.  
  
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
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsolu penceresinde görüntülenir. İstemci, birinci HTTP, ardından TCP ve son olarak NamedPipe 'a erişerek üç uç noktanın her biriyle iletişim kurar. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.  
  
 `namedPipeTransport`Bağlama, makineden makineye işlemleri desteklemiyor. Yalnızca aynı makine üzerindeki iletişim için kullanılır. Bu nedenle, örneği bir çapraz makine senaryosunda çalıştırırken, istemci kod dosyasında aşağıdaki satırları açıklama olarak kodlayın:  
  
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
> Bu örneğe yönelik yapılandırmayı yeniden oluşturmak için Svcutil. exe ' yi kullanırsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinizden emin olun.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C#, C++ veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
