---
title: 'Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 00aa1bbde95c0636391f213f830fc67b2dedf459
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968797"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="0e424-102">Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="0e424-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="0e424-103">Bazı yeni WCF Hizmetleri geliştirdikten sonra, bu hizmetleri bir betikten veya Visual Basic 6,0 uygulamasından çağırabilmek istediğinize karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e424-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="0e424-104">Bir yöntem, bir WCF istemci derlemesi oluşturmak, derlemeyi COM 'a kaydetmek, derlemeyi GAC 'ye yüklemek ve ardından Visual Basic kodunuzda COM türlerine başvurmak olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0e424-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="0e424-105">Uygulamayı dağıttığınızda, WCF Istemci derlemesini de dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e424-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="0e424-106">Daha sonra kullanıcının WCF istemci derlemesini COM 'a kaydetmesi ve GAC 'ye yerleştirmesini gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="0e424-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="0e424-107">WCF COM birlikte çalışması Ayrıca bir WCF istemci derlemesine bağlı olmadan aynı hizmet çağrılarını yapmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e424-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="0e424-108">WCF bilinen adı, hizmet adının türü ayıklamak için kullandığı bir meta veri değişimi (MEX) uç noktası URI 'SI belirterek herhangi bir COM uyumlu dilden (Visual Basic, VBScript, Visual Basic for Applications (VBA) vb.) herhangi bir WCF hizmetini çağırmanızı sağlar hizmet hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="0e424-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="0e424-109">Bu konu, bir MEX uç noktası belirten bir WCF bilinen adı kullanılarak Başlarken WCF örneğinin nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0e424-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e424-110">WCF istemci derlemesi tarafından tanımlanan türler aslında örneklenemez.</span><span class="sxs-lookup"><span data-stu-id="0e424-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="0e424-111">Derleme yalnızca meta veriler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e424-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="0e424-112">Hizmet bilinen adını bir Mex adresiyle kullanma</span><span class="sxs-lookup"><span data-stu-id="0e424-112">Using the service moniker with a Mex address</span></span>  
  
1. <span data-ttu-id="0e424-113">Başlangıç örneğini oluşturun ve Internet Explorer 'ı kullanarak URL 'ye gidin (http://localhost/ServiceModelSamples/Service.svc) hizmetin çalıştığından emin olmak için).</span><span class="sxs-lookup"><span data-stu-id="0e424-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2. <span data-ttu-id="0e424-114">Aşağıdaki kodu içeren bir Visual Basic betiği veya Visual Basic uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0e424-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="0e424-115">Visual Basic uygulamayı veya betiği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0e424-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0e424-116">Çağırmak için kullandığınız hizmet, bilinen adın meta verileri hizmetten okuyabilmesi için bir MEX uç noktası kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e424-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="0e424-117">Daha fazla bilgi için [nasıl yapılır: Yapılandırma dosyası](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)kullanarak bir hizmet için meta verileri yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="0e424-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0e424-118">Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, çağrısı `GetObject` "geçersiz sözdizimi" belirten bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e424-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="0e424-119">Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0e424-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e424-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e424-120">See also</span></span>

- [<span data-ttu-id="0e424-121">Nasıl yapılır: Windows Communication Foundation hizmet bilinen adını kayıt olmadan kullanma</span><span class="sxs-lookup"><span data-stu-id="0e424-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [<span data-ttu-id="0e424-122">Nasıl yapılır: WSDL sözleşmeleriyle hizmet bilinen adı kullanma</span><span class="sxs-lookup"><span data-stu-id="0e424-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
