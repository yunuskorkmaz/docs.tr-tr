---
title: "İzlenecek yol: WPF'de Barındırmak için Direct3D9 İçeriği Oluşturma"
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 321c4ba8659bd2226fff96e74e81ef24f0077c3d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200920"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a><span data-ttu-id="86240-102">İzlenecek yol: WPF'de Barındırmak için Direct3D9 İçeriği Oluşturma</span><span class="sxs-lookup"><span data-stu-id="86240-102">Walkthrough: Creating Direct3D9 Content for Hosting in WPF</span></span>
<span data-ttu-id="86240-103">Bu izlenecek yol, uygun bir Windows Presentation Foundation (WPF) uygulamasında barındırmak için Direct3D9 içeriği oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="86240-103">This walkthrough shows how to create Direct3D9 content that is suitable for hosting in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="86240-104">WPF uygulamalarında Direct3D9 içeriği barındırma ile ilgili daha fazla bilgi için bkz: [WPF ve Direct3D9 birlikte çalışması](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="86240-104">For more information on hosting Direct3D9 content in WPF applications, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).</span></span>

 <span data-ttu-id="86240-105">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="86240-105">In this walkthrough, you perform the following tasks:</span></span>

-   <span data-ttu-id="86240-106">Direct3D9 projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="86240-106">Create a Direct3D9 project.</span></span>

-   <span data-ttu-id="86240-107">Bir WPF uygulamasında barındırmak için Direct3D9 projeyi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="86240-107">Configure the Direct3D9 project for hosting in a WPF application.</span></span>

 <span data-ttu-id="86240-108">İşlemi tamamladığınızda, bir WPF uygulamasını kullanmak için Direct3D9 içeriği içeren bir DLL gerekir.</span><span class="sxs-lookup"><span data-stu-id="86240-108">When you are finished, you will have a DLL that contains Direct3D9 content for use in a WPF application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="86240-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="86240-109">Prerequisites</span></span>
 <span data-ttu-id="86240-110">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="86240-110">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="86240-111">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="86240-111">Visual Studio 2010.</span></span>

-   <span data-ttu-id="86240-112">DirectX SDK 9or daha sonra.</span><span class="sxs-lookup"><span data-stu-id="86240-112">DirectX SDK 9or later.</span></span>

## <a name="creating-the-direct3d9-project"></a><span data-ttu-id="86240-113">Direct3D9 projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="86240-113">Creating the Direct3D9 Project</span></span>
 <span data-ttu-id="86240-114">İlk adım, oluşturma ve Direct3D9 proje yapılandırma sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="86240-114">The first step is to create and configure the Direct3D9 project.</span></span>

#### <a name="to-create-the-direct3d9-project"></a><span data-ttu-id="86240-115">Direct3D9 projeyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="86240-115">To create the Direct3D9 project</span></span>

1.  <span data-ttu-id="86240-116">C++'ta adlı yeni bir Win32 projesi oluşturma `D3DContent`.</span><span class="sxs-lookup"><span data-stu-id="86240-116">Create a new Win32 Project in C++ named `D3DContent`.</span></span>

     <span data-ttu-id="86240-117">Win32 Uygulama Sihirbazı açılır ve karşılama ekranı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="86240-117">The Win32 Application Wizard opens and displays the Welcome screen.</span></span>

2.  <span data-ttu-id="86240-118">**İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="86240-118">Click **Next**.</span></span>

     <span data-ttu-id="86240-119">Uygulama ayarları ekranı görünür.</span><span class="sxs-lookup"><span data-stu-id="86240-119">The Application Settings screen appears.</span></span>

3.  <span data-ttu-id="86240-120">İçinde **uygulama türü:** bölümünden **DLL** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="86240-120">In the **Application type:** section, select the **DLL** option.</span></span>

4.  <span data-ttu-id="86240-121">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="86240-121">Click **Finish**.</span></span>

     <span data-ttu-id="86240-122">D3DContent Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="86240-122">The D3DContent project is generated.</span></span>

5.  <span data-ttu-id="86240-123">Çözüm Gezgini'nde D3DContent projesine sağ tıklayıp **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="86240-123">In Solution Explorer, right-click the D3DContent project and select **Properties**.</span></span>

     <span data-ttu-id="86240-124">**D3DContent özellik sayfaları** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="86240-124">The **D3DContent Property Pages** dialog box opens.</span></span>

6.  <span data-ttu-id="86240-125">Seçin **C/C++** düğümü.</span><span class="sxs-lookup"><span data-stu-id="86240-125">Select the **C/C++** node.</span></span>

7.  <span data-ttu-id="86240-126">İçinde **ek içerik dizinleri** alanında, DirectX konumunu içeren klasörü belirtin.</span><span class="sxs-lookup"><span data-stu-id="86240-126">In the **Additional Include Directories** field, specify the location of the DirectX include folder.</span></span> <span data-ttu-id="86240-127">Bu klasör varsayılan konumu %ProgramFiles%\Microsoft DirectX SDK ise (*sürüm*) \Include.</span><span class="sxs-lookup"><span data-stu-id="86240-127">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Include.</span></span>

8.  <span data-ttu-id="86240-128">Çift **bağlayıcı** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="86240-128">Double-click the **Linker** node to expand it.</span></span>

