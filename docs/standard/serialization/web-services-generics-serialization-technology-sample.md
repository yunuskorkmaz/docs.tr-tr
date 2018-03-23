---
title: Web Hizmetleri genel türler seri hale getirme teknolojisi örneği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0c29e6778cc0749620a7e38d51303356c2e99436
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
---
# <a name="web-services-generics-serialization-technology-sample"></a><span data-ttu-id="cbb92-102">Web Hizmetleri genel türler seri hale getirme teknolojisi örneği</span><span class="sxs-lookup"><span data-stu-id="cbb92-102">Web Services Generics Serialization Technology Sample</span></span>
[<span data-ttu-id="cbb92-103">Örnek indirme</span><span class="sxs-lookup"><span data-stu-id="cbb92-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 <span data-ttu-id="cbb92-104">Bu örnek, kullanma ve ASP.NET Web Hizmetleri'nda genel türler serileştirmek denetim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cbb92-104">This sample shows how to use and control the serialization of generics in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="cbb92-105">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cbb92-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="cbb92-106">Visual Studio'yu açın ve seçin **yeni Web sitesi** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="cbb92-106">Open Visual Studio and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="cbb92-107">İçinde **yeni Web sitesi** iletişim kutusunda, sol bölmeden istediğiniz programlama dili seçin ve ardından sağ bölmeden **ASP.NET Web hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="cbb92-107">In the **New Web Site** dialog, select from the left pane your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="cbb92-108">Tıklatın **Gözat** ve \CS\GenericsService alt dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="cbb92-108">Click **Browse** and navigate to the \CS\GenericsService subdirectory.</span></span>  
  
4.  <span data-ttu-id="cbb92-109">Visual Studio'da dosyayı açmak için QuoteService.asmx'e değiştirin seçin.</span><span class="sxs-lookup"><span data-stu-id="cbb92-109">Select Service.asmx to open the file in Visual Studio.</span></span>  
  
5.  <span data-ttu-id="cbb92-110">Üzerinde **yapı** menüsünde tıklatın **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="cbb92-110">On the **Build** menu, click **Build Solution**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbb92-111">Bu listedeki ilk beş adımları isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cbb92-111">The first five steps in this list are optional.</span></span> <span data-ttu-id="cbb92-112">.NET Framework çalışma zamanı, hizmet istenen Web hizmeti ilk zaman otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cbb92-112">The .NET Framework runtime will automatically generate the Web service the first time the service is requested.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbb92-113">Örneği oluşturmak için aşağıdaki adımları gerekir.</span><span class="sxs-lookup"><span data-stu-id="cbb92-113">The following steps are required to build the sample.</span></span>  
  
1.  <span data-ttu-id="cbb92-114">Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve \CS alt dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="cbb92-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the \CS subdirectory.</span></span>  
  
2.  <span data-ttu-id="cbb92-115">GenericsService alt simgesine sağ tıklayın ve seçin **paylaşım ve güvenlik**.</span><span class="sxs-lookup"><span data-stu-id="cbb92-115">Right-click the icon for the GenericsService subdirectory, and select **Sharing and Security**.</span></span>  
  
3.  <span data-ttu-id="cbb92-116">İçinde **Web Paylaşımı** sekmesine **bu klasörü paylaş**.</span><span class="sxs-lookup"><span data-stu-id="cbb92-116">In the **Web Sharing** tab, select **Share this Folder**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cbb92-117">İçinde listelenen sanal dizin adını not edin **diğer adlar** bölmesinde, çünkü bu örneği çalıştırmak için gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="cbb92-117">Take note of the virtual directory name that is listed in the **Aliases** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-build-the-sample-using-internet-information-services"></a><span data-ttu-id="cbb92-118">Internet Information Services kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cbb92-118">To build the sample using Internet Information Services</span></span>  
  
1.  <span data-ttu-id="cbb92-119">Açık **Internet Information Services** Yönetimi ek bileşenini ve genişletin **Web siteleri**.</span><span class="sxs-lookup"><span data-stu-id="cbb92-119">Open the **Internet Information Services** management snap-in and expand **Web Sites**.</span></span>  
  
2.  <span data-ttu-id="cbb92-120">Sol tıklatma **varsayılan Web sitesi**seçin **yeni**ve ardından **sanal dizin?** oluşturmak için **sanal dizin oluşturma Sihirbazı**.</span><span class="sxs-lookup"><span data-stu-id="cbb92-120">Left-click **Default Web Site**, select **New**, and then select **Virtual Directory?** to create the **Virtual Directory Creation Wizard**.</span></span>  
  
3.  <span data-ttu-id="cbb92-121">Tıklatın **sonraki**, sanal dizin için ortak diğer adı girin ve tıklatın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="cbb92-121">Click **Next**, enter the public alias for your virtual directory, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="cbb92-122">(Normalde \CS\GenericsService alt) örnek kaydettiğiniz dizinin yolunu girin ve tıklayın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="cbb92-122">Enter the path to the directory where you saved the sample (normally the \CS\GenericsService subdirectory) and click **Next**.</span></span> <span data-ttu-id="cbb92-123">Tıklatın **sonraki** Sihirbazı tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="cbb92-123">Click **Next** to finish the wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cbb92-124">İçinde listelenen sanal dizin adını not edin **diğer ad** bölmesinde, çünkü örnek çalıştıracak şekilde gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="cbb92-124">Take note of the virtual directory name that is listed in the **Alias** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="cbb92-125">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="cbb92-125">To run the sample</span></span>  
  
1.  <span data-ttu-id="cbb92-126">Bir tarayıcı penceresi açın ve kendi adres çubuğuna seçin.</span><span class="sxs-lookup"><span data-stu-id="cbb92-126">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="cbb92-127">Tür **http://localhost/ [sanal directory]/Service.asmx**, burada [sanal dizin] örneği oluşturulduğunda, oluşturduğunuz sanal dizini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cbb92-127">Type **http://localhost/[virtual directory]/Service.asmx**, where [virtual directory] represents the virtual directory you created when you built the sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbb92-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbb92-128">Remarks</span></span>  
 <span data-ttu-id="cbb92-129">Örnek Web hizmeti tanımının bağlantılar içeren bir varsayılan ASP.NET sayfasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cbb92-129">The sample displays a default ASP.NET page that contains links to the definition of the Web Service.</span></span> <span data-ttu-id="cbb92-130">Web hizmeti için kaynak kodu değiştirme ek olarak görünen özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbb92-130">You can customize the display in addition to modifying the source code for the Web service.</span></span> <span data-ttu-id="cbb92-131">Daha fazla bilgi için bkz: [XML Web hizmeti istemci derleme](http://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).</span><span class="sxs-lookup"><span data-stu-id="cbb92-131">For more information, see [Building XML Web Service Clients](http://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb92-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbb92-132">See Also</span></span>  
 <xref:System.Collections.Generic>  
 <xref:System.Web.Services>  
 <xref:System.Xml.Serialization>  
 [<span data-ttu-id="cbb92-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="cbb92-133">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="cbb92-134">ASP.NET ve XML Web hizmeti istemcileri kullanılarak oluşturulan XML Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="cbb92-134">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)
