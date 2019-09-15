---
title: WPF'de Win32 İçeriği Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: b598b55c72096daac2487e4c52584abf9735f257
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991467"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="95f7f-102">WPF'de Win32 İçeriği Barındırma</span><span class="sxs-lookup"><span data-stu-id="95f7f-102">Hosting Win32 Content in WPF</span></span>

## <a name="prerequisites"></a><span data-ttu-id="95f7f-103">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="95f7f-103">Prerequisites</span></span>

<span data-ttu-id="95f7f-104">Bkz. [WPF ve Win32 birlikte](wpf-and-win32-interoperation.md)çalışma.</span><span class="sxs-lookup"><span data-stu-id="95f7f-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="95f7f-105">Windows Presentation Framework Içinde Win32 bir adım adım (HwndHost)</span><span class="sxs-lookup"><span data-stu-id="95f7f-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>

<span data-ttu-id="95f7f-106">Uygulamalar içindeki [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği yeniden kullanmak için, <xref:System.Windows.Interop.HwndHost>HWND NDS 'nin içerik gibi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görünmesini sağlayan bir denetim olan kullanın.</span><span class="sxs-lookup"><span data-stu-id="95f7f-106">To reuse [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="95f7f-107">Benzer <xref:System.Windows.Interop.HwndSource> <xref:System.Windows.Interop.HwndHost> `BuildWindowCore` `DestroyWindowCore` şekilde,<xref:System.Windows.Interop.HwndHost> kullanımı basittir: türet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve uygulama ve yöntemlerle türetilmiş sınıfınızı oluşturun ve <xref:System.Windows.Interop.HwndHost> Uygulamanızı.</span><span class="sxs-lookup"><span data-stu-id="95f7f-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

<span data-ttu-id="95f7f-108">Mantığınızın [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zaten bir denetim olarak paketlenmesi durumunda `BuildWindowCore` uygulamanız, öğesine yapılan `CreateWindow`çağrıdan çok daha fazla.</span><span class="sxs-lookup"><span data-stu-id="95f7f-108">If your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span> <span data-ttu-id="95f7f-109">Örneğin, içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] C++bir LISTBOX denetimi oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="95f7f-109">For example, to create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX control in C++:</span></span>

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

<span data-ttu-id="95f7f-110">Ancak kodun yalnızca [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kendi kendine dahil olmadığı varsayın.</span><span class="sxs-lookup"><span data-stu-id="95f7f-110">But suppose the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] code is not quite so self-contained?</span></span> <span data-ttu-id="95f7f-111">Bu durumda, bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] iletişim kutusu oluşturabilir ve içeriğini daha büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulamaya katabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95f7f-111">If so, you can create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="95f7f-112">Örnek bunu [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] ve C++' de bunu farklı bir dilde veya komut satırında yapmak mümkün olsa da gösterir.</span><span class="sxs-lookup"><span data-stu-id="95f7f-112">The sample shows this in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] and C++, although it is also possible to do this in a different language or at the command line.</span></span>

<span data-ttu-id="95f7f-113">Bir C++ DLL projesine derlenmiş basit bir iletişim kutusuyla başlayın.</span><span class="sxs-lookup"><span data-stu-id="95f7f-113">Start with a simple dialog, which is compiled into a C++ DLL project.</span></span>

<span data-ttu-id="95f7f-114">Daha sonra, iletişim kutusunu daha büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaya tanıtın:</span><span class="sxs-lookup"><span data-stu-id="95f7f-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>

- <span data-ttu-id="95f7f-115">DLL 'yi yönetilen (`/clr`) olarak derle</span><span class="sxs-lookup"><span data-stu-id="95f7f-115">Compile the DLL as managed (`/clr`)</span></span>

- <span data-ttu-id="95f7f-116">İletişim kutusunu Denetim haline getirin</span><span class="sxs-lookup"><span data-stu-id="95f7f-116">Turn the dialog into a control</span></span>

- <span data-ttu-id="95f7f-117">Türetilmiş sınıfını <xref:System.Windows.Interop.HwndHost> `BuildWindowCore` ve yöntemlerinitanımlayın`DestroyWindowCore`</span><span class="sxs-lookup"><span data-stu-id="95f7f-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>

