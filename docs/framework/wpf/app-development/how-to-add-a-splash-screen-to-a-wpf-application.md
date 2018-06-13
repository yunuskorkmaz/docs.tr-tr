---
title: 'Nasıl yapılır: WPF Uygulamasına Giriş Ekranı Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 06d6cb7c5a5081d3b6c4979ab50e1caaa726acbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547007"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="375d3-102">Nasıl yapılır: WPF Uygulamasına Giriş Ekranı Ekleme</span><span class="sxs-lookup"><span data-stu-id="375d3-102">How to: Add a Splash Screen to a WPF Application</span></span>
<span data-ttu-id="375d3-103">Bu konuda bir başlangıç penceresi eklemeyi gösterir veya *ekranı*, bir Windows Presentation Foundation (WPF) uygulaması için.</span><span class="sxs-lookup"><span data-stu-id="375d3-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>  
  
### <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="375d3-104">Varolan bir görüntü giriş ekranı eklemek için</span><span class="sxs-lookup"><span data-stu-id="375d3-104">To add an existing image as a splash screen</span></span>  
  
1.  <span data-ttu-id="375d3-105">Oluşturun veya ekranı için kullanmak istediğiniz görüntü bulun.</span><span class="sxs-lookup"><span data-stu-id="375d3-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="375d3-106">Windows görüntüleme bileşeni (WIC) tarafından desteklenen herhangi bir resim biçimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="375d3-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="375d3-107">Örneğin, BMP, GIF, JPEG, PNG veya TIFF biçimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="375d3-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>  
  
2.  <span data-ttu-id="375d3-108">Görüntü dosyası WPF uygulaması projesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="375d3-108">Add the image file to the WPF Application project.</span></span> <span data-ttu-id="375d3-109">Daha fazla bilgi için bkz: [NIB: nasıl yapılır: varolan bir proje öğeleri Ekle](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="375d3-109">For more information, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span>  
  
3.  <span data-ttu-id="375d3-110">Çözüm Gezgini'nde, görüntüyü seçin.</span><span class="sxs-lookup"><span data-stu-id="375d3-110">In Solution Explorer, select the image.</span></span>  
  
4.  <span data-ttu-id="375d3-111">Aşağı açılan okunu Özellikler penceresinde **yapı eylemi** özelliği.</span><span class="sxs-lookup"><span data-stu-id="375d3-111">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>  
  
5.  <span data-ttu-id="375d3-112">Seçin **KarşılamaEkranı** aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="375d3-112">Select **SplashScreen** from the drop-down list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="375d3-113">Görmüyorsanız, **KarşılamaEkranı** seçeneği, kullanmakta olduğunuz kontrol ettiğinizden emin olun [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="375d3-113">If you do not see the **SplashScreen** option, be sure to check that you are using [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 or later.</span></span>  
  
6.  <span data-ttu-id="375d3-114">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="375d3-114">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="375d3-115">Giriş ekranı görüntüsü ekran ortasında görünür ve ana uygulama penceresi göründüğünde kaybolur.</span><span class="sxs-lookup"><span data-stu-id="375d3-115">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="375d3-116">Giriş ekranı uygulamayı kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="375d3-116">To remove the splash screen from an application</span></span>  
  
1.  <span data-ttu-id="375d3-117">Çözüm Gezgini'nde giriş ekranı görüntüsü seçin.</span><span class="sxs-lookup"><span data-stu-id="375d3-117">In Solution Explorer, select the splash screen image.</span></span>  
  
2.  <span data-ttu-id="375d3-118">Özellikler penceresinde ayarlayın **yapı eylemi** için **hiçbiri**.</span><span class="sxs-lookup"><span data-stu-id="375d3-118">In the Properties window, set the **Build Action** to **None**.</span></span>  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="375d3-119">Giriş ekranı uygulamayı kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="375d3-119">To remove the splash screen from an application</span></span>  
  
-   <span data-ttu-id="375d3-120">Çözüm Gezgini'nde giriş ekranı görüntüsü silin.</span><span class="sxs-lookup"><span data-stu-id="375d3-120">In Solution Explorer, delete the splash screen image.</span></span>  
  
-   <span data-ttu-id="375d3-121">Karşılama ekranı resmini projeden çıkarın.</span><span class="sxs-lookup"><span data-stu-id="375d3-121">Exclude the splash screen image from the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="375d3-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="375d3-122">See Also</span></span>  
 <xref:System.Windows.SplashScreen>  
 [<span data-ttu-id="375d3-123">NIB: nasıl yapılır: Varolan öğeleri için bir proje ekleyin</span><span class="sxs-lookup"><span data-stu-id="375d3-123">NIB:How to: Add Existing Items to a Project</span></span>](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)
