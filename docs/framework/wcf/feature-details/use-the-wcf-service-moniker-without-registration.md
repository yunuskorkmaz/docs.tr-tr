---
title: 'Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: be4798663d0b39301ec496df45a4a7a5bf9c88e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918599"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="4dc4a-102">Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma</span><span class="sxs-lookup"><span data-stu-id="4dc4a-102">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>
<span data-ttu-id="4dc4a-103">Bağlanmak ve bir Windows Communication Foundation (WCF) hizmetiyle iletişim kurmak için ayrıntıları hizmeti adresi, bağlama yapılandırma ve hizmet sözleşmesi WCF istemci uygulaması olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-103">To connect to and communicate with a Windows Communication Foundation (WCF) service, a WCF client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="4dc4a-104">WCF hizmet bilinen adı genellikle gerekli sözleşme aracılığıyla önceki kayıt gerekli öznitelik türlerini alır, ancak bu mantıklı olduğu durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-104">The WCF service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="4dc4a-105">Kayıt yerine, kullanımının, Web Hizmetleri tanım dili (WSDL) belgenin biçiminde sözleşme tanımı ad edinebilirsiniz `wsdl` parametresi veya kullanımı aracılığıyla meta veri değişimi üzerinden `mexAddress` parametre.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-105">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="4dc4a-106">Bu, burada hücre değerlerinin bazıları Web hizmeti etkileşimler hesaplanır bir Excel elektronik tablosuna dağıtımını gibi senaryolara olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-106">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="4dc4a-107">Bu senaryoda, belgeyi açabilir tüm istemcilere hizmet sözleşme derlemesi kaydetmek için uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-107">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="4dc4a-108">`wsdl` Parametresi veya `mexAddress` parametresi kendi başına bir çözüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-108">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dc4a-109">Karşılıklı kimlik doğrulaması, istek ve izinsiz veya yanıltma yanıt karşı korumak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-109">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="4dc4a-110">Özellikle, istemcilerin yanıt meta veri değişimi uç noktası hedeflenen güvenilen taraf olduğunu garanti için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-110">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dc4a-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="4dc4a-111">Example</span></span>  
 <span data-ttu-id="4dc4a-112">Bu örnek, hizmet bilinen adı MEX sözleşme ile kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-112">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="4dc4a-113">Şu sözleşme hizmetiyle bir wsHttpBinding kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-113">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
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
  
 <span data-ttu-id="4dc4a-114">Aşağıdaki örnek bilinen ad dizesini uzak hizmet için bir WCF istemcisi oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-114">To construct a WCF client for the remote service the following example moniker string can be used.</span></span>  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="4dc4a-115">İstemci uygulama yürütme sırasında istemci gerçekleştiren bir `WS-MetadataExchange` ile sağlanan `mexAddress`.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-115">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="4dc4a-116">Bu adres, bağlama ve bir dizi hizmet için podrobnosti o kontraktu döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-116">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="4dc4a-117">`address`, `contract`, `contractNamespace`, `binding` Ve `bindingNamespace` parametreleri hedeflenen hizmet tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-117">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="4dc4a-118">Bu parametreleri eşleşen sonra ad uygun sözleşme tanımına sahip bir WCF istemcisi oluşturur ve çağrıları ardından WCF istemcisi kullanarak sözleşmenin yazılı olarak ile yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-118">Once those parameters have been matched, the moniker constructs a WCF client with the appropriate contract definition and calls can then be made using the WCF client, as with the typed contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dc4a-119">Bilinen ad hatalı veya hizmet kullanılamıyor durumunda çağrısı `GetObject` "Geçersiz sözdizimi" belirten bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="4dc4a-120">Bu hata iletisini alırsanız kullandığınız ad doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc4a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4dc4a-121">See also</span></span>

- [<span data-ttu-id="4dc4a-122">Nasıl yapılır: Kaydetme ve hizmet bilinen adı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4dc4a-122">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
