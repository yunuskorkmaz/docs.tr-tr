---
title: 'İzlenecek yol: WPF Saatini Win32 içinde Barındırma'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 98e48060bbb82764e1e541797c666ca33f247c39
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400480"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>İzlenecek yol: WPF Saatini Win32 içinde Barındırma

Uygulamaları içine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] koymak <xref:System.Windows.Interop.HwndSource>için içeriğinizi[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeren HWND 'yi sağlayan kullanın. İlk olarak, <xref:System.Windows.Interop.HwndSource>CreateWindow 'a benzer parametreler vererek oluşturun. Ardından, <xref:System.Windows.Interop.HwndSource> içinde istediğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğe ilişkin bilgi verin. Son olarak, HWND <xref:System.Windows.Interop.HwndSource>'yi ' den alın. Bu izlenecek yol, işletim sistemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] **Tarih ve saat özellikleri** iletişim kutusunu yeniden uygulayan bir karma iç [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamanın nasıl oluşturulacağını göstermektedir.

## <a name="prerequisites"></a>Önkoşullar

Bkz. [WPF ve Win32 birlikte](wpf-and-win32-interoperation.md)çalışma.

## <a name="how-to-use-this-tutorial"></a>Bu öğreticiyi kullanma

Bu öğretici, birlikte çalışabilirlik uygulaması üretmede önemli adımlarla yoğunlaşır. Öğretici örnek, [Win32 saat birlikte çalışabilirlik](https://go.microsoft.com/fwlink/?LinkID=160051)örneğiyle desteklenir, ancak bu örnek, son ürünün yansıtıcı örneğidir. Bu öğreticide, sahip olduğunuz mevcut [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bir projeden, belki de önceden var olan bir projede başladıysanız ve uygulamanıza barındırılmış [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir proje gibi adımlar belgeliyoruz. Son ürününüzü, [Win32 saat birlikte çalışabilirlik](https://go.microsoft.com/fwlink/?LinkID=160051)örneğiyle karşılaştırabilirsiniz.

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Win32 Içindeki Windows Presentation Framework 'e yönelik bir adım adım (HwndSource)

Aşağıdaki grafikte, Bu öğreticinin amaçlanan son ürünü gösterilmektedir:

![Tarih ve saat özellikleri iletişim kutusunu gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

Visual Studio 'da bir C++ Win32 projesi oluşturarak ve iletişim düzenleyicisini kullanarak, aşağıdakileri oluşturmak için bu iletişim kutusunu yeniden oluşturabilirsiniz:

![Yeniden oluşturulan tarih ve saat özellikleri iletişim kutusu](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] (Kullanmak <xref:System.Windows.Interop.HwndSource>için kullanmanız gerekmez ve programları yazmak C++ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] için kullanmanız gerekmez, ancak bunu yapmak için oldukça tipik bir yoldur ve bir tarafınızdaki öğretici açıklamasına göre iyi bir yöntem vardır).

İletişim kutusuna bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saat koymak için beş özel alt adım gerçekleştirmeniz gerekir:

1. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] İçindeki Proje[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]ayarlarını değiştirerek projenizi yönetilen kodu ( **/clr**) çağırmak üzere etkinleştirin.

2. Ayrı bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> dll 'de oluşturun.

3. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bunu<xref:System.Windows.Controls.Page> içine<xref:System.Windows.Interop.HwndSource>koyun.

4. <xref:System.Windows.Controls.Page> Özelliğini kullanarak bir HWND alın. <xref:System.Windows.Interop.HwndSource.Handle%2A>

5. HWND [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 'yi daha büyük [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bir uygulamada nereye yerleştireceğinize karar vermek için kullanın

## <a name="clr"></a>clr

İlk adım, bu yönetilmeyen [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projeyi yönetilen kodu çağıralebilecek birine dönüştürmek olur. Kullanmak istediğiniz gerekli dll 'Lere bağlanacak/clr derleyici seçeneğini kullanın ve ana yöntemi ile [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanmak üzere ayarlayın.

C++ Projenin içinde yönetilen kodun kullanımını etkinleştirmek için: Win32clock projesine sağ tıklayın ve **Özellikler**' i seçin. **Genel** Özellik sayfasında (varsayılan), ortak dil çalışma zamanı desteğini olarak `/clr`değiştirin.

Ardından, için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]gereken dll 'lere başvurular ekleyin: PresentationCore. dll, PresentationFramework. dll, System. dll, WindowsBase. dll, UIAutomationProvider. dll ve UIAutomationTypes. dll. (Aşağıdaki yönergelerde, işletim sisteminin C: Drive üzerinde yüklü olduğu varsayılır.)

1. Win32clock projesi öğesine sağ tıklayın ve **Başvurular...** ' ı seçin ve bu iletişim kutusunun içinde:

2. Win32clock projesi öğesine sağ tıklayın ve başvurular ' ı seçin. **..** .

3. **Yeni Başvuru Ekle**' ye tıklayın, göz at sekmesine tıklayın, C:\Program Files\Reference, bir Lies\microsoft\framework\v3,\presentationcore.dll yazın ve Tamam ' a tıklayın.

4. PresentationFramework. dll için yineleyin: C:\Program Files\Reference, Lies\microsoft\framework\v3,\presentationframework.exe.

5. WindowsBase. dll için yineleyin: C:\Program Files\Reference, Lies\microsoft\framework\v3.0\base.exe.

6. UIAutomationTypes. dll için yineleyin: C:\Program Files\Reference, Lies\microsoft\framework\v3,\uıautomationtypes.exe.

7. UIAutomationProvider. dll için yineleyin: C:\Program Files\Reference, Lies\microsoft\framework\v3,\uıautomationprovider.exe.

8. **Yeni Başvuru Ekle**' ye tıklayın, System. dll öğesini seçin ve **Tamam**' a tıklayın.

9. Başvuru eklemek için win32clock Özellik Sayfalarından çıkmak üzere **Tamam** ' a tıklayın.

 Son olarak, öğesini `STAThreadAttribute` ile [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanmak `_tWinMain` için yöntemine ekleyin:

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

Bu öznitelik, başlatıldığında ortak dil çalışma zamanına (CLR) [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], (ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]) için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gerekli olan tek bir iş parçacıklı grup modeli (STA) kullanması gerektiğini söyler.

## <a name="create-a-windows-presentation-framework-page"></a>Windows Presentation Framework Oluştur sayfası

Ardından, öğesini tanımlayan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>bir dll oluşturursunuz. Tek başına uygulama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> olarak oluşturmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve bölümü bu şekilde yazmak ve hata ayıklamak genellikle en kolay yöntemdir. Bu proje tamamlandığında, projeye sağ tıklayıp **Özellikler**' e tıklayıp uygulamaya giderek ve çıkış türünü Windows sınıf kitaplığı olarak değiştirerek dll 'ye açılabilir.

DLL projesi daha sonra [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] proje ile birleştirilebilir (iki proje içeren bir çözüm) – çözüme sağ tıklayın, **var olan projeyi add\'** ı seçin. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

Bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 'yi projeden kullanmak için bir başvuru eklemeniz gerekir:

1. Win32clock projesi öğesine sağ tıklayın ve başvurular ' ı seçin. **..** .

2. **Yeni Başvuru Ekle**' ye tıklayın.

3. **Projeler** sekmesine tıklayın. WPFClock ' ı seçin, Tamam ' a tıklayın.

4. Başvuru eklemek için win32clock Özellik Sayfalarından çıkmak üzere **Tamam** ' a tıklayın.

## <a name="hwndsource"></a>HwndSource

Ardından, bir HWND <xref:System.Windows.Interop.HwndSource> gibi <xref:System.Windows.Controls.Page> görünmesini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sağlamak için kullanırsınız. Bu kod bloğunu bir C++ dosyaya eklersiniz:

```cpp
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

 Bu, bir açıklama kullanan uzun bir kod parçasıdır. İlk bölüm çeşitli yan tümcelerdir, böylece tüm çağrıları tamamen nitelemeniz gerekmez:

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 Ardından, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği oluşturan bir işlev tanımlar, etrafına bir <xref:System.Windows.Interop.HwndSource> ekler ve HWND 'yi döndürür:

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

İlk olarak, parametreleri <xref:System.Windows.Interop.HwndSource>CreateWindow 'unkine benzer olan bir oluşturun:

```cpp
HwndSource^ source = gcnew HwndSource(
    0, // class style
    WS_VISIBLE | WS_CHILD, // style
    0, // exstyle
    x, y, width, height,
    "hi", // NAME
    IntPtr(parent) // parent window
);
```

Ardından, yapıcısını çağırarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfını oluşturursunuz:

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

Daha sonra bu sayfayı öğesine <xref:System.Windows.Interop.HwndSource>bağlayabilirsiniz:

```cpp
source->RootVisual = page;
```

 Son satırda, için <xref:System.Windows.Interop.HwndSource>HWND 'yi geri döndürün:

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a>HWND 'yi konumlandırma

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Saati içeren bir HWND 'ye sahip olduğunuza göre, bu HWND 'yi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] iletişim kutusu içine koymanız gerekir. Yalnızca HWND 'yi nereye koyabileceğinizi biliyorsanız, bu boyutu ve konumu `GetHwnd` daha önce tanımladığınız işleve geçitirsiniz. Ancak, iletişim kutusunu tanımlamak için bir kaynak dosyası kullandınız, bu nedenle bir HWND NDS 'nin nerede konumlandığını tam olarak unutmayın. [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] İletişim düzenleyicisini kullanarak saatin gitmesini istediğiniz yere bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] statik denetim koyabilirsiniz ("saati buraya ekleyin") ve bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati kullanarak saati konumlandırabilirsiniz.

WM_INITDIALOG 'yi işleyturun, `GetDlgItem` statik yer tutucu için HWND 'yi almak için kullanırsınız:

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

Daha sonra bu yer tutucunun statik boyutunu ve konumunu hesaplayabilirsiniz, bu sayede [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati ilgili yere koyabilirsiniz:

Dikdörtgen dikdörtgen;

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

Sonra STATIK yer tutucuyu gizlemeniz gerekir:

```cpp
ShowWindow(placeholder, SW_HIDE);
```

Ve bu konumdaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saat HWND 'yi oluşturun:

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

Öğreticiyi ilginç hale getirmek ve gerçek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir saat üretmek için bu noktada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saat denetimi oluşturmanız gerekecektir. Arka plan kod içinde yalnızca birkaç olay işleyicileriyle bu şekilde biçimlendirme yapabilirsiniz. Bu öğretici birlikte çalışabilirlik ile ilgili olduğundan ve denetim tasarımı hakkında olmadığından, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saat için tüm kod burada bir kod bloğu olarak sağlanır. Denetimin görünümünü ve işlevselliğini değiştirmek için bu kodla denemeler yapın.

Biçimlendirme şu şekildedir:

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

Arka plan kodu aşağıda verilmiştir:

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

Nihai sonuç şöyle görünür:

![Son sonuç tarihi ve saati özellikleri iletişim kutusu](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

Nihai sonucu bu ekran görüntüsünü üreten kodla karşılaştırmak için bkz. [Win32 saat karşılıklı çalışma örneği](https://go.microsoft.com/fwlink/?LinkID=160051).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndSource>
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
- [Win32 saat birlikte çalışabilirlik örneği](https://go.microsoft.com/fwlink/?LinkID=160051)
