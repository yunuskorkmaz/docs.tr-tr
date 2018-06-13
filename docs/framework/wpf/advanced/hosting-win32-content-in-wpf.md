---
title: WPF'de Win32 İçeriği Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: beb7d5e6e1f934b89bb7516eb7e9bbbaad696238
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547361"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="157c3-102">WPF'de Win32 İçeriği Barındırma</span><span class="sxs-lookup"><span data-stu-id="157c3-102">Hosting Win32 Content in WPF</span></span>
## <a name="prerequisites"></a><span data-ttu-id="157c3-103">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="157c3-103">Prerequisites</span></span>  
 <span data-ttu-id="157c3-104">Bkz: [WPF ve Win32 birlikte çalışabilirlik](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="157c3-104">See [WPF and Win32 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span></span>  
  
## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="157c3-105">Win32 Windows Presentation Framework (HwndHost) içinde bir kılavuz</span><span class="sxs-lookup"><span data-stu-id="157c3-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>  
 <span data-ttu-id="157c3-106">Yeniden [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] içinde içerik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları, <xref:System.Windows.Interop.HwndHost>, neye benzediğini gösteren Cwnd'lerden yapan bir denetim olduğu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği.</span><span class="sxs-lookup"><span data-stu-id="157c3-106">To reuse [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>  <span data-ttu-id="157c3-107">Gibi <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> kullanılacak basittir: öğesinden türetilen <xref:System.Windows.Interop.HwndHost> ve uygulamanıza `BuildWindowCore` ve `DestroyWindowCore` yöntemleri, ardından örneği, <xref:System.Windows.Interop.HwndHost> türetilmiş sınıf ve içine yerleştirin, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="157c3-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  
  
 <span data-ttu-id="157c3-108">Varsa, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] mantığı zaten bir denetim olarak paketlenmiş sonra `BuildWindowCore` uygulamasıdır yapılan bir çağrı değerinden biraz daha fazla `CreateWindow`.</span><span class="sxs-lookup"><span data-stu-id="157c3-108">If your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span>  <span data-ttu-id="157c3-109">Örneğin, oluşturmak için bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX denetimi [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="157c3-109">For example, to create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX control in [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span></span>  
  
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
  
 <span data-ttu-id="157c3-110">Ancak varsayalım [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu oldukça şekilde kendi içinde değil mi?</span><span class="sxs-lookup"><span data-stu-id="157c3-110">But suppose the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] code is not quite so self-contained?</span></span> <span data-ttu-id="157c3-111">Bu nedenle, oluşturursanız, bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] iletişim kutusu ve içeriğini büyük embed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="157c3-111">If so, you can create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="157c3-112">Bu örnek göstermektedir [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] ve [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], ancak farklı bir dilde veya komut satırından bunu da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="157c3-112">The sample shows this in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], although it is also possible to do this in a different language or at the command line.</span></span>  
  
 <span data-ttu-id="157c3-113">Başlangıç derlenir basit bir iletişim kutusuyla bir [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projesi.</span><span class="sxs-lookup"><span data-stu-id="157c3-113">Start with a simple dialog, which is compiled into a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] project.</span></span>  
  
 <span data-ttu-id="157c3-114">Ardından, iletişim büyük tanıtmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama:</span><span class="sxs-lookup"><span data-stu-id="157c3-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>  
  
-   <span data-ttu-id="157c3-115">Derleme [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] yönetilen olarak (`/clr`)</span><span class="sxs-lookup"><span data-stu-id="157c3-115">Compile the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] as managed (`/clr`)</span></span>  
  
-   <span data-ttu-id="157c3-116">Bir denetime iletişim kutusunu aç</span><span class="sxs-lookup"><span data-stu-id="157c3-116">Turn the dialog into a control</span></span>  
  
-   <span data-ttu-id="157c3-117">Türetilmiş sınıf tanımlama <xref:System.Windows.Interop.HwndHost> ile `BuildWindowCore` ve `DestroyWindowCore` yöntemleri</span><span class="sxs-lookup"><span data-stu-id="157c3-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>  
  
-   <span data-ttu-id="157c3-118">Geçersiz kılma `TranslateAccelerator` iletişim anahtarlarını işlemek için yöntemi</span><span class="sxs-lookup"><span data-stu-id="157c3-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>  
  
