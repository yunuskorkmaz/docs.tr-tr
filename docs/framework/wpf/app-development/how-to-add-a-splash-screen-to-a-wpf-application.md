---
title: Giriş ekranı ekleme
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 39f53e21c40f036c65894b4f275cd5fb414999be
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740455"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="2e358-102">Nasıl yapılır: WPF Uygulamasına Giriş Ekranı Ekleme</span><span class="sxs-lookup"><span data-stu-id="2e358-102">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="2e358-103">Bu konu, bir Windows Presentation Foundation (WPF) uygulamasına başlangıç penceresi veya *giriş ekranının*nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e358-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="2e358-104">Varolan bir görüntüyü karşılama ekranı olarak eklemek için</span><span class="sxs-lookup"><span data-stu-id="2e358-104">To add an existing image as a splash screen</span></span>

1. <span data-ttu-id="2e358-105">Giriş ekranı için kullanmak istediğiniz bir görüntü oluşturun veya bulun.</span><span class="sxs-lookup"><span data-stu-id="2e358-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="2e358-106">Windows Imaging bileşeni (WIC) tarafından desteklenen herhangi bir görüntü biçimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e358-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="2e358-107">Örneğin, BMP, GIF, JPEG, PNG veya TIFF biçimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e358-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2. <span data-ttu-id="2e358-108">Resim dosyasını WPF uygulaması projesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2e358-108">Add the image file to the WPF Application project.</span></span>

3. <span data-ttu-id="2e358-109">**Çözüm Gezgini**, görüntüyü seçin.</span><span class="sxs-lookup"><span data-stu-id="2e358-109">In **Solution Explorer**, select the image.</span></span>

4. <span data-ttu-id="2e358-110">Özellikler penceresi, **Yapı eylemi** özelliği için aşağı açılan oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2e358-110">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5. <span data-ttu-id="2e358-111">Aşağı açılan listeden **SplashScreen** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="2e358-111">Select **SplashScreen** from the drop-down list.</span></span>

6. <span data-ttu-id="2e358-112">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2e358-112">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="2e358-113">Giriş ekranı görüntüsü ekranın ortasında görünür ve ana uygulama penceresi göründüğünde kaybolur.</span><span class="sxs-lookup"><span data-stu-id="2e358-113">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="2e358-114">Tanıtım ekranını derlemeden dışlamak için</span><span class="sxs-lookup"><span data-stu-id="2e358-114">To exclude the splash screen from build</span></span>

1. <span data-ttu-id="2e358-115">**Çözüm Gezgini**giriş ekranı görüntüsünü seçin.</span><span class="sxs-lookup"><span data-stu-id="2e358-115">In **Solution Explorer**, select the splash screen image.</span></span>

2. <span data-ttu-id="2e358-116">**Özellikler** penceresinde, **derleme eylemini** **hiçbiri**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2e358-116">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="2e358-117">Giriş ekranını bir uygulamadan kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="2e358-117">To remove the splash screen from an application</span></span>

<span data-ttu-id="2e358-118">**Çözüm Gezgini**, giriş ekranı görüntüsünü silin.</span><span class="sxs-lookup"><span data-stu-id="2e358-118">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e358-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e358-119">See also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="2e358-120">[Nasıl yapılır: bir projeye varolan öğeleri ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2e358-120">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
