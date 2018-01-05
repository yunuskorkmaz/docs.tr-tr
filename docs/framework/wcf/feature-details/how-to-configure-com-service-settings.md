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
ms.workload: dotnet
ms.openlocfilehash: 1bdbdbae857685ddb447843fd704896de018b1c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-com-service-settings"></a><span data-ttu-id="fcc13-102">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fcc13-102">How to: Configure COM+ Service Settings</span></span>
<span data-ttu-id="fcc13-103">Bir uygulama arabirimi eklendiğinde veya COM + hizmet yapılandırması aracını kullanarak kaldırıldığında, Web hizmeti yapılandırması uygulamanın yapılandırma dosyasında güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fcc13-103">When an application interface is added or removed by using the COM+ Service Configuration tool, the Web service configuration is updated within the application's configuration file.</span></span> <span data-ttu-id="fcc13-104">COM + barındırılan modunda uygulama kök dizininde Application.config dosya yerleştirilir (%PROGRAMFILES%\ComPlus uygulamaları\\{AppID} varsayılandır).</span><span class="sxs-lookup"><span data-stu-id="fcc13-104">In the COM+ hosted mode, the Application.config file is placed in the Application Root Directory (%PROGRAMFILES%\ComPlus Applications\\{appid} is the default).</span></span> <span data-ttu-id="fcc13-105">Ya da Web barındırılan modları, Web.config dosyasında belirtilen vroot dizininde yer alır.</span><span class="sxs-lookup"><span data-stu-id="fcc13-105">In either of the Web-hosted modes, the Web.config file is placed in the specified vroot directory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcc13-106">İleti imzalama iletilerinin bir istemci ve sunucu arasındaki kurcalanmaya karşı korumak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fcc13-106">Message signing should be used to protect against tampering of messages between a client and a server.</span></span> <span data-ttu-id="fcc13-107">Ayrıca, ileti veya Aktarım katmanı şifreleme iletilerden bir istemci ve sunucu arasında bilginin açığa çıkmasına karşı korumak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fcc13-107">Also, message or transport layer encryption should be used to protect against information disclosure from messages between a client and a server.</span></span> <span data-ttu-id="fcc13-108">İle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri için kullanmanız gereken azaltma eşzamanlı çağrıları, bağlantıları, örnekler ve bekleyen işlemler sayısını sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="fcc13-108">As with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services, you should use throttling to limit the number of concurrent calls, connections, instances, and pending operations.</span></span> <span data-ttu-id="fcc13-109">Bu kaynakların fazla tüketimi önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="fcc13-109">This helps prevent over-consumption of resources.</span></span> <span data-ttu-id="fcc13-110">Davranış azaltma hizmet yapılandırma dosyası ayarları aracılığıyla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="fcc13-110">Throttling behavior is specified through service configuration file settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcc13-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="fcc13-111">Example</span></span>  
 <span data-ttu-id="fcc13-112">Aşağıdaki arabirimini uygulayan bir bileşeni göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="fcc13-112">Consider a component that implements the following interface:</span></span>  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 <span data-ttu-id="fcc13-113">Bileşen bir Web hizmeti olarak açılırsa, açıksa ve istemciler için uyması gereken karşılık gelen bir hizmet sözleşmesini aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fcc13-113">If the component is exposed as a Web service, the corresponding service contract that is exposed, and that clients would need to conform to, is as follows:</span></span>  
  
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
>  <span data-ttu-id="fcc13-114">IID sözleşmesi için ilk ad alanının parçası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fcc13-114">IID forms part of the initial namespace for the contract.</span></span>  
  
 <span data-ttu-id="fcc13-115">Bu hizmeti kullanan istemci uygulamaları, uygulama yapılandırmasında belirtilen bir ile uyumlu bir bağlamayı kullanarak yanı sıra bu sözleşme, uygun olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fcc13-115">Client applications that use this service would need to conform to this contract, along with using a binding that is compatible with the one specified in the application configuration.</span></span>  
  
 <span data-ttu-id="fcc13-116">Aşağıdaki kod örneği, varsayılan yapılandırma dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="fcc13-116">The following code example shows a default configuration file.</span></span> <span data-ttu-id="fcc13-117">Olan bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web hizmeti, bu standart hizmet modeli yapılandırma şemasıyla uyumlu ve aynı şekilde diğer düzenlenebilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yapılandırma dosyalarını Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="fcc13-117">Being a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web service, this conforms to the standard service model configuration schema and can be edited in the same way as other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services configuration files.</span></span>  
  
 <span data-ttu-id="fcc13-118">Tipik değişiklikler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="fcc13-118">Typical modifications would include:</span></span>  
  
-   <span data-ttu-id="fcc13-119">Uç nokta adresi varsayılan ComponentName/ApplicationName/InterfaceName formundan daha kullanışlı bir forma değiştirme.</span><span class="sxs-lookup"><span data-stu-id="fcc13-119">Changing the endpoint address from the default ApplicationName/ComponentName/InterfaceName form to a more usable form.</span></span>  
  
-   <span data-ttu-id="fcc13-120">Varsayılan "http://tempuri.org/InterfaceID" form hizmetinden daha ilgili bir form için ad alanı değiştirme.</span><span class="sxs-lookup"><span data-stu-id="fcc13-120">Modifying the namespace of the service from the default "http://tempuri.org/InterfaceID" form to a more relevant form.</span></span>  
  
-   <span data-ttu-id="fcc13-121">Farklı bir aktarım bağlama kullanmak için uç nokta değiştirme.</span><span class="sxs-lookup"><span data-stu-id="fcc13-121">Changing the endpoint to use a different transport binding.</span></span>  
  
     <span data-ttu-id="fcc13-122">COM +-barındırılan durumda, adlandırılmış kanallar taşıma, varsayılan olarak kullanılır, ancak bunun yerine bir makine kapalı taşıması TCP gibi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fcc13-122">In the COM+-hosted case, the named pipes transport is used by default, but an off-machine transport like TCP can be used instead.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fcc13-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fcc13-123">See Also</span></span>  
 [<span data-ttu-id="fcc13-124">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="fcc13-124">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
