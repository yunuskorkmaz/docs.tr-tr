---
title: WPF'de Win32 İçeriği Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: 10bdeae8fe46f78e60d278fdbe93883a1c6bd356
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629891"
---
# <a name="hosting-win32-content-in-wpf"></a>WPF'de Win32 İçeriği Barındırma

## <a name="prerequisites"></a>Önkoşullar

Bkz. [WPF ve Win32 birlikte](wpf-and-win32-interoperation.md)çalışma.

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Windows Presentation Framework Içinde Win32 bir adım adım (HwndHost)

Uygulamalar içindeki [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği yeniden kullanmak için, <xref:System.Windows.Interop.HwndHost>HWND NDS 'nin içerik gibi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görünmesini sağlayan bir denetim olan kullanın. Benzer <xref:System.Windows.Interop.HwndSource> <xref:System.Windows.Interop.HwndHost> `BuildWindowCore` `DestroyWindowCore` şekilde,<xref:System.Windows.Interop.HwndHost> kullanımı basittir: türet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve uygulama ve yöntemlerle türetilmiş sınıfınızı oluşturun ve <xref:System.Windows.Interop.HwndHost> Uygulamanızı.

Mantığınızın [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zaten bir denetim olarak paketlenmesi durumunda `BuildWindowCore` uygulamanız, öğesine yapılan `CreateWindow`çağrıdan çok daha fazla. Örneğin, içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] C++bir LISTBOX denetimi oluşturmak için:

```cpp
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
    HWND handle = CreateWindowEx(0, L"LISTBOX",
    L"this is a Win32 listbox",
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY
    | WS_VSCROLL | WS_BORDER,
    0, 0, // x, y
    30, 70, // height, width
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd
    0, // hmenu
    0, // hinstance
    0); // lparam

    return HandleRef(this, IntPtr(handle));
}

virtual void DestroyWindowCore(HandleRef hwnd) override {
    // HwndHost will dispose the hwnd for us
}
```

Ancak kodun yalnızca [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kendi kendine dahil olmadığı varsayın. Bu durumda, bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] iletişim kutusu oluşturabilir ve içeriğini daha büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulamaya katabilirsiniz. Örnek bunu [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] ve C++' de bunu farklı bir dilde veya komut satırında yapmak mümkün olsa da gösterir.

Bir C++ DLL projesine derlenmiş basit bir iletişim kutusuyla başlayın.

Daha sonra, iletişim kutusunu daha büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaya tanıtın:

- DLL 'yi yönetilen (`/clr`) olarak derle

- İletişim kutusunu Denetim haline getirin

- Türetilmiş sınıfını <xref:System.Windows.Interop.HwndHost> `BuildWindowCore` ve yöntemlerinitanımlayın`DestroyWindowCore`

- İletişim `TranslateAccelerator` anahtarlarını işlemek için geçersiz kılma yöntemi

- Sekmeyi `TabInto` desteklemek için geçersiz kılma yöntemi

- Anımsatıcıları `OnMnemonic` desteklemek için yöntemi geçersiz kıl

- Alt sınıfı oluştur ve sağ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğenin altına koy <xref:System.Windows.Interop.HwndHost>

### <a name="turn-the-dialog-into-a-control"></a>Iletişim kutusunu Denetim haline getirin

WS_CHILD ve DS_CONTROL stillerini kullanarak bir iletişim kutusunu alt HWND 'e dönüştürebilirsiniz. İletişim kutusunun tanımlandığı kaynak dosyasına (. RC) gidin ve iletişim kutusunun tanımının başlangıcını bulun:

```
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

İkinci satırı şu şekilde değiştirin:

```
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

Bu eylem, kendisini bağımsız bir denetime tam olarak paketlemez; Yine de çağırmanız `IsDialogMessage()` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] gerekir, ancak bazı iletileri işleyebilir, ancak Denetim değişikliği bu denetimleri başka bir HWND içinde yerleştirmenin basit bir yolunu sağlar.

## <a name="subclass-hwndhost"></a>HwndHost alt sınıfı

Aşağıdaki ad alanlarını içeri aktarın:

```cpp
namespace ManagedCpp
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Input;
    using namespace System::Windows::Media;
    using namespace System::Runtime::InteropServices;
```

Ardından türetilmiş bir sınıfı <xref:System.Windows.Interop.HwndHost> oluşturun ve `BuildWindowCore` ve `DestroyWindowCore` yöntemlerini geçersiz kılın:

```cpp
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {
    private:
        HWND dialog;

    protected:
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
            InitializeGlobals();
            dialog = CreateDialog(hInstance,
                MAKEINTRESOURCE(IDD_DIALOG1),
                (HWND) hwndParent.Handle.ToPointer(),
                (DLGPROC) About);
            return HandleRef(this, IntPtr(dialog));
        }

        virtual void DestroyWindowCore(HandleRef hwnd) override {
            // hwnd will be disposed for us
        }
```