- <span data-ttu-id="95f7f-118">İletişim `TranslateAccelerator` anahtarlarını işlemek için geçersiz kılma yöntemi</span><span class="sxs-lookup"><span data-stu-id="95f7f-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>

- <span data-ttu-id="95f7f-119">Sekmeyi `TabInto` desteklemek için geçersiz kılma yöntemi</span><span class="sxs-lookup"><span data-stu-id="95f7f-119">Override `TabInto` method to support tabbing</span></span>

- <span data-ttu-id="95f7f-120">Anımsatıcıları `OnMnemonic` desteklemek için yöntemi geçersiz kıl</span><span class="sxs-lookup"><span data-stu-id="95f7f-120">Override `OnMnemonic` method to support mnemonics</span></span>

- <span data-ttu-id="95f7f-121">Alt sınıfı oluştur ve sağ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğenin altına koy <xref:System.Windows.Interop.HwndHost></span><span class="sxs-lookup"><span data-stu-id="95f7f-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>

### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="95f7f-122">Iletişim kutusunu Denetim haline getirin</span><span class="sxs-lookup"><span data-stu-id="95f7f-122">Turn the Dialog into a Control</span></span>

<span data-ttu-id="95f7f-123">WS_CHILD ve DS_CONTROL stillerini kullanarak bir iletişim kutusunu alt HWND 'e dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95f7f-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span> <span data-ttu-id="95f7f-124">İletişim kutusunun tanımlandığı kaynak dosyasına (. RC) gidin ve iletişim kutusunun tanımının başlangıcını bulun:</span><span class="sxs-lookup"><span data-stu-id="95f7f-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

<span data-ttu-id="95f7f-125">İkinci satırı şu şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="95f7f-125">Change the second line to:</span></span>

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

<span data-ttu-id="95f7f-126">Bu eylem, kendisini bağımsız bir denetime tam olarak paketlemez; Yine de çağırmanız `IsDialogMessage()` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] gerekir, ancak bazı iletileri işleyebilir, ancak Denetim değişikliği bu denetimleri başka bir HWND içinde yerleştirmenin basit bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="95f7f-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>

## <a name="subclass-hwndhost"></a><span data-ttu-id="95f7f-127">HwndHost alt sınıfı</span><span class="sxs-lookup"><span data-stu-id="95f7f-127">Subclass HwndHost</span></span>

<span data-ttu-id="95f7f-128">Aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="95f7f-128">Import the following namespaces:</span></span>

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

<span data-ttu-id="95f7f-129">Ardından türetilmiş bir sınıfı <xref:System.Windows.Interop.HwndHost> oluşturun ve `BuildWindowCore` ve `DestroyWindowCore` yöntemlerini geçersiz kılın:</span><span class="sxs-lookup"><span data-stu-id="95f7f-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>

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

<span data-ttu-id="95f7f-130">Burada, `CreateDialog` gerçekten bir denetim olan iletişim kutusunu oluşturmak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="95f7f-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span> <span data-ttu-id="95f7f-131">Bu, dll içinde çağrılan ilk metotlardan biri olduğundan, daha sonra [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] `InitializeGlobals()`kullanacağınız bir işlevi çağırarak bazı standart başlatma da yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="95f7f-131">Since this is one of the first methods called inside the DLL, you should also do some standard [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>

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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="95f7f-132">Iletişim anahtarlarını Işlemek için TranslateAccelerator metodunu geçersiz kılın</span><span class="sxs-lookup"><span data-stu-id="95f7f-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>

<span data-ttu-id="95f7f-133">Bu örneği şu anda çalıştırdıysanız, görüntülenen bir iletişim kutusu denetimi alırsınız, ancak iletişim kutusunu işlevsel bir iletişim kutusu yapan tüm klavye işlemlerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="95f7f-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span> <span data-ttu-id="95f7f-134">Artık `TranslateAccelerator` uygulamayı (' den `IKeyboardInputSink`gelen bir arabirimi <xref:System.Windows.Interop.HwndHost> ) geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="95f7f-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span> <span data-ttu-id="95f7f-135">Bu yöntem, uygulama WM_KEYDOWN ve WM_SYSKEYDOWN aldığında çağırılır.</span><span class="sxs-lookup"><span data-stu-id="95f7f-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>

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

