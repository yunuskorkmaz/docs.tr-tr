---
title: 'Nasıl yapılır: WPF Uygulamasına Giriş Ekranı Ekleme'
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 46efa041736870c5c0f08baa321ef0dc53cacc0d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502760"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="16e6b-102">Nasıl yapılır: WPF Uygulamasına Giriş Ekranı Ekleme</span><span class="sxs-lookup"><span data-stu-id="16e6b-102">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="16e6b-103">Bu konuda, bir başlangıç penceresi ekleme işlemi açıklanır veya *giriş ekranı*, bir Windows Presentation Foundation (WPF) uygulaması için.</span><span class="sxs-lookup"><span data-stu-id="16e6b-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="16e6b-104">Giriş ekranı varolan bir görüntü eklemek için</span><span class="sxs-lookup"><span data-stu-id="16e6b-104">To add an existing image as a splash screen</span></span>

1.  <span data-ttu-id="16e6b-105">Oluşturun veya Karşılama ekranı olarak kullanmak istediğiniz görüntüyü bulun.</span><span class="sxs-lookup"><span data-stu-id="16e6b-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="16e6b-106">Windows görüntüleme bileşeni (WIC) tarafından desteklenen herhangi bir resim biçimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16e6b-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="16e6b-107">Örneğin, BMP, GIF, JPEG, PNG ve TIFF biçimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16e6b-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2.  <span data-ttu-id="16e6b-108">Görüntü dosyası WPF uygulaması projesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="16e6b-108">Add the image file to the WPF Application project.</span></span>

3.  <span data-ttu-id="16e6b-109">İçinde **Çözüm Gezgini**, görüntüyü seçin.</span><span class="sxs-lookup"><span data-stu-id="16e6b-109">In **Solution Explorer**, select the image.</span></span>

4.  <span data-ttu-id="16e6b-110">Özellikler penceresinde, aşağı açılan oka tıklayın **derleme eylemi** özelliği.</span><span class="sxs-lookup"><span data-stu-id="16e6b-110">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5.  <span data-ttu-id="16e6b-111">Seçin **SplashScreen** aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="16e6b-111">Select **SplashScreen** from the drop-down list.</span></span>

6.  <span data-ttu-id="16e6b-112">Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="16e6b-112">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="16e6b-113">Karşılama ekranı görüntüsü ekranın ortasında görünür ve ana uygulama penceresini göründüğünde kaybolur.</span><span class="sxs-lookup"><span data-stu-id="16e6b-113">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="16e6b-114">Karşılama ekranında derlemeden hariç tutmak için</span><span class="sxs-lookup"><span data-stu-id="16e6b-114">To exclude the splash screen from build</span></span>

1.  <span data-ttu-id="16e6b-115">İçinde **Çözüm Gezgini**, Karşılama ekran görüntüsünü seçin.</span><span class="sxs-lookup"><span data-stu-id="16e6b-115">In **Solution Explorer**, select the splash screen image.</span></span>

2.  <span data-ttu-id="16e6b-116">İçinde **özellikleri** penceresinde **derleme eylemi** için **hiçbiri**.</span><span class="sxs-lookup"><span data-stu-id="16e6b-116">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="16e6b-117">Bir uygulamaya ait karşılama ekranında kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="16e6b-117">To remove the splash screen from an application</span></span>

<span data-ttu-id="16e6b-118">İçinde **Çözüm Gezgini**, Karşılama ekranı görüntüyü silin.</span><span class="sxs-lookup"><span data-stu-id="16e6b-118">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="16e6b-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16e6b-119">See Also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="16e6b-120">[Nasıl yapılır: bir projeye var olan öğeleri Ekle](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="16e6b-120">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
