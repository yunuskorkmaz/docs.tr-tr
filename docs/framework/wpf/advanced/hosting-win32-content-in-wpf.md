---
title: WPF'de Win32 İçeriği Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: 3c00539eb5f2a96fec974accda2fea1c0200aeec
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807751"
---
# <a name="hosting-win32-content-in-wpf"></a>WPF'de Win32 İçeriği Barındırma

## <a name="prerequisites"></a>Önkoşullar

Bkz: [WPF ve Win32 birlikte çalışması](wpf-and-win32-interoperation.md).

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Win32 Windows Presentation Framework (HwndHost) içinde bir kılavuz

Yeniden [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] içindeki içerik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları, <xref:System.Windows.Interop.HwndHost>, görünmesi Cwnd'lerden sağlayan bir denetimi olan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Gibi <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> kullanmak oldukça basittir: türetilen <xref:System.Windows.Interop.HwndHost> ve uygulama `BuildWindowCore` ve `DestroyWindowCore` yöntemleri, ardından örneği, <xref:System.Windows.Interop.HwndHost> türetilmiş bir sınıf ve içine yerleştirin, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.

Varsa, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] mantıksal bir denetim olarak zaten paketlenmiş sonra `BuildWindowCore` uygulamasıdır çağrısı değerinden biraz daha fazla `CreateWindow`. Örneğin, oluşturmak için bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX denetiminde [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:

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

Ancak varsayalım [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu oldukça, bu nedenle kendi içinde değil mi? Bu nedenle, oluşturursanız, bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] iletişim kutusu ve içeriğinin büyük ekleme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. Bu örnek gösterir [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] ve [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], ancak bunu başka bir dilde veya komut satırında yapmak da mümkündür.

Derlenir basit bir iletişim ile başlayıp bir [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] proje.

Ardından, iletişim kutusu büyük tanıtmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama:

- Derleme [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] yönetilen olarak (`/clr`)

- Bir denetime iletişim kutusunu kapat

- Türetilen sınıfı tanımlayın <xref:System.Windows.Interop.HwndHost> ile `BuildWindowCore` ve `DestroyWindowCore` yöntemleri

- Geçersiz kılma `TranslateAccelerator` iletişim anahtarları işlemek için yöntemi

- Geçersiz kılma `TabInto` sekmeyle gitmeyi desteklemek için yöntemi

- Geçersiz kılma `OnMnemonic` anımsatıcıları desteklemek için yöntemi

- Örneği <xref:System.Windows.Interop.HwndHost> alt ve sağ yerleştirmek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi

### <a name="turn-the-dialog-into-a-control"></a>Bir denetime iletişim kutusunu kapat

Alt HWND WS_CHILD ve DS_CONTROL stilleri kullanarak iletişim kutusunu kapatabilirsiniz. İletişim tanımlandığı kaynak dosyasına (.rc) gidin ve başına iletişim kutusu tanımını bulun:

```
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

İkinci satırın değiştirin:

```
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

Bu eylem tamamen bağımsız bir denetime paketi değil; çağrılacak yine `IsDialogMessage()` şekilde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] belirli iletileri işleyebilir, ancak denetim değişikliği başka bir HWND içinde bu denetimler yerleştirme için basit bir yol sağlar.

## <a name="subclass-hwndhost"></a>Alt HwndHost

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

Ardından, türetilmiş bir sınıf oluşturun <xref:System.Windows.Interop.HwndHost> ve geçersiz kılma `BuildWindowCore` ve `DestroyWindowCore` yöntemleri:

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

Burada kullandığınız `CreateDialog` gerçekten bir denetim iletişim kutusu oluşturmak için. Bu içinde adlı ilk yöntemlerden birini olduğundan [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], ayrıca bazı standart yapmanız gerektiğini [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] tanımladığınız daha sonra bir işlev çağırarak başlatma adlı `InitializeGlobals()`:

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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>TranslateAccelerator iletişim anahtarları işlemek için yöntemi geçersiz kılın

Bu örnek çalıştırdıysanız şimdi görüntüleyen bir iletişim denetimi elde edersiniz ancak, tüm bu yaptığı işleme klavye iletişim kutusundan bir işlev iletişim kutusu yok. Artık geçersiz kılmalıdır `TranslateAccelerator` uygulama (hangi geldiği `IKeyboardInputSink`, arabirim, <xref:System.Windows.Interop.HwndHost> uygular). Bu yöntem, uygulama WM_KEYDOWN ve WM_SYSKEYDOWN aldığında çağrılır.

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