<span data-ttu-id="95f7f-136">Bu, tek bir parçadaki çok büyük bir kod olduğundan, daha ayrıntılı açıklamaları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="95f7f-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span> <span data-ttu-id="95f7f-137">İlk olarak, ve C++ C++ makroları kullanan kod; zaten Winuser. h içinde tanımlanan adlı `TranslateAccelerator`bir makronun zaten bulunduğunu bilmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="95f7f-137">First, the code using C++ and C++ macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

<span data-ttu-id="95f7f-138">Bu nedenle, bir yöntemi `TranslateAccelerator` `TranslateAcceleratorW` değil bir yöntem tanımlamadığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="95f7f-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>

<span data-ttu-id="95f7f-139">Benzer şekilde, hem yönetilmeyen Winuser. h msg hem de yönetilen `Microsoft::Win32::MSG` yapı mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="95f7f-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span> <span data-ttu-id="95f7f-140">`::` İşlecini kullanarak C++ iki arasındaki ilişkiyi ayırt edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95f7f-140">You can disambiguate between the two using the C++ `::` operator.</span></span>

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

<span data-ttu-id="95f7f-141">Öğesine `TranslateAccelerator`geri dönün.</span><span class="sxs-lookup"><span data-stu-id="95f7f-141">Back to `TranslateAccelerator`.</span></span> <span data-ttu-id="95f7f-142">Temel prensibi, mümkün olduğunca çok [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] iş `IsDialogMessage` yapmak için işlevi çağırıldır, ancak `IsDialogMessage` iletişim kutusunun dışında bir şeye erişemez.</span><span class="sxs-lookup"><span data-stu-id="95f7f-142">The basic principle is to call the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="95f7f-143">İletişim kutusunda bir kullanıcı sekmesi olarak sekme, iletişim kutusundaki son denetimden sonra çalıştırıldığında, öğesini çağırarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `IKeyboardInputSite::OnNoMoreStops`odağı bölümüne ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="95f7f-143">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>

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

