---
title: 'Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: 3fb4b31038845d223248e72d32b3e7413f2aef63
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597182"
---
# <a name="how-to-configure-com-service-settings"></a>Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma
Bir uygulama arabirimi COM+ hizmet yapılandırma aracı kullanılarak eklendiğinde veya kaldırıldığında, Web hizmeti yapılandırması uygulamanın yapılandırma dosyası içinde güncelleştirilir. COM+ barındırılan modunda, Application. config dosyası uygulama kök dizinine yerleştirilir (%PROGRAMFILES%\ComPlus uygulamaları \\ {AppID} varsayılandır). Web 'de barındırılan modlardan birinde, Web. config dosyası belirtilen vroot dizinine yerleştirilir.  
  
> [!NOTE]
> İleti imzalama, istemci ve sunucu arasında ileti izinsiz değişikliklere karşı korunmak için kullanılmalıdır. Ayrıca, bir istemci ile sunucu arasındaki iletilerden bilgilerin açığa çıkmasına karşı korumak için ileti veya Aktarım katmanı şifrelemesi kullanılmalıdır. Windows Communication Foundation (WCF) hizmetlerinde olduğu gibi, eşzamanlı çağrıların sayısını, bağlantıları, örnekleri ve bekleyen işlemleri kısıtlamak için azaltmayı kullanmanız gerekir. Bu, kaynakların aşırı kullanımını önlemeye yardımcı olur. Daraltma davranışı, hizmet yapılandırma dosyası ayarları aracılığıyla belirtilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki arabirimi uygulayan bir bileşeni göz önünde bulundurun:  
  
```csharp
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 Bileşen bir Web hizmeti olarak sunuluyorsa, sunulan ilgili hizmet sözleşmesi ve istemcilerin uyması gereken, aşağıdaki gibidir:  
  
```csharp
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
> IID, sözleşmenin ilk ad alanının bir parçasını oluşturur.  
  
 Bu hizmeti kullanan istemci uygulamalarının, uygulama yapılandırmasında belirtilen bir bağlama kullanımıyla birlikte bu sözleşmeyle uyumlu olması gerekir.  
  
 Aşağıdaki kod örneği, varsayılan bir yapılandırma dosyasını gösterir. Windows Communication Foundation (WCF) Web hizmeti olan bu, standart hizmet modeli yapılandırma şemasına uyar ve diğer WCF Hizmetleri yapılandırma dosyalarıyla aynı şekilde düzenlenebilir.  
  
 Normal değişiklikler şunları içerir:  
  
- Varsayılan ApplicationName/ComponentName/InterfaceName formundaki bitiş noktası adresini daha kullanılabilir bir biçime değiştirme.  
  
- Hizmetin ad alanını varsayılan `http://tempuri.org/InterfaceID` formdan daha ilgili bir biçime değiştirme.  
  
- Uç nokta, farklı bir aktarım bağlamayı kullanacak şekilde değiştiriliyor.  
  
     COM+ barındırılan durumunda, adlandırılmış yöneltme taşıması varsayılan olarak kullanılır, ancak bunun yerine TCP gibi bir makine dışı taşıma kullanılabilir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM+ uygulamalarıyla tümleştirme](integrating-with-com-plus-applications.md)