Bazı daha ayrıntılı açıklamaları kullanın böylece kaygılarının çoğunu bir parça kodu budur. İlk olarak, kod kullanarak [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] ve [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] makroları; olduğunu zaten bir makro adlı dikkat etmeniz gerekir `TranslateAccelerator`, winuser.h içinde tanımlanmıştır:

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

Bu nedenle tanımladığınızdan emin olun bir `TranslateAccelerator` yöntemi ve bir `TranslateAcceleratorW` yöntemi.

Benzer şekilde, hem yönetilmeyen winuser.h MSG ve yoktur yönetilen `Microsoft::Win32::MSG` yapısı. Kullanarak iki tür arasında belirsizliğinin ortadan kaldırılmasını [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` işleci.

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

Geri `TranslateAccelerator`. Temel ilke çağırmaktır [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işlevi `IsDialogMessage` kadar kitaplıklarımızı mümkün olduğunca ancak `IsDialogMessage` iletişim dışında herhangi bir şey için erişimi yok. Kullanıcı sekme tuşuyla olduğunda iletişim kutusunda, geçici bizim iletişim son denetimi geçmiş çalışırken odak ayarlamanız gerekecek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çağırarak bölümü `IKeyboardInputSite::OnNoMoreStops`.

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

Son olarak, arama `IsDialogMessage`. Ancak sorumluluklarını bir `TranslateAccelerator` yöntemi unsurdur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veya tuş vuruşu işlenen olup olmadığı. Giriş olayı, işlemedi, tünel oluşturabilir ve kabarcık uygulama kalanında. Burada, klavye messange işleme oluþturmaz ve giriş mimaride doğasını gösterecek [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Ne yazık ki `IsDialogMessage` herhangi bir şekilde belirli bir tuş vuruşu işleme olup olmadığını döndürmez. Daha da kötüsü, çağıracak `DispatchMessage()` tuş vuruşları, değil işlemek üzerinde!  Ters mühendislik sahiptir; bu nedenle `IsDialogMessage`ve yalnızca bu bildiğiniz anahtarları işleyecek için çağırın:

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

### <a name="override-tabinto-method-to-support-tabbing"></a>Destek sekme için TabInto yöntemi geçersiz kılın

Uyguladıysanız göre `TranslateAccelerator`, kullanıcının çevresine içinde iletişim sekme kutusu ve sekmesine dışına büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. Ancak, bir kullanıcı iletişim kutusuna sekme olamaz. Bu durumu çözmek için geçersiz kılma `TabInto`:

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

`TraversalRequest` Parametresi bildirir, bir sekme veya SHIFT SEKME sekmesinde Eylem olup.

### <a name="override-onmnemonic-method-to-support-mnemonics"></a>Anımsatıcıları desteklemek için OnMnemonic yöntemi geçersiz kılın

Klavye işleme neredeyse tamamlandı, ancak bir şey eksik – anımsatıcıları çalışmaz. Bir kullanıcı alt-F bastığında odak doe Atla değil "ad:" düzenleme kutusu. Bu nedenle, geçersiz kılmanız `OnMnemonic` yöntemi:

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

Neden arama `IsDialogMessage` burada?  Daha önce bildirmek için gerektiği şekilde aynı sorunu yaşayıp [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodunuzu tuş vuruşu veya değil, işlenmiş olmadığını kod ve `IsDialogMessage` bunu yapamazsınız. Ayrıca mevcuttur ikinci bir sorun nedeniyle `IsDialogMessage` odaklanmış HWND iletişim kutusu içinde değilse, anımsatıcı işlenecek reddeder.

### <a name="instantiate-the-hwndhost-derived-class"></a>Örneği HwndHost türetilmiş sınıf

Son olarak, tüm anahtar ve sekme destek yerinde olduğuna göre koyabilirsiniz, <xref:System.Windows.Interop.HwndHost> büyük içine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. Ana uygulama yazılmışsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], doğru yere koymak için en kolay yolu boş bırakmaktır <xref:System.Windows.Controls.Border> yerleştirmek istediğiniz öğe <xref:System.Windows.Interop.HwndHost>. Burada oluşturduğunuz bir <xref:System.Windows.Controls.Border> adlı `insertHwndHostHere`:

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

İyi bir yer oluşturmak için kod sırayla bulmak için kaldı sonra <xref:System.Windows.Interop.HwndHost> ve buna bağlanmak <xref:System.Windows.Controls.Border>. Bu örnekte, bu oluşturucusu içinde bırakacaktır <xref:System.Windows.Window> türetilmiş sınıf:

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

Hangi size sunar:

![Çalışan WPF uygulamasında ekran görüntüsü.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a>Ayrıca bkz.

- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
