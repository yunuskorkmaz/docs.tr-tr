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
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>İzlenecek yol: WPF'de Barındırmak için Direct3D9 İçeriği Oluşturma
Bu izlenecek yol, bir Windows Presentation Foundation (WPF) uygulamasında barındırmak için uygun olan Direct3D9 içeriğinin nasıl oluşturulacağını gösterir. WPF uygulamalarında Direct3D9 içeriğini barındırma hakkında daha fazla bilgi için bkz. [WPF ve Direct3D9 birlikte](wpf-and-direct3d9-interoperation.md)çalışma.

 Bu kılavuzda, aşağıdaki görevleri gerçekleştirirsiniz:

- Direct3D9 projesi oluşturun.

- WPF uygulamasında barındırmak üzere Direct3D9 Projesini yapılandırın.

 İşiniz bittiğinde, WPF uygulamasında kullanmak üzere Direct3D9 içeriğini içeren bir DLL 'ye sahip olursunuz.

## <a name="prerequisites"></a>Prerequisites
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio 2010.

- DirectX SDK 9 veya üzeri.

## <a name="creating-the-direct3d9-project"></a>Direct3D9 projesi oluşturma
 İlk adım, Direct3D9 projesini oluşturmak ve yapılandırmak için kullanılır.

#### <a name="to-create-the-direct3d9-project"></a>Direct3D9 projesi oluşturmak için

1. C++ Adlı `D3DContent`yeni bir Win32 projesi oluşturun.

     Win32 uygulama Sihirbazı açılır ve hoş geldiniz ekranını görüntüler.

2. **İleri**'ye tıklayın.

     Uygulama ayarları ekranı görüntülenir.

3. **Uygulama türü:** bölümünde, **DLL** seçeneğini belirleyin.

4. **Son**'a tıklayın.

     D3DContent projesi oluşturulur.

5. Çözüm Gezgini, D3DContent projesine sağ tıklayın ve **Özellikler**' i seçin.

     **D3DContent Özellik sayfaları** iletişim kutusu açılır.

6. **C/C++**  düğümünü seçin.

7. **Ek ekleme dizinleri** alanında DirectX içerme klasörünün konumunu belirtin. Bu klasör için varsayılan konum%ProgramFiles%\Microsoft DirectX SDK (*Sürüm*) \ıncludeşeklindedir.

8. Genişletmek için **bağlayıcı** düğümüne çift tıklayın.

9. **Ek kitaplık dizinleri** alanında, DirectX kitaplıkları klasörünün konumunu belirtin. Bu klasör için varsayılan konum%ProgramFiles%\Microsoft DirectX SDK (*Sürüm*) \Lib\x86şeklindedir.

10. **Giriş** düğümünü seçin.

11. **Ek bağımlılıklar** alanında `d3d9.lib` ve `d3dx9.lib` dosyalarını ekleyin.

12. Çözüm Gezgini, projeye `D3DContent.def` adlı yeni bir modül tanım dosyası (. def) ekleyin.

## <a name="creating-the-direct3d9-content"></a>Direct3D9 Içeriği oluşturma
 En iyi performansı elde etmek için, Direct3D9 içeriğinizin belirli ayarları kullanması gerekir. Aşağıdaki kod, en iyi performans özelliklerine sahip bir Direct3D9 yüzeyi oluşturmayı gösterir. Daha fazla bilgi için bkz. [Direct3D9 ve WPF birlikte çalışabilirliği Için performans konuları](performance-considerations-for-direct3d9-and-wpf-interoperability.md).

#### <a name="to-create-the-direct3d9-content"></a>Direct3D9 içeriğini oluşturmak için

1. Çözüm Gezgini kullanarak, aşağıdaki adlı C++ projeye üç sınıf ekleyin.

     `CRenderer` (Sanal yıkıcı ile)

     `CRendererManager`

     `CTriangleRenderer`

2. Kod düzenleyicisinde Renderer. h ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3. Kod düzenleyicisinde Renderer. cpp ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4. Kod düzenleyicisinde RendererManager. h ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5. Kod düzenleyicisinde RendererManager. cpp ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6. Kod düzenleyicisinde üzerinde Epglerenderer. h ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7. Kod düzenleyicisinde üzerinde Epglerenderer. cpp ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8. Kod düzenleyicisinde stdadfx. h ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. Kod düzenleyicisinde DllMain. cpp ' i açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. Kod Düzenleyicisi 'nde D3DContent. def ' i açın.

11. Otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

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

12. Projeyi oluşturun.

## <a name="next-steps"></a>Sonraki Adımlar

- Direct3D9 içeriğini bir WPF uygulamasında barındırın. Daha fazla bilgi için bkz. [Izlenecek yol: WPF 'de Direct3D9 Içeriği barındırma](walkthrough-hosting-direct3d9-content-in-wpf.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [İzlenecek yol: WPF'de Direct3D9 İçeriği Barındırma](walkthrough-hosting-direct3d9-content-in-wpf.md)
