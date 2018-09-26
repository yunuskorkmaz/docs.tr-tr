---
title: 'Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: d14fd1434cb87dc62babeabb79cb780e568aacb7
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204748"
---
# <a name="how-to-configure-com-service-settings"></a>Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma
Bir uygulama arabirimi eklendi veya kaldırıldı COM + hizmet yapılandırması aracını kullanarak, Web hizmeti yapılandırması uygulamanın yapılandırma dosyası içinde güncelleştirilir. COM + barındırılan modunda Application.config dosya uygulamanın kök dizinine yerleştirilir (%PROGRAMFILES%\ComPlus uygulamaları\\{AppID} varsayılan değerdir). Ya da Web barındırılan modları, Web.config dosyasının vroot belirtilen dizine yerleştirilir.  
  
> [!NOTE]
>  İleti imzalama bir istemci ve sunucu arasındaki mesajların kurcalanmaya karşı korumak için kullanılmalıdır. Ayrıca, ileti veya Aktarım katmanı şifreleme bilgi ifşaatına karşı bir istemci ve sunucu arasında iletileri karşı korumak için kullanılmalıdır. Windows Communication Foundation (WCF) Hizmetleri gibi ile azaltma eş zamanlı çağrılar, bağlantılar, örnekler ve bekleyen işlemler sınırlamak için kullanmanız gerekir. Bu durum, kaynakların aşırı kullanımını önlemeye yardımcı olur. Azaltma davranışı, hizmet yapılandırma dosyası ayarlarının ile belirtilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki arabirimi uygulayan bir bileşeni göz önünde bulundurun:  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 Bileşen bir Web hizmeti olarak kullanıma sunulan, karşılık gelen hizmet sözleşmesi kullanıma sunulmuştur ve istemciler için uyması gereken aşağıdaki gibidir:  
  
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
>  IID ilk ad alanının sözleşmenin parçası oluşturur.  
  
 Bu hizmet kullanan istemci uygulamalar uygulama yapılandırmasında belirtilen ile uyumlu bir bağlamayı kullanarak yanı sıra, bu sözleşme uygun gerekecektir.  
  
 Aşağıdaki kod örneği, varsayılan yapılandırma dosyası gösterir. Bir Windows Communication Foundation (WCF) Web hizmeti olduğundan, bu standart hizmet modeli yapılandırma şemasına uyan ve diğer WCF hizmetleri yapılandırma dosyaları aynı şekilde düzenlenebilir.  
  
 Tipik değişiklikleri aşağıdakileri içerir:  
  
- Uç nokta adresini varsayılan ComponentName/ApplicationName/InterfaceName formdan daha kullanışlı bir forma değiştiriliyor.  
  
- Hizmet varsayılan ad alanını değiştirme `http://tempuri.org/InterfaceID` daha uygun bir form için form.  
  
- Farklı bir aktarım bağlama kullanılacak uç nokta değiştiriliyor.  
  
     COM +-adlandırılmış taşıma barındırılan durumda, varsayılan olarak kullanılır, ancak bunun yerine bir makine kapalı aktarım TCP gibi kullanılabilir.  
  
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