Burada, `CreateDialog` gerçekten bir denetim olan iletişim kutusunu oluşturmak için kullanırsınız. Bu, dll içinde çağrılan ilk metotlardan biri olduğundan, daha sonra [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] `InitializeGlobals()`kullanacağınız bir işlevi çağırarak bazı standart başlatma da yapmanız gerekir:

```cpp
bool initialized = false;
    void InitializeGlobals() {
        if (initialized) return;
        initialized = true;

        // TODO: Place code here.
        MSG msg;
        HACCEL hAccelTable;

        // Initialize global strings
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);
        MyRegisterClass(hInstance);
```

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>Iletişim anahtarlarını Işlemek için TranslateAccelerator metodunu geçersiz kılın

Bu örneği şu anda çalıştırdıysanız, görüntülenen bir iletişim kutusu denetimi alırsınız, ancak iletişim kutusunu işlevsel bir iletişim kutusu yapan tüm klavye işlemlerini yoksayar. Artık `TranslateAccelerator` uygulamayı (' den `IKeyboardInputSink`gelen bir arabirimi <xref:System.Windows.Interop.HwndHost> ) geçersiz kılmanız gerekir. Bu yöntem, uygulama WM_KEYDOWN ve WM_SYSKEYDOWN aldığında çağırılır.

```cpp
#undef TranslateAccelerator
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
            ModifierKeys modifiers) override
        {
            ::MSG m = ConvertMessage(msg);

            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know
            // what to do when it reaches the last tab stop
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
                TraversalRequest^ request = nullptr;

                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
                    // this code should work, but there’s a bug with interop shift-tab in current builds
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);
                }
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);
                }

                if (request != nullptr)
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);

            }

            // Only call IsDialogMessage for keys it will do something with.
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
                switch (m.wParam) {
                    case VK_TAB:
                    case VK_LEFT:
                    case VK_UP:
                    case VK_RIGHT:
                    case VK_DOWN:
                    case VK_EXECUTE:
                    case VK_RETURN:
                    case VK_ESCAPE:
                    case VK_CANCEL:
                        IsDialogMessage(dialog, &m);
                        // IsDialogMessage should be called ProcessDialogMessage --
                        // it processes messages without ever really telling you
                        // if it handled a specific message or not
                        return true;
                }
            }

            return false; // not a key we handled
        }
```

Bu, tek bir parçadaki çok büyük bir kod olduğundan, daha ayrıntılı açıklamaları kullanabilir. İlk olarak, ve C++ C++ makroları kullanan kod; zaten Winuser. h içinde tanımlanan adlı `TranslateAccelerator`bir makronun zaten bulunduğunu bilmeniz gerekir:

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

Bu nedenle, bir yöntemi `TranslateAccelerator` `TranslateAcceleratorW` değil bir yöntem tanımlamadığınızdan emin olun.

Benzer şekilde, hem yönetilmeyen Winuser. h msg hem de yönetilen `Microsoft::Win32::MSG` yapı mevcuttur. `::` İşlecini kullanarak C++ iki arasındaki ilişkiyi ayırt edebilirsiniz.

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}

Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:

```cpp
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {
    ::MSG m;
    m.hwnd = (HWND) msg.hwnd.ToPointer();
    m.lParam = (LPARAM) msg.lParam.ToPointer();
    m.message = msg.message;
    m.wParam = (WPARAM) msg.wParam.ToPointer();

    m.time = msg.time;

    POINT pt;
    pt.x = msg.pt_x;
    pt.y = msg.pt_y;
    m.pt = pt;

    return m;
}
```

Öğesine `TranslateAccelerator`geri dönün. Temel prensibi, mümkün olduğunca çok [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] iş `IsDialogMessage` yapmak için işlevi çağırıldır, ancak `IsDialogMessage` iletişim kutusunun dışında bir şeye erişemez. İletişim kutusunda bir kullanıcı sekmesi olarak sekme, iletişim kutusundaki son denetimden sonra çalıştırıldığında, öğesini çağırarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `IKeyboardInputSite::OnNoMoreStops`odağı bölümüne ayarlamanız gerekir.

```cpp
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know
// what to do when it reaches the last tab stop
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
    TraversalRequest^ request = nullptr;

    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);
    }
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);
    }

    if (request != nullptr)
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);
}
```

Son olarak, `IsDialogMessage`çağırın. Ancak bir `TranslateAccelerator` yöntemin sorumluluklarıyla, tuş vuruşu işlenip işlemeyeceğinizi söylemiş [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olabilirsiniz. Bunu yapmadıysanız, giriş olayı uygulamanın geri kalanı aracılığıyla tünel ve balon oluşturabilir. Burada, klavye messange işleme ve içindeki giriş mimarisinin doğasını bir olağandışı şekilde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]kullanıma sunacaksınız. Ne yazık `IsDialogMessage` ki, belirli bir tuş vuruşunu işleymeksizin hiçbir şekilde döndürmez. Daha da kötüsü, bu `DispatchMessage()` , işleyememesi gereken tuş vuruşlarına çağrı görür!  Bu nedenle, bunu tersine mühendislik `IsDialogMessage`yapmanız ve yalnızca işleyeceğimizi bildiğiniz anahtarlar için çağırmanız gerekir:

