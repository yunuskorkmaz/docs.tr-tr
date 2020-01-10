---
title: WPF'de Win32 İçeriği Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: a9d9de1f35375e48981f895d096e46fd501ef8ec
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740368"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="38b26-102">WPF'de Win32 İçeriği Barındırma</span><span class="sxs-lookup"><span data-stu-id="38b26-102">Hosting Win32 Content in WPF</span></span>

## <a name="prerequisites"></a><span data-ttu-id="38b26-103">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="38b26-103">Prerequisites</span></span>

<span data-ttu-id="38b26-104">Bkz. [WPF ve Win32 birlikte](wpf-and-win32-interoperation.md)çalışma.</span><span class="sxs-lookup"><span data-stu-id="38b26-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="38b26-105">Windows Presentation Framework Içinde Win32 bir adım adım (HwndHost)</span><span class="sxs-lookup"><span data-stu-id="38b26-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>

<span data-ttu-id="38b26-106">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalarında Win32 içeriğini yeniden kullanmak için, HWNDs 'nin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik gibi görünmesini sağlayan bir denetim olan <xref:System.Windows.Interop.HwndHost>kullanın.</span><span class="sxs-lookup"><span data-stu-id="38b26-106">To reuse Win32 content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="38b26-107"><xref:System.Windows.Interop.HwndSource>gibi, <xref:System.Windows.Interop.HwndHost> kullanımı basittir: <xref:System.Windows.Interop.HwndHost> türetebilir ve `BuildWindowCore` ve `DestroyWindowCore` yöntemleri uygulayıp <xref:System.Windows.Interop.HwndHost> türetilmiş sınıfınızın örneğini oluşturup [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanızın içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="38b26-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

<span data-ttu-id="38b26-108">Win32 mantığınızın zaten bir denetim olarak paketlenmesi durumunda `BuildWindowCore` uygulamanız `CreateWindow`bir çağrıdan çok daha fazla.</span><span class="sxs-lookup"><span data-stu-id="38b26-108">If your Win32 logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span> <span data-ttu-id="38b26-109">Örneğin, içinde C++BIR Win32 LISTBOX denetimi oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="38b26-109">For example, to create a Win32 LISTBOX control in C++:</span></span>

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

<span data-ttu-id="38b26-110">Ancak, Win32 kodunun kendine dahil olmadığı varsayın.</span><span class="sxs-lookup"><span data-stu-id="38b26-110">But suppose the Win32 code is not quite so self-contained?</span></span> <span data-ttu-id="38b26-111">Bu durumda, bir Win32 iletişim kutusu oluşturabilir ve içeriğini daha büyük bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38b26-111">If so, you can create a Win32 dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="38b26-112">Örnek, bunu Visual Studio 'da ve C++farklı bir dilde veya komut satırında yapmak mümkün olsa da gösterir.</span><span class="sxs-lookup"><span data-stu-id="38b26-112">The sample shows this in Visual Studio and C++, although it is also possible to do this in a different language or at the command line.</span></span>

<span data-ttu-id="38b26-113">Bir C++ DLL projesine derlenmiş basit bir iletişim kutusuyla başlayın.</span><span class="sxs-lookup"><span data-stu-id="38b26-113">Start with a simple dialog, which is compiled into a C++ DLL project.</span></span>

<span data-ttu-id="38b26-114">Daha sonra, iletişim kutusunu daha büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasına tanıtın:</span><span class="sxs-lookup"><span data-stu-id="38b26-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>

- <span data-ttu-id="38b26-115">DLL 'yi yönetilen olarak derle (`/clr`)</span><span class="sxs-lookup"><span data-stu-id="38b26-115">Compile the DLL as managed (`/clr`)</span></span>

- <span data-ttu-id="38b26-116">İletişim kutusunu Denetim haline getirin</span><span class="sxs-lookup"><span data-stu-id="38b26-116">Turn the dialog into a control</span></span>

- <span data-ttu-id="38b26-117">`BuildWindowCore` ve `DestroyWindowCore` yöntemleriyle birlikte <xref:System.Windows.Interop.HwndHost> türetilen sınıfını tanımlayın</span><span class="sxs-lookup"><span data-stu-id="38b26-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>

