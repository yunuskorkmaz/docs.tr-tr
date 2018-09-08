---
title: "İzlenecek yol: WPF'de Direct3D9 İçeriği Barındırma"
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 5e7edfbeb9a3cddcdcd81d9c87e5e85bfc947339
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188715"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="24a34-102">İzlenecek yol: WPF'de Direct3D9 İçeriği Barındırma</span><span class="sxs-lookup"><span data-stu-id="24a34-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>
<span data-ttu-id="24a34-103">Bu izlenecek yol, bir Windows Presentation Foundation (WPF) uygulamasındaki Direct3D9 içeriği barındırma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="24a34-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="24a34-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="24a34-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="24a34-105">Direct3D9 içeriğini barındırmak için bir WPF projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24a34-105">Create a WPF project to host the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="24a34-106">Direct3D9 içeriğini içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="24a34-106">Import the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="24a34-107">Direct3D9 içeriğini kullanarak görüntüleyin <xref:System.Windows.Interop.D3DImage> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="24a34-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>  
  
 <span data-ttu-id="24a34-108">İşlemi tamamladığınızda, bir WPF uygulamasında Direct3D9 içeriğini barındırmak nasıl atayacağınızı biliyor olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="24a34-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="24a34-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="24a34-109">Prerequisites</span></span>  
 <span data-ttu-id="24a34-110">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="24a34-110">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="24a34-111">.</span><span class="sxs-lookup"><span data-stu-id="24a34-111">.</span></span>  
  
-   <span data-ttu-id="24a34-112">DirectX SDK 9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="24a34-112">DirectX SDK 9 or later.</span></span>  
  
-   <span data-ttu-id="24a34-113">WPF ile uyumlu bir biçimde Direct3D9 içeriği içeren bir DLL.</span><span class="sxs-lookup"><span data-stu-id="24a34-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="24a34-114">Daha fazla bilgi için [WPF ve Direct3D9 birlikte çalışması](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) ve [izlenecek yol: oluşturma Direct3D9 içeriği barındırma ' WPF'de](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="24a34-114">For more information, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>  
  
## <a name="creating-the-wpf-project"></a><span data-ttu-id="24a34-115">WPF projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="24a34-115">Creating the WPF Project</span></span>  
 <span data-ttu-id="24a34-116">İlk adım WPF uygulaması için proje oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="24a34-116">The first step is to create the project for the WPF application.</span></span>  
  
#### <a name="to-create-the-wpf-project"></a><span data-ttu-id="24a34-117">WPF projesini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="24a34-117">To create the WPF project</span></span>  
  
-   <span data-ttu-id="24a34-118">Visual C# ' adlı yeni bir WPF uygulaması projesi oluşturma `D3DHost`.</span><span class="sxs-lookup"><span data-stu-id="24a34-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="24a34-119">Daha fazla bilgi için [nasıl yapılır: yeni bir WPF uygulaması projesi oluşturma](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="24a34-119">For more information, see [How to: Create a New WPF Application Project](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
     <span data-ttu-id="24a34-120">MainWindow.xaml açılır [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="24a34-120">MainWindow.xaml opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="24a34-121">Direct3D9 içeriğini alma</span><span class="sxs-lookup"><span data-stu-id="24a34-121">Importing the Direct3D9 Content</span></span>  
 <span data-ttu-id="24a34-122">Direct3D9 içeriğini kullanarak yönetilmeyen DLL dosyasından içeri `DllImport` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="24a34-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>  
  
#### <a name="to-import-direct3d9-content"></a><span data-ttu-id="24a34-123">Direct3D9 içeriğini içeri aktarmak için</span><span class="sxs-lookup"><span data-stu-id="24a34-123">To import Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="24a34-124">Kod Düzenleyicisi'nde MainWindow.xaml.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="24a34-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="24a34-125">Otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="24a34-125">Replace the automatically generated code with the following code.</span></span>  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="24a34-126">Direct3D9 içeriği barındırma</span><span class="sxs-lookup"><span data-stu-id="24a34-126">Hosting the Direct3D9 Content</span></span>  
 <span data-ttu-id="24a34-127">Son olarak, <xref:System.Windows.Interop.D3DImage> Direct3D9 içeriğini barındırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="24a34-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>  
  
#### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="24a34-128">Direct3D9 içeriğini barındırmak için</span><span class="sxs-lookup"><span data-stu-id="24a34-128">To host the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="24a34-129">MainWindow.xaml içinde otomatik olarak oluşturulan XAML aşağıdaki XAML ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="24a34-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  <span data-ttu-id="24a34-130">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24a34-130">Build the project.</span></span>  
  
3.  <span data-ttu-id="24a34-131">Direct3D9 içeriği bin/Debug klasörüne içeren DLL kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="24a34-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>  
  
4.  <span data-ttu-id="24a34-132">Projeyi çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="24a34-132">Press F5 to run the project.</span></span>  
  
     <span data-ttu-id="24a34-133">Direct3D9 içeriği WPF uygulaması içinde görünür.</span><span class="sxs-lookup"><span data-stu-id="24a34-133">The Direct3D9 content appears within the WPF application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24a34-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24a34-134">See Also</span></span>  
 <xref:System.Windows.Interop.D3DImage>  
 [<span data-ttu-id="24a34-135">Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="24a34-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
