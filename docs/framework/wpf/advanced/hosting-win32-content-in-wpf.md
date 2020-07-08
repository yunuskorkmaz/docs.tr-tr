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
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="b1505-102">WPF'de Win32 İçeriği Barındırma</span><span class="sxs-lookup"><span data-stu-id="b1505-102">Hosting Win32 Content in WPF</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b1505-103">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="b1505-103">Prerequisites</span></span>

<span data-ttu-id="b1505-104">Bkz. [WPF ve Win32 birlikte](wpf-and-win32-interoperation.md)çalışma.</span><span class="sxs-lookup"><span data-stu-id="b1505-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="b1505-105">Windows Presentation Framework Içinde Win32 bir adım adım (HwndHost)</span><span class="sxs-lookup"><span data-stu-id="b1505-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>

<span data-ttu-id="b1505-106">Uygulamalar içinde Win32 içeriğini yeniden kullanmak için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Interop.HwndHost> HWND NDS 'nin içerik gibi görünmesini sağlayan bir denetim olan kullanın [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b1505-106">To reuse Win32 content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="b1505-107">Benzer <xref:System.Windows.Interop.HwndSource> <xref:System.Windows.Interop.HwndHost> şekilde, kullanımı basittir: türet <xref:System.Windows.Interop.HwndHost> ve uygulama `BuildWindowCore` ve `DestroyWindowCore` yöntemlerle <xref:System.Windows.Interop.HwndHost> türetilmiş sınıfınızı oluşturun ve uygulamanızın içine yerleştirin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b1505-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

<span data-ttu-id="b1505-108">Win32 mantığınızın zaten bir denetim olarak paketlenmesi durumunda `BuildWindowCore` uygulamanız, öğesine yapılan çağrıdan biraz daha fazla olur `CreateWindow` .</span><span class="sxs-lookup"><span data-stu-id="b1505-108">If your Win32 logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span> <span data-ttu-id="b1505-109">Örneğin, C++ ' da bir Win32 LISTBOX denetimi oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="b1505-109">For example, to create a Win32 LISTBOX control in C++:</span></span>

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

<span data-ttu-id="b1505-110">Ancak, Win32 kodunun kendine dahil olmadığı varsayın.</span><span class="sxs-lookup"><span data-stu-id="b1505-110">But suppose the Win32 code is not quite so self-contained?</span></span> <span data-ttu-id="b1505-111">Bu durumda, bir Win32 iletişim kutusu oluşturabilir ve içeriğini daha büyük bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaya katabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1505-111">If so, you can create a Win32 dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="b1505-112">Örnek, bunu farklı bir dilde veya komut satırında yapmak mümkün olsa da Visual Studio ve C++ içinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1505-112">The sample shows this in Visual Studio and C++, although it is also possible to do this in a different language or at the command line.</span></span>

<span data-ttu-id="b1505-113">C++ DLL projesine derlenmiş basit bir iletişim kutusuyla başlayın.</span><span class="sxs-lookup"><span data-stu-id="b1505-113">Start with a simple dialog, which is compiled into a C++ DLL project.</span></span>

<span data-ttu-id="b1505-114">Daha sonra, iletişim kutusunu daha büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaya tanıtın:</span><span class="sxs-lookup"><span data-stu-id="b1505-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>

- <span data-ttu-id="b1505-115">DLL 'yi yönetilen () olarak derle `/clr`</span><span class="sxs-lookup"><span data-stu-id="b1505-115">Compile the DLL as managed (`/clr`)</span></span>

- <span data-ttu-id="b1505-116">İletişim kutusunu Denetim haline getirin</span><span class="sxs-lookup"><span data-stu-id="b1505-116">Turn the dialog into a control</span></span>

- <span data-ttu-id="b1505-117">Türetilmiş sınıfını <xref:System.Windows.Interop.HwndHost> `BuildWindowCore` ve `DestroyWindowCore` yöntemlerini tanımlayın</span><span class="sxs-lookup"><span data-stu-id="b1505-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>

- <span data-ttu-id="b1505-118">`TranslateAccelerator`İletişim anahtarlarını işlemek için geçersiz kılma yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1505-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>

