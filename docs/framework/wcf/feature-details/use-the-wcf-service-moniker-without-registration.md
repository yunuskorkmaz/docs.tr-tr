---
title: "Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9e91889947a17f8cba66d822b857e1c8bc875cab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="10694-102">Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma</span><span class="sxs-lookup"><span data-stu-id="10694-102">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>
<span data-ttu-id="10694-103">Bağlanmak ve ile iletişim kurmak için bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti, bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci uygulaması hizmeti adresi, bağlama yapılandırma ve hizmet sözleşmesi ayrıntılarını olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="10694-103">To connect to and communicate with a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="10694-104">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmet bilinen adı genellikle gerekli öznitelik türlerini önceki kaydı aracılığıyla gerekli sözleşme alır, ancak bu olduğu uygun durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="10694-104">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="10694-105">Kayıt yerine, kullanım yoluyla, bir Web Hizmetleri tanım dili (WSDL) belge biçiminde sözleşme tanımı ad edinebilirsiniz `wsdl` parametresi veya kullanımı aracılığıyla meta veri değişimi üzerinden `mexAddress` parametre.</span><span class="sxs-lookup"><span data-stu-id="10694-105">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="10694-106">Bu, bazı hücre değerleri Web hizmeti etkileşimleri burada hesaplanan bir Excel elektronik tablosuna dağıtımı gibi senaryolara olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="10694-106">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="10694-107">Bu senaryoda, belgeyi açabilir tüm istemcilere hizmet sözleşmesi derlemesi kaydetmek için uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="10694-107">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="10694-108">`wsdl` Parametresi veya `mexAddress` parametresi kendi başına bir çözüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="10694-108">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10694-109">Karşılıklı kimlik doğrulaması istek ve yanıt değiştirilmesine veya yanıltmaya karşı korumak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="10694-109">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="10694-110">Özellikle, istemcilerin yanıt meta veri değişimi uç nokta hedeflenen güvenilen taraf olduğunu da gösterilmeyeceği için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="10694-110">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10694-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="10694-111">Example</span></span>  
 <span data-ttu-id="10694-112">Bu örnek, hizmet bilinen adı MEX sözleşme ile kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="10694-112">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="10694-113">Aşağıdaki sözleşme hizmetiyle wsHttpBinding ile sunulur.</span><span class="sxs-lookup"><span data-stu-id="10694-113">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
```  
using System.ServiceModel;  
  
...  
  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Demo")]  
public interface IAffiliate  
{  
    [OperationContract]  
    bool NewAffiliate(string ID, string company, string fullname, string accountsCode);  
    [OperationContract]  
    bool RemoveAffiliate(string ID);  
    [OperationContract]  
    double RevenueCheckMonthly(ref string ID);  
    [OperationContract]  
    double RevenueCheckTotal(ref string ID);  
}  
```  
  
 <span data-ttu-id="10694-114">Oluşturmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcisi aşağıdaki örnek ad dizesini kullanılabilir uzak hizmeti.</span><span class="sxs-lookup"><span data-stu-id="10694-114">To construct a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client for the remote service the following example moniker string can be used.</span></span>  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="10694-115">İstemci uygulaması yürütülmesi sırasında istemci gerçekleştiren bir `WS-MetadataExchange` sağlanan ile `mexAddress`.</span><span class="sxs-lookup"><span data-stu-id="10694-115">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="10694-116">Bu adresi, bağlama ve hizmetlerin sayısı sözleşme ayrıntılarını döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="10694-116">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="10694-117">`address`, `contract`, `contractNamespace`, `binding` Ve `bindingNamespace` parametreleri hedeflenen hizmet tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="10694-117">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="10694-118">Bu parametreler eşleşen sonra ad yapıları bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çağrıları ve uygun sözleşme tanımı istemcisiyle sonra yapılabilir kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, yazılı sözleşme ile.</span><span class="sxs-lookup"><span data-stu-id="10694-118">Once those parameters have been matched, the moniker constructs a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client with the appropriate contract definition and calls can then be made using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, as with the typed contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10694-119">Ad hatalı veya hizmet kullanılamıyor çağrısı `GetObject` "Geçersiz sözdizimi" bildiren bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="10694-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="10694-120">Bu hatayı alırsanız, kullanmakta olduğunuz adının doğru olduğundan ve hizmet kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="10694-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10694-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10694-121">See Also</span></span>  
 [<span data-ttu-id="10694-122">Nasıl yapılır: kaydetmek ve hizmet bilinen adı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="10694-122">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
