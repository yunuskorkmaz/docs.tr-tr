---
title: "Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa497567c5cf380d7764499991ad9e7e95a5cbe0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-com-service-settings"></a>Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma
Bir uygulama arabirimi eklendiğinde veya COM + hizmet yapılandırması aracını kullanarak kaldırıldığında, Web hizmeti yapılandırması uygulamanın yapılandırma dosyasında güncelleştirilir. COM + barındırılan modunda uygulama kök dizininde Application.config dosya yerleştirilir (%PROGRAMFILES%\ComPlus uygulamaları\\{AppID} varsayılandır). Ya da Web barındırılan modları, Web.config dosyasında belirtilen vroot dizininde yer alır.  
  
> [!NOTE]
>  İleti imzalama iletilerinin bir istemci ve sunucu arasındaki kurcalanmaya karşı korumak için kullanılmalıdır. Ayrıca, ileti veya Aktarım katmanı şifreleme iletilerden bir istemci ve sunucu arasında bilginin açığa çıkmasına karşı korumak için kullanılmalıdır. İle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri için kullanmanız gereken azaltma eşzamanlı çağrıları, bağlantıları, örnekler ve bekleyen işlemler sayısını sınırlandırın. Bu kaynakların fazla tüketimi önlemeye yardımcı olur. Davranış azaltma hizmet yapılandırma dosyası ayarları aracılığıyla belirtilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki arabirimini uygulayan bir bileşeni göz önünde bulundurun:  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 Bileşen bir Web hizmeti olarak açılırsa, açıksa ve istemciler için uyması gereken karşılık gelen bir hizmet sözleşmesini aşağıdaki gibidir:  
  
```  
[ServiceContract(Session = true,  
Namespace = "http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7",  
Name = "IFinances")]  
public interface IFinancesContract : IDisposable  
{  
    [OperationContract]  
    string Debit(string accountNo, double amount);  
    [OperationContract]  
    string Credit(string accountNo, double amount);  
}  
```  
  
> [!NOTE]
>  IID sözleşmesi için ilk ad alanının parçası oluşturur.  
  
 Bu hizmeti kullanan istemci uygulamaları, uygulama yapılandırmasında belirtilen bir ile uyumlu bir bağlamayı kullanarak yanı sıra bu sözleşme, uygun olması gerekir.  
  
 Aşağıdaki kod örneği, varsayılan yapılandırma dosyası gösterir. Olan bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web hizmeti, bu standart hizmet modeli yapılandırma şemasıyla uyumlu ve aynı şekilde diğer düzenlenebilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yapılandırma dosyalarını Hizmetleri.  
  
 Tipik değişiklikler aşağıdakileri içerir:  
  
-   Uç nokta adresi varsayılan ComponentName/ApplicationName/InterfaceName formundan daha kullanışlı bir forma değiştirme.  
  
-   Varsayılan "http://tempuri.org/InterfaceID" form hizmetinden daha ilgili bir form için ad alanı değiştirme.  
  
-   Farklı bir aktarım bağlama kullanmak için uç nokta değiştirme.  
  
     COM +-barındırılan durumda, adlandırılmış kanallar taşıma, varsayılan olarak kullanılır, ancak bunun yerine bir makine kapalı taşıması TCP gibi kullanılabilir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="comNonTransactionalBinding" />  
                <binding name="comTransactionalBinding" transactionFlow="true" />  
            </netNamedPipeBinding>  
        </bindings>  
        <comContracts>  
            <comContract contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"  
                name="IFinances" namespace="http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7"  
                requiresSession="true">  
                <exposedMethods>  
                    <add exposedMethod="Debit" />  
                    <add exposedMethod="Credit" />  
                </exposedMethods>  
            </comContract>  
        </comContracts>  
        <services>  
            <service name="{DCDB24CC-0B19-4534-95CD-FBBFF4D67DD9},{C942B840-AD54-4A44-B5F7-928130980AB9}">  
                <endpoint address="IFinances" binding="netNamedPipeBinding" bindingConfiguration="comNonTransactionalBinding"  
                    contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" />  
                <host>  
                    <baseAddresses>  
                        <add baseAddress="net.pipe://localhost/ServiceModelDocSampleApp/ServiceModelDocSample.esFinance" />  
                    </baseAddresses>  
                </host>  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM + uygulamaları ile tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