- <span data-ttu-id="b1505-119">`TabInto`Sekmeyi desteklemek için geçersiz kılma yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1505-119">Override `TabInto` method to support tabbing</span></span>

- <span data-ttu-id="b1505-120">`OnMnemonic`Anımsatıcıları desteklemek için yöntemi geçersiz kıl</span><span class="sxs-lookup"><span data-stu-id="b1505-120">Override `OnMnemonic` method to support mnemonics</span></span>

- <span data-ttu-id="b1505-121"><xref:System.Windows.Interop.HwndHost>Alt sınıfı oluştur ve sağ öğenin altına koy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1505-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>

### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="b1505-122">Iletişim kutusunu Denetim haline getirin</span><span class="sxs-lookup"><span data-stu-id="b1505-122">Turn the Dialog into a Control</span></span>

<span data-ttu-id="b1505-123">WS_CHILD ve DS_CONTROL stillerini kullanarak bir iletişim kutusunu alt HWND 'ye dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1505-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span> <span data-ttu-id="b1505-124">İletişim kutusunun tanımlandığı kaynak dosyasına (. RC) gidin ve iletişim kutusunun tanımının başlangıcını bulun:</span><span class="sxs-lookup"><span data-stu-id="b1505-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

<span data-ttu-id="b1505-125">İkinci satırı şu şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b1505-125">Change the second line to:</span></span>

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

<span data-ttu-id="b1505-126">Bu eylem, kendisini bağımsız bir denetime tam olarak paketlemez; hala `IsDialogMessage()` Win32 bazı iletileri işleyebilir, ancak Denetim değişikliği bu denetimleri başka BIR HWND içinde yerleştirmenin basit bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1505-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so Win32 can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>

## <a name="subclass-hwndhost"></a><span data-ttu-id="b1505-127">HwndHost alt sınıfı</span><span class="sxs-lookup"><span data-stu-id="b1505-127">Subclass HwndHost</span></span>

<span data-ttu-id="b1505-128">Aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="b1505-128">Import the following namespaces:</span></span>

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

<span data-ttu-id="b1505-129">Ardından türetilmiş bir sınıfı oluşturun <xref:System.Windows.Interop.HwndHost> ve `BuildWindowCore` ve yöntemlerini geçersiz kılın `DestroyWindowCore` :</span><span class="sxs-lookup"><span data-stu-id="b1505-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>

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

<span data-ttu-id="b1505-130">Burada, `CreateDialog` gerçekten bir denetim olan iletişim kutusunu oluşturmak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b1505-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span> <span data-ttu-id="b1505-131">Bu, DLL içinde çağrılan ilk metotlardan biri olduğundan, daha sonra kullanacağınız bir işlevi çağırarak bazı standart Win32 başlatma işlemi de yapmalısınız `InitializeGlobals()` :</span><span class="sxs-lookup"><span data-stu-id="b1505-131">Since this is one of the first methods called inside the DLL, you should also do some standard Win32 initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>

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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="b1505-132">Iletişim anahtarlarını Işlemek için TranslateAccelerator metodunu geçersiz kılın</span><span class="sxs-lookup"><span data-stu-id="b1505-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>

<span data-ttu-id="b1505-133">Bu örneği şu anda çalıştırdıysanız, görüntülenen bir iletişim kutusu denetimi alırsınız, ancak iletişim kutusunu işlevsel bir iletişim kutusu yapan tüm klavye işlemlerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="b1505-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span> <span data-ttu-id="b1505-134">Artık `TranslateAccelerator` uygulamayı (' den gelen `IKeyboardInputSink` bir arabirimi) geçersiz kılmanız gerekir <xref:System.Windows.Interop.HwndHost> .</span><span class="sxs-lookup"><span data-stu-id="b1505-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span> <span data-ttu-id="b1505-135">Bu yöntem, uygulama WM_KEYDOWN ve WM_SYSKEYDOWN aldığında çağırılır.</span><span class="sxs-lookup"><span data-stu-id="b1505-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>

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

<span data-ttu-id="b1505-136">Bu, tek bir parçadaki çok büyük bir kod olduğundan, daha ayrıntılı açıklamaları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b1505-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span> <span data-ttu-id="b1505-137">Birincisi, C++ ve C++ makrolarını kullanan kod; zaten `TranslateAccelerator` Winuser. h içinde tanımlanan adlı bir makronun zaten bulunduğunu bilmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="b1505-137">First, the code using C++ and C++ macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

