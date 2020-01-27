---
title: "İzlenecek yol: Win32 'de WPF saati barındırma"
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 79f79e42652ca51c409fabb12a572485ad734b35
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744892"
---
# <a name="walkthrough-host-a-wpf-clock-in-win32"></a>İzlenecek yol: Win32 'de WPF saati barındırma

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32 uygulamalarının içine koymak için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğinizi içeren HWND 'yi sağlayan <xref:System.Windows.Interop.HwndSource>kullanın. İlk olarak <xref:System.Windows.Interop.HwndSource>oluşturun ve bu parametrelere CreateWindow 'a benzer. Daha sonra <xref:System.Windows.Interop.HwndSource> içinde istediğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik hakkında söylemeniz gerekir. Son olarak, <xref:System.Windows.Interop.HwndSource>HWND 'den yararlanın. Bu izlenecek yol, Win32 uygulamasının içinde işletim sistemi **Tarih ve saat özellikleri** iletişim kutusunu yeniden uygulayan bir karma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oluşturmayı gösterir.

## <a name="prerequisites"></a>Prerequisites

Bkz. [WPF ve Win32 birlikte](wpf-and-win32-interoperation.md)çalışma.

## <a name="how-to-use-this-tutorial"></a>Bu öğreticiyi kullanma

Bu öğretici, birlikte çalışabilirlik uygulaması üretmede önemli adımlarla yoğunlaşır. Öğretici örnek, [Win32 saat birlikte çalışabilirlik](https://go.microsoft.com/fwlink/?LinkID=160051)örneğiyle desteklenir, ancak bu örnek, son ürünün yansıtıcı örneğidir. Bu öğreticide, kendi mevcut bir Win32 projesiyle başladıysanız, belki de önceden var olan bir projede ve bir barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanıza eklemiş olabilirsiniz. Son ürününüzü, [Win32 saat birlikte çalışabilirlik](https://go.microsoft.com/fwlink/?LinkID=160051)örneğiyle karşılaştırabilirsiniz.

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Win32 Içindeki Windows Presentation Framework 'e yönelik bir adım adım (HwndSource)

Aşağıdaki grafikte, Bu öğreticinin amaçlanan son ürünü gösterilmektedir:

![Tarih ve saat özellikleri iletişim kutusunu gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

Visual Studio 'da bir C++ Win32 projesi oluşturarak ve iletişim düzenleyicisini kullanarak, aşağıdakileri oluşturmak için bu iletişim kutusunu yeniden oluşturabilirsiniz:

![Yeniden oluşturulan tarih ve saat özellikleri iletişim kutusu](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

(<xref:System.Windows.Interop.HwndSource>kullanmak için Visual Studio kullanmanız gerekmez ve Win32 programları yazmak için kullanmanız C++ gerekmez, ancak bunu yapmak için oldukça tipik bir yoldur ve bir tarafınızdaki öğretici açıklamasında iyi bir yöntem vardır).

İletişim kutusuna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir saat koymak için beş özel alt adım gerçekleştirmeniz gerekir:

1. Visual Studio 'da proje ayarlarını değiştirerek, Win32 projenizi yönetilen kodu ( **/clr**) çağırmak üzere etkinleştirin.

2. Ayrı bir DLL 'de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> oluşturun.

3. Bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> <xref:System.Windows.Interop.HwndSource>içine koyun.

4. Bu <xref:System.Windows.Controls.Page> için <xref:System.Windows.Interop.HwndSource.Handle%2A> özelliğini kullanarak bir HWND alın.

5. HWND 'yi daha büyük Win32 uygulamasına nereye yerleştireceğinize karar vermek için kullanın

## <a name="clr"></a>clr

İlk adım, bu yönetilmeyen Win32 projesini yönetilen kodu çağıralebilecek birine dönüştürmek olur. Kullanmak istediğiniz gerekli dll 'Lere bağlanacak/clr derleyici seçeneğini kullanın ve ana yöntemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ile kullanmak üzere ayarlayın.

C++ Projenin içinde yönetilen kodun kullanımını etkinleştirmek için: Win32clock projesine sağ tıklayın ve **Özellikler**' i seçin. **Genel** Özellik sayfasında (varsayılan), `/clr`Için ortak dil çalışma zamanı desteğini değiştirin.

Daha sonra, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]için gereken dll 'lere başvuruları ekleyin: PresentationCore. dll, PresentationFramework. dll, System. dll, WindowsBase. dll, UIAutomationProvider. dll ve UIAutomationTypes. dll. (Aşağıdaki yönergelerde, işletim sisteminin C: Drive üzerinde yüklü olduğu varsayılır.)

1. Win32clock projesi öğesine sağ tıklayın ve **Başvurular...** ' ı seçin ve bu iletişim kutusunun içinde:

2. Win32clock projesi öğesine sağ tıklayın ve başvurular ' ı seçin. **..** .

3. **Yeni Başvuru Ekle**' ye tıklayın, göz at sekmesine tıklayın, C:\Program Files\Reference, bir Lies\microsoft\framework\v3,\presentationcore.dll yazın ve Tamam ' a tıklayın.

4. PresentationFramework. dll için yineleyin: C:\Program Files\Reference, Lıes\microsoft\framework\v3.0\presentationframework.exe.

5. WindowsBase. dll için yineleyin: C:\Program Files\Reference, Lıes\microsoft\framework\v3.0\base.exe.

6. UIAutomationTypes. dll için yineleme: C:\Program Files\Reference, Lıes\microsoft\framework\v3,\uıautomationtypes.exe.

7. UIAutomationProvider. dll için yineleyin: C:\Program Files\Reference, Lıes\microsoft\framework\v3,\uıautomationprovider.exe.

8. **Yeni Başvuru Ekle**' ye tıklayın, System. dll öğesini seçin ve **Tamam**' a tıklayın.

9. Başvuru eklemek için win32clock Özellik Sayfalarından çıkmak üzere **Tamam** ' a tıklayın.

 Son olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ile kullanmak için `_tWinMain` yöntemine `STAThreadAttribute` ekleyin:

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

Bu öznitelik, bileşen nesne modeli (COM) başlatıldığında ortak dil çalışma zamanına (CLR), [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]) için gerekli olan tek bir iş parçacıklı grup modeli (STA) kullanması gerektiğini söyler.

## <a name="create-a-windows-presentation-framework-page"></a>Windows Presentation Framework Oluştur sayfası

Sonra, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>tanımlayan bir DLL oluşturursunuz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> tek başına uygulama olarak oluşturmak ve bu şekilde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bölümünü yazmak ve hatalarını ayıklamak en kolay yöntemdir. Bu proje tamamlandığında, projeye sağ tıklayıp **Özellikler**' e tıklayıp uygulamaya giderek ve çıkış türünü Windows sınıf kitaplığı olarak değiştirerek dll 'ye açılabilir.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] DLL projesi daha sonra Win32 projesi (iki proje içeren bir çözüm) ile birleştirilebilir – çözüme sağ tıklayın, **var olan projeyi add\'** ı seçin.

Bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll dosyasını Win32 projesinden kullanmak için, bir başvuru eklemeniz gerekir:

1. Win32clock projesi öğesine sağ tıklayın ve başvurular ' ı seçin. **..** .

2. **Yeni Başvuru Ekle**' ye tıklayın.

3. **Projeler** sekmesine tıklayın. WPFClock ' i seçin, Tamam ' a tıklayın.

4. Başvuru eklemek için win32clock Özellik Sayfalarından çıkmak üzere **Tamam** ' a tıklayın.

## <a name="hwndsource"></a>HwndSource

Sonra, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> bir HWND gibi görünmesini sağlamak için <xref:System.Windows.Interop.HwndSource> kullanırsınız. Bu kod bloğunu bir C++ dosyaya eklersiniz:

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

 Daha sonra, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğini oluşturan bir işlev tanımlar, onun etrafına bir <xref:System.Windows.Interop.HwndSource> koyar ve HWND 'yi döndürür:

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

İlk olarak, parametreleri CreateWindow ile benzer olan bir <xref:System.Windows.Interop.HwndSource>oluşturursunuz:

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

Ardından oluşturucusunu çağırarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfını oluşturursunuz:

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

Daha sonra sayfayı <xref:System.Windows.Interop.HwndSource>bağlayabilirsiniz:

```cpp
source->RootVisual = page;
```

 Son satırda, <xref:System.Windows.Interop.HwndSource>HWND 'yi geri döndürün:

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a>HWND 'yi konumlandırma

Artık [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saatini içeren bir HWND olduğuna göre, bu HWND 'yi Win32 iletişim kutusunun içine koymanız gerekir. Yalnızca HWND 'yi nereye koyabileceğinizi biliyorsanız, bu boyutu ve konumu daha önce tanımladığınız `GetHwnd` işleve geçitirsiniz. Ancak, iletişim kutusunu tanımlamak için bir kaynak dosyası kullandınız, bu nedenle bir HWND NDS 'nin nerede konumlandığını tam olarak unutmayın. Visual Studio iletişim düzenleyicisini, saatin gitmesini istediğiniz yere bir Win32 STATIK denetimi koymak için kullanabilirsiniz ("saati buraya ekle") ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saatini konumlandırmak için kullanın.

WM_INITDIALOG nerede işleyeceğinizi kullanırsanız, STATIK yer tutucu için HWND 'yi almak üzere `GetDlgItem` kullanırsınız:

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

Daha sonra bu yer tutucunun STATIK boyutunu ve konumunu hesaplayabilirsiniz ve bu durumda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati bu yere koyabilirsiniz:

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

Ve bu konumda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saat HWND oluşturun:

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

Öğreticiyi ilginç hale getirmek ve gerçek bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saat üretmek için, bu noktada bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saat denetimi oluşturmanız gerekir. Arka plan kod içinde yalnızca birkaç olay işleyicileriyle bu şekilde biçimlendirme yapabilirsiniz. Bu öğretici birlikte çalışabilirlik ile ilgili olduğundan ve denetim tasarımı hakkında olmadığından, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saatinin tüm kodu, bu bilgileri oluşturmak için ayrık yönergeler veya her parçanın anlamı olmadan bir kod bloğu olarak sunulmaktadır. Denetimin görünümünü ve işlevselliğini değiştirmek için bu kodla denemeler yapın.

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
