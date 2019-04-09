---
title: 'İzlenecek yol: Direct3D9 İçeriğini WPF’de Barındırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 90d0c578c6797342c667f16afdb523b1b4ad6685
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145918"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="e9b67-102">İzlenecek yol: Direct3D9 İçeriğini WPF’de Barındırma</span><span class="sxs-lookup"><span data-stu-id="e9b67-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>
<span data-ttu-id="e9b67-103">Bu izlenecek yol, bir Windows Presentation Foundation (WPF) uygulamasındaki Direct3D9 içeriği barındırma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e9b67-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="e9b67-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="e9b67-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="e9b67-105">Direct3D9 içeriğini barındırmak için bir WPF projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e9b67-105">Create a WPF project to host the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="e9b67-106">Direct3D9 içeriğini içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="e9b67-106">Import the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="e9b67-107">Direct3D9 içeriğini kullanarak görüntüleyin <xref:System.Windows.Interop.D3DImage> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e9b67-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>  
  
 <span data-ttu-id="e9b67-108">İşlemi tamamladığınızda, bir WPF uygulamasında Direct3D9 içeriğini barındırmak nasıl atayacağınızı biliyor olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e9b67-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e9b67-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e9b67-109">Prerequisites</span></span>  
 <span data-ttu-id="e9b67-110">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="e9b67-110">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="e9b67-111">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e9b67-111">Visual Studio.</span></span>  
  
-   <span data-ttu-id="e9b67-112">DirectX SDK 9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="e9b67-112">DirectX SDK 9 or later.</span></span>  
  
-   <span data-ttu-id="e9b67-113">WPF ile uyumlu bir biçimde Direct3D9 içeriği içeren bir DLL.</span><span class="sxs-lookup"><span data-stu-id="e9b67-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="e9b67-114">Daha fazla bilgi için [WPF ve Direct3D9 birlikte çalışması](wpf-and-direct3d9-interoperation.md) ve [izlenecek yol: WPF'de barındırmak için Direct3D9 içeriği oluşturma](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="e9b67-114">For more information, see [WPF and Direct3D9 Interoperation](wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>  
  
## <a name="creating-the-wpf-project"></a><span data-ttu-id="e9b67-115">WPF projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e9b67-115">Creating the WPF Project</span></span>  
 <span data-ttu-id="e9b67-116">İlk adım WPF uygulaması için proje oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="e9b67-116">The first step is to create the project for the WPF application.</span></span>  
  
#### <a name="to-create-the-wpf-project"></a><span data-ttu-id="e9b67-117">WPF projesini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e9b67-117">To create the WPF project</span></span>  
  
-   <span data-ttu-id="e9b67-118">Visual C# ' adlı yeni bir WPF uygulaması projesi oluşturma `D3DHost`.</span><span class="sxs-lookup"><span data-stu-id="e9b67-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="e9b67-119">Daha fazla bilgi için [izlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="e9b67-119">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
     <span data-ttu-id="e9b67-120">MainWindow.xaml açılır [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9b67-120">MainWindow.xaml opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="e9b67-121">Direct3D9 içeriğini alma</span><span class="sxs-lookup"><span data-stu-id="e9b67-121">Importing the Direct3D9 Content</span></span>  
 <span data-ttu-id="e9b67-122">Direct3D9 içeriğini kullanarak yönetilmeyen DLL dosyasından içeri `DllImport` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e9b67-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>  
  
#### <a name="to-import-direct3d9-content"></a><span data-ttu-id="e9b67-123">Direct3D9 içeriğini içeri aktarmak için</span><span class="sxs-lookup"><span data-stu-id="e9b67-123">To import Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="e9b67-124">Kod Düzenleyicisi'nde MainWindow.xaml.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e9b67-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="e9b67-125">Otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e9b67-125">Replace the automatically generated code with the following code.</span></span>  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="e9b67-126">Direct3D9 içeriği barındırma</span><span class="sxs-lookup"><span data-stu-id="e9b67-126">Hosting the Direct3D9 Content</span></span>  
 <span data-ttu-id="e9b67-127">Son olarak, <xref:System.Windows.Interop.D3DImage> Direct3D9 içeriğini barındırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="e9b67-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>  
  
#### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="e9b67-128">Direct3D9 içeriğini barındırmak için</span><span class="sxs-lookup"><span data-stu-id="e9b67-128">To host the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="e9b67-129">MainWindow.xaml içinde otomatik olarak oluşturulan XAML aşağıdaki XAML ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e9b67-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  <span data-ttu-id="e9b67-130">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e9b67-130">Build the project.</span></span>  
  
3.  <span data-ttu-id="e9b67-131">Direct3D9 içeriği bin/Debug klasörüne içeren DLL kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e9b67-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>  
  
4.  <span data-ttu-id="e9b67-132">Projeyi çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e9b67-132">Press F5 to run the project.</span></span>  
  
     <span data-ttu-id="e9b67-133">Direct3D9 içeriği WPF uygulaması içinde görünür.</span><span class="sxs-lookup"><span data-stu-id="e9b67-133">The Direct3D9 content appears within the WPF application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9b67-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9b67-134">See also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="e9b67-135">Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="e9b67-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
