---
title: Win32 Içeriğini barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: c0c62f1999feaf591c512314515f01e83fa12591
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052097"
---
# <a name="hosting-win32-content-in-wpf"></a>WPF'de Win32 İçeriği Barındırma

## <a name="prerequisites"></a>Ön koşullar

Bkz. [WPF ve Win32 birlikte](wpf-and-win32-interoperation.md)çalışma.

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Windows Presentation Framework Içinde Win32 bir adım adım (HwndHost)

Uygulamalar içinde Win32 içeriğini yeniden kullanmak için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Interop.HwndHost> HWND NDS 'nin içerik gibi görünmesini sağlayan bir denetim olan kullanın [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Benzer <xref:System.Windows.Interop.HwndSource> <xref:System.Windows.Interop.HwndHost> şekilde, kullanımı basittir: türet <xref:System.Windows.Interop.HwndHost> ve uygulama `BuildWindowCore` ve `DestroyWindowCore` yöntemlerle <xref:System.Windows.Interop.HwndHost> türetilmiş sınıfınızı oluşturun ve uygulamanızın içine yerleştirin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .

Win32 mantığınızın zaten bir denetim olarak paketlenmesi durumunda `BuildWindowCore` uygulamanız, öğesine yapılan çağrıdan biraz daha fazla olur `CreateWindow` . Örneğin, C++ ' da bir Win32 LISTBOX denetimi oluşturmak için:

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

Ancak, Win32 kodunun kendine dahil olmadığı varsayın. Bu durumda, bir Win32 iletişim kutusu oluşturabilir ve içeriğini daha büyük bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaya katabilirsiniz. Örnek, bunu farklı bir dilde veya komut satırında yapmak mümkün olsa da Visual Studio ve C++ içinde gösterir.

C++ DLL projesine derlenmiş basit bir iletişim kutusuyla başlayın.

Daha sonra, iletişim kutusunu daha büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaya tanıtın:

- DLL 'yi yönetilen () olarak derle `/clr`

- İletişim kutusunu Denetim haline getirin

- Türetilmiş sınıfını <xref:System.Windows.Interop.HwndHost> `BuildWindowCore` ve `DestroyWindowCore` yöntemlerini tanımlayın

- `TranslateAccelerator`İletişim anahtarlarını işlemek için geçersiz kılma yöntemi

- `TabInto`Sekmeyi desteklemek için geçersiz kılma yöntemi

- `OnMnemonic`Anımsatıcıları desteklemek için yöntemi geçersiz kıl

- <xref:System.Windows.Interop.HwndHost>Alt sınıfı oluştur ve sağ öğenin altına koy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

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

Bu eylem, kendisini bağımsız bir denetime tam olarak paketlemez; hala `IsDialogMessage()` Win32 bazı iletileri işleyebilir, ancak Denetim değişikliği bu denetimleri başka BIR HWND içinde yerleştirmenin basit bir yolunu sağlar.

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

Ardından türetilmiş bir sınıfı oluşturun <xref:System.Windows.Interop.HwndHost> ve `BuildWindowCore` ve yöntemlerini geçersiz kılın `DestroyWindowCore` :

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

Burada, `CreateDialog` gerçekten bir denetim olan iletişim kutusunu oluşturmak için kullanırsınız. Bu, DLL içinde çağrılan ilk metotlardan biri olduğundan, daha sonra kullanacağınız bir işlevi çağırarak bazı standart Win32 başlatma işlemi de yapmalısınız `InitializeGlobals()` :

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

