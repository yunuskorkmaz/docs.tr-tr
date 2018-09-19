---
title: "İzlenecek yol: Win32'de WPF Saati Barındırma"
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: ce8209c89430988f57c211d388c6e73b2dc17004
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45990003"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>İzlenecek yol: Win32'de WPF Saati Barındırma
Yerleştirmenin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamaları kullanın <xref:System.Windows.Interop.HwndSource>, içeren HWND sağlar, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Oluşturduğunuz ilk <xref:System.Windows.Interop.HwndSource>, parametreler için CreateWindow benzer vererek.  Size daha sonra <xref:System.Windows.Interop.HwndSource> hakkında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik içinde olmasını istediğiniz.  Son olarak, / HWND elde <xref:System.Windows.Interop.HwndSource>. Bu izlenecek yol karma oluşturma işlemini gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işletim sistemi in uygulama **tarih ve saat özellikleri** iletişim.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bkz: [WPF ve Win32 birlikte çalışması](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
## <a name="how-to-use-this-tutorial"></a>Bu öğreticide kullanma  
 Bu öğreticide, birlikte çalışabilirlik uygulama oluşturmanın önemli adımlar yoğunlaşır. Öğretici, bir örnek tarafından yedeklenen [Win32 saati birlikte çalışma örneği](https://go.microsoft.com/fwlink/?LinkID=160051), ancak bu örnek son ürünün yansıtıcı. Varolan ile başlayan gibi Bu öğreticide adımları belgeler [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kendi proje, belki de önceden mevcut olan bir proje ve, ekleme barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanıza. Son ürününüzü ile karşılaştırabileceğiniz [Win32 saati birlikte çalışma örneği](https://go.microsoft.com/fwlink/?LinkID=160051).  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Bir kılavuz içinde Win32 Windows Presentation Framework (HwndSource)  
 Aşağıdaki grafikte, bu öğreticinin hedeflenen son ürün gösterilmektedir:  
  
 ![Tarih ve Saat Özellikleri iletişim kutusu](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")  
  
 C++ oluşturarak bu iletişim kutusunu yeniden oluşturabileceğinizi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projesi [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]ve aşağıdaki oluşturmak için iletişim kutusu düzenleyicisini kullanma:  
  
 ![Tarih ve Saat Özellikleri iletişim kutusu](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")  
  
 (Kullanın gerekmez [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] kullanılacak <xref:System.Windows.Interop.HwndSource>, ve yazmak için C++ kullanın gerekmez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlar, ancak bunu yapmak için oldukça tipik bir yoludur ve kendisi de adım öğretici açıklaması için uygundur).  
  
 Beş belirli yerleştirmek için gerçekleştirmeniz gereken bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iletişim saati:  
  
1.  Etkinleştirme, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] yönetilen kodu çağırmak için proje (**/CLR**) proje ayarlarını değiştirerek [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].  
  
2.  Oluşturma bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> ayrı bir DLL içinde.  
  
3.  Yerleştirme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> içinde bir <xref:System.Windows.Interop.HwndSource>.  
  
4.  HWND için alma <xref:System.Windows.Controls.Page> kullanarak <xref:System.Windows.Interop.HwndSource.Handle%2A> özelliği.  
  
5.  Kullanım [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HWND büyük içinde yerleştirileceği yeri karar [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulama  
  
## <a name="clr"></a>/ CLR  
 İlk adım, bu yönetilmeyen olarak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] çağırana projeye yönetilen kod.  Gerekli DLL'leri kullanma ve ile kullanmak için ana yöntemi ayarlamak istediğiniz bağlanacağı/CLR derleyici seçeneği kullanmanız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Yönetilen kod C++ projesi içinde kullanımını etkinleştirmek için: win32clock proje üzerinde sağ tıklayıp **özellikleri**.  Üzerinde **genel** özellik sayfası (varsayılan) değiştirmek için ortak dil çalışma zamanı desteği `/clr`.  
  
 Ardından, DLL'ler için gerekli başvuruları eklemek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll ve UIAutomationTypes.dll. (Yönergeleri izleyerek, C: sürücüsünde işletim sisteminin yüklü varsayılır.)  
  
1.  Win32clock projesine sağ tıklayıp **başvuruları...** , söz konusu iletişim içindeydi ve:  
  
2.  Win32clock projesine sağ tıklayıp **başvuruları...** .  
  
3.  Tıklayın **Yeni Başvuru Ekle**Gözat sekmesini tıklatın, C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll'e girin ve Tamam'a tıklayın.  
  
4.  PresentationFramework.dll için işlemi tekrarlayın: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.  
  
5.  WindowsBase.dll için işlemi tekrarlayın: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.  
  
6.  UIAutomationTypes.dll için işlemi tekrarlayın: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.  
  
7.  UIAutomationProvider.dll için işlemi tekrarlayın: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.  
  
8.  Tıklayın **Yeni Başvuru Ekle**System.dll seçin ve tıklayın **Tamam**.  
  
9. Tıklayın **Tamam** başvuruları eklemek için win32clock özellik sayfaları'ndan çıkmak için.  
  
 Son olarak, ekleme `STAThreadAttribute` için `_tWinMain` ile kullanmak için yöntemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 Bu öznitelik söyler [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] , ne zaman başlatır [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], için gerekli olan bir tek iş parçacıklı model (STA) kullanması gereken [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).  
  
## <a name="create-a-windows-presentation-framework-page"></a>Windows Presentation Framework sayfası oluşturma  
 Tanımlayan bir DLL ardından, oluşturduğunuz bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>. Genellikle oluşturmak en kolay yöntemdir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> bir tek başına uygulama yazma ve hata ayıklama olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] böylece kısmını.  Bunu yaptıktan sonra bu proje bir DLL içine tıklayarak projeyi sağ tıklatarak kapatılabilir **özellikleri**, uygulamaya gidip ve Windows sınıf kitaplığı için çıktı türünü değiştirme.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Dll projesi ardından ile birleştirilebilir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projesi (iki proje içeren bir çözüm) – sağ tıklayın, çözümü, select **sağa proje**.  
  
 Bunu kullanmayı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] DLL'den [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projesi, bir başvuru eklemeniz gerekir:  
  
1.  Win32clock projesine sağ tıklayıp **başvuruları...** .  
  
2.  Tıklayın **Yeni Başvuru Ekle**.  
  
3.  Tıklayın **projeleri** sekmesi.  WPFClock'ı seçin, Tamam'a tıklayın.  
  
4.  Tıklayın **Tamam** başvuruları eklemek için win32clock özellik sayfaları'ndan çıkmak için.  
  
## <a name="hwndsource"></a>HwndSource  
 Ardından, kullandığınız <xref:System.Windows.Interop.HwndSource> yapmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> HWND gibi arayın.  Bu kod bloğu bir C++ dosyaya ekleyin:  
  
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
  
 Bu bazı açıklamalar kullanan kod uzun bir parçasıdır.  İlk bölümü çeşitli yan tümceleri olduğundan tüm çağrıları tam olarak nitelemek gerekmez:  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 Oluşturan bir işlev tanımlayın ardından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik, yerleştiren bir <xref:System.Windows.Interop.HwndSource> ve HWND döndürür:  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 İlk olarak, oluşturun bir <xref:System.Windows.Interop.HwndSource>, parametreleri için CreateWindow benzerdir:  
  
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
  
 Oluşturduğunuz sonra [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıf oluşturucusuna çağrı yaparak içerik:  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 Sayfaya bağlandıktan sonra <xref:System.Windows.Interop.HwndSource>:  
  
```  
source->RootVisual = page;  
```  
  
 Ve son satırında HWND döndürür <xref:System.Windows.Interop.HwndSource>:  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a>Hwnd konumlandırma  
 İçeren bir HWND sahip olduğunuza göre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzende, getirmeniz gerekir bu HWND içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] iletişim.  HWND yalnızca nereye koyacağınızı ise, yalnızca o boyutunu ve konumunu geçip geçmeyeceğini `GetHwnd` önceden tanımladığınız işlevi.  Ancak, bir kaynak dosyası iletişim Cwnd'lerden hiçbirini nerede konumlandırılacağını tam olarak emin olacak şekilde tanımlamak için kullanılan.  Kullanabileceğiniz [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] koymak için iletişim kutusu Düzenleyicisi bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] statik denetim, Git saati istediğiniz ("Ekle düzende burada") ve konumlandırmak için kullanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati.  
  
 WM_INITDIALOG işlediğiniz burada kullandığınız `GetDlgItem` HWND yer tutucusu için almak için:  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 Böylece, ardından bu yer tutucu statik konumunu ve boyutunu hesaplayabilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , yerinde saati:  
  
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
  
 Ardından statik yer tutucu Gizle:  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 Oluşturup [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND o konumda saati:  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 Öğreticiyi ilginç hale getirmek ve gerçek üretmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzende, oluşturmanız gerekir bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati denetimi bu noktada. Arka plan kod yalnızca birkaç olay işleyicileri ile çoğunlukla biçimlendirme içinde yapabilirsiniz. Bu öğreticide, birlikte çalışabilirlik ve denetimi tasarım hakkında değil olduğundan, için kod tamamlama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saat sağlanır için ayrı yönergeler onu oluşturmak veya her bir parçası olarak ne anlama geldiğini olmadan bir kod bloğu olarak burada. Görünüm veya denetimi işlevlerini değiştirmek için bu kodla denemeler çekinmeyin.  
  
 Biçimlendirme şöyledir:  
  
 [!code-xaml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 Ve eşlik eden arka plan kod şu şekildedir:  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 Nihai sonucu şu şekilde görünür:  
  
 ![Tarih ve Saat Özellikleri iletişim kutusu](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")  
  
 Sonuç şu ekran üretilen kod için karşılaştırmak için bkz [Win32 saati birlikte çalışma örneği](https://go.microsoft.com/fwlink/?LinkID=160051).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Interop.HwndSource>  
 [WPF ve Win32 Birlikte Çalışması](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Win32 saati birlikte çalışabilirlik örneği](https://go.microsoft.com/fwlink/?LinkID=160051)