<span data-ttu-id="95f7f-144">Son olarak, `IsDialogMessage`çağırın.</span><span class="sxs-lookup"><span data-stu-id="95f7f-144">Finally, call `IsDialogMessage`.</span></span> <span data-ttu-id="95f7f-145">Ancak bir `TranslateAccelerator` yöntemin sorumluluklarıyla, tuş vuruşu işlenip işlemeyeceğinizi söylemiş [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95f7f-145">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="95f7f-146">Bunu yapmadıysanız, giriş olayı uygulamanın geri kalanı aracılığıyla tünel ve balon oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="95f7f-146">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="95f7f-147">Burada, klavye messange işleme ve içindeki giriş mimarisinin doğasını bir olağandışı şekilde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]kullanıma sunacaksınız.</span><span class="sxs-lookup"><span data-stu-id="95f7f-147">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span></span> <span data-ttu-id="95f7f-148">Ne yazık `IsDialogMessage` ki, belirli bir tuş vuruşunu işleymeksizin hiçbir şekilde döndürmez.</span><span class="sxs-lookup"><span data-stu-id="95f7f-148">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span> <span data-ttu-id="95f7f-149">Daha da kötüsü, bu `DispatchMessage()` , işleyememesi gereken tuş vuruşlarına çağrı görür!</span><span class="sxs-lookup"><span data-stu-id="95f7f-149">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="95f7f-150">Bu nedenle, bunu tersine mühendislik `IsDialogMessage`yapmanız ve yalnızca işleyeceğimizi bildiğiniz anahtarlar için çağırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="95f7f-150">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>

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

### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="95f7f-151">Sekmeyi desteklemek için TabInto metodunu geçersiz kılın</span><span class="sxs-lookup"><span data-stu-id="95f7f-151">Override TabInto Method to Support Tabbing</span></span>

<span data-ttu-id="95f7f-152">Artık uyguladığınıza `TranslateAccelerator`göre, bir Kullanıcı, iletişim kutusunun içinde sekme ve üzerini daha büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulamada sekmeye dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95f7f-152">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="95f7f-153">Ancak bir Kullanıcı iletişim kutusuna geri sekme kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="95f7f-153">But a user cannot tab back into the dialog box.</span></span> <span data-ttu-id="95f7f-154">Bunu çözümlemek için geçersiz kılabilirsiniz `TabInto`:</span><span class="sxs-lookup"><span data-stu-id="95f7f-154">To solve that, you override `TabInto`:</span></span>

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

<span data-ttu-id="95f7f-155">`TraversalRequest` Parametresi sekme eyleminin sekme veya kaydırma sekmesi olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="95f7f-155">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>

### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="95f7f-156">Anımsatıcıları desteklemek için Onanımsatıcı metodunu geçersiz kılın</span><span class="sxs-lookup"><span data-stu-id="95f7f-156">Override OnMnemonic Method to Support Mnemonics</span></span>

<span data-ttu-id="95f7f-157">Klavye işleme neredeyse tamamlanmıştır, ancak bir şey eksik, ancak anımsatıcıları çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="95f7f-157">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span> <span data-ttu-id="95f7f-158">Bir kullanıcı alt-F tuşlarına basarsa, odak "Ilk ad:" düzenleme kutusuna atmaz.</span><span class="sxs-lookup"><span data-stu-id="95f7f-158">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="95f7f-159">Bu nedenle, `OnMnemonic` yöntemini geçersiz kılarsınız:</span><span class="sxs-lookup"><span data-stu-id="95f7f-159">So, you override the `OnMnemonic` method:</span></span>

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

<span data-ttu-id="95f7f-160">Neden burada çağırmayın `IsDialogMessage` ?</span><span class="sxs-lookup"><span data-stu-id="95f7f-160">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="95f7f-161">Yukarıdaki ile aynı sorun var, ancak kodunuzun tuş vuruşu yapıp gerçekleştirmediğini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `IsDialogMessage` kodlayabilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="95f7f-161">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span> <span data-ttu-id="95f7f-162">İkinci bir sorun da vardır, çünkü `IsDialogMessage` odaklanmış HWND iletişim kutusunun içinde değilse, anımsatıcı işlemeyi reddeder.</span><span class="sxs-lookup"><span data-stu-id="95f7f-162">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>

### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="95f7f-163">HwndHost türetilen sınıfının örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="95f7f-163">Instantiate the HwndHost Derived Class</span></span>

<span data-ttu-id="95f7f-164">Son olarak, artık tüm anahtar ve sekme desteği hazır olduğuna göre, uygulamanızı <xref:System.Windows.Interop.HwndHost> daha büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulamaya yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95f7f-164">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="95f7f-165">Ana uygulama dilinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yazılmışsa, doğru yere yerleştirmenin en kolay yolu, koymak <xref:System.Windows.Interop.HwndHost>istediğiniz yerde boş <xref:System.Windows.Controls.Border> bir öğe bırakmamadır.</span><span class="sxs-lookup"><span data-stu-id="95f7f-165">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span> <span data-ttu-id="95f7f-166">Burada adlı bir <xref:System.Windows.Controls.Border> ad `insertHwndHostHere`oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="95f7f-166">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>

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

<span data-ttu-id="95f7f-167">Bu durumda, <xref:System.Windows.Interop.HwndHost> ' nin örneğini oluşturmak ve <xref:System.Windows.Controls.Border>öğesine bağlamak için kod dizisinde iyi bir yer bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95f7f-167">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="95f7f-168">Bu örnekte, <xref:System.Windows.Window> türetilmiş sınıf için oluşturucuyu içine koyacaksınız:</span><span class="sxs-lookup"><span data-stu-id="95f7f-168">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>

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

<span data-ttu-id="95f7f-169">Şunları sağlar:</span><span class="sxs-lookup"><span data-stu-id="95f7f-169">Which gives you:</span></span>

![Çalışan WPF uygulamasının ekran görüntüsü.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a><span data-ttu-id="95f7f-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95f7f-171">See also</span></span>

- [<span data-ttu-id="95f7f-172">WPF ve Win32 Birlikte Çalışması</span><span class="sxs-lookup"><span data-stu-id="95f7f-172">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
