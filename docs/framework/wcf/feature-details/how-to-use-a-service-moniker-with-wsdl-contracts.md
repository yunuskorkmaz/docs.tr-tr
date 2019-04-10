---
title: 'Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 2968641538bf0b4d0e136d5784bf69e5e7fcb3a0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298090"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="5f008-102">Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="5f008-102">How to: Use a Service Moniker with WSDL Contracts</span></span>
<span data-ttu-id="5f008-103">Tamamen bağımsız bir COM birlikte çalışma istemciniz isteyebileceğiniz durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="5f008-103">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="5f008-104">Hizmeti çağırmak istediğinizde bir MEX uç noktası ve DLL COM birlikte çalışması için kayıtlı olmayabilir WCF istemcisini açığa çıkarmamak.</span><span class="sxs-lookup"><span data-stu-id="5f008-104">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="5f008-105">Bu durumlarda, hizmeti tanımlayan bir WSDL dosyası oluşturun ve WCF hizmet bilinen adını geçirin.</span><span class="sxs-lookup"><span data-stu-id="5f008-105">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="5f008-106">Bu konu, bir WSDL WCF bilinen adını kullanarak çalışmaya WCF başlama örneği çağrılacak açıklar.</span><span class="sxs-lookup"><span data-stu-id="5f008-106">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="5f008-107">WSDL hizmet bilinen adı kullanma</span><span class="sxs-lookup"><span data-stu-id="5f008-107">Using the WSDL service moniker</span></span>  
  
1. <span data-ttu-id="5f008-108">Açın ve GettingStarted örnek Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="5f008-108">Open and build the GettingStarted sample solution.</span></span>  
  
2. <span data-ttu-id="5f008-109">Internet Explorer'ı açın ve `http://localhost/ServiceModelSamples/Service.svc` hizmetinin çalıştığından emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="5f008-109">Open Internet Explorer and browse to `http://localhost/ServiceModelSamples/Service.svc` to make sure that the service is working.</span></span>  
  
3. <span data-ttu-id="5f008-110">Adını da dosyasında CalculatorService sınıfında aşağıdaki özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5f008-110">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. <span data-ttu-id="5f008-111">Bir bağlama ad alanı, App.config hizmete ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5f008-111">Add a binding namespace to the service App.config:</span></span>  

5. <span data-ttu-id="5f008-112">Uygulamanın okuma WSDL dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f008-112">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="5f008-113">Adım 3 ve 4 ad alanlarını eklenmiş olduğundan, hizmetin tüm WSDL açıklaması göz atarak sorgulamak için IE kullanabilirsiniz `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="5f008-113">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span></span> <span data-ttu-id="5f008-114">Dosyayı serviceWSDL.xml Internet Explorer'dan kaydedin.</span><span class="sxs-lookup"><span data-stu-id="5f008-114">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="5f008-115">Adım 3 ve 4 ad belirtmezseniz, yukarıdaki URL'yi sorgulamasını döndürülen WSDL belgesinde tam WSDL olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="5f008-115">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="5f008-116">WSDL belgesi döndürülen diğer WSDL belgeleri içe birkaç içeri aktarma deyimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5f008-116">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="5f008-117">Her içeri aktarma deyimi aracılığıyla gidin ve tam bir WSDL belgesi oluşturmak WSDL içe WSDL ile hizmetten döndürülen birleştirme gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f008-117">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6. <span data-ttu-id="5f008-118">Visual Basic 6.0 açın ve yeni bir standart .exe dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f008-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="5f008-119">Forma bir düğme ekleyin ve aşağıdaki kodu için tıklama işleyicisi eklemek için Ekle düğmesine çift tıklayın:</span><span class="sxs-lookup"><span data-stu-id="5f008-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    >  Bilinen ad hatalı veya hizmet kullanılamıyorsa çağrısı `GetObject` "Geçersiz sözdizimi" belirten bir hata döndürür.  <span data-ttu-id="5f008-121">Bu hata iletisini alırsanız kullandığınız ad doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5f008-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7. <span data-ttu-id="5f008-122">Visual Basic uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5f008-122">Run the Visual Basic application.</span></span> <span data-ttu-id="5f008-123">Bir ileti kutusu arama çıkarma (145, 76.54) sonuçlarını görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5f008-123">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f008-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f008-124">See also</span></span>

- [<span data-ttu-id="5f008-125">Başlarken</span><span class="sxs-lookup"><span data-stu-id="5f008-125">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="5f008-126">COM Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5f008-126">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
