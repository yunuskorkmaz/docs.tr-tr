---
title: 'Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 367cbd4a2bfbde3d4ab0a74eeeaf5d5f5662ec27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972906"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="284de-102">Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="284de-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="284de-103">Yeni bazı WCF hizmetlerinde geliştirme sonra bir komut dosyası veya Visual Basic 6.0 bir uygulamadan bu hizmetleri çağıran mümkün olmasını istediğiniz karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="284de-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="284de-104">Bir WCF istemcisi derleme oluşturma, derleme COM ile kaydetme, derlemeyi GAC'ye yüklemek ve ardından, Visual Basic kodundan başvuru COM türleri için bir yöntem olacaktır.</span><span class="sxs-lookup"><span data-stu-id="284de-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="284de-105">Uygulamayı dağıtırken de WCF istemci bütünleştirilmiş kodu dağıtmak gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="284de-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="284de-106">Ardından, kullanıcı WCF istemci derleme COM ile kaydetme ve GAC'de yerleştirme sahip olur.</span><span class="sxs-lookup"><span data-stu-id="284de-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="284de-107">WCF COM birlikte çalışma bir WCF istemcisi derleme üzerinde bağlı olmadan aynı hizmet çağrıları yapmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="284de-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="284de-108">WCF bilinen adını bir meta veri değişimi (Mex) uç noktası türü ayıklamak için hizmet bilinen adı kullanan bir URI belirterek herhangi bir WCF Hizmeti (Visual Basic, VBScript, Visual Basic for Applications (VBA) ve benzeri) herhangi bir COM uyumlu dil çağırmanızı sağlar. hizmeti hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="284de-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="284de-109">Bu konu, bir Mex uç noktasını belirtir bir WCF bilinen adını kullanarak çalışmaya WCF başlama örneği çağırmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="284de-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="284de-110">WCF istemci derlemesi tarafından tanımlanan türler gerçekten hiçbir zaman örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="284de-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="284de-111">Derleme yalnızca meta veriler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="284de-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="284de-112">Bir Mex adresa ile hizmet bilinen adı kullanma</span><span class="sxs-lookup"><span data-stu-id="284de-112">Using the service moniker with a Mex address</span></span>  
  
1. <span data-ttu-id="284de-113">Başlarken örneği oluşturmak ve kendi URL'sine göz atmak için Internet Explorer'ı kullanın (http://localhost/ServiceModelSamples/Service.svc) hizmetinin çalıştığından emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="284de-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2. <span data-ttu-id="284de-114">Visual Basic komut dosyası veya aşağıdaki kodu içeren bir Visual Basic uygulama oluşturun:</span><span class="sxs-lookup"><span data-stu-id="284de-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="284de-115">Visual Basic uygulama veya betik çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="284de-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="284de-116">Aradığınız hizmet, hizmetten bulunan meta verileri okuyabilmesi bilinen ad için bir Mex uç noktasını açığa çıkarmalıdır.</span><span class="sxs-lookup"><span data-stu-id="284de-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="284de-117">Daha fazla bilgi için [nasıl yapılır: Bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="284de-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="284de-118">Bilinen ad hatalı veya hizmet kullanılamıyor durumunda çağrısı `GetObject` "Geçersiz sözdizimi." belirten bir hata döndürür</span><span class="sxs-lookup"><span data-stu-id="284de-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="284de-119">Bu hata iletisini alırsanız kullandığınız ad doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="284de-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="284de-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="284de-120">See also</span></span>

- [<span data-ttu-id="284de-121">Nasıl yapılır: Windows Communication Foundation Hizmeti bilinen adını kaydolmadan kullanma</span><span class="sxs-lookup"><span data-stu-id="284de-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [<span data-ttu-id="284de-122">Nasıl yapılır: WSDL sözleşmeleriyle hizmet bilinen adı kullanma</span><span class="sxs-lookup"><span data-stu-id="284de-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
