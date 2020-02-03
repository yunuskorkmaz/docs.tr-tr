---
title: WPF 'de Direct3D9 İçeriği barındırma
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: e65b0c59268b44abed289e54181bf0bda9355664
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742613"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="d0a48-102">İzlenecek yol: WPF'de Direct3D9 İçeriği Barındırma</span><span class="sxs-lookup"><span data-stu-id="d0a48-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>

<span data-ttu-id="d0a48-103">Bu izlenecek yol, Direct3D9 içeriğinin bir Windows Presentation Foundation (WPF) uygulamasında nasıl barındıralınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0a48-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>

<span data-ttu-id="d0a48-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0a48-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="d0a48-105">Direct3D9 içeriğini barındırmak için bir WPF projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d0a48-105">Create a WPF project to host the Direct3D9 content.</span></span>

- <span data-ttu-id="d0a48-106">Direct3D9 içeriğini içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="d0a48-106">Import the Direct3D9 content.</span></span>

- <span data-ttu-id="d0a48-107"><xref:System.Windows.Interop.D3DImage> sınıfını kullanarak Direct3D9 içeriğini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="d0a48-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>

 <span data-ttu-id="d0a48-108">İşiniz bittiğinde, bir WPF uygulamasında Direct3D9 içeriğini nasıl barındırabileceğinizi bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0a48-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d0a48-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="d0a48-109">Prerequisites</span></span>

<span data-ttu-id="d0a48-110">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="d0a48-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="d0a48-111">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0a48-111">Visual Studio.</span></span>

- <span data-ttu-id="d0a48-112">DirectX SDK 9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="d0a48-112">DirectX SDK 9 or later.</span></span>

- <span data-ttu-id="d0a48-113">WPF uyumlu bir biçimde Direct3D9 içeriğini içeren bir DLL.</span><span class="sxs-lookup"><span data-stu-id="d0a48-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="d0a48-114">Daha fazla bilgi için bkz. [WPF ve Direct3D9 birlikte](wpf-and-direct3d9-interoperation.md) çalışma ve [Izlenecek yol: WPF 'de barındırmak Için Direct3D9 İçeriği oluşturma](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="d0a48-114">For more information, see [WPF and Direct3D9 Interoperation](wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>

## <a name="creating-the-wpf-project"></a><span data-ttu-id="d0a48-115">WPF projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0a48-115">Creating the WPF Project</span></span>

<span data-ttu-id="d0a48-116">İlk adım WPF uygulaması için proje oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="d0a48-116">The first step is to create the project for the WPF application.</span></span>

### <a name="to-create-the-wpf-project"></a><span data-ttu-id="d0a48-117">WPF projesini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d0a48-117">To create the WPF project</span></span>

<span data-ttu-id="d0a48-118">`D3DHost`görsel C# adında yenı bir WPF uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d0a48-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="d0a48-119">Daha fazla bilgi için bkz. [Izlenecek yol: Ilk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam.</span><span class="sxs-lookup"><span data-stu-id="d0a48-119">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

<span data-ttu-id="d0a48-120">MainWindow. xaml WPF tasarımcısında açılır.</span><span class="sxs-lookup"><span data-stu-id="d0a48-120">MainWindow.xaml opens in the WPF Designer.</span></span>

## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="d0a48-121">Direct3D9 Içeriğini içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="d0a48-121">Importing the Direct3D9 Content</span></span>

<span data-ttu-id="d0a48-122">Yönetilmeyen bir DLL 'den Direct3D9 içeriğini `DllImport` özniteliğini kullanarak içeri aktarırsınız.</span><span class="sxs-lookup"><span data-stu-id="d0a48-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>

### <a name="to-import-direct3d9-content"></a><span data-ttu-id="d0a48-123">Direct3D9 içeriğini içeri aktarmak için</span><span class="sxs-lookup"><span data-stu-id="d0a48-123">To import Direct3D9 content</span></span>

1. <span data-ttu-id="d0a48-124">Kod düzenleyicisinde MainWindow.xaml.cs öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="d0a48-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>

2. <span data-ttu-id="d0a48-125">Otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d0a48-125">Replace the automatically generated code with the following code.</span></span>

    [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]

## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="d0a48-126">Direct3D9 Içeriğini barındırma</span><span class="sxs-lookup"><span data-stu-id="d0a48-126">Hosting the Direct3D9 Content</span></span>

<span data-ttu-id="d0a48-127">Son olarak, Direct3D9 içeriğini barındırmak için <xref:System.Windows.Interop.D3DImage> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0a48-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>

### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="d0a48-128">Direct3D9 içeriğini barındırmak için</span><span class="sxs-lookup"><span data-stu-id="d0a48-128">To host the Direct3D9 content</span></span>

1. <span data-ttu-id="d0a48-129">MainWindow. xaml içinde, otomatik olarak oluşturulan XAML 'yi aşağıdaki XAML ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d0a48-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>

    [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]

2. <span data-ttu-id="d0a48-130">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d0a48-130">Build the project.</span></span>

3. <span data-ttu-id="d0a48-131">Direct3D9 içeriğini içeren DLL 'yi bin/Debug klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d0a48-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>

4. <span data-ttu-id="d0a48-132">Projeyi çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d0a48-132">Press F5 to run the project.</span></span>

    <span data-ttu-id="d0a48-133">Direct3D9 İçeriği WPF uygulaması içinde görünür.</span><span class="sxs-lookup"><span data-stu-id="d0a48-133">The Direct3D9 content appears within the WPF application.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0a48-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0a48-134">See also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="d0a48-135">Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="d0a48-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