<span data-ttu-id="b1505-138">Bu nedenle, bir yöntemi değil bir yöntem tanımlamadığınızdan emin olun `TranslateAccelerator` `TranslateAcceleratorW` .</span><span class="sxs-lookup"><span data-stu-id="b1505-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>

<span data-ttu-id="b1505-139">Benzer şekilde, hem yönetilmeyen Winuser. h MSG hem de yönetilen yapı mevcuttur `Microsoft::Win32::MSG` .</span><span class="sxs-lookup"><span data-stu-id="b1505-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span> <span data-ttu-id="b1505-140">C++ işlecini kullanarak ikisi arasındaki belirsizliği ortadan kaldırabilirsiniz `::` .</span><span class="sxs-lookup"><span data-stu-id="b1505-140">You can disambiguate between the two using the C++ `::` operator.</span></span>

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}
```

<span data-ttu-id="b1505-141">Her iki mesaj de aynı verilere sahiptir, ancak bazen yönetilmeyen tanımıyla çalışmak daha kolaydır, bu nedenle bu örnekte belirgin dönüştürme yordamını tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b1505-141">Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:</span></span>

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

<span data-ttu-id="b1505-142">Öğesine geri dönün `TranslateAccelerator` .</span><span class="sxs-lookup"><span data-stu-id="b1505-142">Back to `TranslateAccelerator`.</span></span> <span data-ttu-id="b1505-143">Temel prensibi, `IsDialogMessage` mümkün olduğunca fazla iş yapmak Için Win32 işlevini `IsDialogMessage` çağırıldır, ancak iletişim kutusunun dışında bir şeye erişemez.</span><span class="sxs-lookup"><span data-stu-id="b1505-143">The basic principle is to call the Win32 function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="b1505-144">İletişim kutusunda bir kullanıcı sekmesi olarak sekme, iletişim kutusundaki son denetimden sonra çalıştırıldığında, öğesini çağırarak odağı bölümüne ayarlamanız gerekir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `IKeyboardInputSite::OnNoMoreStops` .</span><span class="sxs-lookup"><span data-stu-id="b1505-144">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>

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

<span data-ttu-id="b1505-145">Son olarak, çağırın `IsDialogMessage` .</span><span class="sxs-lookup"><span data-stu-id="b1505-145">Finally, call `IsDialogMessage`.</span></span> <span data-ttu-id="b1505-146">Ancak bir yöntemin sorumluluklarıyla, `TranslateAccelerator` [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tuş vuruşu işlenip işlemeyeceğinizi söylemiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1505-146">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="b1505-147">Bunu yapmadıysanız, giriş olayı uygulamanın geri kalanı aracılığıyla tünel ve balon oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="b1505-147">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="b1505-148">Burada, bir klavye messange işleme ve Win32 'teki giriş mimarisinin doğası gibi bir olağandışı işlem sergileirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1505-148">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in Win32.</span></span> <span data-ttu-id="b1505-149">Ne yazık ki, `IsDialogMessage` belirli bir tuş vuruşunu işleymeksizin hiçbir şekilde döndürmez.</span><span class="sxs-lookup"><span data-stu-id="b1505-149">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span> <span data-ttu-id="b1505-150">Daha da kötüsü, bu, `DispatchMessage()` işleyememesi gereken tuş vuruşlarına çağrı görür!</span><span class="sxs-lookup"><span data-stu-id="b1505-150">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="b1505-151">Bu nedenle, bunu tersine mühendislik yapmanız `IsDialogMessage` ve yalnızca işleyeceğimizi bildiğiniz anahtarlar için çağırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="b1505-151">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>

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

### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="b1505-152">Sekmeyi desteklemek için TabInto metodunu geçersiz kılın</span><span class="sxs-lookup"><span data-stu-id="b1505-152">Override TabInto Method to Support Tabbing</span></span>

<span data-ttu-id="b1505-153">Artık uyguladığınıza `TranslateAccelerator` göre, bir Kullanıcı, iletişim kutusunun içinde sekme ve üzerini daha büyük bir uygulamada sekmeye dönüştürebilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b1505-153">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="b1505-154">Ancak bir Kullanıcı iletişim kutusuna geri sekme kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="b1505-154">But a user cannot tab back into the dialog box.</span></span> <span data-ttu-id="b1505-155">Bunu çözümlemek için geçersiz kılabilirsiniz `TabInto` :</span><span class="sxs-lookup"><span data-stu-id="b1505-155">To solve that, you override `TabInto`:</span></span>

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

<span data-ttu-id="b1505-156">`TraversalRequest`Parametresi sekme eyleminin sekme veya kaydırma sekmesi olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="b1505-156">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>

### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="b1505-157">Anımsatıcıları desteklemek için Onanımsatıcı metodunu geçersiz kılın</span><span class="sxs-lookup"><span data-stu-id="b1505-157">Override OnMnemonic Method to Support Mnemonics</span></span>

<span data-ttu-id="b1505-158">Klavye işleme neredeyse tamamlanmıştır, ancak bir şey eksik, ancak anımsatıcıları çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="b1505-158">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span> <span data-ttu-id="b1505-159">Bir kullanıcı alt-F tuşlarına basarsa, odak "Ilk ad:" düzenleme kutusuna atmaz.</span><span class="sxs-lookup"><span data-stu-id="b1505-159">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="b1505-160">Bu nedenle, yöntemini geçersiz kılarsınız `OnMnemonic` :</span><span class="sxs-lookup"><span data-stu-id="b1505-160">So, you override the `OnMnemonic` method:</span></span>

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

<span data-ttu-id="b1505-161">Neden burada çağırmayın `IsDialogMessage` ?</span><span class="sxs-lookup"><span data-stu-id="b1505-161">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="b1505-162">Yukarıdaki ile aynı sorun var, ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodunuzun tuş vuruşu yapıp gerçekleştirmediğini kodlayabilmeniz gerekir `IsDialogMessage` .</span><span class="sxs-lookup"><span data-stu-id="b1505-162">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span> <span data-ttu-id="b1505-163">İkinci bir sorun da vardır, çünkü `IsDialogMessage` ODAKLANMıŞ HWND iletişim kutusunun içinde değilse, anımsatıcı işlemeyi reddeder.</span><span class="sxs-lookup"><span data-stu-id="b1505-163">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>

### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="b1505-164">HwndHost türetilen sınıfının örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1505-164">Instantiate the HwndHost Derived Class</span></span>

<span data-ttu-id="b1505-165">Son olarak, artık tüm anahtar ve sekme desteği hazır olduğuna göre, uygulamanızı <xref:System.Windows.Interop.HwndHost> daha büyük bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaya yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1505-165">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="b1505-166">Ana uygulama dilinde yazılmışsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , doğru yere yerleştirmenin en kolay yolu, koymak istediğiniz yerde boş bir öğe bırakmamadır <xref:System.Windows.Controls.Border> <xref:System.Windows.Interop.HwndHost> .</span><span class="sxs-lookup"><span data-stu-id="b1505-166">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span> <span data-ttu-id="b1505-167">Burada <xref:System.Windows.Controls.Border> adlı bir ad oluşturursunuz `insertHwndHostHere` :</span><span class="sxs-lookup"><span data-stu-id="b1505-167">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>

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

<span data-ttu-id="b1505-168">Bu durumda, ' nin örneğini oluşturmak ve öğesine bağlamak için kod dizisinde iyi bir yer bulabilirsiniz <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Controls.Border> .</span><span class="sxs-lookup"><span data-stu-id="b1505-168">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="b1505-169">Bu örnekte, türetilmiş sınıf için oluşturucuyu içine koyacaksınız <xref:System.Windows.Window> :</span><span class="sxs-lookup"><span data-stu-id="b1505-169">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>

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

<span data-ttu-id="b1505-170">Şunları sağlar:</span><span class="sxs-lookup"><span data-stu-id="b1505-170">Which gives you:</span></span>

![Çalışan WPF uygulamasının ekran görüntüsü.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a><span data-ttu-id="b1505-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1505-172">See also</span></span>

- [<span data-ttu-id="b1505-173">WPF ve Win32 Birlikte Çalışması</span><span class="sxs-lookup"><span data-stu-id="b1505-173">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