-   <span data-ttu-id="157c3-119">Geçersiz kılma `TabInto` sekme desteklemek için yöntemi</span><span class="sxs-lookup"><span data-stu-id="157c3-119">Override `TabInto` method to support tabbing</span></span>  
  
-   <span data-ttu-id="157c3-120">Geçersiz kılma `OnMnemonic` anımsatıcıları desteklemek için yöntemi</span><span class="sxs-lookup"><span data-stu-id="157c3-120">Override `OnMnemonic` method to support mnemonics</span></span>  
  
-   <span data-ttu-id="157c3-121">Örneği <xref:System.Windows.Interop.HwndHost> alt ve sağ altında yerleştirin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi</span><span class="sxs-lookup"><span data-stu-id="157c3-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>  
  
### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="157c3-122">Bir denetime iletişim kutusunu aç</span><span class="sxs-lookup"><span data-stu-id="157c3-122">Turn the Dialog into a Control</span></span>  
 <span data-ttu-id="157c3-123">Alt HWND WS_CHILD ve DS_CONTROL stilleri kullanarak iletişim kutusunu kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="157c3-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span>  <span data-ttu-id="157c3-124">İletişim kutusu tanımlandığı kaynak dosyasına (.rc) gidin ve iletişim kutusu tanımını başlangıcını bulur:</span><span class="sxs-lookup"><span data-stu-id="157c3-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 <span data-ttu-id="157c3-125">İkinci satır değiştirin:</span><span class="sxs-lookup"><span data-stu-id="157c3-125">Change the second line to:</span></span>  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 <span data-ttu-id="157c3-126">Bu eylem tam olarak kendi içinde bulunan bir denetime paketi değil; yine de çağrı gerekiyorsa `IsDialogMessage()` şekilde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] belirli iletileri işleyebilmesi için ancak denetim değişikliği başka bir HWND içinde bu denetimleri yerleştirme basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="157c3-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>  
  
## <a name="subclass-hwndhost"></a><span data-ttu-id="157c3-127">Bir alt HwndHost</span><span class="sxs-lookup"><span data-stu-id="157c3-127">Subclass HwndHost</span></span>  
 <span data-ttu-id="157c3-128">Şu ad alanlarından içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="157c3-128">Import the following namespaces:</span></span>  
  
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
  
 <span data-ttu-id="157c3-129">Ardından, türetilmiş bir sınıf oluşturun <xref:System.Windows.Interop.HwndHost> ve geçersiz kılma `BuildWindowCore` ve `DestroyWindowCore` yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="157c3-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>  
  
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
  
 <span data-ttu-id="157c3-130">Burada kullandığınız `CreateDialog` gerçekten bir denetimdir, iletişim kutusu oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="157c3-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span>  <span data-ttu-id="157c3-131">Bu içinde adlı ilk yöntemlerden birini olduğundan [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], bazı standart yapması gerektiğini [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] tanımladığınız daha sonra bir işlev çağırarak başlatma adlı `InitializeGlobals()`:</span><span class="sxs-lookup"><span data-stu-id="157c3-131">Since this is one of the first methods called inside the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], you should also do some standard [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>  
  
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
  
### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="157c3-132">İletişim anahtarlarını işlemek için TranslateAccelerator yöntemi geçersiz kılın</span><span class="sxs-lookup"><span data-stu-id="157c3-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>  
 <span data-ttu-id="157c3-133">Bu örnek çalıştırdıysanız şimdi görüntüleyen bir iletişim kutusu denetim elde edebileceğiniz, ancak bu yaptığı işleme klavye tümünün bir iletişim kutusu bir işlev iletişim kutusu yok sayın.</span><span class="sxs-lookup"><span data-stu-id="157c3-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span>  <span data-ttu-id="157c3-134">Şimdi kılmalıdır `TranslateAccelerator` uygulaması (hangi gelir `IKeyboardInputSink`, bir arabirim, <xref:System.Windows.Interop.HwndHost> uygulayan).</span><span class="sxs-lookup"><span data-stu-id="157c3-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span>  <span data-ttu-id="157c3-135">Bu yöntem, uygulama WM_KEYDOWN ve WM_SYSKEYDOWN aldığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="157c3-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>  
  
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
  
 <span data-ttu-id="157c3-136">Bazı daha ayrıntılı açıklamaları kullanabilirsiniz şekilde bir parça kod çok budur.</span><span class="sxs-lookup"><span data-stu-id="157c3-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span>  <span data-ttu-id="157c3-137">İlk olarak, kod kullanarak [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] ve [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] makroları; zaten var olduğu adlı bir makro bilmeniz gereken `TranslateAccelerator`, winuser.h içinde tanımlanan:</span><span class="sxs-lookup"><span data-stu-id="157c3-137">First, the code using [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 <span data-ttu-id="157c3-138">Bu nedenle tanımladığınızdan emin olun bir `TranslateAccelerator` yöntemi ve bir `TranslateAcceleratorW` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="157c3-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>  
  
 <span data-ttu-id="157c3-139">Benzer şekilde, hem yönetilmeyen winuser.h MSG ve yoktur yönetilen `Microsoft::Win32::MSG` yapısı.</span><span class="sxs-lookup"><span data-stu-id="157c3-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span>  <span data-ttu-id="157c3-140">Kullanarak bunları birbirinden ayırt etmek [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` işleci.</span><span class="sxs-lookup"><span data-stu-id="157c3-140">You can disambiguate between the two using the [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operator.</span></span>  
  
