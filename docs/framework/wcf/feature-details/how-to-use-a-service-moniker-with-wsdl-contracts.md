---
title: 'Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 838e7affcf47742c8f372879fcb33946d53ba43f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491049"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="b3265-102">Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="b3265-102">How to: Use a Service Moniker with WSDL Contracts</span></span>
<span data-ttu-id="b3265-103">Tamamen kendi içinde bulunan bir COM birlikte çalışma istemciniz isteyebileceğiniz durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="b3265-103">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="b3265-104">Aramak istediğiniz hizmet MEX bitiş noktası ve DLL COM birlikte çalışma için kaydettirilmemiş olabilir WCF istemcisi getirebilir değil.</span><span class="sxs-lookup"><span data-stu-id="b3265-104">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="b3265-105">Bu durumlarda, hizmet açıklayan bir WSDL dosyası oluşturun ve WCF hizmet bilinen adı geçirin.</span><span class="sxs-lookup"><span data-stu-id="b3265-105">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="b3265-106">Bu konuda, bir WCF WSDL ad kullanarak alma başlatıldı WCF örnek çağrı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b3265-106">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="b3265-107">WSDL hizmet bilinen adı kullanma</span><span class="sxs-lookup"><span data-stu-id="b3265-107">Using the WSDL service moniker</span></span>  
  
1.  <span data-ttu-id="b3265-108">Açın ve GettingStarted örnek çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b3265-108">Open and build the GettingStarted sample solution.</span></span>  
  
2.  <span data-ttu-id="b3265-109">Internet Explorer'ı açın ve http://localhost/ServiceModelSamples/Service.svc hizmetinin çalıştığından emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="b3265-109">Open Internet Explorer and browse to http://localhost/ServiceModelSamples/Service.svc to make sure that the service is working.</span></span>  
  
3.  <span data-ttu-id="b3265-110">Adını da dosyasında CalculatorService sınıfında şu özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b3265-110">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4.  <span data-ttu-id="b3265-111">Bir bağlama ad alanı hizmeti App.config ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b3265-111">Add a binding namespace to the service App.config:</span></span>  
  
  
  
5.  <span data-ttu-id="b3265-112">WSDL dosyası okumak üzere bir uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b3265-112">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="b3265-113">Ad alanları 3 ve 4. adımlarda eklenmiş olduğundan göz atarak hizmetin tüm WSDL açıklamasını sorgulamak için IE kullanabilirsiniz http://localhost/ServiceModelSamples/Service.svc?wsdl.</span><span class="sxs-lookup"><span data-stu-id="b3265-113">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to http://localhost/ServiceModelSamples/Service.svc?wsdl.</span></span> <span data-ttu-id="b3265-114">Dosyayı serviceWSDL.xml Internet Explorer'dan kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b3265-114">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="b3265-115">Adım 3 ve 4 ad belirtmezseniz, yukarıdaki URL sorgulama döndürülen WSDL belge tam WSDL olmaz.</span><span class="sxs-lookup"><span data-stu-id="b3265-115">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="b3265-116">Döndürülen WSDL belge diğer WSDL belgeleri içe birkaç içeri aktarma deyimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="b3265-116">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="b3265-117">Her alma deyimi aracılığıyla gidin ve tam WSDL belgesi oluşturmak, hizmetten içeri WSDL ile döndürülen WSDL birleştirme gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3265-117">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6.  <span data-ttu-id="b3265-118">Visual Basic 6.0 açın ve yeni bir standart .exe dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b3265-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="b3265-119">Aşağıdaki kod tıklatın işleyicisine eklemek için düğmesini çift tıklayın ve forma düğme ekleme:</span><span class="sxs-lookup"><span data-stu-id="b3265-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
    >  Ad hatalı veya hizmet kullanılamıyor çağrısı `GetObject` "Geçersiz sözdizimi" bildiren bir hata döndürecektir.  <span data-ttu-id="b3265-121">Bu hatayı alırsanız, kullanmakta olduğunuz adının doğru olduğundan ve hizmet kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b3265-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7.  <span data-ttu-id="b3265-122">Visual Basic uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b3265-122">Run the Visual Basic application.</span></span> <span data-ttu-id="b3265-123">Bir ileti kutusu arama çıkarma (145, 76.54) sonuçlarını görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b3265-123">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3265-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3265-124">See Also</span></span>  
 [<span data-ttu-id="b3265-125">Başlarken</span><span class="sxs-lookup"><span data-stu-id="b3265-125">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="b3265-126">COM Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b3265-126">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
