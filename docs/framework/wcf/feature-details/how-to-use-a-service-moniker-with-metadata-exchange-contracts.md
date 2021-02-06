---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: meta veri değişimi sözleşmeleriyle hizmet bilinen adı kullanma'
title: 'Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 220132a10cb637be9e3724232d0ddaf80a13551a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643104"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="86c7d-103">Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="86c7d-103">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>

<span data-ttu-id="86c7d-104">Bazı yeni WCF Hizmetleri geliştirdikten sonra, bu hizmetleri bir betikten veya Visual Basic 6,0 uygulamasından çağırabilmek istediğinize karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86c7d-104">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="86c7d-105">Bir yöntem, bir WCF istemci derlemesi oluşturmak, derlemeyi COM 'a kaydetmek, derlemeyi GAC 'ye yüklemek ve ardından Visual Basic kodunuzda COM türlerine başvurmak olacaktır.</span><span class="sxs-lookup"><span data-stu-id="86c7d-105">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="86c7d-106">Uygulamayı dağıttığınızda, WCF Istemci derlemesini de dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="86c7d-106">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="86c7d-107">Daha sonra kullanıcının WCF istemci derlemesini COM 'a kaydetmesi ve GAC 'ye yerleştirmesini gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="86c7d-107">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="86c7d-108">WCF COM birlikte çalışması Ayrıca bir WCF istemci derlemesine bağlı olmadan aynı hizmet çağrılarını yapmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="86c7d-108">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="86c7d-109">WCF takma adı, hizmet adının hizmet hakkındaki tür bilgilerini ayıklamak için kullandığı bir meta veri değişimi (MEX) uç noktası URI 'SI belirterek herhangi bir COM uyumlu dilden (Visual Basic, VBScript, Visual Basic for Applications (VBA) vb.) herhangi bir WCF hizmetini çağırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="86c7d-109">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="86c7d-110">Bu konu, bir MEX uç noktası belirten bir WCF bilinen adı kullanılarak Başlarken WCF örneğinin nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="86c7d-110">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86c7d-111">WCF istemci derlemesi tarafından tanımlanan türler aslında örneklenemez.</span><span class="sxs-lookup"><span data-stu-id="86c7d-111">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="86c7d-112">Derleme yalnızca meta veriler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86c7d-112">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="86c7d-113">Hizmet bilinen adını bir Mex adresiyle kullanma</span><span class="sxs-lookup"><span data-stu-id="86c7d-113">Using the service moniker with a Mex address</span></span>  
  
1. <span data-ttu-id="86c7d-114">Hizmetin çalıştığından emin olmak için başlangıç örneğini oluşturun ve URL 'sine () gitmek için Internet Explorer 'ı kullanın `http://localhost/ServiceModelSamples/Service.svc` .</span><span class="sxs-lookup"><span data-stu-id="86c7d-114">Build the Getting Started sample and use Internet Explorer to browse to its URL (`http://localhost/ServiceModelSamples/Service.svc`) to ensure that the service is working.</span></span>  
  
2. <span data-ttu-id="86c7d-115">Aşağıdaki kodu içeren bir Visual Basic betiği veya Visual Basic uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="86c7d-115">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```vb
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="86c7d-116">Visual Basic uygulamayı veya betiği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="86c7d-116">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="86c7d-117">Çağırmak için kullandığınız hizmet, bilinen adın meta verileri hizmetten okuyabilmesi için bir MEX uç noktası kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86c7d-117">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="86c7d-118">Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma dosyası kullanarak bir hizmet Için meta verileri yayımlama](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="86c7d-118">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="86c7d-119">Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, çağrısı `GetObject` "geçersiz sözdizimi" belirten bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="86c7d-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="86c7d-120">Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="86c7d-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c7d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86c7d-121">See also</span></span>

- [<span data-ttu-id="86c7d-122">Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma</span><span class="sxs-lookup"><span data-stu-id="86c7d-122">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](use-the-wcf-service-moniker-without-registration.md)
- [<span data-ttu-id="86c7d-123">Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="86c7d-123">How to: Use a Service Moniker with WSDL Contracts</span></span>](how-to-use-a-service-moniker-with-wsdl-contracts.md)