- <span data-ttu-id="38b26-118">İletişim anahtarlarını işlemek için `TranslateAccelerator` yöntemi geçersiz kıl</span><span class="sxs-lookup"><span data-stu-id="38b26-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>

- <span data-ttu-id="38b26-119">Sekmeyi desteklemek için `TabInto` yöntemi geçersiz kıl</span><span class="sxs-lookup"><span data-stu-id="38b26-119">Override `TabInto` method to support tabbing</span></span>

- <span data-ttu-id="38b26-120">Anımsatıcıları desteklemek için `OnMnemonic` yöntemi geçersiz kıl</span><span class="sxs-lookup"><span data-stu-id="38b26-120">Override `OnMnemonic` method to support mnemonics</span></span>

- <span data-ttu-id="38b26-121"><xref:System.Windows.Interop.HwndHost> alt sınıfını oluşturun ve sağ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinin altına yerleştirin</span><span class="sxs-lookup"><span data-stu-id="38b26-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>

### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="38b26-122">Iletişim kutusunu Denetim haline getirin</span><span class="sxs-lookup"><span data-stu-id="38b26-122">Turn the Dialog into a Control</span></span>

<span data-ttu-id="38b26-123">WS_CHILD ve DS_CONTROL stillerini kullanarak bir iletişim kutusunu alt HWND 'ye dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38b26-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span> <span data-ttu-id="38b26-124">İletişim kutusunun tanımlandığı kaynak dosyasına (. RC) gidin ve iletişim kutusunun tanımının başlangıcını bulun:</span><span class="sxs-lookup"><span data-stu-id="38b26-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

<span data-ttu-id="38b26-125">İkinci satırı şu şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="38b26-125">Change the second line to:</span></span>

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

<span data-ttu-id="38b26-126">Bu eylem, kendisini bağımsız bir denetime tam olarak paketlemez; Win32 'in belirli iletileri işleyebilmesi için yine de `IsDialogMessage()` çağırmanız gerekir, ancak Denetim değişikliği bu denetimleri başka bir HWND içinde yerleştirmenin basit bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="38b26-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so Win32 can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>

## <a name="subclass-hwndhost"></a><span data-ttu-id="38b26-127">HwndHost alt sınıfı</span><span class="sxs-lookup"><span data-stu-id="38b26-127">Subclass HwndHost</span></span>

<span data-ttu-id="38b26-128">Aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="38b26-128">Import the following namespaces:</span></span>

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

<span data-ttu-id="38b26-129">Ardından <xref:System.Windows.Interop.HwndHost> türetilmiş bir sınıf oluşturun ve `BuildWindowCore` ve `DestroyWindowCore` yöntemleri geçersiz kılın:</span><span class="sxs-lookup"><span data-stu-id="38b26-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>

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

<span data-ttu-id="38b26-130">Burada, gerçekten bir denetim olan iletişim kutusunu oluşturmak için `CreateDialog` kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="38b26-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span> <span data-ttu-id="38b26-131">Bu, DLL içinde çağrılan ilk metotlardan biri olduğundan, daha sonra `InitializeGlobals()`adlı bir işlevi çağırarak bazı standart Win32 başlatma işlemi de yapmalısınız:</span><span class="sxs-lookup"><span data-stu-id="38b26-131">Since this is one of the first methods called inside the DLL, you should also do some standard Win32 initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>

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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="38b26-132">Iletişim anahtarlarını Işlemek için TranslateAccelerator metodunu geçersiz kılın</span><span class="sxs-lookup"><span data-stu-id="38b26-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>

<span data-ttu-id="38b26-133">Bu örneği şu anda çalıştırdıysanız, görüntülenen bir iletişim kutusu denetimi alırsınız, ancak iletişim kutusunu işlevsel bir iletişim kutusu yapan tüm klavye işlemlerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="38b26-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span> <span data-ttu-id="38b26-134">Artık `TranslateAccelerator` uygulamasını geçersiz kılmanız gerekir (`IKeyboardInputSink`<xref:System.Windows.Interop.HwndHost> uygulayan bir arabirim).</span><span class="sxs-lookup"><span data-stu-id="38b26-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span> <span data-ttu-id="38b26-135">Bu yöntem, uygulama WM_KEYDOWN ve WM_SYSKEYDOWN aldığında çağırılır.</span><span class="sxs-lookup"><span data-stu-id="38b26-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>

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

