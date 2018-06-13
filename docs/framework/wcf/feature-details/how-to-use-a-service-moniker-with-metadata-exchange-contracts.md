---
title: 'Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 6265860c2e1efb2f74a0243157a223a33889629a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491256"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="e85ea-102">Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="e85ea-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="e85ea-103">Bazı yeni WCF hizmetleri geliştirme sonra bir komut dosyası veya Visual Basic 6.0 uygulamadan bu hizmetleri çağıran kullanabilmek ister karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e85ea-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="e85ea-104">Bir yöntemin bir WCF istemcisi derlemesini oluşturmak, derlemesini COM ile kaydetme, derlemeyi GAC'ye yükleyin ve ardından Visual Basic kodunuzdan COM türlerini başvuru olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e85ea-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="e85ea-105">Uygulamayı dağıttığınızda, WCF istemcisi derleme de dağıtmak gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="e85ea-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="e85ea-106">Ardından, kullanıcı WCF istemcisi derlemesini COM ile kaydetme ve GAC'ye yerleştirmek sahip olur.</span><span class="sxs-lookup"><span data-stu-id="e85ea-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="e85ea-107">WCF COM birlikte çalışma bir WCF istemcisi derlemeye bağlı olmadan aynı hizmeti çağrıları yapma sağlar.</span><span class="sxs-lookup"><span data-stu-id="e85ea-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="e85ea-108">WCF bilinen adını herhangi bir WCF Hizmeti herhangi bir COM uyumlu dili (Visual Basic, VBScript, Visual Basic for Applications (VBA) ve benzeri) bir meta veri değişimi (Mex) uç noktası türü ayıklamak için hizmet adının kullanır URI belirterek çağırmanıza olanak tanır hizmeti hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="e85ea-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="e85ea-109">Bu konu, Mex uç nokta belirtir WCF bilinen adını kullanarak alma başlatıldı WCF örnek çağrı açıklar.</span><span class="sxs-lookup"><span data-stu-id="e85ea-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e85ea-110">WCF istemci derlemesi tarafından tanımlanan türleri aslında hiç örneği.</span><span class="sxs-lookup"><span data-stu-id="e85ea-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="e85ea-111">Derleme yalnızca meta veriler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e85ea-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="e85ea-112">Mex adresi ile hizmet bilinen adı kullanma</span><span class="sxs-lookup"><span data-stu-id="e85ea-112">Using the service moniker with a Mex address</span></span>  
  
1.  <span data-ttu-id="e85ea-113">Başlarken örneği oluşturmak ve kendi URL'ye göz atmak için Internet Explorer kullanın (http://localhost/ServiceModelSamples/Service.svc) hizmetinin çalıştığından emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="e85ea-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2.  <span data-ttu-id="e85ea-114">Visual Basic komut dosyası veya aşağıdaki kodu içeren bir Visual Basic uygulama oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e85ea-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="e85ea-115">Visual Basic uygulama veya komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e85ea-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e85ea-116">Aradığınız hizmeti Mex bitiş noktası ad hizmeti meta verileri okuyabilir için kullanıma gerekir.</span><span class="sxs-lookup"><span data-stu-id="e85ea-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="e85ea-117">Daha fazla bilgi için bkz: [nasıl yapılır: bir yapılandırma dosyası kullanarak bir hizmet için meta veri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="e85ea-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e85ea-118">Ad hatalı veya hizmet kullanılamıyor çağrısı `GetObject` "Geçersiz sözdizimi." bildiren bir hata döndürür</span><span class="sxs-lookup"><span data-stu-id="e85ea-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="e85ea-119">Bu hatayı alırsanız, kullanmakta olduğunuz adının doğru olduğundan ve hizmet kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85ea-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e85ea-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e85ea-120">See Also</span></span>  
 [<span data-ttu-id="e85ea-121">Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma</span><span class="sxs-lookup"><span data-stu-id="e85ea-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [<span data-ttu-id="e85ea-122">Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="e85ea-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
