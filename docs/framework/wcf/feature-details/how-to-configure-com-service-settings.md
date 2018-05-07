---
title: 'Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: 43964331f6728db0f094eaceb63e2c306d2dd3ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-com-service-settings"></a>Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma
Bir uygulama arabirimi eklendiğinde veya COM + hizmet yapılandırması aracını kullanarak kaldırıldığında, Web hizmeti yapılandırması uygulamanın yapılandırma dosyasında güncelleştirilir. COM + barındırılan modunda uygulama kök dizininde Application.config dosya yerleştirilir (%PROGRAMFILES%\ComPlus uygulamaları\\{AppID} varsayılandır). Ya da Web barındırılan modları, Web.config dosyasında belirtilen vroot dizininde yer alır.  
  
> [!NOTE]
>  İleti imzalama iletilerinin bir istemci ve sunucu arasındaki kurcalanmaya karşı korumak için kullanılmalıdır. Ayrıca, ileti veya Aktarım katmanı şifreleme iletilerden bir istemci ve sunucu arasında bilginin açığa çıkmasına karşı korumak için kullanılmalıdır. Windows Communication Foundation (WCF) hizmetlerini gibi ile azaltma eşzamanlı çağrıları, bağlantıları, örnekler ve bekleyen işlemler sınırlamak için kullanmanız gerekir. Bu kaynakların fazla tüketimi önlemeye yardımcı olur. Davranış azaltma hizmet yapılandırma dosyası ayarları aracılığıyla belirtilir.  
  
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
  
 Aşağıdaki kod örneği, varsayılan yapılandırma dosyası gösterir. Bir Windows Communication Foundation (WCF) Web hizmeti, bu standart hizmet modeli yapılandırma şemasıyla uyumlu ve diğer WCF hizmetleri yapılandırma dosyaları aynı şekilde düzenlenebilir.  
  
 Tipik değişiklikler aşağıdakileri içerir:  
  
-   Uç nokta adresi varsayılan ComponentName/ApplicationName/InterfaceName formundan daha kullanışlı bir forma değiştirme.  
  
-   Varsayılan hizmet ad alanı değiştirme "http://tempuri.org/InterfaceID" daha ilgili bir form için form.  
  
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
 [COM+ Uygulamaları ile Tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