<span data-ttu-id="38b26-136">Bu, tek bir parçadaki çok büyük bir kod olduğundan, daha ayrıntılı açıklamaları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="38b26-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span> <span data-ttu-id="38b26-137">İlk olarak, ve C++ C++ makroları kullanan kod; Winuser. h içinde tanımlanan `TranslateAccelerator`adlı bir makronun zaten bulunduğunu bilmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="38b26-137">First, the code using C++ and C++ macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

<span data-ttu-id="38b26-138">Bu nedenle, bir `TranslateAcceleratorW` yöntemi değil `TranslateAccelerator` yöntemi tanımladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="38b26-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>

<span data-ttu-id="38b26-139">Benzer şekilde, hem yönetilmeyen Winuser. h MSG hem de yönetilen `Microsoft::Win32::MSG` yapısı vardır.</span><span class="sxs-lookup"><span data-stu-id="38b26-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span> <span data-ttu-id="38b26-140">C++ `::` işlecini kullanarak ikisi arasındaki ilişkiyi ortadan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38b26-140">You can disambiguate between the two using the C++ `::` operator.</span></span>

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

<span data-ttu-id="38b26-141">`TranslateAccelerator`geri dönün.</span><span class="sxs-lookup"><span data-stu-id="38b26-141">Back to `TranslateAccelerator`.</span></span> <span data-ttu-id="38b26-142">Temel prensibi, mümkün olduğunca fazla iş yapmak için `IsDialogMessage` Win32 işlevini çağır, ancak `IsDialogMessage` iletişim kutusunun dışında herhangi bir şeye erişemez.</span><span class="sxs-lookup"><span data-stu-id="38b26-142">The basic principle is to call the Win32 function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="38b26-143">İletişim kutusunda bir kullanıcı sekmesi olarak sekme, iletişim kutusundaki son denetimden sonra çalıştırıldığında, `IKeyboardInputSite::OnNoMoreStops`çağırarak odağı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bölümüne ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="38b26-143">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>

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

<span data-ttu-id="38b26-144">Son olarak, `IsDialogMessage`çağırın.</span><span class="sxs-lookup"><span data-stu-id="38b26-144">Finally, call `IsDialogMessage`.</span></span> <span data-ttu-id="38b26-145">Ancak, bir `TranslateAccelerator` yönteminin sorumluluklarıyla, tuş vuruşunu işlemiş olup olmadığını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] söylemiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="38b26-145">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="38b26-146">Bunu yapmadıysanız, giriş olayı uygulamanın geri kalanı aracılığıyla tünel ve balon oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="38b26-146">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="38b26-147">Burada, bir klavye messange işleme ve Win32 'teki giriş mimarisinin doğası gibi bir olağandışı işlem sergileirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38b26-147">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in Win32.</span></span> <span data-ttu-id="38b26-148">Ne yazık ki, `IsDialogMessage` belirli bir tuş vuruşunu işleymeksizin hiçbir şekilde döndürmez.</span><span class="sxs-lookup"><span data-stu-id="38b26-148">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span> <span data-ttu-id="38b26-149">Daha da kötüleşse de, işlem yapılmamalıdır `DispatchMessage()`.</span><span class="sxs-lookup"><span data-stu-id="38b26-149">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="38b26-150">Bu nedenle, `IsDialogMessage`tersine mühendislik yapmanız ve yalnızca işleyeceği anahtarlar için çağırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="38b26-150">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>

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

### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="38b26-151">Sekmeyi desteklemek için TabInto metodunu geçersiz kılın</span><span class="sxs-lookup"><span data-stu-id="38b26-151">Override TabInto Method to Support Tabbing</span></span>

