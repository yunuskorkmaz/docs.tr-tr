---
title: "Özel Bağlama Taşıma ve Kodlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e4e26e332cc67fc462c703c502594a8a36758501
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-binding-transport-and-encoding"></a>Özel Bağlama Taşıma ve Kodlama
Özel bağlama ayrık bağlama öğeleri sıralı bir listesi tanımlanır. Bu örnek özel bağlama çeşitli aktarım ve öğeleri kodlama ileti ile nasıl yapılandırılacağını gösterir.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnek dayanır [kendini barındırma](../../../../docs/framework/wcf/samples/self-host.md)ve HTTP, TCP ve NamedPipe taşımaları özel bağlamalarla desteklemek için üç bitiş noktalarını yapılandırmak için değiştirilebilir. İstemci yapılandırması benzer şekilde değiştirilmiş ve her üç uç noktalar ile iletişim kurmak için istemci kodu değiştirildi.  
  
 Örnek bir nasıl gösterir, belirli bir destekleyen özel bağlama ve ileti kodlama yapılandırmak için. Bu bir taşıma ve kodlama için bir ileti yapılandırarak gerçekleştirilir `binding` öğesi. Bağlama öğeleri sıralama her bir katman kanal yığınında olabilmesinden dolayı bir özel bağlama, tanımlamak önemlidir (bkz [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)). Bu örnek üç özel bağlamalar yapılandırır: metin kodlaması ile bir HTTP taşıması, metin kodlama ile TCP taşıma ve bir ikili kodlama ile NamedPipe taşıma.  
  
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
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol penceresinde görüntülenir. İstemci, her üç uç noktaları ile ilk HTTP sonra TCP ve son olarak NamedPipe erişme iletişim kurar. Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın.  
  
 `namedPipeTransport` Bağlama makine makine işlemlerini desteklemiyor. Yalnızca aynı makine üzerindeki iletişim için kullanılır. Bu nedenle, istemci kodu dosyası aşağıdaki satırları çıkışı örnek makineler arası senaryoda çalıştırırken, Açıklama:  
  
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
>  Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanırsanız, istemci kodu eşleşecek şekilde istemci yapılandırmasında uç nokta adı değiştirdiğinizden emin olun.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  C#, C++, Visual Basic .NET edition çözümü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a>Ayrıca Bkz.