Bu örneği şu anda çalıştırdıysanız, görüntülenen bir iletişim kutusu denetimi alırsınız, ancak iletişim kutusunu işlevsel bir iletişim kutusu yapan tüm klavye işlemlerini yoksayar. Artık `TranslateAccelerator` uygulamayı (' den gelen `IKeyboardInputSink` bir arabirimi) geçersiz kılmanız gerekir <xref:System.Windows.Interop.HwndHost> . Bu yöntem, uygulama WM_KEYDOWN ve WM_SYSKEYDOWN aldığında çağırılır.

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

Bu, tek bir parçadaki çok büyük bir kod olduğundan, daha ayrıntılı açıklamaları kullanabilir. Birincisi, C++ ve C++ makrolarını kullanan kod; zaten `TranslateAccelerator` Winuser. h içinde tanımlanan adlı bir makronun zaten bulunduğunu bilmeniz gerekir:

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

Bu nedenle, bir yöntemi değil bir yöntem tanımlamadığınızdan emin olun `TranslateAccelerator` `TranslateAcceleratorW` .

Benzer şekilde, hem yönetilmeyen Winuser. h MSG hem de yönetilen yapı mevcuttur `Microsoft::Win32::MSG` . C++ işlecini kullanarak ikisi arasındaki belirsizliği ortadan kaldırabilirsiniz `::` .

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}
```

Her iki mesaj de aynı verilere sahiptir, ancak bazen yönetilmeyen tanımıyla çalışmak daha kolaydır, bu nedenle bu örnekte belirgin dönüştürme yordamını tanımlayabilirsiniz:

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

Öğesine geri dönün `TranslateAccelerator` . Temel prensibi, `IsDialogMessage` mümkün olduğunca fazla iş yapmak Için Win32 işlevini `IsDialogMessage` çağırıldır, ancak iletişim kutusunun dışında bir şeye erişemez. İletişim kutusunda bir kullanıcı sekmesi olarak sekme, iletişim kutusundaki son denetimden sonra çalıştırıldığında, öğesini çağırarak odağı bölümüne ayarlamanız gerekir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `IKeyboardInputSite::OnNoMoreStops` .

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

Son olarak, çağırın `IsDialogMessage` . Ancak bir yöntemin sorumluluklarıyla, `TranslateAccelerator` [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tuş vuruşu işlenip işlemeyeceğinizi söylemiş olabilirsiniz. Bunu yapmadıysanız, giriş olayı uygulamanın geri kalanı aracılığıyla tünel ve balon oluşturabilir. Burada, bir klavye messange işleme ve Win32 'teki giriş mimarisinin doğası gibi bir olağandışı işlem sergileirsiniz. Ne yazık ki, `IsDialogMessage` belirli bir tuş vuruşunu işleymeksizin hiçbir şekilde döndürmez. Daha da kötüsü, bu, `DispatchMessage()` işleyememesi gereken tuş vuruşlarına çağrı görür!  Bu nedenle, bunu tersine mühendislik yapmanız `IsDialogMessage` ve yalnızca işleyeceğimizi bildiğiniz anahtarlar için çağırmanız gerekir:

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

Artık uyguladığınıza `TranslateAccelerator` göre, bir Kullanıcı, iletişim kutusunun içinde sekme ve üzerini daha büyük bir uygulamada sekmeye dönüştürebilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Ancak bir Kullanıcı iletişim kutusuna geri sekme kullanamaz. Bunu çözümlemek için geçersiz kılabilirsiniz `TabInto` :

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

`TraversalRequest`Parametresi sekme eyleminin sekme veya kaydırma sekmesi olduğunu söyler.

### <a name="override-onmnemonic-method-to-support-mnemonics"></a>Anımsatıcıları desteklemek için Onanımsatıcı metodunu geçersiz kılın

Klavye işleme neredeyse tamamlanmıştır, ancak bir şey eksik, ancak anımsatıcıları çalışmaz. Bir kullanıcı alt-F tuşlarına basarsa, odak "Ilk ad:" düzenleme kutusuna atmaz. Bu nedenle, yöntemini geçersiz kılarsınız `OnMnemonic` :

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

Neden burada çağırmayın `IsDialogMessage` ?  Yukarıdaki ile aynı sorun var, ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodunuzun tuş vuruşu yapıp gerçekleştirmediğini kodlayabilmeniz gerekir `IsDialogMessage` . İkinci bir sorun da vardır, çünkü `IsDialogMessage` ODAKLANMıŞ HWND iletişim kutusunun içinde değilse, anımsatıcı işlemeyi reddeder.

### <a name="instantiate-the-hwndhost-derived-class"></a>HwndHost türetilen sınıfının örneğini oluşturma

Son olarak, artık tüm anahtar ve sekme desteği hazır olduğuna göre, uygulamanızı <xref:System.Windows.Interop.HwndHost> daha büyük bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaya yerleştirebilirsiniz. Ana uygulama dilinde yazılmışsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , doğru yere yerleştirmenin en kolay yolu, koymak istediğiniz yerde boş bir öğe bırakmamadır <xref:System.Windows.Controls.Border> <xref:System.Windows.Interop.HwndHost> . Burada <xref:System.Windows.Controls.Border> adlı bir ad oluşturursunuz `insertHwndHostHere` :

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

Bu durumda, ' nin örneğini oluşturmak ve öğesine bağlamak için kod dizisinde iyi bir yer bulabilirsiniz <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Controls.Border> . Bu örnekte, türetilmiş sınıf için oluşturucuyu içine koyacaksınız <xref:System.Windows.Window> :

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
