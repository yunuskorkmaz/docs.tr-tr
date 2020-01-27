---
title: Win32 Içeriğini barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: b3113d9f3146e1590363dc9db6f751a429dda74b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747018"
---
# <a name="hosting-win32-content-in-wpf"></a>WPF'de Win32 İçeriği Barındırma

## <a name="prerequisites"></a>Prerequisites

Bkz. [WPF ve Win32 birlikte](wpf-and-win32-interoperation.md)çalışma.

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Windows Presentation Framework Içinde Win32 bir adım adım (HwndHost)

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalarında Win32 içeriğini yeniden kullanmak için, HWNDs 'nin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik gibi görünmesini sağlayan bir denetim olan <xref:System.Windows.Interop.HwndHost>kullanın. <xref:System.Windows.Interop.HwndSource>gibi, <xref:System.Windows.Interop.HwndHost> kullanımı basittir: <xref:System.Windows.Interop.HwndHost> türetebilir ve `BuildWindowCore` ve `DestroyWindowCore` yöntemleri uygulayıp <xref:System.Windows.Interop.HwndHost> türetilmiş sınıfınızın örneğini oluşturup [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanızın içine yerleştirin.

Win32 mantığınızın zaten bir denetim olarak paketlenmesi durumunda `BuildWindowCore` uygulamanız `CreateWindow`bir çağrıdan çok daha fazla. Örneğin, içinde C++BIR Win32 LISTBOX denetimi oluşturmak için:

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

Ancak, Win32 kodunun kendine dahil olmadığı varsayın. Bu durumda, bir Win32 iletişim kutusu oluşturabilir ve içeriğini daha büyük bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasına ekleyebilirsiniz. Örnek, bunu Visual Studio 'da ve C++farklı bir dilde veya komut satırında yapmak mümkün olsa da gösterir.

Bir C++ DLL projesine derlenmiş basit bir iletişim kutusuyla başlayın.

Daha sonra, iletişim kutusunu daha büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasına tanıtın:

- DLL 'yi yönetilen olarak derle (`/clr`)

- İletişim kutusunu Denetim haline getirin

- `BuildWindowCore` ve `DestroyWindowCore` yöntemleriyle birlikte <xref:System.Windows.Interop.HwndHost> türetilen sınıfını tanımlayın

- İletişim anahtarlarını işlemek için `TranslateAccelerator` yöntemi geçersiz kıl

- Sekmeyi desteklemek için `TabInto` yöntemi geçersiz kıl

- Anımsatıcıları desteklemek için `OnMnemonic` yöntemi geçersiz kıl

- <xref:System.Windows.Interop.HwndHost> alt sınıfını oluşturun ve sağ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinin altına yerleştirin

### <a name="turn-the-dialog-into-a-control"></a>Iletişim kutusunu Denetim haline getirin

WS_CHILD ve DS_CONTROL stillerini kullanarak bir iletişim kutusunu alt HWND 'ye dönüştürebilirsiniz. İletişim kutusunun tanımlandığı kaynak dosyasına (. RC) gidin ve iletişim kutusunun tanımının başlangıcını bulun:

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

İkinci satırı şu şekilde değiştirin:

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

Bu eylem, kendisini bağımsız bir denetime tam olarak paketlemez; Win32 'in belirli iletileri işleyebilmesi için yine de `IsDialogMessage()` çağırmanız gerekir, ancak Denetim değişikliği bu denetimleri başka bir HWND içinde yerleştirmenin basit bir yolunu sağlar.

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

Ardından <xref:System.Windows.Interop.HwndHost> türetilmiş bir sınıf oluşturun ve `BuildWindowCore` ve `DestroyWindowCore` yöntemleri geçersiz kılın:

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

Burada, gerçekten bir denetim olan iletişim kutusunu oluşturmak için `CreateDialog` kullanırsınız. Bu, DLL içinde çağrılan ilk metotlardan biri olduğundan, daha sonra `InitializeGlobals()`adlı bir işlevi çağırarak bazı standart Win32 başlatma işlemi de yapmalısınız:

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

Bu örneği şu anda çalıştırdıysanız, görüntülenen bir iletişim kutusu denetimi alırsınız, ancak iletişim kutusunu işlevsel bir iletişim kutusu yapan tüm klavye işlemlerini yoksayar. Artık `TranslateAccelerator` uygulamasını geçersiz kılmanız gerekir (`IKeyboardInputSink`<xref:System.Windows.Interop.HwndHost> uygulayan bir arabirim). Bu yöntem, uygulama WM_KEYDOWN ve WM_SYSKEYDOWN aldığında çağırılır.

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

