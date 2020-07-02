---
title: Giriş ekranı ekleme
description: Bir Windows Presentation Foundation (WPF) uygulamasına başlangıç penceresi veya giriş ekranı ekleme hakkında bilgi edinin.
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 0d0cf2e2a550320650c3b4a0c257071a0403c32b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617966"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="899e2-103">Nasıl yapılır: WPF Uygulamasına Giriş Ekranı Ekleme</span><span class="sxs-lookup"><span data-stu-id="899e2-103">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="899e2-104">Bu konu, bir Windows Presentation Foundation (WPF) uygulamasına başlangıç penceresi veya *giriş ekranının*nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="899e2-104">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="899e2-105">Varolan bir görüntüyü karşılama ekranı olarak eklemek için</span><span class="sxs-lookup"><span data-stu-id="899e2-105">To add an existing image as a splash screen</span></span>

1. <span data-ttu-id="899e2-106">Giriş ekranı için kullanmak istediğiniz bir görüntü oluşturun veya bulun.</span><span class="sxs-lookup"><span data-stu-id="899e2-106">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="899e2-107">Windows Imaging bileşeni (WIC) tarafından desteklenen herhangi bir görüntü biçimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="899e2-107">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="899e2-108">Örneğin, BMP, GIF, JPEG, PNG veya TIFF biçimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="899e2-108">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2. <span data-ttu-id="899e2-109">Resim dosyasını WPF uygulaması projesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="899e2-109">Add the image file to the WPF Application project.</span></span>

3. <span data-ttu-id="899e2-110">**Çözüm Gezgini**, görüntüyü seçin.</span><span class="sxs-lookup"><span data-stu-id="899e2-110">In **Solution Explorer**, select the image.</span></span>

4. <span data-ttu-id="899e2-111">Özellikler penceresi, **Yapı eylemi** özelliği için aşağı açılan oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="899e2-111">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5. <span data-ttu-id="899e2-112">Aşağı açılan listeden **SplashScreen** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="899e2-112">Select **SplashScreen** from the drop-down list.</span></span>

6. <span data-ttu-id="899e2-113">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="899e2-113">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="899e2-114">Giriş ekranı görüntüsü ekranın ortasında görünür ve ana uygulama penceresi göründüğünde kaybolur.</span><span class="sxs-lookup"><span data-stu-id="899e2-114">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="899e2-115">Tanıtım ekranını derlemeden dışlamak için</span><span class="sxs-lookup"><span data-stu-id="899e2-115">To exclude the splash screen from build</span></span>

1. <span data-ttu-id="899e2-116">**Çözüm Gezgini**giriş ekranı görüntüsünü seçin.</span><span class="sxs-lookup"><span data-stu-id="899e2-116">In **Solution Explorer**, select the splash screen image.</span></span>

2. <span data-ttu-id="899e2-117">**Özellikler** penceresinde, **derleme eylemini** **hiçbiri**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="899e2-117">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="899e2-118">Giriş ekranını bir uygulamadan kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="899e2-118">To remove the splash screen from an application</span></span>

<span data-ttu-id="899e2-119">**Çözüm Gezgini**, giriş ekranı görüntüsünü silin.</span><span class="sxs-lookup"><span data-stu-id="899e2-119">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="899e2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="899e2-120">See also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="899e2-121">[Nasıl yapılır: bir projeye varolan öğeleri ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="899e2-121">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
