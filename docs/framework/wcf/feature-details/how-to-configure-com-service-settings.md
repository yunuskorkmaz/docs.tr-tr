---
title: 'Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: 31096ca510c868cf43ca6ef60126c98a8832d2c5
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895118"
---
# <a name="how-to-configure-com-service-settings"></a><span data-ttu-id="77456-102">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="77456-102">How to: Configure COM+ Service Settings</span></span>
<span data-ttu-id="77456-103">Bir uygulama arabirimi COM+ hizmet yapılandırma aracı kullanılarak eklendiğinde veya kaldırıldığında, Web hizmeti yapılandırması uygulamanın yapılandırma dosyası içinde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="77456-103">When an application interface is added or removed by using the COM+ Service Configuration tool, the Web service configuration is updated within the application's configuration file.</span></span> <span data-ttu-id="77456-104">COM+ barındırılan modunda, Application. config dosyası uygulama kök dizinine yerleştirilir (%ProgramFiles%\ComPlus uygulamaları\\{AppID} varsayılandır).</span><span class="sxs-lookup"><span data-stu-id="77456-104">In the COM+ hosted mode, the Application.config file is placed in the Application Root Directory (%PROGRAMFILES%\ComPlus Applications\\{appid} is the default).</span></span> <span data-ttu-id="77456-105">Web 'de barındırılan modlardan birinde, Web. config dosyası belirtilen vroot dizinine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="77456-105">In either of the Web-hosted modes, the Web.config file is placed in the specified vroot directory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77456-106">İleti imzalama, istemci ve sunucu arasında ileti izinsiz değişikliklere karşı korunmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="77456-106">Message signing should be used to protect against tampering of messages between a client and a server.</span></span> <span data-ttu-id="77456-107">Ayrıca, bir istemci ile sunucu arasındaki iletilerden bilgilerin açığa çıkmasına karşı korumak için ileti veya Aktarım katmanı şifrelemesi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="77456-107">Also, message or transport layer encryption should be used to protect against information disclosure from messages between a client and a server.</span></span> <span data-ttu-id="77456-108">Windows Communication Foundation (WCF) hizmetlerinde olduğu gibi, eşzamanlı çağrıların sayısını, bağlantıları, örnekleri ve bekleyen işlemleri kısıtlamak için azaltmayı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="77456-108">As with Windows Communication Foundation (WCF) services, you should use throttling to limit the number of concurrent calls, connections, instances, and pending operations.</span></span> <span data-ttu-id="77456-109">Bu, kaynakların aşırı kullanımını önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="77456-109">This helps prevent over-consumption of resources.</span></span> <span data-ttu-id="77456-110">Daraltma davranışı, hizmet yapılandırma dosyası ayarları aracılığıyla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="77456-110">Throttling behavior is specified through service configuration file settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77456-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="77456-111">Example</span></span>  
 <span data-ttu-id="77456-112">Aşağıdaki arabirimi uygulayan bir bileşeni göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="77456-112">Consider a component that implements the following interface:</span></span>  
  
```csharp
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 <span data-ttu-id="77456-113">Bileşen bir Web hizmeti olarak sunuluyorsa, sunulan ilgili hizmet sözleşmesi ve istemcilerin uyması gereken, aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="77456-113">If the component is exposed as a Web service, the corresponding service contract that is exposed, and that clients would need to conform to, is as follows:</span></span>  
  
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
> <span data-ttu-id="77456-114">IID, sözleşmenin ilk ad alanının bir parçasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77456-114">IID forms part of the initial namespace for the contract.</span></span>  
  
 <span data-ttu-id="77456-115">Bu hizmeti kullanan istemci uygulamalarının, uygulama yapılandırmasında belirtilen bir bağlama kullanımıyla birlikte bu sözleşmeyle uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="77456-115">Client applications that use this service would need to conform to this contract, along with using a binding that is compatible with the one specified in the application configuration.</span></span>  
  
 <span data-ttu-id="77456-116">Aşağıdaki kod örneği, varsayılan bir yapılandırma dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="77456-116">The following code example shows a default configuration file.</span></span> <span data-ttu-id="77456-117">Windows Communication Foundation (WCF) Web hizmeti olan bu, standart hizmet modeli yapılandırma şemasına uyar ve diğer WCF Hizmetleri yapılandırma dosyalarıyla aynı şekilde düzenlenebilir.</span><span class="sxs-lookup"><span data-stu-id="77456-117">Being a Windows Communication Foundation (WCF) Web service, this conforms to the standard service model configuration schema and can be edited in the same way as other WCF services configuration files.</span></span>  
  
 <span data-ttu-id="77456-118">Normal değişiklikler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="77456-118">Typical modifications would include:</span></span>  
  
- <span data-ttu-id="77456-119">Varsayılan ApplicationName/ComponentName/InterfaceName formundaki bitiş noktası adresini daha kullanılabilir bir biçime değiştirme.</span><span class="sxs-lookup"><span data-stu-id="77456-119">Changing the endpoint address from the default ApplicationName/ComponentName/InterfaceName form to a more usable form.</span></span>  
  
- <span data-ttu-id="77456-120">Hizmetin ad alanını varsayılan `http://tempuri.org/InterfaceID` formdan daha ilgili bir biçime değiştirme.</span><span class="sxs-lookup"><span data-stu-id="77456-120">Modifying the namespace of the service from the default `http://tempuri.org/InterfaceID` form to a more relevant form.</span></span>  
  
- <span data-ttu-id="77456-121">Uç nokta, farklı bir aktarım bağlamayı kullanacak şekilde değiştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="77456-121">Changing the endpoint to use a different transport binding.</span></span>  
  
     <span data-ttu-id="77456-122">COM+ barındırılan durumunda, adlandırılmış yöneltme taşıması varsayılan olarak kullanılır, ancak bunun yerine TCP gibi bir makine dışı taşıma kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="77456-122">In the COM+-hosted case, the named pipes transport is used by default, but an off-machine transport like TCP can be used instead.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="77456-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77456-123">See also</span></span>

- [<span data-ttu-id="77456-124">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="77456-124">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
