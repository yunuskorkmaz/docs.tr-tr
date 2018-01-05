---
title: "WPF'de Win32 İçeriği Barındırma"
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
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c92e5b045b248337f1cb96c333ac38f1228dd90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-win32-content-in-wpf"></a>WPF'de Win32 İçeriği Barındırma
## <a name="prerequisites"></a>Önkoşullar  
 Bkz: [WPF ve Win32 birlikte çalışabilirlik](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Win32 Windows Presentation Framework (HwndHost) içinde bir kılavuz  
 Yeniden [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] içinde içerik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları, <xref:System.Windows.Interop.HwndHost>, neye benzediğini gösteren Cwnd'lerden yapan bir denetim olduğu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği.  Gibi <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> kullanılacak basittir: öğesinden türetilen <xref:System.Windows.Interop.HwndHost> ve uygulamanıza `BuildWindowCore` ve `DestroyWindowCore` yöntemleri, ardından örneği, <xref:System.Windows.Interop.HwndHost> türetilmiş sınıf ve içine yerleştirin, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.  
  
 Varsa, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] mantığı zaten bir denetim olarak paketlenmiş sonra `BuildWindowCore` uygulamasıdır yapılan bir çağrı değerinden biraz daha fazla `CreateWindow`.  Örneğin, oluşturmak için bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX denetimi [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:  
  
```  
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
  
 Ancak varsayalım [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu oldukça şekilde kendi içinde değil mi? Bu nedenle, oluşturursanız, bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] iletişim kutusu ve içeriğini büyük embed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.  Bu örnek göstermektedir [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] ve [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], ancak farklı bir dilde veya komut satırından bunu da mümkündür.  
  
 Başlangıç derlenir basit bir iletişim kutusuyla bir [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projesi.  
  
 Ardından, iletişim büyük tanıtmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama:  
  
-   Derleme [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] yönetilen olarak (`/clr`)  
  
-   Bir denetime iletişim kutusunu aç  
  
-   Türetilmiş sınıf tanımlama <xref:System.Windows.Interop.HwndHost> ile `BuildWindowCore` ve `DestroyWindowCore` yöntemleri  
  
-   Geçersiz kılma `TranslateAccelerator` iletişim anahtarlarını işlemek için yöntemi  
  
-   Geçersiz kılma `TabInto` sekme desteklemek için yöntemi  
  
-   Geçersiz kılma `OnMnemonic` anımsatıcıları desteklemek için yöntemi  
  
-   Örneği <xref:System.Windows.Interop.HwndHost> alt ve sağ altında yerleştirin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi  
  
### <a name="turn-the-dialog-into-a-control"></a>Bir denetime iletişim kutusunu aç  
 Alt HWND WS_CHILD ve DS_CONTROL stilleri kullanarak iletişim kutusunu kapatabilirsiniz.  İletişim kutusu tanımlandığı kaynak dosyasına (.rc) gidin ve iletişim kutusu tanımını başlangıcını bulur:  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 İkinci satır değiştirin:  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 Bu eylem tam olarak kendi içinde bulunan bir denetime paketi değil; yine de çağrı gerekiyorsa `IsDialogMessage()` şekilde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] belirli iletileri işleyebilmesi için ancak denetim değişikliği başka bir HWND içinde bu denetimleri yerleştirme basit bir yol sağlar.  
  
## <a name="subclass-hwndhost"></a>Bir alt HwndHost  
 Şu ad alanlarından içeri aktarın:  
  
```  
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
  
```  
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
  
 Burada kullandığınız `CreateDialog` gerçekten bir denetimdir, iletişim kutusu oluşturmak için.  Bu içinde adlı ilk yöntemlerden birini olduğundan [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], bazı standart yapması gerektiğini [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] tanımladığınız daha sonra bir işlev çağırarak başlatma adlı `InitializeGlobals()`:  
  
```  
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
  
### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>İletişim anahtarlarını işlemek için TranslateAccelerator yöntemi geçersiz kılın  
 Bu örnek çalıştırdıysanız şimdi görüntüleyen bir iletişim kutusu denetim elde edebileceğiniz, ancak bu yaptığı işleme klavye tümünün bir iletişim kutusu bir işlev iletişim kutusu yok sayın.  Şimdi kılmalıdır `TranslateAccelerator` uygulaması (hangi gelir `IKeyboardInputSink`, bir arabirim, <xref:System.Windows.Interop.HwndHost> uygulayan).  Bu yöntem, uygulama WM_KEYDOWN ve WM_SYSKEYDOWN aldığında çağrılır.  
  
```  
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
  
 Bazı daha ayrıntılı açıklamaları kullanabilirsiniz şekilde bir parça kod çok budur.  İlk olarak, kod kullanarak [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] ve [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] makroları; zaten var olduğu adlı bir makro bilmeniz gereken `TranslateAccelerator`, winuser.h içinde tanımlanan:  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 Bu nedenle tanımladığınızdan emin olun bir `TranslateAccelerator` yöntemi ve bir `TranslateAcceleratorW` yöntemi.  
  
 Benzer şekilde, hem yönetilmeyen winuser.h MSG ve yoktur yönetilen `Microsoft::Win32::MSG` yapısı.  Kullanarak bunları birbirinden ayırt etmek [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` işleci.  
  
```  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 Hem iletileri aynı verilere sahip, ancak bazı durumlarda bu örnekte belirgin dönüştürme yordamına tanımlayabilirsiniz şekilde yönetilmeyen tanımıyla çalışmak daha kolay olur:  
  
```  
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
  
 Geri `TranslateAccelerator`.  Temel ilke çağırmaktır [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işlevi `IsDialogMessage` kadar iş mümkün olduğunca yapmak için ancak `IsDialogMessage` iletişim dışında bir şey için erişimi yok. Sekme tuşuyla ilerlerken iletişim kutusunda, geçici bir kullanıcı sekmesi bizim iletişim kutusunda en son denetim geçmiş çalışırken odak ayarlamak için gereken [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çağırarak bölümü `IKeyboardInputSite::OnNoMoreStops`.  
  
```  
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
  
 Son olarak, arama `IsDialogMessage`.  Ancak sorumluluklarını bir `TranslateAccelerator` yöntemi bildiren [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veya tuş vuruşu olup işlenmiş. Bunu işlemedi, giriş olayı tünel oluşturabilir ve uygulama kalanında Kabarcık. Klavye messange işleme oluþturmaz ve giriş mimarisinde yapısını burada açığa çıkarır [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Ne yazık ki, `IsDialogMessage` herhangi bir şekilde belirli bir tuş vuruşu işleme olup olmadığını döndürmüyor.  Kötüsü, çağıracak `DispatchMessage()` , değil işlemek tuş vuruşları üzerinde!  Ters mühendislik sahip şekilde `IsDialogMessage`ve yalnızca bu bildiğiniz anahtarları işleyecek için çağırın:  
  
```  
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
  
### <a name="override-tabinto-method-to-support-tabbing"></a>Destek sekme için TabInto yöntemini geçersiz kılın  
 Uygulanan olduğunuza `TranslateAccelerator`, bir kullanıcı geçici bir çözüm içinde iletişim sekme kutusu ve sekmesine onu dışında büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.  Ancak, bir kullanıcı iletişim kutusuna geri sekmesinde olamaz.  Çözmek için geçersiz kılma `TabInto`:  
  
```  
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
  
 `TraversalRequest` Parametresi bildirir, sekmesi eylem sekme veya SHIFT SEKME olup.  
  
### <a name="override-onmnemonic-method-to-support-mnemonics"></a>Anımsatıcıları desteklemek için OnMnemonic yöntemini geçersiz kılın  
 Klavye işleme neredeyse tamamlandı, ancak bir şey eksik – anımsatıcıları çalışmaz.  Bir kullanıcı alt-F basarsa odak doe atlamak değil "ad:" düzenleme kutusu. Bu nedenle, geçersiz `OnMnemonic` yöntemi:  
  
```  
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
  
 Neden çağrı `IsDialogMessage` burada?  --Önce bildirmek için gerek duyduğunuz aynı sorunu yaşayıp [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veya değil, tuş vuruşu kodunuzu işlenmiş olup olmadığını kod ve `IsDialogMessage` , yapamazsınız.  Ayrıca vardır ikinci bir sorun nedeniyle `IsDialogMessage` odaklanmış HWND iletişim kutusunun içine değilse anımsatıcı işlemeye reddediyor.  
  
### <a name="instantiate-the-hwndhost-derived-class"></a>Örneği HwndHost türetilen sınıfı  
 Anahtar ve sekmesi tüm destek bulunduğundan, son olarak, koyabilirsiniz, <xref:System.Windows.Interop.HwndHost> büyük içine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.  Ana uygulama yazılmışsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], doğru yerde yerleştirilecek en kolay yolu boş bırakmaktır <xref:System.Windows.Controls.Border> yerleştirmek istediğiniz öğe <xref:System.Windows.Interop.HwndHost>.  Burada oluşturduğunuz bir <xref:System.Windows.Controls.Border> adlı `insertHwndHostHere`:  
  
```  
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
  
 Uygun bir yerdir örneği oluşturmak için kodu sırayla bulmak için kalan tek şey sonra <xref:System.Windows.Interop.HwndHost> ve buna bağlanmak <xref:System.Windows.Controls.Border>.  Bu örnekte, onu oluşturucusu içinde sokar <xref:System.Windows.Window> türetilmiş sınıf:  
  
```  
public partial class Window1 : Window {  
    public Window1() {  
    }  
  
    void Window1_Loaded(object sender, RoutedEventArgs e) {  
        HwndHost host = new ManagedCpp.MyHwndHost();  
        insertHwndHostHere.Child = host;  
    }  
}  
```  
  
 Hangi, sunar:  
  
 ![WPF uygulaması ekran görüntüsü](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF ve Win32 Birlikte Çalışması](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
