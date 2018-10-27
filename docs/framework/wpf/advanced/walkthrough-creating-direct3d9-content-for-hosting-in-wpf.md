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
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50049340"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>İzlenecek yol: WPF'de Barındırmak için Direct3D9 İçeriği Oluşturma
Bu izlenecek yol, uygun bir Windows Presentation Foundation (WPF) uygulamasında barındırmak için Direct3D9 içeriği oluşturma işlemi gösterilmektedir. WPF uygulamalarında Direct3D9 içeriği barındırma ile ilgili daha fazla bilgi için bkz: [WPF ve Direct3D9 birlikte çalışması](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).

 Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:

-   Direct3D9 projesi oluşturun.

-   Bir WPF uygulamasında barındırmak için Direct3D9 projeyi yapılandırın.

 İşlemi tamamladığınızda, bir WPF uygulamasını kullanmak için Direct3D9 içeriği içeren bir DLL gerekir.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

-   Visual Studio 2010.

-   DirectX SDK 9or daha sonra.

## <a name="creating-the-direct3d9-project"></a>Direct3D9 projesi oluşturma
 İlk adım, oluşturma ve Direct3D9 proje yapılandırma sağlamaktır.

#### <a name="to-create-the-direct3d9-project"></a>Direct3D9 projeyi oluşturmak için

1.  C++'ta adlı yeni bir Win32 projesi oluşturma `D3DContent`.

     Win32 Uygulama Sihirbazı açılır ve karşılama ekranı görüntülenir.

2.  **İleri**'ye tıklayın.

     Uygulama ayarları ekranı görünür.

3.  İçinde **uygulama türü:** bölümünden **DLL** seçeneği.

4.  **Son**'a tıklayın.

     D3DContent Proje oluşturulur.

5.  Çözüm Gezgini'nde D3DContent projesine sağ tıklayıp **özellikleri**.

     **D3DContent özellik sayfaları** iletişim kutusu açılır.

6.  Seçin **C/C++** düğümü.

7.  İçinde **ek içerik dizinleri** alanında, DirectX konumunu içeren klasörü belirtin. Bu klasör varsayılan konumu %ProgramFiles%\Microsoft DirectX SDK ise (*sürüm*) \Include.

8.  Çift **bağlayıcı** düğümünü genişletin.

9. İçinde **ek kitaplık dizinleri** alanında, DirectX kitaplıkları klasörünün konumunu belirtin. Bu klasör varsayılan konumu %ProgramFiles%\Microsoft DirectX SDK ise (*sürüm*) \Lib\x86'dır.

10. Seçin **giriş** düğümü.

11. İçinde **ek bağımlılıklar** Ekle, alan `d3d9.lib` ve `d3dx9.lib` dosyaları.

12. Çözüm Gezgini'nde, adlı yeni modül tanım dosyası (.def) ekleme `D3DContent.def` projeye.

## <a name="creating-the-direct3d9-content"></a>Direct3D9 içeriği oluşturma
 En iyi performansı elde etmek, Direct3D9 içeriği belirli ayarlarını kullanmanız gerekir. Aşağıdaki kod, en iyi performans özellikleri olan bir Direct3D9 yüzeyinin nasıl oluşturulacağını gösterir. Daha fazla bilgi için [Direct3D9 ve WPF birlikte çalışabilirlik için başarım düşünceleri](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).

#### <a name="to-create-the-direct3d9-content"></a>Direct3D9 içeriği oluşturma

1.  Çözüm Gezgini'nde, üç C++ sınıfları aşağıdaki adlı projeye ekleyin.

     `CRenderer` (sanal yıkıcı ile)

     `CRendererManager`

     `CTriangleRenderer`

2.  Renderer.h'ı Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3.  Renderer.cpp'yi Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4.  RendererManager.h'ı Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5.  RendererManager.cpp'yi Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6.  TriangleRenderer.h'ı Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7.  TriangleRenderer.cpp'yi Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8.  Stdafx.h Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. DllMain.cpp Kod Düzenleyicisi'nde açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. D3DContent.def'i Kod Düzenleyicisi'nde açın.

11. Otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

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

12. Projeyi oluşturun.

## <a name="next-steps"></a>Sonraki Adımlar

-   Direct3D9 içeriği WPF uygulamasında barındırır. Daha fazla bilgi için [izlenecek yol: barındırma Direct3D9 içeriği WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [İzlenecek yol: WPF'de Direct3D9 İçeriği Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)