---
title: Barındırma için Direct3D9 Içeriği oluşturma
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 847ee74da5b295c2c9d3824b3df74f94bc98a4db
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727922"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a><span data-ttu-id="fc4ba-102">İzlenecek yol: WPF'de Barındırmak için Direct3D9 İçeriği Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc4ba-102">Walkthrough: Creating Direct3D9 Content for Hosting in WPF</span></span>
<span data-ttu-id="fc4ba-103">Bu izlenecek yol, bir Windows Presentation Foundation (WPF) uygulamasında barındırmak için uygun olan Direct3D9 içeriğinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-103">This walkthrough shows how to create Direct3D9 content that is suitable for hosting in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="fc4ba-104">WPF uygulamalarında Direct3D9 içeriğini barındırma hakkında daha fazla bilgi için bkz. [WPF ve Direct3D9 birlikte](wpf-and-direct3d9-interoperation.md)çalışma.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-104">For more information on hosting Direct3D9 content in WPF applications, see [WPF and Direct3D9 Interoperation](wpf-and-direct3d9-interoperation.md).</span></span>

 <span data-ttu-id="fc4ba-105">Bu kılavuzda, aşağıdaki görevleri gerçekleştirirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fc4ba-105">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="fc4ba-106">Direct3D9 projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-106">Create a Direct3D9 project.</span></span>

- <span data-ttu-id="fc4ba-107">WPF uygulamasında barındırmak üzere Direct3D9 Projesini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-107">Configure the Direct3D9 project for hosting in a WPF application.</span></span>

 <span data-ttu-id="fc4ba-108">İşiniz bittiğinde, WPF uygulamasında kullanmak üzere Direct3D9 içeriğini içeren bir DLL 'ye sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-108">When you are finished, you will have a DLL that contains Direct3D9 content for use in a WPF application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fc4ba-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="fc4ba-109">Prerequisites</span></span>
 <span data-ttu-id="fc4ba-110">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="fc4ba-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="fc4ba-111">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-111">Visual Studio 2010.</span></span>

- <span data-ttu-id="fc4ba-112">DirectX SDK 9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-112">DirectX SDK 9 or later.</span></span>

## <a name="creating-the-direct3d9-project"></a><span data-ttu-id="fc4ba-113">Direct3D9 projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc4ba-113">Creating the Direct3D9 Project</span></span>
 <span data-ttu-id="fc4ba-114">İlk adım, Direct3D9 projesini oluşturmak ve yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-114">The first step is to create and configure the Direct3D9 project.</span></span>

#### <a name="to-create-the-direct3d9-project"></a><span data-ttu-id="fc4ba-115">Direct3D9 projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fc4ba-115">To create the Direct3D9 project</span></span>

1. <span data-ttu-id="fc4ba-116">C++ Adlı `D3DContent`yeni bir Win32 projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-116">Create a new Win32 Project in C++ named `D3DContent`.</span></span>

     <span data-ttu-id="fc4ba-117">Win32 uygulama Sihirbazı açılır ve hoş geldiniz ekranını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-117">The Win32 Application Wizard opens and displays the Welcome screen.</span></span>

2. <span data-ttu-id="fc4ba-118">**İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-118">Click **Next**.</span></span>

     <span data-ttu-id="fc4ba-119">Uygulama ayarları ekranı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-119">The Application Settings screen appears.</span></span>

3. <span data-ttu-id="fc4ba-120">**Uygulama türü:** bölümünde, **DLL** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-120">In the **Application type:** section, select the **DLL** option.</span></span>

4. <span data-ttu-id="fc4ba-121">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-121">Click **Finish**.</span></span>

     <span data-ttu-id="fc4ba-122">D3DContent projesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-122">The D3DContent project is generated.</span></span>

5. <span data-ttu-id="fc4ba-123">Çözüm Gezgini, D3DContent projesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-123">In Solution Explorer, right-click the D3DContent project and select **Properties**.</span></span>

     <span data-ttu-id="fc4ba-124">**D3DContent Özellik sayfaları** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-124">The **D3DContent Property Pages** dialog box opens.</span></span>

6. <span data-ttu-id="fc4ba-125">**C/C++**  düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-125">Select the **C/C++** node.</span></span>

7. <span data-ttu-id="fc4ba-126">**Ek ekleme dizinleri** alanında DirectX içerme klasörünün konumunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-126">In the **Additional Include Directories** field, specify the location of the DirectX include folder.</span></span> <span data-ttu-id="fc4ba-127">Bu klasör için varsayılan konum%ProgramFiles%\Microsoft DirectX SDK (*Sürüm*) \ıncludeşeklindedir.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-127">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Include.</span></span>

8. <span data-ttu-id="fc4ba-128">Genişletmek için **bağlayıcı** düğümüne çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-128">Double-click the **Linker** node to expand it.</span></span>

9. <span data-ttu-id="fc4ba-129">**Ek kitaplık dizinleri** alanında, DirectX kitaplıkları klasörünün konumunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-129">In the **Additional Library Directories** field, specify the location of the DirectX libraries folder.</span></span> <span data-ttu-id="fc4ba-130">Bu klasör için varsayılan konum%ProgramFiles%\Microsoft DirectX SDK (*Sürüm*) \Lib\x86şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-130">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Lib\x86.</span></span>

