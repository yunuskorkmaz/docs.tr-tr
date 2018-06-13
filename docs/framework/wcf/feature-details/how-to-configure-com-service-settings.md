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
ms.locfileid: "33490110"
---
# <a name="how-to-configure-com-service-settings"></a><span data-ttu-id="a442b-102">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a442b-102">How to: Configure COM+ Service Settings</span></span>
<span data-ttu-id="a442b-103">Bir uygulama arabirimi eklendiğinde veya COM + hizmet yapılandırması aracını kullanarak kaldırıldığında, Web hizmeti yapılandırması uygulamanın yapılandırma dosyasında güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a442b-103">When an application interface is added or removed by using the COM+ Service Configuration tool, the Web service configuration is updated within the application's configuration file.</span></span> <span data-ttu-id="a442b-104">COM + barındırılan modunda uygulama kök dizininde Application.config dosya yerleştirilir (%PROGRAMFILES%\ComPlus uygulamaları\\{AppID} varsayılandır).</span><span class="sxs-lookup"><span data-stu-id="a442b-104">In the COM+ hosted mode, the Application.config file is placed in the Application Root Directory (%PROGRAMFILES%\ComPlus Applications\\{appid} is the default).</span></span> <span data-ttu-id="a442b-105">Ya da Web barındırılan modları, Web.config dosyasında belirtilen vroot dizininde yer alır.</span><span class="sxs-lookup"><span data-stu-id="a442b-105">In either of the Web-hosted modes, the Web.config file is placed in the specified vroot directory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a442b-106">İleti imzalama iletilerinin bir istemci ve sunucu arasındaki kurcalanmaya karşı korumak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a442b-106">Message signing should be used to protect against tampering of messages between a client and a server.</span></span> <span data-ttu-id="a442b-107">Ayrıca, ileti veya Aktarım katmanı şifreleme iletilerden bir istemci ve sunucu arasında bilginin açığa çıkmasına karşı korumak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a442b-107">Also, message or transport layer encryption should be used to protect against information disclosure from messages between a client and a server.</span></span> <span data-ttu-id="a442b-108">Windows Communication Foundation (WCF) hizmetlerini gibi ile azaltma eşzamanlı çağrıları, bağlantıları, örnekler ve bekleyen işlemler sınırlamak için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a442b-108">As with Windows Communication Foundation (WCF) services, you should use throttling to limit the number of concurrent calls, connections, instances, and pending operations.</span></span> <span data-ttu-id="a442b-109">Bu kaynakların fazla tüketimi önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a442b-109">This helps prevent over-consumption of resources.</span></span> <span data-ttu-id="a442b-110">Davranış azaltma hizmet yapılandırma dosyası ayarları aracılığıyla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a442b-110">Throttling behavior is specified through service configuration file settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a442b-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="a442b-111">Example</span></span>  
 <span data-ttu-id="a442b-112">Aşağıdaki arabirimini uygulayan bir bileşeni göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a442b-112">Consider a component that implements the following interface:</span></span>  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 <span data-ttu-id="a442b-113">Bileşen bir Web hizmeti olarak açılırsa, açıksa ve istemciler için uyması gereken karşılık gelen bir hizmet sözleşmesini aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a442b-113">If the component is exposed as a Web service, the corresponding service contract that is exposed, and that clients would need to conform to, is as follows:</span></span>  
  
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
>  <span data-ttu-id="a442b-114">IID sözleşmesi için ilk ad alanının parçası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a442b-114">IID forms part of the initial namespace for the contract.</span></span>  
  
 <span data-ttu-id="a442b-115">Bu hizmeti kullanan istemci uygulamaları, uygulama yapılandırmasında belirtilen bir ile uyumlu bir bağlamayı kullanarak yanı sıra bu sözleşme, uygun olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a442b-115">Client applications that use this service would need to conform to this contract, along with using a binding that is compatible with the one specified in the application configuration.</span></span>  
  
 <span data-ttu-id="a442b-116">Aşağıdaki kod örneği, varsayılan yapılandırma dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="a442b-116">The following code example shows a default configuration file.</span></span> <span data-ttu-id="a442b-117">Bir Windows Communication Foundation (WCF) Web hizmeti, bu standart hizmet modeli yapılandırma şemasıyla uyumlu ve diğer WCF hizmetleri yapılandırma dosyaları aynı şekilde düzenlenebilir.</span><span class="sxs-lookup"><span data-stu-id="a442b-117">Being a Windows Communication Foundation (WCF) Web service, this conforms to the standard service model configuration schema and can be edited in the same way as other WCF services configuration files.</span></span>  
  
 <span data-ttu-id="a442b-118">Tipik değişiklikler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="a442b-118">Typical modifications would include:</span></span>  
  
-   <span data-ttu-id="a442b-119">Uç nokta adresi varsayılan ComponentName/ApplicationName/InterfaceName formundan daha kullanışlı bir forma değiştirme.</span><span class="sxs-lookup"><span data-stu-id="a442b-119">Changing the endpoint address from the default ApplicationName/ComponentName/InterfaceName form to a more usable form.</span></span>  
  
-   <span data-ttu-id="a442b-120">Varsayılan hizmet ad alanı değiştirme "http://tempuri.org/InterfaceID" daha ilgili bir form için form.</span><span class="sxs-lookup"><span data-stu-id="a442b-120">Modifying the namespace of the service from the default "http://tempuri.org/InterfaceID" form to a more relevant form.</span></span>  
  
-   <span data-ttu-id="a442b-121">Farklı bir aktarım bağlama kullanmak için uç nokta değiştirme.</span><span class="sxs-lookup"><span data-stu-id="a442b-121">Changing the endpoint to use a different transport binding.</span></span>  
  
     <span data-ttu-id="a442b-122">COM +-barındırılan durumda, adlandırılmış kanallar taşıma, varsayılan olarak kullanılır, ancak bunun yerine bir makine kapalı taşıması TCP gibi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a442b-122">In the COM+-hosted case, the named pipes transport is used by default, but an off-machine transport like TCP can be used instead.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a442b-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a442b-123">See Also</span></span>  
 [<span data-ttu-id="a442b-124">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="a442b-124">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
