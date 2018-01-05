---
title: "Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d2b5b6d4a671a3eb281f49dd60fd3c00ee76f8a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="b8c09-102">Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="b8c09-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="b8c09-103">Bazı yeni geliştirme sonra [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri karar bir komut dosyası veya Visual Basic 6.0 uygulamadan bu hizmetleri çağıran kullanabilmek ister.</span><span class="sxs-lookup"><span data-stu-id="b8c09-103">After developing some new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="b8c09-104">Bir yöntem oluşturmak için olacak bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci derleme derlemesini COM ile kaydetme, derlemeyi GAC'ye yükleyin ve ardından Visual Basic kodunuzdan COM türlerini başvuru.</span><span class="sxs-lookup"><span data-stu-id="b8c09-104">One method would be to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="b8c09-105">Uygulamayı dağıttığınızda, dağıtmanız gerekecek [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci derleme.</span><span class="sxs-lookup"><span data-stu-id="b8c09-105">When you distribute the application, you will have to distribute the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Client assembly as well.</span></span> <span data-ttu-id="b8c09-106">Ardından, kullanıcı WCF istemcisi derlemesini COM ile kaydetme ve GAC'ye yerleştirmek sahip olur.</span><span class="sxs-lookup"><span data-stu-id="b8c09-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b8c09-107">COM birlikte çalışma de aynı hizmet çağrıları öğesine bağlı kalmadan almanıza imkan tanır bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci derleme.</span><span class="sxs-lookup"><span data-stu-id="b8c09-107"> COM Interop also allows you to make the same service calls without relying on a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly.</span></span> <span data-ttu-id="b8c09-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Ad herhangi bir çağrıda olanak tanır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet herhangi bir dilden bir meta veri exchange (Mex) uç noktası kullanan hizmet adının URI belirterek COM uyumlu (Visual Basic, VBScript, Visual Basic for Applications (VBA) ve benzeri) hizmeti hakkında türü bilgi ayıklamak için.</span><span class="sxs-lookup"><span data-stu-id="b8c09-108">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker allows you to call any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="b8c09-109">Bu konu, Başlarken çağrılacağını açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanarak örnek bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Mex uç nokta belirtir ad.</span><span class="sxs-lookup"><span data-stu-id="b8c09-109">This topic describes how to call the Getting Started [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8c09-110">Tanımlanan türlerden [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci derleme aslında hiç örneği.</span><span class="sxs-lookup"><span data-stu-id="b8c09-110">The types defined by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly are never actually instantiated.</span></span> <span data-ttu-id="b8c09-111">Derleme yalnızca meta veriler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b8c09-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="b8c09-112">Mex adresi ile hizmet bilinen adı kullanma</span><span class="sxs-lookup"><span data-stu-id="b8c09-112">Using the service moniker with a Mex address</span></span>  
  
1.  <span data-ttu-id="b8c09-113">Başlarken örneği oluşturmak ve hizmetin çalıştığından emin olmak için URL'ye (http://localhost/ServiceModelSamples/Service.svc) göz atmak için Internet Explorer'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b8c09-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2.  <span data-ttu-id="b8c09-114">Visual Basic komut dosyası veya aşağıdaki kodu içeren bir Visual Basic uygulama oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b8c09-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="b8c09-115">Visual Basic uygulama veya komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b8c09-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b8c09-116">Aradığınız hizmeti Mex bitiş noktası ad hizmeti meta verileri okuyabilir için kullanıma gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8c09-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="b8c09-117">Daha fazla bilgi için bkz: [nasıl yapılır: bir yapılandırma dosyası kullanarak bir hizmet için meta veri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="b8c09-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b8c09-118">Ad hatalı veya hizmet kullanılamıyor çağrısı `GetObject` "Geçersiz sözdizimi." bildiren bir hata döndürür</span><span class="sxs-lookup"><span data-stu-id="b8c09-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="b8c09-119">Bu hatayı alırsanız, kullanmakta olduğunuz adının doğru olduğundan ve hizmet kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b8c09-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c09-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8c09-120">See Also</span></span>  
 [<span data-ttu-id="b8c09-121">Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma</span><span class="sxs-lookup"><span data-stu-id="b8c09-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [<span data-ttu-id="b8c09-122">Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="b8c09-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