```  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 <span data-ttu-id="157c3-141">Hem iletileri aynı verilere sahip, ancak bazı durumlarda bu örnekte belirgin dönüştürme yordamına tanımlayabilirsiniz şekilde yönetilmeyen tanımıyla çalışmak daha kolay olur:</span><span class="sxs-lookup"><span data-stu-id="157c3-141">Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:</span></span>  
  
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
  
 <span data-ttu-id="157c3-142">Geri `TranslateAccelerator`.</span><span class="sxs-lookup"><span data-stu-id="157c3-142">Back to `TranslateAccelerator`.</span></span>  <span data-ttu-id="157c3-143">Temel ilke çağırmaktır [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işlevi `IsDialogMessage` kadar iş mümkün olduğunca yapmak için ancak `IsDialogMessage` iletişim dışında bir şey için erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="157c3-143">The basic principle is to call the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="157c3-144">Sekme tuşuyla ilerlerken iletişim kutusunda, geçici bir kullanıcı sekmesi bizim iletişim kutusunda en son denetim geçmiş çalışırken odak ayarlamak için gereken [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çağırarak bölümü `IKeyboardInputSite::OnNoMoreStops`.</span><span class="sxs-lookup"><span data-stu-id="157c3-144">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>  
  
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
  
 <span data-ttu-id="157c3-145">Son olarak, arama `IsDialogMessage`.</span><span class="sxs-lookup"><span data-stu-id="157c3-145">Finally, call `IsDialogMessage`.</span></span>  <span data-ttu-id="157c3-146">Ancak sorumluluklarını bir `TranslateAccelerator` yöntemi bildiren [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veya tuş vuruşu olup işlenmiş.</span><span class="sxs-lookup"><span data-stu-id="157c3-146">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="157c3-147">Bunu işlemedi, giriş olayı tünel oluşturabilir ve uygulama kalanında Kabarcık.</span><span class="sxs-lookup"><span data-stu-id="157c3-147">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="157c3-148">Klavye messange işleme oluþturmaz ve giriş mimarisinde yapısını burada açığa çıkarır [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span><span class="sxs-lookup"><span data-stu-id="157c3-148">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span></span> <span data-ttu-id="157c3-149">Ne yazık ki, `IsDialogMessage` herhangi bir şekilde belirli bir tuş vuruşu işleme olup olmadığını döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="157c3-149">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span>  <span data-ttu-id="157c3-150">Kötüsü, çağıracak `DispatchMessage()` , değil işlemek tuş vuruşları üzerinde!</span><span class="sxs-lookup"><span data-stu-id="157c3-150">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="157c3-151">Ters mühendislik sahip şekilde `IsDialogMessage`ve yalnızca bu bildiğiniz anahtarları işleyecek için çağırın:</span><span class="sxs-lookup"><span data-stu-id="157c3-151">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>  
  
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
  
### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="157c3-152">Destek sekme için TabInto yöntemini geçersiz kılın</span><span class="sxs-lookup"><span data-stu-id="157c3-152">Override TabInto Method to Support Tabbing</span></span>  
 <span data-ttu-id="157c3-153">Uygulanan olduğunuza `TranslateAccelerator`, bir kullanıcı geçici bir çözüm içinde iletişim sekme kutusu ve sekmesine onu dışında büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="157c3-153">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="157c3-154">Ancak, bir kullanıcı iletişim kutusuna geri sekmesinde olamaz.</span><span class="sxs-lookup"><span data-stu-id="157c3-154">But a user cannot tab back into the dialog box.</span></span>  <span data-ttu-id="157c3-155">Çözmek için geçersiz kılma `TabInto`:</span><span class="sxs-lookup"><span data-stu-id="157c3-155">To solve that, you override `TabInto`:</span></span>  
  
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
  
 <span data-ttu-id="157c3-156">`TraversalRequest` Parametresi bildirir, sekmesi eylem sekme veya SHIFT SEKME olup.</span><span class="sxs-lookup"><span data-stu-id="157c3-156">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>  
  
### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="157c3-157">Anımsatıcıları desteklemek için OnMnemonic yöntemini geçersiz kılın</span><span class="sxs-lookup"><span data-stu-id="157c3-157">Override OnMnemonic Method to Support Mnemonics</span></span>  
 <span data-ttu-id="157c3-158">Klavye işleme neredeyse tamamlandı, ancak bir şey eksik – anımsatıcıları çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="157c3-158">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span>  <span data-ttu-id="157c3-159">Bir kullanıcı alt-F basarsa odak doe atlamak değil "ad:" düzenleme kutusu.</span><span class="sxs-lookup"><span data-stu-id="157c3-159">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="157c3-160">Bu nedenle, geçersiz `OnMnemonic` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="157c3-160">So, you override the `OnMnemonic` method:</span></span>  
  
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
  
 <span data-ttu-id="157c3-161">Neden çağrı `IsDialogMessage` burada?</span><span class="sxs-lookup"><span data-stu-id="157c3-161">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="157c3-162">--Önce bildirmek için gerek duyduğunuz aynı sorunu yaşayıp [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veya değil, tuş vuruşu kodunuzu işlenmiş olup olmadığını kod ve `IsDialogMessage` , yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="157c3-162">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span>  <span data-ttu-id="157c3-163">Ayrıca vardır ikinci bir sorun nedeniyle `IsDialogMessage` odaklanmış HWND iletişim kutusunun içine değilse anımsatıcı işlemeye reddediyor.</span><span class="sxs-lookup"><span data-stu-id="157c3-163">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>  
  
### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="157c3-164">Örneği HwndHost türetilen sınıfı</span><span class="sxs-lookup"><span data-stu-id="157c3-164">Instantiate the HwndHost Derived Class</span></span>  
 <span data-ttu-id="157c3-165">Anahtar ve sekmesi tüm destek bulunduğundan, son olarak, koyabilirsiniz, <xref:System.Windows.Interop.HwndHost> büyük içine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="157c3-165">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="157c3-166">Ana uygulama yazılmışsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], doğru yerde yerleştirilecek en kolay yolu boş bırakmaktır <xref:System.Windows.Controls.Border> yerleştirmek istediğiniz öğe <xref:System.Windows.Interop.HwndHost>.</span><span class="sxs-lookup"><span data-stu-id="157c3-166">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span>  <span data-ttu-id="157c3-167">Burada oluşturduğunuz bir <xref:System.Windows.Controls.Border> adlı `insertHwndHostHere`:</span><span class="sxs-lookup"><span data-stu-id="157c3-167">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>  
  
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
  
 <span data-ttu-id="157c3-168">Uygun bir yerdir örneği oluşturmak için kodu sırayla bulmak için kalan tek şey sonra <xref:System.Windows.Interop.HwndHost> ve buna bağlanmak <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="157c3-168">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span>  <span data-ttu-id="157c3-169">Bu örnekte, onu oluşturucusu içinde sokar <xref:System.Windows.Window> türetilmiş sınıf:</span><span class="sxs-lookup"><span data-stu-id="157c3-169">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>  
  
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
  
 <span data-ttu-id="157c3-170">Hangi, sunar:</span><span class="sxs-lookup"><span data-stu-id="157c3-170">Which gives you:</span></span>  
  
 <span data-ttu-id="157c3-171">![WPF uygulaması ekran görüntüsü](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")</span><span class="sxs-lookup"><span data-stu-id="157c3-171">![WPF application screen shot](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="157c3-172">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="157c3-172">See Also</span></span>  
 [<span data-ttu-id="157c3-173">WPF ve Win32 Birlikte Çalışması</span><span class="sxs-lookup"><span data-stu-id="157c3-173">WPF and Win32 Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