```cpp
// Only call IsDialogMessage for keys it will do something with.
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
    switch (m.wParam) {
        case VK_TAB:
        case VK_LEFT:
        case VK_UP:
        case VK_RIGHT:
        case VK_DOWN:
        case VK_EXECUTE:
        case VK_RETURN:
        case VK_ESCAPE:
        case VK_CANCEL:
            IsDialogMessage(dialog, &m);
            // IsDialogMessage should be called ProcessDialogMessage --
            // it processes messages without ever really telling you
            // if it handled a specific message or not
            return true;
    }
```

### <a name="override-tabinto-method-to-support-tabbing"></a>Sekmeyi desteklemek için TabInto metodunu geçersiz kılın

Artık uyguladığınıza `TranslateAccelerator`göre, bir Kullanıcı, iletişim kutusunun içinde sekme ve üzerini daha büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulamada sekmeye dönüştürebilirsiniz. Ancak bir Kullanıcı iletişim kutusuna geri sekme kullanamaz. Bunu çözümlemek için geçersiz kılabilirsiniz `TabInto`:

```cpp
public:
    virtual bool TabInto(TraversalRequest^ request) override {
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
            SetFocus(lastTabStop);
        }
        else {
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
            SetFocus(firstTabStop);
        }
        return true;
    }
```

`TraversalRequest` Parametresi sekme eyleminin sekme veya kaydırma sekmesi olduğunu söyler.

### <a name="override-onmnemonic-method-to-support-mnemonics"></a>Anımsatıcıları desteklemek için Onanımsatıcı metodunu geçersiz kılın

Klavye işleme neredeyse tamamlanmıştır, ancak bir şey eksik, ancak anımsatıcıları çalışmaz. Bir kullanıcı alt-F tuşlarına basarsa, odak "Ilk ad:" düzenleme kutusuna atmaz. Bu nedenle, `OnMnemonic` yöntemini geçersiz kılarsınız:

```cpp
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {
    ::MSG m = ConvertMessage(msg);

    // If it's one of our mnemonics, set focus to the appropriate hwnd
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {
        int dialogitem = 9999;
        switch (m.wParam) {
            case 's': dialogitem = IDOK; break;
            case 'c': dialogitem = IDCANCEL; break;
            case 'f': dialogitem = IDC_EDIT1; break;
            case 'l': dialogitem = IDC_EDIT2; break;
            case 'p': dialogitem = IDC_EDIT3; break;
            case 'a': dialogitem = IDC_EDIT4; break;
            case 'i': dialogitem = IDC_EDIT5; break;
            case 't': dialogitem = IDC_EDIT6; break;
            case 'z': dialogitem = IDC_EDIT7; break;
        }
        if (dialogitem != 9999) {
            HWND hwnd = GetDlgItem(dialog, dialogitem);
            SetFocus(hwnd);
            return true;
        }
    }
    return false; // key unhandled
};
```

Neden burada çağırmayın `IsDialogMessage` ?  Yukarıdaki ile aynı sorun var, ancak kodunuzun tuş vuruşu yapıp gerçekleştirmediğini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `IsDialogMessage` kodlayabilmeniz gerekir. İkinci bir sorun da vardır, çünkü `IsDialogMessage` odaklanmış HWND iletişim kutusunun içinde değilse, anımsatıcı işlemeyi reddeder.

### <a name="instantiate-the-hwndhost-derived-class"></a>HwndHost türetilen sınıfının örneğini oluşturma

Son olarak, artık tüm anahtar ve sekme desteği hazır olduğuna göre, uygulamanızı <xref:System.Windows.Interop.HwndHost> daha büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulamaya yerleştirebilirsiniz. Ana uygulama dilinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yazılmışsa, doğru yere yerleştirmenin en kolay yolu, koymak <xref:System.Windows.Interop.HwndHost>istediğiniz yerde boş <xref:System.Windows.Controls.Border> bir öğe bırakmamadır. Burada adlı bir <xref:System.Windows.Controls.Border> ad `insertHwndHostHere`oluşturursunuz:

```xaml
<Window x:Class="WPFApplication1.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Windows Presentation Framework Application"
    Loaded="Window1_Loaded"
    >
    <StackPanel>
        <Button Content="WPF button"/>
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>
        <Button Content="WPF button"/>
    </StackPanel>
</Window>
```

Bu durumda, <xref:System.Windows.Interop.HwndHost> ' nin örneğini oluşturmak ve <xref:System.Windows.Controls.Border>öğesine bağlamak için kod dizisinde iyi bir yer bulabilirsiniz. Bu örnekte, <xref:System.Windows.Window> türetilmiş sınıf için oluşturucuyu içine koyacaksınız:

```csharp
public partial class Window1 : Window {
    public Window1() {
    }

    void Window1_Loaded(object sender, RoutedEventArgs e) {
        HwndHost host = new ManagedCpp.MyHwndHost();
        insertHwndHostHere.Child = host;
    }
}
```

Şunları sağlar:

![Çalışan WPF uygulamasının ekran görüntüsü.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a>Ayrıca bkz.

- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