10. <span data-ttu-id="fc4ba-131">**Giriş** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-131">Select the **Input** node.</span></span>

11. <span data-ttu-id="fc4ba-132">**Ek bağımlılıklar** alanında `d3d9.lib` ve `d3dx9.lib` dosyalarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-132">In the **Additional Dependencies** field, add the `d3d9.lib` and `d3dx9.lib` files.</span></span>

12. <span data-ttu-id="fc4ba-133">Çözüm Gezgini, projeye `D3DContent.def` adlı yeni bir modül tanım dosyası (. def) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-133">In Solution Explorer, add a new module definition file (.def) named `D3DContent.def` to the project.</span></span>

## <a name="creating-the-direct3d9-content"></a><span data-ttu-id="fc4ba-134">Direct3D9 Içeriği oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc4ba-134">Creating the Direct3D9 Content</span></span>
 <span data-ttu-id="fc4ba-135">En iyi performansı elde etmek için, Direct3D9 içeriğinizin belirli ayarları kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-135">To get the best performance, your Direct3D9 content must use particular settings.</span></span> <span data-ttu-id="fc4ba-136">Aşağıdaki kod, en iyi performans özelliklerine sahip bir Direct3D9 yüzeyi oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-136">The following code shows how to create a Direct3D9 surface that has the best performance characteristics.</span></span> <span data-ttu-id="fc4ba-137">Daha fazla bilgi için bkz. [Direct3D9 ve WPF birlikte çalışabilirliği Için performans konuları](performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span><span class="sxs-lookup"><span data-stu-id="fc4ba-137">For more information, see [Performance Considerations for Direct3D9 and WPF Interoperability](performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span></span>

#### <a name="to-create-the-direct3d9-content"></a><span data-ttu-id="fc4ba-138">Direct3D9 içeriğini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fc4ba-138">To create the Direct3D9 content</span></span>

1. <span data-ttu-id="fc4ba-139">Çözüm Gezgini kullanarak, aşağıdaki adlı C++ projeye üç sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-139">Using Solution Explorer, add three C++ classes to the project named the following.</span></span>

     <span data-ttu-id="fc4ba-140">`CRenderer` (Sanal yıkıcı ile)</span><span class="sxs-lookup"><span data-stu-id="fc4ba-140">`CRenderer` (with virtual destructor)</span></span>

     `CRendererManager`

     `CTriangleRenderer`

2. <span data-ttu-id="fc4ba-141">Kod düzenleyicisinde Renderer. h ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-141">Open Renderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3. <span data-ttu-id="fc4ba-142">Kod düzenleyicisinde Renderer. cpp ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-142">Open Renderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4. <span data-ttu-id="fc4ba-143">Kod düzenleyicisinde RendererManager. h ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-143">Open RendererManager.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5. <span data-ttu-id="fc4ba-144">Kod düzenleyicisinde RendererManager. cpp ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-144">Open RendererManager.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6. <span data-ttu-id="fc4ba-145">Kod düzenleyicisinde üzerinde Epglerenderer. h ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-145">Open TriangleRenderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7. <span data-ttu-id="fc4ba-146">Kod düzenleyicisinde üzerinde Epglerenderer. cpp ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-146">Open TriangleRenderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8. <span data-ttu-id="fc4ba-147">Kod düzenleyicisinde stdadfx. h ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-147">Open stdafx.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. <span data-ttu-id="fc4ba-148">Kod düzenleyicisinde DllMain. cpp ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-148">Open dllmain.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. <span data-ttu-id="fc4ba-149">Kod Düzenleyicisi 'nde D3DContent. def ' i açın.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-149">Open D3DContent.def in the code editor.</span></span>

11. <span data-ttu-id="fc4ba-150">Otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-150">Replace the automatically generated code with the following code.</span></span>

    ```cpp
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

12. <span data-ttu-id="fc4ba-151">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-151">Build the project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fc4ba-152">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="fc4ba-152">Next Steps</span></span>

- <span data-ttu-id="fc4ba-153">Direct3D9 içeriğini bir WPF uygulamasında barındırın.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-153">Host the Direct3D9 content in a WPF application.</span></span> <span data-ttu-id="fc4ba-154">Daha fazla bilgi için bkz. [Izlenecek yol: WPF 'de Direct3D9 Içeriği barındırma](walkthrough-hosting-direct3d9-content-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="fc4ba-154">For more information, see [Walkthrough: Hosting Direct3D9 Content in WPF](walkthrough-hosting-direct3d9-content-in-wpf.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fc4ba-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc4ba-155">See also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="fc4ba-156">Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="fc4ba-156">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [<span data-ttu-id="fc4ba-157">İzlenecek yol: WPF'de Direct3D9 İçeriği Barındırma</span><span class="sxs-lookup"><span data-stu-id="fc4ba-157">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>](walkthrough-hosting-direct3d9-content-in-wpf.md)