<span data-ttu-id="38b26-152">`TranslateAccelerator`uyguladığınıza göre, bir Kullanıcı, iletişim kutusunun içinde sekme ve daha fazla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasına sekme ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="38b26-152">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="38b26-153">Ancak bir Kullanıcı iletişim kutusuna geri sekme kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="38b26-153">But a user cannot tab back into the dialog box.</span></span> <span data-ttu-id="38b26-154">Bunu çözümlemek için `TabInto`geçersiz kılabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="38b26-154">To solve that, you override `TabInto`:</span></span>

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

<span data-ttu-id="38b26-155">`TraversalRequest` parametresi, sekme eyleminin sekme veya kaydırma sekmesi olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="38b26-155">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>

### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="38b26-156">Anımsatıcıları desteklemek için Onanımsatıcı metodunu geçersiz kılın</span><span class="sxs-lookup"><span data-stu-id="38b26-156">Override OnMnemonic Method to Support Mnemonics</span></span>

<span data-ttu-id="38b26-157">Klavye işleme neredeyse tamamlanmıştır, ancak bir şey eksik, ancak anımsatıcıları çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="38b26-157">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span> <span data-ttu-id="38b26-158">Bir kullanıcı alt-F tuşlarına basarsa, odak "Ilk ad:" düzenleme kutusuna atmaz.</span><span class="sxs-lookup"><span data-stu-id="38b26-158">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="38b26-159">Bu nedenle `OnMnemonic` yöntemi geçersiz kılınır:</span><span class="sxs-lookup"><span data-stu-id="38b26-159">So, you override the `OnMnemonic` method:</span></span>

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

<span data-ttu-id="38b26-160">Neden `IsDialogMessage` çağırmayın?</span><span class="sxs-lookup"><span data-stu-id="38b26-160">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="38b26-161">Yukarıdaki ile aynı sorun var, kodunuzun tuş vuruşu yapıp gerçekleştirmediğini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodu bilgilendirebilmeniz gerekir ve `IsDialogMessage` bunu yapamaz.</span><span class="sxs-lookup"><span data-stu-id="38b26-161">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span> <span data-ttu-id="38b26-162">Ayrıca, odaklanmış HWND iletişim kutusunun içinde değilse, `IsDialogMessage` bir ikinci sorun da vardır.</span><span class="sxs-lookup"><span data-stu-id="38b26-162">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>

### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="38b26-163">HwndHost türetilen sınıfının örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="38b26-163">Instantiate the HwndHost Derived Class</span></span>

<span data-ttu-id="38b26-164">Son olarak, artık tüm anahtar ve sekme desteği hazır olduğuna göre <xref:System.Windows.Interop.HwndHost> daha büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasına koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38b26-164">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="38b26-165">Ana uygulama [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yazılmışsa, doğru yere koymanın en kolay yolu, <xref:System.Windows.Interop.HwndHost>koymak istediğiniz boş bir <xref:System.Windows.Controls.Border> öğesi bırakmamadır.</span><span class="sxs-lookup"><span data-stu-id="38b26-165">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span> <span data-ttu-id="38b26-166">Burada `insertHwndHostHere`adlı bir <xref:System.Windows.Controls.Border> oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="38b26-166">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>

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

<span data-ttu-id="38b26-167">Bu durumda, <xref:System.Windows.Interop.HwndHost> örneklendirilecek ve <xref:System.Windows.Controls.Border>bağlamak için kod dizisinde iyi bir yer bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38b26-167">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="38b26-168">Bu örnekte, <xref:System.Windows.Window> türetilmiş sınıfına ait oluşturucuyu içine koyacaksınız:</span><span class="sxs-lookup"><span data-stu-id="38b26-168">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>

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

<span data-ttu-id="38b26-169">Şunları sağlar:</span><span class="sxs-lookup"><span data-stu-id="38b26-169">Which gives you:</span></span>

![Çalışan WPF uygulamasının ekran görüntüsü.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a><span data-ttu-id="38b26-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38b26-171">See also</span></span>

- [<span data-ttu-id="38b26-172">WPF ve Win32 Birlikte Çalışması</span><span class="sxs-lookup"><span data-stu-id="38b26-172">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
