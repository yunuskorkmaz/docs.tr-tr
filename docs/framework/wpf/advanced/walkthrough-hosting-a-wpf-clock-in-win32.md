---
title: "İzlenecek yol: Win32'de WPF Saati Barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: caf652f8a80da8e927a74ffc012d09b2389b1b09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>İzlenecek yol: Win32'de WPF Saati Barındırma
Yerleştirilecek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamaları, <xref:System.Windows.Interop.HwndSource>, içeren HWND sağlayan, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Oluşturduğunuz ilk <xref:System.Windows.Interop.HwndSource>, CreateWindow'unkine benzer parametreler vererek.  Size sonra <xref:System.Windows.Interop.HwndSource> hakkında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde içerik istiyor.  Son olarak, dışı HWND almak <xref:System.Windows.Interop.HwndSource>. Bu kılavuz karma oluşturma gösterilmektedir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işletim sistemi in uygulama **tarih ve saat özellikleri** iletişim.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bkz: [WPF ve Win32 birlikte çalışabilirlik](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
## <a name="how-to-use-this-tutorial"></a>Bu öğretici nasıl kullanılır?  
 Bu öğretici, birlikte çalışabilirlik uygulama oluşturmanın önemli adımlar yoğunlaşır. Öğretici bir örneği tarafından desteklenen [Win32 saati birlikte çalışabilirlik örneği](http://go.microsoft.com/fwlink/?LinkID=160051), ancak bu örnek son ürünün yansıtıcı. Varolan ile başlayan gibi Bu öğreticide adımları belgeler [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kendi projesi, belki de önceden var olan bir proje ve ekleme barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanıza. Son ürününüzü karşılaştırabilirsiniz [Win32 saati birlikte çalışabilirlik örneği](http://go.microsoft.com/fwlink/?LinkID=160051).  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>İzlenecek yol Win32 içinde Windows Presentation Framework'ün (HwndSource)  
 Aşağıdaki grafikte Bu öğreticinin hedeflediği son ürünü gösterir:  
  
 ![Tarih ve Saat Özellikleri iletişim kutusu](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")  
  
 C++ oluşturarak bu iletişim kutusunu yeniden oluşturabilirsiniz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] proje [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]ve aşağıdaki oluşturmak için iletişim kutusu düzenleyicisini kullanma:  
  
 ![Tarih ve Saat Özellikleri iletişim kutusu](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")  
  
 (Kullanmak gerekmez [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] kullanmak için <xref:System.Windows.Interop.HwndSource>, ve yazmak için C++ kullanma gerekmez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programları, ancak bunu yapmak için oldukça tipik bir yoludur ve kendisi de bir adım öğretici açıklaması için uygundur).  
  
 Beş belirli yerleştirmek için gerçekleştirmeniz gereken bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iletişim saati:  
  
1.  Etkinleştirme, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] yönetilen kod projesi (**/CLR**) içinde proje ayarlarını değiştirerek [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].  
  
2.  Oluşturma bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> ayrı bir DLL içinde.  
  
3.  Put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> içinde bir <xref:System.Windows.Interop.HwndSource>.  
  
4.  Bunun için bir HWND alın <xref:System.Windows.Controls.Page> kullanarak <xref:System.Windows.Interop.HwndSource.Handle%2A> özelliği.  
  
5.  Kullanım [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HWND büyük içinde nereye yerleştireceğinizi karar vermek için [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulama  
  
## <a name="clr"></a>/ CLR  
 Etkinleştirmek için bunu yönetilmeyen ilk adımdır [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] çağırana projeye yönetilen kod.  Kullanın ve Main yöntemi ile kullanmak için ayarlamak istediğiniz gerekli DLL'leri bağlayacak/CLR derleyici seçeneği kullandığınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 C++ projesi içinde yönetilen kod kullanımını etkinleştirmek için: win32clock projeye sağ tıklayın ve seçin **özellikleri**.  Üzerinde **genel** özellik sayfası (varsayılan) değiştirmek için ortak dil çalışma zamanı desteğini `/clr`.  
  
 Ardından, DLL'ler için gerekli başvurular ekleyin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll ve UIAutomationTypes.dll. (Yönergeleri izleyerek C: sürücüsüne işletim sisteminin yüklü olduğu varsayılır.)  
  
1.  Win32clock projesine sağ tıklatın ve **başvuruları...** ve o iletişim içinde:  
  
2.  Win32clock projesine sağ tıklatın ve **başvuruları...** .  
  
3.  Tıklatın **Yeni Başvuru Ekle**Gözat sekmesini tıklatın, C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll'e girin ve Tamam'ı tıklatın.  
  
4.  PresentationFramework.dll için yineleyin: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.  
  
5.  WindowsBase.dll için yineleyin: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.  
  
6.  UIAutomationTypes.dll için yineleyin: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.  
  
7.  UIAutomationProvider.dll için yineleyin: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.  
  
8.  Tıklatın **Yeni Başvuru Ekle**System.dll seçin ve tıklatın **Tamam**.  
  
9. Tıklatın **Tamam** başvuruları ekleme win32clock özellik sayfalarından çıkmak için.  
  
 Son olarak, ekleme `STAThreadAttribute` için `_tWinMain` ile kullanmak için yöntemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 Bu öznitelik söyler [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] , ne zaman başlatır [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], için gerekli olan tek iş parçacıklı model (STA) kullanması gereken [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).  
  
## <a name="create-a-windows-presentation-framework-page"></a>Bir Windows Presentation Framework sayfası oluşturun  
 Tanımlayan bir DLL ardından, oluşturduğunuz bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>. Genellikle oluşturmak en kolay yoludur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> tek başına uygulama ve yazma ve hata ayıklama olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bu şekilde bölümü.  Bunu yaptıktan sonra bu proje bir DLL'e tıklayarak projeyi sağ tıklatarak açılabilir **özellikleri**, uygulamaya giderek ve çıktı türü Windows Sınıf Kitaplığı'na değiştirme.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Dll projesi birleştirilebilir ile [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projesi (iki proje içeren bir çözüm) – çözüm üzerinde select **sağa proje**.  
  
 Bunu kullanmayı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] DLL'den [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] proje, gereken bir başvuru ekleyin:  
  
1.  Win32clock projesine sağ tıklatın ve **başvuruları...** .  
  
2.  Tıklatın **Yeni Başvuru Ekle**.  
  
3.  Tıklatın **projeleri** sekmesi.  WPFClock'ı seçin, Tamam'ı tıklatın.  
  
4.  Tıklatın **Tamam** başvuruları ekleme win32clock özellik sayfalarından çıkmak için.  
  
## <a name="hwndsource"></a>HwndSource  
 Ardından, kullandığınız <xref:System.Windows.Interop.HwndSource> yapmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> HWND gibi arayın.  Bu kod bloğu bir C++ dosyasına ekleyin:  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
  
    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
        HwndSource^ source = gcnew HwndSource(  
            0, // class style  
            WS_VISIBLE | WS_CHILD, // style  
            0, // exstyle  
            x, y, width, height,  
            "hi", // NAME  
            IntPtr(parent)        // parent window   
            );  
  
        UIElement^ page = gcnew WPFClock::Clock();  
        source->RootVisual = page;  
        return (HWND) source->Handle.ToPointer();  
    }  
}  
}  
```  
  
 Bu, bazı açıklamalar kullanan kodu uzun bir parçasıdır.  İlk bölümü çeşitli yan tümceleri, böylelikle tüm çağrıları tam olarak nitelemek gerekmez:  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 Oluşturan bir işlev tanımlayın sonra [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik, yerleştiren bir <xref:System.Windows.Interop.HwndSource> ve HWND döndürür:  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 Önce oluşturduğunuz bir <xref:System.Windows.Interop.HwndSource>, parametreleri CreateWindow'unkine benzer:  
  
```  
HwndSource^ source = gcnew HwndSource(  
    0, // class style  
    WS_VISIBLE | WS_CHILD, // style  
    0, // exstyle  
    x, y, width, height,  
    "hi", // NAME  
    IntPtr(parent) // parent window   
    );  
