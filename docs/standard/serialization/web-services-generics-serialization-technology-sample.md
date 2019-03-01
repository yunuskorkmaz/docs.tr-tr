---
title: Web Hizmetleri genel serileştirme teknolojisi örneği
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 59224df97d54ac089293068bbb5dfa3fe26a8d8c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971877"
---
# <a name="web-services-generics-serialization-technology-sample"></a><span data-ttu-id="f4072-102">Web Hizmetleri genel serileştirme teknolojisi örneği</span><span class="sxs-lookup"><span data-stu-id="f4072-102">Web Services Generics Serialization Technology Sample</span></span>
[<span data-ttu-id="f4072-103">Örneği indirin</span><span class="sxs-lookup"><span data-stu-id="f4072-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 <span data-ttu-id="f4072-104">Bu örnek, ASP.NET Web Hizmetleri genel türler serileştirmek denetlemek ve nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4072-104">This sample shows how to use and control the serialization of generics in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="f4072-105">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f4072-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="f4072-106">Visual Studio açıp seçin **yeni Web sitesi** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="f4072-106">Open Visual Studio and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="f4072-107">İçinde **yeni Web sitesi** iletişim kutusunda, sol bölmede, istediğiniz programlama dili seçin, sonra sağ bölmeden **ASP.NET Web hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="f4072-107">In the **New Web Site** dialog, select from the left pane your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="f4072-108">Tıklayın **Gözat** ve \CS\GenericsService alt dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="f4072-108">Click **Browse** and navigate to the \CS\GenericsService subdirectory.</span></span>  
  
4.  <span data-ttu-id="f4072-109">Visual Studio'da dosyayı açmak için QuoteService.asmx'e değiştirin seçin.</span><span class="sxs-lookup"><span data-stu-id="f4072-109">Select Service.asmx to open the file in Visual Studio.</span></span>  
  
5.  <span data-ttu-id="f4072-110">Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="f4072-110">On the **Build** menu, click **Build Solution**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4072-111">Bu listedeki ilk beş adımları isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f4072-111">The first five steps in this list are optional.</span></span> <span data-ttu-id="f4072-112">.NET Framework çalışma zamanı, hizmet istenen Web hizmeti ilk zaman otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f4072-112">The .NET Framework runtime will automatically generate the Web service the first time the service is requested.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4072-113">Örneği oluşturmak için aşağıdaki adımları gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4072-113">The following steps are required to build the sample.</span></span>  
  
1.  <span data-ttu-id="f4072-114">Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve \CS alt dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="f4072-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the \CS subdirectory.</span></span>  
  
2.  <span data-ttu-id="f4072-115">GenericsService alt simgesini sağ tıklatın ve seçin **paylaşım ve güvenlik**.</span><span class="sxs-lookup"><span data-stu-id="f4072-115">Right-click the icon for the GenericsService subdirectory, and select **Sharing and Security**.</span></span>  
  
3.  <span data-ttu-id="f4072-116">İçinde **Web Paylaşımı** sekmesinde **bu klasörü paylaş**.</span><span class="sxs-lookup"><span data-stu-id="f4072-116">In the **Web Sharing** tab, select **Share this Folder**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f4072-117">Listelenen sanal dizin adı Not **diğer adlar** bölmesinde örneği çalıştırmak için gerekeceği.</span><span class="sxs-lookup"><span data-stu-id="f4072-117">Take note of the virtual directory name that is listed in the **Aliases** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-build-the-sample-using-internet-information-services"></a><span data-ttu-id="f4072-118">Internet Information Services kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f4072-118">To build the sample using Internet Information Services</span></span>  
  
1.  <span data-ttu-id="f4072-119">Açık **Internet Information Services** yönetim ek bileşenini ve genişletme **Web siteleri**.</span><span class="sxs-lookup"><span data-stu-id="f4072-119">Open the **Internet Information Services** management snap-in and expand **Web Sites**.</span></span>  
  
2.  <span data-ttu-id="f4072-120">Sol tıklatma **varsayılan Web sitesi**seçin **yeni**ve ardından **sanal dizin?** oluşturmak için **sanal dizin oluşturma Sihirbazı**.</span><span class="sxs-lookup"><span data-stu-id="f4072-120">Left-click **Default Web Site**, select **New**, and then select **Virtual Directory?** to create the **Virtual Directory Creation Wizard**.</span></span>  
  
3.  <span data-ttu-id="f4072-121">Tıklayın **sonraki**, sanal dizin için ortak diğer adı girin ve tıklayın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="f4072-121">Click **Next**, enter the public alias for your virtual directory, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="f4072-122">Örnek (normal olarak \CS\GenericsService alt) kaydettiğiniz dizine yolu girin ve tıklayın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="f4072-122">Enter the path to the directory where you saved the sample (normally the \CS\GenericsService subdirectory) and click **Next**.</span></span> <span data-ttu-id="f4072-123">Tıklayın **sonraki** Sihirbazı tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="f4072-123">Click **Next** to finish the wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f4072-124">Listelenen sanal dizin adı Not **diğer** bölmesinde örneği çalıştırmak için gerekeceği.</span><span class="sxs-lookup"><span data-stu-id="f4072-124">Take note of the virtual directory name that is listed in the **Alias** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="f4072-125">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f4072-125">To run the sample</span></span>  
  
1.  <span data-ttu-id="f4072-126">Bir tarayıcı penceresi açın ve kendi adres çubuğuna seçin.</span><span class="sxs-lookup"><span data-stu-id="f4072-126">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="f4072-127">Tür `http://localhost/[virtual directory]/Service.asmx`burada `[virtual directory]` örnek yapılandırıldığında oluşturduğunuz sanal dizini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f4072-127">Type `http://localhost/[virtual directory]/Service.asmx`, where `[virtual directory]` represents the virtual directory you created when you built the sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4072-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4072-128">Remarks</span></span>  
 <span data-ttu-id="f4072-129">Örnek Web hizmeti tanımının bağlantılar içeren bir varsayılan ASP.NET sayfasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f4072-129">The sample displays a default ASP.NET page that contains links to the definition of the Web Service.</span></span> <span data-ttu-id="f4072-130">Web hizmeti için kaynak kodu değiştirme ek olarak görünen özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4072-130">You can customize the display in addition to modifying the source code for the Web service.</span></span> <span data-ttu-id="f4072-131">Daha fazla bilgi için [yapı XML Web hizmeti istemcileriyle](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f4072-131">For more information, see [Building XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4072-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4072-132">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Web.Services>
- <xref:System.Xml.Serialization>
- [<span data-ttu-id="f4072-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="f4072-133">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- <span data-ttu-id="f4072-134">[ASP.NET ve XML Web hizmeti istemcileriyle kullanılarak oluşturulan XML Web Hizmetleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f4072-134">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>
