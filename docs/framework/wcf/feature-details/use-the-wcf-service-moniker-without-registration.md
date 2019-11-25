---
title: 'Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: c08fc362694469560eb7368eb5e536c08ec19bdf
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975992"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="8deeb-102">Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma</span><span class="sxs-lookup"><span data-stu-id="8deeb-102">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>
<span data-ttu-id="8deeb-103">Bir Windows Communication Foundation (WCF) hizmetine bağlanmak ve iletişim kurmak için, bir WCF istemci uygulaması hizmet adresi, bağlama yapılandırması ve hizmet sözleşmesinin ayrıntılarına sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8deeb-103">To connect to and communicate with a Windows Communication Foundation (WCF) service, a WCF client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="8deeb-104">WCF hizmeti bilinen adı genellikle gerekli öznitelik türlerinin önceki kayıtları aracılığıyla gerekli sözleşmeyi edinir, ancak bunun olanaklı olmadığı durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="8deeb-104">The WCF service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="8deeb-105">Kayıt yerinde, bilinen ad, `mexAddress` parametresinin kullanımı aracılığıyla `wsdl` parametresi veya meta veri değişimi aracılığıyla bir Web Hizmetleri tanım dili (WSDL) belgesi biçiminde sözleşmenin tanımını alabilir.</span><span class="sxs-lookup"><span data-stu-id="8deeb-105">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="8deeb-106">Bu, bazı hücre değerlerinden bazıları Web hizmeti etkileşimleri aracılığıyla hesaplanıyorsa Excel elektronik tablosunun dağıtılması gibi senaryolara izin vermez.</span><span class="sxs-lookup"><span data-stu-id="8deeb-106">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="8deeb-107">Bu senaryoda, belge açmış olabilecek tüm istemcilere hizmet sözleşmesi derlemesini kaydetmek uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8deeb-107">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="8deeb-108">`wsdl` parametresi veya `mexAddress` parametresi, kendi içinde bir çözüm sunar.</span><span class="sxs-lookup"><span data-stu-id="8deeb-108">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8deeb-109">Karşılıklı kimlik doğrulaması, istek ve yanıt üzerinde değişiklik yapılmasını veya yanıltmayı korumak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8deeb-109">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="8deeb-110">Özellikle, istemcilerin yanıt veren meta veri değişimi uç noktasının amaçlanan güvenilen taraf olduğundan emin olmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8deeb-110">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8deeb-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8deeb-111">Example</span></span>  
 <span data-ttu-id="8deeb-112">Bu örnek, hizmet adının bir MEX sözleşmesiyle kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8deeb-112">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="8deeb-113">Bir wsHttpBinding ile aşağıdaki sözleşmeye sahip bir hizmet sunulur.</span><span class="sxs-lookup"><span data-stu-id="8deeb-113">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
```csharp
using System.ServiceModel;  
  
// ...
  
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
  
 <span data-ttu-id="8deeb-114">Uzak hizmet için bir WCF istemcisi oluşturmak üzere aşağıdaki örnek bilinen ad dizesi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8deeb-114">To construct a WCF client for the remote service the following example moniker string can be used.</span></span>  
  
```
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="8deeb-115">İstemci uygulamasının yürütülmesi sırasında istemci, sağlanmış `mexAddress`bir `WS-MetadataExchange` gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8deeb-115">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="8deeb-116">Bu işlem, birkaç hizmet için adres, bağlama ve Sözleşme ayrıntılarını döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="8deeb-116">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="8deeb-117">`address`, `contract`, `contractNamespace`, `binding` ve `bindingNamespace` parametreleri amaçlanan hizmeti belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8deeb-117">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="8deeb-118">Bu parametreler eşleştirildiği sürece bilinen ad, uygun sözleşme tanımına sahip bir WCF istemcisi oluşturur ve çağrılar, yazılı sözleşmede olduğu gibi WCF istemcisi kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="8deeb-118">Once those parameters have been matched, the moniker constructs a WCF client with the appropriate contract definition and calls can then be made using the WCF client, as with the typed contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8deeb-119">Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, `GetObject` çağrısı "geçersiz sözdizimi" belirten bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="8deeb-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="8deeb-120">Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8deeb-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8deeb-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8deeb-121">See also</span></span>

- [<span data-ttu-id="8deeb-122">Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8deeb-122">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
