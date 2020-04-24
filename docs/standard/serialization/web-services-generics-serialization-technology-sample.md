---
title: Web Hizmetleri Genel Serileştirme Teknolojisi Örneği
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 467bfe1fd9eb8a0222385c34cb29a90df00dc937
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960759"
---
# <a name="web-services-generics-serialization-technology-sample"></a><span data-ttu-id="0846e-102">Web Hizmetleri Genel Serileştirme Teknolojisi Örneği</span><span class="sxs-lookup"><span data-stu-id="0846e-102">Web Services Generics Serialization Technology Sample</span></span>
[<span data-ttu-id="0846e-103">Örnek indir</span><span class="sxs-lookup"><span data-stu-id="0846e-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 <span data-ttu-id="0846e-104">Bu örnek, ASP.NET Web hizmetlerindeki genel türlerin serileştirilmesi ve denetimini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0846e-104">This sample shows how to use and control the serialization of generics in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="0846e-105">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0846e-105">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="0846e-106">Visual Studio 'Yu açın ve **Dosya** menüsünden **Yeni Web sitesi ' ni** seçin.</span><span class="sxs-lookup"><span data-stu-id="0846e-106">Open Visual Studio and select **New Web Site** from the **File** menu.</span></span>  
  
2. <span data-ttu-id="0846e-107">**Yeni Web sitesi** iletişim kutusunda, istediğiniz programlama dilinizdeki sol bölmeden seçim yapın, ardından sağ bölmedeki **ASP.NET Web hizmeti**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="0846e-107">In the **New Web Site** dialog, select from the left pane your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3. <span data-ttu-id="0846e-108">**Göz at** ' a tıklayın ve \CS\GenericsService alt dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="0846e-108">Click **Browse** and navigate to the \CS\GenericsService subdirectory.</span></span>  
  
4. <span data-ttu-id="0846e-109">Visual Studio'da dosyayı açmak için QuoteService.asmx'e değiştirin seçin.</span><span class="sxs-lookup"><span data-stu-id="0846e-109">Select Service.asmx to open the file in Visual Studio.</span></span>  
  
5. <span data-ttu-id="0846e-110">**Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0846e-110">On the **Build** menu, click **Build Solution**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0846e-111">Bu listedeki ilk beş adımları isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0846e-111">The first five steps in this list are optional.</span></span> <span data-ttu-id="0846e-112">.NET Framework çalışma zamanı, hizmet istenen Web hizmeti ilk zaman otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0846e-112">The .NET Framework runtime will automatically generate the Web service the first time the service is requested.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0846e-113">Örneği oluşturmak için aşağıdaki adımları gerekir.</span><span class="sxs-lookup"><span data-stu-id="0846e-113">The following steps are required to build the sample.</span></span>  
  
1. <span data-ttu-id="0846e-114">Dosya Gezgini 'ni açın ve \CS alt dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="0846e-114">Open File Explorer and navigate to the \CS subdirectory.</span></span>  
  
2. <span data-ttu-id="0846e-115">GenericsService alt dizini simgesine sağ tıklayın ve **Paylaşım ve güvenlik**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0846e-115">Right-click the icon for the GenericsService subdirectory, and select **Sharing and Security**.</span></span>  
  
3. <span data-ttu-id="0846e-116">**Web Paylaşımı** sekmesinde **Bu klasörü paylaşma**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="0846e-116">In the **Web Sharing** tab, select **Share this Folder**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0846e-117">**Diğer adlar** bölmesinde listelenen sanal dizin adını, örneği çalıştırmak için gerekli olacak şekilde bir yere göz atın.</span><span class="sxs-lookup"><span data-stu-id="0846e-117">Take note of the virtual directory name that is listed in the **Aliases** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-build-the-sample-using-internet-information-services"></a><span data-ttu-id="0846e-118">Internet Information Services kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0846e-118">To build the sample using Internet Information Services</span></span>  
  
1. <span data-ttu-id="0846e-119">**Internet Information Services** Yönetimi ek bileşenini açın ve **Web siteleri**' ni genişletin.</span><span class="sxs-lookup"><span data-stu-id="0846e-119">Open the **Internet Information Services** management snap-in and expand **Web Sites**.</span></span>  
  
2. <span data-ttu-id="0846e-120">**Varsayılan Web sitesi**' ni sağ tıklatın, **Yeni**' yi seçin ve ardından **sanal dizin?** ' i seçerek sanal **Dizin Oluşturma Sihirbazı**'nı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0846e-120">Left-click **Default Web Site**, select **New**, and then select **Virtual Directory?** to create the **Virtual Directory Creation Wizard**.</span></span>  
  
3. <span data-ttu-id="0846e-121">**İleri**' ye tıklayın, sanal dizininizin ortak diğer adını girin ve **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0846e-121">Click **Next**, enter the public alias for your virtual directory, and click **Next**.</span></span>  
  
4. <span data-ttu-id="0846e-122">Örneği kaydettiğiniz dizinin yolunu girin (normalde \CS\GenericsService alt dizini) ve **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0846e-122">Enter the path to the directory where you saved the sample (normally the \CS\GenericsService subdirectory) and click **Next**.</span></span> <span data-ttu-id="0846e-123">**İleri** ' ye tıklayarak Sihirbazı sona erdirin.</span><span class="sxs-lookup"><span data-stu-id="0846e-123">Click **Next** to finish the wizard.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0846e-124">**Diğer ad** bölmesinde listelenen sanal dizin adını, örneği çalıştırmak için gerekli olacak şekilde bir yere göz atın.</span><span class="sxs-lookup"><span data-stu-id="0846e-124">Take note of the virtual directory name that is listed in the **Alias** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="0846e-125">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0846e-125">To run the sample</span></span>  
  
1. <span data-ttu-id="0846e-126">Bir tarayıcı penceresi açın ve kendi adres çubuğuna seçin.</span><span class="sxs-lookup"><span data-stu-id="0846e-126">Open a browser window and select its address bar.</span></span>  
  
2. <span data-ttu-id="0846e-127">Türü `http://localhost/[virtual directory]/Service.asmx`, örneği `[virtual directory]` oluşturduğunuzda oluşturduğunuz sanal dizini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0846e-127">Type `http://localhost/[virtual directory]/Service.asmx`, where `[virtual directory]` represents the virtual directory you created when you built the sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0846e-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0846e-128">Remarks</span></span>  
 <span data-ttu-id="0846e-129">Örnek Web hizmeti tanımının bağlantılar içeren bir varsayılan ASP.NET sayfasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0846e-129">The sample displays a default ASP.NET page that contains links to the definition of the Web Service.</span></span> <span data-ttu-id="0846e-130">Web hizmeti için kaynak kodu değiştirme ek olarak görünen özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0846e-130">You can customize the display in addition to modifying the source code for the Web service.</span></span> <span data-ttu-id="0846e-131">Daha fazla bilgi için bkz. [XML Web hizmeti Istemcileri oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0846e-131">For more information, see [Building XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0846e-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0846e-132">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Web.Services>
- <xref:System.Xml.Serialization>
- [<span data-ttu-id="0846e-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="0846e-133">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- <span data-ttu-id="0846e-134">[ASP.NET ve XML Web hizmeti Istemcileri kullanılarak oluşturulan XML Web Hizmetleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0846e-134">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>
