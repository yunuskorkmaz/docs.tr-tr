---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: WSDL sözleşmeleriyle hizmet bilinen adı kullanma'
title: 'Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 70a8ef0258cd8490d8e14b6a80e8de0248fa0ae2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734379"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="14b28-103">Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="14b28-103">How to: Use a Service Moniker with WSDL Contracts</span></span>

<span data-ttu-id="14b28-104">Tamamen kendi kendine bağımsız bir COM birlikte çalışma istemcisine sahip olmak isteyebileceğiniz durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="14b28-104">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="14b28-105">Çağırmak istediğiniz hizmet bir MEX uç noktası açığa sunmayabilir ve WCF istemci DLL 'SI COM birlikte çalışması için kaydedilmemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="14b28-105">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="14b28-106">Bu durumlarda, hizmeti açıklayan bir WSDL dosyası oluşturabilir ve bunu WCF hizmeti bilinen adına geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14b28-106">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="14b28-107">Bu konu, bir WCF WSDL bilinen adı kullanılarak Başlarken WCF örneğinin nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="14b28-107">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="14b28-108">WSDL hizmeti bilinen adını kullanma</span><span class="sxs-lookup"><span data-stu-id="14b28-108">Using the WSDL service moniker</span></span>  
  
1. <span data-ttu-id="14b28-109">GettingStarted örnek çözümünü açın ve oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14b28-109">Open and build the GettingStarted sample solution.</span></span>  
  
2. <span data-ttu-id="14b28-110">Internet Explorer 'ı açın ve `http://localhost/ServiceModelSamples/Service.svc` hizmetin çalıştığından emin olmak için öğesine gidin.</span><span class="sxs-lookup"><span data-stu-id="14b28-110">Open Internet Explorer and browse to `http://localhost/ServiceModelSamples/Service.svc` to make sure that the service is working.</span></span>  
  
3. <span data-ttu-id="14b28-111">Service.cs dosyasında, Hesaplatorservice sınıfına aşağıdaki özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="14b28-111">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. <span data-ttu-id="14b28-112">Hizmet App.config bir bağlama ad alanı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="14b28-112">Add a binding namespace to the service App.config:</span></span>  

5. <span data-ttu-id="14b28-113">Uygulamanın okuması için bir WSDL dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14b28-113">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="14b28-114">Ad alanları 3 ve 4. adımlarda eklendiğinden, ' a giderek hizmetin WSDL açıklamasının tamamını sorgulamak için IE kullanabilirsiniz `http://localhost/ServiceModelSamples/Service.svc?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="14b28-114">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span></span> <span data-ttu-id="14b28-115">Daha sonra dosyayı Internet Explorer 'dan serviceWSDL.xml olarak kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14b28-115">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="14b28-116">Adım 3 ve 4 ' te ad alanlarını belirtmezseniz, yukarıdaki URL 'yi sorgulamadan döndürülen WSDL belgesi, WSDL 'nin tamamını belirtmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="14b28-116">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="14b28-117">Döndürülen WSDL belgesi, diğer WSDL belgelerini içeri aktaracak birkaç içeri aktarma deyimi içerir.</span><span class="sxs-lookup"><span data-stu-id="14b28-117">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="14b28-118">Her bir içeri aktarma ekstresini ilerlemenize ve WSDL 'yi içeri aktarılan wsdl ile birleştiren WSDL belgesinin tamamını derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="14b28-118">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6. <span data-ttu-id="14b28-119">Visual Basic 6,0 ' i açın ve yeni bir standart. exe dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14b28-119">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="14b28-120">Forma bir düğme ekleyin ve tıklama işleyicisine aşağıdaki kodu eklemek için düğmeye çift tıklayın:</span><span class="sxs-lookup"><span data-stu-id="14b28-120">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
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
    > Bilinen ad hatalı biçimlendirilmiş veya hizmet kullanılamıyorsa, `GetObject` "geçersiz söz dizimi" belirten bir hata döndürür.  <span data-ttu-id="14b28-122">Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="14b28-122">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7. <span data-ttu-id="14b28-123">Visual Basic uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="14b28-123">Run the Visual Basic application.</span></span> <span data-ttu-id="14b28-124">Çıkarma çağrısı sonuçlarıyla birlikte bir ileti kutusu görüntülenir (145, 76,54).</span><span class="sxs-lookup"><span data-stu-id="14b28-124">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14b28-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14b28-125">See also</span></span>

- [<span data-ttu-id="14b28-126">Başlarken</span><span class="sxs-lookup"><span data-stu-id="14b28-126">Getting Started</span></span>](../samples/getting-started-sample.md)
- [<span data-ttu-id="14b28-127">COM Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="14b28-127">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)