Bu, tek bir parçadaki çok büyük bir kod olduğundan, daha ayrıntılı açıklamaları kullanabilir. İlk olarak, ve C++ C++ makroları kullanan kod; Winuser. h içinde tanımlanan `TranslateAccelerator`adlı bir makronun zaten bulunduğunu bilmeniz gerekir:

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

Bu nedenle, bir `TranslateAcceleratorW` yöntemi değil `TranslateAccelerator` yöntemi tanımladığınızdan emin olun.

Benzer şekilde, hem yönetilmeyen Winuser. h MSG hem de yönetilen `Microsoft::Win32::MSG` yapısı vardır. C++ `::` işlecini kullanarak ikisi arasındaki ilişkiyi ortadan kaldırabilirsiniz.

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

`TranslateAccelerator`geri dönün. Temel prensibi, mümkün olduğunca fazla iş yapmak için `IsDialogMessage` Win32 işlevini çağır, ancak `IsDialogMessage` iletişim kutusunun dışında herhangi bir şeye erişemez. İletişim kutusunda bir kullanıcı sekmesi olarak sekme, iletişim kutusundaki son denetimden sonra çalıştırıldığında, `IKeyboardInputSite::OnNoMoreStops`çağırarak odağı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bölümüne ayarlamanız gerekir.

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

Son olarak, `IsDialogMessage`çağırın. Ancak, bir `TranslateAccelerator` yönteminin sorumluluklarıyla, tuş vuruşunu işlemiş olup olmadığını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] söylemiş olursunuz. Bunu yapmadıysanız, giriş olayı uygulamanın geri kalanı aracılığıyla tünel ve balon oluşturabilir. Burada, bir klavye messange işleme ve Win32 'teki giriş mimarisinin doğası gibi bir olağandışı işlem sergileirsiniz. Ne yazık ki, `IsDialogMessage` belirli bir tuş vuruşunu işleymeksizin hiçbir şekilde döndürmez. Daha da kötüleşse de, işlem yapılmamalıdır `DispatchMessage()`.  Bu nedenle, `IsDialogMessage`tersine mühendislik yapmanız ve yalnızca işleyeceği anahtarlar için çağırmanız gerekir:

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

`TranslateAccelerator`uyguladığınıza göre, bir Kullanıcı, iletişim kutusunun içinde sekme ve daha fazla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasına sekme ekleyebilir. Ancak bir Kullanıcı iletişim kutusuna geri sekme kullanamaz. Bunu çözümlemek için `TabInto`geçersiz kılabilirsiniz:

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

`TraversalRequest` parametresi, sekme eyleminin sekme veya kaydırma sekmesi olduğunu söyler.

### <a name="override-onmnemonic-method-to-support-mnemonics"></a>Anımsatıcıları desteklemek için Onanımsatıcı metodunu geçersiz kılın

Klavye işleme neredeyse tamamlanmıştır, ancak bir şey eksik, ancak anımsatıcıları çalışmaz. Bir kullanıcı alt-F tuşlarına basarsa, odak "Ilk ad:" düzenleme kutusuna atmaz. Bu nedenle `OnMnemonic` yöntemi geçersiz kılınır:

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

Neden `IsDialogMessage` çağırmayın?  Yukarıdaki ile aynı sorun var, kodunuzun tuş vuruşu yapıp gerçekleştirmediğini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodu bilgilendirebilmeniz gerekir ve `IsDialogMessage` bunu yapamaz. Ayrıca, odaklanmış HWND iletişim kutusunun içinde değilse, `IsDialogMessage` bir ikinci sorun da vardır.

### <a name="instantiate-the-hwndhost-derived-class"></a>HwndHost türetilen sınıfının örneğini oluşturma

Son olarak, artık tüm anahtar ve sekme desteği hazır olduğuna göre <xref:System.Windows.Interop.HwndHost> daha büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasına koyabilirsiniz. Ana uygulama [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yazılmışsa, doğru yere koymanın en kolay yolu, <xref:System.Windows.Interop.HwndHost>koymak istediğiniz boş bir <xref:System.Windows.Controls.Border> öğesi bırakmamadır. Burada `insertHwndHostHere`adlı bir <xref:System.Windows.Controls.Border> oluşturursunuz:

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

Bu durumda, <xref:System.Windows.Interop.HwndHost> örneklendirilecek ve <xref:System.Windows.Controls.Border>bağlamak için kod dizisinde iyi bir yer bulabilirsiniz. Bu örnekte, <xref:System.Windows.Window> türetilmiş sınıfına ait oluşturucuyu içine koyacaksınız:

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