```  
  
 Oluşturduğunuz sonra [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfını onun oluşturucusunu çağırarak:  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 Ardından sayfasına bağlanmak <xref:System.Windows.Interop.HwndSource>:  
  
```  
source->RootVisual = page;  
```  
  
 Ve son satırında için HWND döndürün <xref:System.Windows.Interop.HwndSource>:  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a>Hwnd konumlandırma  
 İçeren bir HWND sahip olduğunuza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati, gereken o HWND içine yerleştirilecek [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] iletişim.  HWND yalnızca nereye koyacağınızı biliyorsanız, yalnızca o boyutunu ve konumunu geçip geçmeyeceğini `GetHwnd` daha önce tanımlanan işlevi.  Ancak, bir kaynak dosyası Cwnd'lerden hiçbirini nereye konumlandırılır kesinlikle emin; bu nedenle iletişim tanımlamak için kullanılır.  Kullanabileceğiniz [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] koymak için iletişim kutusu Düzenleyicisi bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] statik kontrol gitmek için saatin istediğiniz yere ("saati Buraya Ekle") ve konumlandırmak için kullanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saat.  
  
 WM_INITDIALOG işlediğiniz yerde, kullandığınız `GetDlgItem` HWND STATIC yer tutucusu için:  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 Koyabilirsiniz şekilde, daha sonra bu yer tutucu statik, konumunu ve boyutunu hesaplayabilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bu yerinde saat:  
  
 RECT dikdörtgeni;  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 STATİK tutucu Gizle sonra:  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 Ve oluşturma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o konumda HWND saat:  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 Öğreticiyi ilginç hale getirmek ve gerçek üretmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati, gerekir oluşturmak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati denetimi bu noktada. Arka plan kodu birkaç olay işleyicileri ile çoğunlukla biçimlendirme içinde yapabilirsiniz. Bu öğretici denetim tasarımı ile ilgili değildir ve birlikte çalışma hakkında olduğundan için tam kod [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati sağlanır burada için ayrı yönergeler onu oluşturmak veya her bölümü anlamı olmadan bir kod bloğu olarak. Görünüm veya denetim işlevselliğini değiştirmek için bu kodla denemeler çekinmeyin.  
  
 Biçimlendirme aşağıdaki gibidir:  
  
 [!code-xaml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 Ve eşlik eden arka plan kod şöyledir:  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 Nihai sonucu şuna benzer:  
  
 ![Tarih ve Saat Özellikleri iletişim kutusu](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")  
  
 Bu ekran görüntüsünde üretilen kod için sonuç karşılaştırmak için bkz: [Win32 saati birlikte çalışabilirlik örneği](http://go.microsoft.com/fwlink/?LinkID=160051).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Interop.HwndSource>  
 [WPF ve Win32 Birlikte Çalışması](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Win32 saati birlikte çalışabilirlik örneği](http://go.microsoft.com/fwlink/?LinkID=160051)
