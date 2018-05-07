---
title: "İzlenecek yol: WPF'de Barındırmak için Direct3D9 İçeriği Oluşturma"
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: f279fb1749be9953e6d09d4b1bd4dd8578d42615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>İzlenecek yol: WPF'de Barındırmak için Direct3D9 İçeriği Oluşturma
Bu kılavuzda, bir Windows Presentation Foundation (WPF) uygulamasında barındırmak için uygun olan Direct3D9 içeriğinin nasıl oluşturulacağını gösterir. WPF uygulamalarında Direct3D9 içeriği barındırma ile ilgili daha fazla bilgi için bkz: [WPF ve Direct3D9 birlikte çalışabilirlik](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
 Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:  
  
-   Direct3D9 projesi oluşturun.  
  
-   Bir WPF uygulamasında barındırmak için Direct3D9 projesini yapılandırın.  
  
 İşiniz bittiğinde, bir WPF uygulamasında kullanmak için Direct3D9 içeriği içeren bir DLL sahip olur.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   DirectX SDK 9or daha sonra.  
  
## <a name="creating-the-direct3d9-project"></a>Direct3D9 projesi oluşturma  
 İlk adım, Direct3D9 projesini oluşturmak ve yapılandırmaktır.  
  
#### <a name="to-create-the-direct3d9-project"></a>Direct3D9 projesi oluşturmak için  
  
1.  C++'ta adlı yeni bir Win32 projesi oluşturma `D3DContent`.  
  
     Win32 Uygulama Sihirbazı'nı açar ve Hoş Geldiniz ekranı görüntüler.  
  
2.  **İleri**'ye tıklayın.  
  
     Uygulama ayarları ekranı görüntülenir.  
  
3.  İçinde **uygulama türü:** bölümünde, select **DLL** seçeneği.  
  
4.  **Son**'a tıklayın.  
  
     D3DContent projesi oluşturulur.  
  
5.  Çözüm Gezgini'nde, D3DContent projesine sağ tıklatın ve **özellikleri**.  
  
     **D3DContent özellik sayfaları** iletişim kutusu açılır.  
  
6.  Seçin **C/C++** düğümü.  
  
7.  İçinde **ek içeren dizinler** alanında, DirectX konumunu içeren klasörü belirtin. Bu klasör için varsayılan konum %ProgramFiles%\Microsoft DirectX SDK olduğu (*sürüm*) \Include.  
  
8.  Çift **bağlayıcı** düğümünü genişletin.  
  
9. İçinde **ek kitaplık dizinleri** alanında, DirectX kitaplık klasörünün konumunu belirtin. Bu klasör için varsayılan konum %ProgramFiles%\Microsoft DirectX SDK olduğu (*sürüm*) \Lib\x86'dır.  
  
10. Seçin **giriş** düğümü.  
  
11. İçinde **ek bağımlılıklar** alanında, eklemek `d3d9.lib` ve `d3dx9.lib` dosyaları.  
  
12. Çözüm Gezgininde adlı yeni modül tanım dosyası (.def) ekleyin `D3DContent.def` projeye.  
  
## <a name="creating-the-direct3d9-content"></a>Direct3D9 içeriği oluşturma  
 En iyi performansı elde etmek Direct3D9 içeriğinizin belirli ayarları kullanmanız gerekir. Aşağıdaki kod en iyi performans özelliklere sahip bir Direct3D9 yüzeyinin nasıl oluşturulacağını gösterir. Daha fazla bilgi için bkz: [Direct3D9 ve WPF birlikte çalışabilirlik için başarım düşünceleri](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
#### <a name="to-create-the-direct3d9-content"></a>Direct3D9 içeriği oluşturmak için  
  
1.  Çözüm Gezgini'nde, üç C++ sınıfları aşağıdaki adlı projeye ekleyin.  
  
     `CRenderer` (sanal yıkıcı ile)  
  
     `CRendererManager`  
  
     `CTriangleRenderer`  
  
2.  Kod düzenleyicisinde Renderer.h'ı açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]  
  
3.  Kod düzenleyicisinde Renderer.cpp'yi açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]  
  
4.  Kod düzenleyicisinde RendererManager.h'ı açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]  
  
5.  Kod düzenleyicisinde RendererManager.cpp'yi açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]  
  
6.  Kod düzenleyicisinde TriangleRenderer.h'ı açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]  
  
7.  Kod düzenleyicisinde TriangleRenderer.cpp'yi açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]  
  
8.  Kod Düzenleyicisi'nde Stdafx.h açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]  
  
9. Kod düzenleyicisinde dllmain.cpp'yi açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]  
  
10. D3DContent.def'i Kod düzenleyicisinde açın.  
  
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
  
-   Bir WPF uygulamasında Direct3D9 içeriğini barındırır. Daha fazla bilgi için bkz: [izlenecek yol: barındırma Direct3D9 içerik WPF'de](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Interop.D3DImage>  
 [Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)  
 [İzlenecek yol: WPF'de Direct3D9 İçeriği Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
