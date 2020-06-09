---
title: 'Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: f69314948a0e0a69e49ec148f94572f17d0b8e3c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595056"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="f1ca2-102">Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma</span><span class="sxs-lookup"><span data-stu-id="f1ca2-102">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>
<span data-ttu-id="f1ca2-103">Bir Windows Communication Foundation (WCF) hizmetine bağlanmak ve iletişim kurmak için, bir WCF istemci uygulaması hizmet adresi, bağlama yapılandırması ve hizmet sözleşmesinin ayrıntılarına sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-103">To connect to and communicate with a Windows Communication Foundation (WCF) service, a WCF client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="f1ca2-104">WCF hizmeti bilinen adı genellikle gerekli öznitelik türlerinin önceki kayıtları aracılığıyla gerekli sözleşmeyi edinir, ancak bunun olanaklı olmadığı durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-104">The WCF service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="f1ca2-105">Kayıt yerinde, ad, bir Web Hizmetleri tanım dili (WSDL) belgesi biçiminde veya parametresi kullanılarak `wsdl` veya meta veri değişimi aracılığıyla sözleşmenin tanımını alabilir `mexAddress` .</span><span class="sxs-lookup"><span data-stu-id="f1ca2-105">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="f1ca2-106">Bu, bazı hücre değerlerinden bazıları Web hizmeti etkileşimleri aracılığıyla hesaplanıyorsa Excel elektronik tablosunun dağıtılması gibi senaryolara izin vermez.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-106">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="f1ca2-107">Bu senaryoda, belge açmış olabilecek tüm istemcilere hizmet sözleşmesi derlemesini kaydetmek uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-107">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="f1ca2-108">`wsdl`Parametresi veya parametresi, `mexAddress` bağımsız bir çözüm sunar.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-108">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1ca2-109">Karşılıklı kimlik doğrulaması, istek ve yanıt üzerinde değişiklik yapılmasını veya yanıltmayı korumak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-109">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="f1ca2-110">Özellikle, istemcilerin yanıt veren meta veri değişimi uç noktasının amaçlanan güvenilen taraf olduğundan emin olmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-110">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1ca2-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1ca2-111">Example</span></span>  
 <span data-ttu-id="f1ca2-112">Bu örnek, hizmet adının bir MEX sözleşmesiyle kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-112">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="f1ca2-113">Bir wsHttpBinding ile aşağıdaki sözleşmeye sahip bir hizmet sunulur.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-113">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
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
  
 <span data-ttu-id="f1ca2-114">Uzak hizmet için bir WCF istemcisi oluşturmak üzere aşağıdaki örnek bilinen ad dizesi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-114">To construct a WCF client for the remote service the following example moniker string can be used.</span></span>  
  
```
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="f1ca2-115">İstemci uygulamasının yürütülmesi sırasında istemci, `WS-MetadataExchange` belirtilen ile bir kullanır `mexAddress` .</span><span class="sxs-lookup"><span data-stu-id="f1ca2-115">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="f1ca2-116">Bu işlem, birkaç hizmet için adres, bağlama ve Sözleşme ayrıntılarını döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-116">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="f1ca2-117">`address`,, `contract` `contractNamespace` `binding` Ve `bindingNamespace` parametreleri amaçlanan hizmeti belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-117">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="f1ca2-118">Bu parametreler eşleştirildiği sürece bilinen ad, uygun sözleşme tanımına sahip bir WCF istemcisi oluşturur ve çağrılar, yazılı sözleşmede olduğu gibi WCF istemcisi kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-118">Once those parameters have been matched, the moniker constructs a WCF client with the appropriate contract definition and calls can then be made using the WCF client, as with the typed contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1ca2-119">Bilinen ad hatalı biçimlendirilmiş veya hizmet kullanılamaz durumdaysa, çağrı `GetObject` "geçersiz sözdizimi" belirten bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="f1ca2-120">Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1ca2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1ca2-121">See also</span></span>

- [<span data-ttu-id="f1ca2-122">Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f1ca2-122">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)