9. <span data-ttu-id="86240-129">İçinde **ek kitaplık dizinleri** alanında, DirectX kitaplıkları klasörünün konumunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="86240-129">In the **Additional Library Directories** field, specify the location of the DirectX libraries folder.</span></span> <span data-ttu-id="86240-130">Bu klasör varsayılan konumu %ProgramFiles%\Microsoft DirectX SDK ise (*sürüm*) \Lib\x86'dır.</span><span class="sxs-lookup"><span data-stu-id="86240-130">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Lib\x86.</span></span>

10. <span data-ttu-id="86240-131">Seçin **giriş** düğümü.</span><span class="sxs-lookup"><span data-stu-id="86240-131">Select the **Input** node.</span></span>

11. <span data-ttu-id="86240-132">İçinde **ek bağımlılıklar** Ekle, alan `d3d9.lib` ve `d3dx9.lib` dosyaları.</span><span class="sxs-lookup"><span data-stu-id="86240-132">In the **Additional Dependencies** field, add the `d3d9.lib` and `d3dx9.lib` files.</span></span>

12. <span data-ttu-id="86240-133">Çözüm Gezgini'nde, adlı yeni modül tanım dosyası (.def) ekleme `D3DContent.def` projeye.</span><span class="sxs-lookup"><span data-stu-id="86240-133">In Solution Explorer, add a new module definition file (.def) named `D3DContent.def` to the project.</span></span>

## <a name="creating-the-direct3d9-content"></a><span data-ttu-id="86240-134">Direct3D9 içeriği oluşturma</span><span class="sxs-lookup"><span data-stu-id="86240-134">Creating the Direct3D9 Content</span></span>
 <span data-ttu-id="86240-135">En iyi performansı elde etmek, Direct3D9 içeriği belirli ayarlarını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="86240-135">To get the best performance, your Direct3D9 content must use particular settings.</span></span> <span data-ttu-id="86240-136">Aşağıdaki kod, en iyi performans özellikleri olan bir Direct3D9 yüzeyinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="86240-136">The following code shows how to create a Direct3D9 surface that has the best performance characteristics.</span></span> <span data-ttu-id="86240-137">Daha fazla bilgi için [Direct3D9 ve WPF birlikte çalışabilirlik için başarım düşünceleri](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span><span class="sxs-lookup"><span data-stu-id="86240-137">For more information, see [Performance Considerations for Direct3D9 and WPF Interoperability](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span></span>

#### <a name="to-create-the-direct3d9-content"></a><span data-ttu-id="86240-138">Direct3D9 içeriği oluşturma</span><span class="sxs-lookup"><span data-stu-id="86240-138">To create the Direct3D9 content</span></span>

1.  <span data-ttu-id="86240-139">Çözüm Gezgini'nde, üç C++ sınıfları aşağıdaki adlı projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="86240-139">Using Solution Explorer, add three C++ classes to the project named the following.</span></span>

     <span data-ttu-id="86240-140">`CRenderer` (sanal yıkıcı ile)</span><span class="sxs-lookup"><span data-stu-id="86240-140">`CRenderer` (with virtual destructor)</span></span>

     `CRendererManager`

     `CTriangleRenderer`

2.  <span data-ttu-id="86240-141">Renderer.h'ı Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="86240-141">Open Renderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3.  <span data-ttu-id="86240-142">Renderer.cpp'yi Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="86240-142">Open Renderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4.  <span data-ttu-id="86240-143">RendererManager.h'ı Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="86240-143">Open RendererManager.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5.  <span data-ttu-id="86240-144">RendererManager.cpp'yi Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="86240-144">Open RendererManager.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6.  <span data-ttu-id="86240-145">TriangleRenderer.h'ı Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="86240-145">Open TriangleRenderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7.  <span data-ttu-id="86240-146">TriangleRenderer.cpp'yi Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="86240-146">Open TriangleRenderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8.  <span data-ttu-id="86240-147">Stdafx.h Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="86240-147">Open stdafx.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. <span data-ttu-id="86240-148">DllMain.cpp Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="86240-148">Open dllmain.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. <span data-ttu-id="86240-149">D3DContent.def'i Kod Düzenleyicisi'nde açın.</span><span class="sxs-lookup"><span data-stu-id="86240-149">Open D3DContent.def in the code editor.</span></span>

11. <span data-ttu-id="86240-150">Otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="86240-150">Replace the automatically generated code with the following code.</span></span>

    ```
    LIBRARY "D3DContent"

    EXPORTS

    SetSize
    SetAlpha
    SetNumDesiredSamples
    SetAdapter

    GetBackBufferNoRef
    Render
    Destroy
    ```

12. <span data-ttu-id="86240-151">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="86240-151">Build the project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="86240-152">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="86240-152">Next Steps</span></span>

-   <span data-ttu-id="86240-153">Direct3D9 içeriği WPF uygulamasında barındırır.</span><span class="sxs-lookup"><span data-stu-id="86240-153">Host the Direct3D9 content in a WPF application.</span></span> <span data-ttu-id="86240-154">Daha fazla bilgi için [izlenecek yol: barındırma Direct3D9 içeriği WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="86240-154">For more information, see [Walkthrough: Hosting Direct3D9 Content in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="86240-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86240-155">See Also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="86240-156">Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="86240-156">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [<span data-ttu-id="86240-157">İzlenecek yol: WPF'de Direct3D9 İçeriği Barındırma</span><span class="sxs-lookup"><span data-stu-id="86240-157">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)