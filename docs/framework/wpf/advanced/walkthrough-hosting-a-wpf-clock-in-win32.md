---
title: "İzlenecek yol: Win32 'de WPF saati barındırma"
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 1fdc0c9ccf1464d7519a4c5935520de1206ca9bb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794151"
---
# <a name="walkthrough-host-a-wpf-clock-in-win32"></a><span data-ttu-id="58ee0-102">İzlenecek yol: Win32 'de WPF saati barındırma</span><span class="sxs-lookup"><span data-stu-id="58ee0-102">Walkthrough: Host a WPF Clock in Win32</span></span>

<span data-ttu-id="58ee0-103">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32 uygulamalarının içine koymak için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğinizi içeren HWND 'yi sağlayan <xref:System.Windows.Interop.HwndSource>kullanın.</span><span class="sxs-lookup"><span data-stu-id="58ee0-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside Win32 applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="58ee0-104">İlk olarak <xref:System.Windows.Interop.HwndSource>oluşturun ve bu parametrelere CreateWindow 'a benzer.</span><span class="sxs-lookup"><span data-stu-id="58ee0-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span> <span data-ttu-id="58ee0-105">Daha sonra <xref:System.Windows.Interop.HwndSource> içinde istediğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik hakkında söylemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="58ee0-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span> <span data-ttu-id="58ee0-106">Son olarak, <xref:System.Windows.Interop.HwndSource>HWND 'den yararlanın.</span><span class="sxs-lookup"><span data-stu-id="58ee0-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="58ee0-107">Bu izlenecek yol, Win32 uygulamasının içinde işletim sistemi **Tarih ve saat özellikleri** iletişim kutusunu yeniden uygulayan bir karma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="58ee0-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside Win32 application that reimplements the operating system **Date and Time Properties** dialog.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="58ee0-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="58ee0-108">Prerequisites</span></span>

<span data-ttu-id="58ee0-109">Bkz. [WPF ve Win32 birlikte](wpf-and-win32-interoperation.md)çalışma.</span><span class="sxs-lookup"><span data-stu-id="58ee0-109">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="58ee0-110">Bu öğreticiyi kullanma</span><span class="sxs-lookup"><span data-stu-id="58ee0-110">How to Use This Tutorial</span></span>

<span data-ttu-id="58ee0-111">Bu öğretici, birlikte çalışabilirlik uygulaması üretmede önemli adımlarla yoğunlaşır.</span><span class="sxs-lookup"><span data-stu-id="58ee0-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="58ee0-112">Öğretici örnek, [Win32 saat birlikte çalışabilirlik](https://go.microsoft.com/fwlink/?LinkID=160051)örneğiyle desteklenir, ancak bu örnek, son ürünün yansıtıcı örneğidir.</span><span class="sxs-lookup"><span data-stu-id="58ee0-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051), but that sample is reflective of the end product.</span></span> <span data-ttu-id="58ee0-113">Bu öğreticide, kendi mevcut bir Win32 projesiyle başladıysanız, belki de önceden var olan bir projede ve bir barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanıza eklemiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58ee0-113">This tutorial documents the steps as if you were starting with an existing Win32 project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="58ee0-114">Son ürününüzü, [Win32 saat birlikte çalışabilirlik](https://go.microsoft.com/fwlink/?LinkID=160051)örneğiyle karşılaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58ee0-114">You can compare your end product with [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="58ee0-115">Win32 Içindeki Windows Presentation Framework 'e yönelik bir adım adım (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="58ee0-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>

<span data-ttu-id="58ee0-116">Aşağıdaki grafikte, Bu öğreticinin amaçlanan son ürünü gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="58ee0-116">The following graphic shows the intended end product of this tutorial:</span></span>

![Tarih ve saat özellikleri iletişim kutusunu gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

<span data-ttu-id="58ee0-118">Visual Studio 'da bir C++ Win32 projesi oluşturarak ve iletişim düzenleyicisini kullanarak, aşağıdakileri oluşturmak için bu iletişim kutusunu yeniden oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="58ee0-118">You can recreate this dialog by creating a C++ Win32 project in Visual Studio, and using the dialog editor to create the following:</span></span>

![Yeniden oluşturulan tarih ve saat özellikleri iletişim kutusu](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

<span data-ttu-id="58ee0-120">(<xref:System.Windows.Interop.HwndSource>kullanmak için Visual Studio kullanmanız gerekmez ve Win32 programları yazmak için kullanmanız C++ gerekmez, ancak bunu yapmak için oldukça tipik bir yoldur ve bir tarafınızdaki öğretici açıklamasında iyi bir yöntem vardır).</span><span class="sxs-lookup"><span data-stu-id="58ee0-120">(You do not need to use Visual Studio to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write Win32 programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>

<span data-ttu-id="58ee0-121">İletişim kutusuna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir saat koymak için beş özel alt adım gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="58ee0-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>

1. <span data-ttu-id="58ee0-122">Visual Studio 'da proje ayarlarını değiştirerek, Win32 projenizi yönetilen kodu ( **/clr**) çağırmak üzere etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="58ee0-122">Enable your Win32 project to call managed code (**/clr**) by changing project settings in Visual Studio.</span></span>

2. <span data-ttu-id="58ee0-123">Ayrı bir DLL 'de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> oluşturun.</span><span class="sxs-lookup"><span data-stu-id="58ee0-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>

3. <span data-ttu-id="58ee0-124">Bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> <xref:System.Windows.Interop.HwndSource>içine koyun.</span><span class="sxs-lookup"><span data-stu-id="58ee0-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>

4. <span data-ttu-id="58ee0-125">Bu <xref:System.Windows.Controls.Page> için <xref:System.Windows.Interop.HwndSource.Handle%2A> özelliğini kullanarak bir HWND alın.</span><span class="sxs-lookup"><span data-stu-id="58ee0-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>

5. <span data-ttu-id="58ee0-126">HWND 'yi daha büyük Win32 uygulamasına nereye yerleştireceğinize karar vermek için kullanın</span><span class="sxs-lookup"><span data-stu-id="58ee0-126">Use Win32 to decide where to place the HWND within the larger Win32 application</span></span>

## <a name="clr"></a><span data-ttu-id="58ee0-127">clr</span><span class="sxs-lookup"><span data-stu-id="58ee0-127">/clr</span></span>

<span data-ttu-id="58ee0-128">İlk adım, bu yönetilmeyen Win32 projesini yönetilen kodu çağıralebilecek birine dönüştürmek olur.</span><span class="sxs-lookup"><span data-stu-id="58ee0-128">The first step is to turn this unmanaged Win32 project into one that can call managed code.</span></span> <span data-ttu-id="58ee0-129">Kullanmak istediğiniz gerekli dll 'Lere bağlanacak/clr derleyici seçeneğini kullanın ve ana yöntemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ile kullanmak üzere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="58ee0-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>

<span data-ttu-id="58ee0-130">C++ Projenin içinde yönetilen kodun kullanımını etkinleştirmek için: Win32clock projesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="58ee0-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span> <span data-ttu-id="58ee0-131">**Genel** Özellik sayfasında (varsayılan), `/clr`Için ortak dil çalışma zamanı desteğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="58ee0-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>

<span data-ttu-id="58ee0-132">Daha sonra, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]için gereken dll 'lere başvuruları ekleyin: PresentationCore. dll, PresentationFramework. dll, System. dll, WindowsBase. dll, UIAutomationProvider. dll ve UIAutomationTypes. dll.</span><span class="sxs-lookup"><span data-stu-id="58ee0-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="58ee0-133">(Aşağıdaki yönergelerde, işletim sisteminin C: Drive üzerinde yüklü olduğu varsayılır.)</span><span class="sxs-lookup"><span data-stu-id="58ee0-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>

1. <span data-ttu-id="58ee0-134">Win32clock projesi öğesine sağ tıklayın ve **Başvurular...** ' ı seçin ve bu iletişim kutusunun içinde:</span><span class="sxs-lookup"><span data-stu-id="58ee0-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>

2. <span data-ttu-id="58ee0-135">Win32clock projesi öğesine sağ tıklayın ve başvurular ' ı seçin. **..** .</span><span class="sxs-lookup"><span data-stu-id="58ee0-135">Right-click win32clock project and select **References...**.</span></span>

3. <span data-ttu-id="58ee0-136">**Yeni Başvuru Ekle**' ye tıklayın, göz at sekmesine tıklayın, C:\Program Files\Reference, bir Lies\microsoft\framework\v3,\presentationcore.dll yazın ve Tamam ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="58ee0-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>

4. <span data-ttu-id="58ee0-137">PresentationFramework. dll için yineleyin: C:\Program Files\Reference, Lıes\microsoft\framework\v3.0\presentationframework.exe.</span><span class="sxs-lookup"><span data-stu-id="58ee0-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>

5. <span data-ttu-id="58ee0-138">WindowsBase. dll için yineleyin: C:\Program Files\Reference, Lıes\microsoft\framework\v3.0\base.exe.</span><span class="sxs-lookup"><span data-stu-id="58ee0-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>

6. <span data-ttu-id="58ee0-139">UIAutomationTypes. dll için yineleme: C:\Program Files\Reference, Lıes\microsoft\framework\v3,\uıautomationtypes.exe.</span><span class="sxs-lookup"><span data-stu-id="58ee0-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>

7. <span data-ttu-id="58ee0-140">UIAutomationProvider. dll için yineleyin: C:\Program Files\Reference, Lıes\microsoft\framework\v3,\uıautomationprovider.exe.</span><span class="sxs-lookup"><span data-stu-id="58ee0-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>

8. <span data-ttu-id="58ee0-141">**Yeni Başvuru Ekle**' ye tıklayın, System. dll öğesini seçin ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="58ee0-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>

9. <span data-ttu-id="58ee0-142">Başvuru eklemek için win32clock Özellik Sayfalarından çıkmak üzere **Tamam** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="58ee0-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

 <span data-ttu-id="58ee0-143">Son olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ile kullanmak için `_tWinMain` yöntemine `STAThreadAttribute` ekleyin:</span><span class="sxs-lookup"><span data-stu-id="58ee0-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

<span data-ttu-id="58ee0-144">Bu öznitelik, bileşen nesne modeli (COM) başlatıldığında ortak dil çalışma zamanına (CLR), [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (ve Windows Forms) için gerekli olan tek bir iş parçacıklı grup modeli (STA) kullanması gerektiğini söyler.</span><span class="sxs-lookup"><span data-stu-id="58ee0-144">This attribute tells the common language runtime (CLR) that when it initializes Component Object Model (COM), it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and Windows Forms).</span></span>

## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="58ee0-145">Windows Presentation Framework Oluştur sayfası</span><span class="sxs-lookup"><span data-stu-id="58ee0-145">Create a Windows Presentation Framework Page</span></span>

<span data-ttu-id="58ee0-146">Sonra, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>tanımlayan bir DLL oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="58ee0-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="58ee0-147">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> tek başına uygulama olarak oluşturmak ve bu şekilde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bölümünü yazmak ve hatalarını ayıklamak en kolay yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="58ee0-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span> <span data-ttu-id="58ee0-148">Bu proje tamamlandığında, projeye sağ tıklayıp **Özellikler**' e tıklayıp uygulamaya giderek ve çıkış türünü Windows sınıf kitaplığı olarak değiştirerek dll 'ye açılabilir.</span><span class="sxs-lookup"><span data-stu-id="58ee0-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>

<span data-ttu-id="58ee0-149">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] DLL projesi daha sonra Win32 projesi (iki proje içeren bir çözüm) ile birleştirilebilir – çözüme sağ tıklayın, **var olan projeyi add\'** ı seçin.</span><span class="sxs-lookup"><span data-stu-id="58ee0-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the Win32 project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>

<span data-ttu-id="58ee0-150">Bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll dosyasını Win32 projesinden kullanmak için, bir başvuru eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="58ee0-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the Win32 project, you need to add a reference:</span></span>

1. <span data-ttu-id="58ee0-151">Win32clock projesi öğesine sağ tıklayın ve başvurular ' ı seçin. **..** .</span><span class="sxs-lookup"><span data-stu-id="58ee0-151">Right-click win32clock project and select **References...**.</span></span>

2. <span data-ttu-id="58ee0-152">**Yeni Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="58ee0-152">Click **Add New Reference**.</span></span>

3. <span data-ttu-id="58ee0-153">**Projeler** sekmesine tıklayın. WPFClock ' i seçin, Tamam ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="58ee0-153">Click the **Projects** tab. Select WPFClock, click OK.</span></span>

4. <span data-ttu-id="58ee0-154">Başvuru eklemek için win32clock Özellik Sayfalarından çıkmak üzere **Tamam** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="58ee0-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

## <a name="hwndsource"></a><span data-ttu-id="58ee0-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="58ee0-155">HwndSource</span></span>

<span data-ttu-id="58ee0-156">Sonra, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> bir HWND gibi görünmesini sağlamak için <xref:System.Windows.Interop.HwndSource> kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="58ee0-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span> <span data-ttu-id="58ee0-157">Bu kod bloğunu bir C++ dosyaya eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="58ee0-157">You add this block of code to a C++ file:</span></span>

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

 <span data-ttu-id="58ee0-158">Bu, bir açıklama kullanan uzun bir kod parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="58ee0-158">This is a long piece of code that could use some explanation.</span></span> <span data-ttu-id="58ee0-159">İlk bölüm çeşitli yan tümcelerdir, böylece tüm çağrıları tamamen nitelemeniz gerekmez:</span><span class="sxs-lookup"><span data-stu-id="58ee0-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 <span data-ttu-id="58ee0-160">Daha sonra, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğini oluşturan bir işlev tanımlar, onun etrafına bir <xref:System.Windows.Interop.HwndSource> koyar ve HWND 'yi döndürür:</span><span class="sxs-lookup"><span data-stu-id="58ee0-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

<span data-ttu-id="58ee0-161">İlk olarak, parametreleri CreateWindow ile benzer olan bir <xref:System.Windows.Interop.HwndSource>oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="58ee0-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>

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

<span data-ttu-id="58ee0-162">Ardından oluşturucusunu çağırarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="58ee0-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

<span data-ttu-id="58ee0-163">Daha sonra sayfayı <xref:System.Windows.Interop.HwndSource>bağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="58ee0-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
source->RootVisual = page;
```

 <span data-ttu-id="58ee0-164">Son satırda, <xref:System.Windows.Interop.HwndSource>HWND 'yi geri döndürün:</span><span class="sxs-lookup"><span data-stu-id="58ee0-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a><span data-ttu-id="58ee0-165">HWND 'yi konumlandırma</span><span class="sxs-lookup"><span data-stu-id="58ee0-165">Positioning the Hwnd</span></span>

<span data-ttu-id="58ee0-166">Artık [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saatini içeren bir HWND olduğuna göre, bu HWND 'yi Win32 iletişim kutusunun içine koymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="58ee0-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the Win32 dialog.</span></span> <span data-ttu-id="58ee0-167">Yalnızca HWND 'yi nereye koyabileceğinizi biliyorsanız, bu boyutu ve konumu daha önce tanımladığınız `GetHwnd` işleve geçitirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58ee0-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span> <span data-ttu-id="58ee0-168">Ancak, iletişim kutusunu tanımlamak için bir kaynak dosyası kullandınız, bu nedenle bir HWND NDS 'nin nerede konumlandığını tam olarak unutmayın.</span><span class="sxs-lookup"><span data-stu-id="58ee0-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span> <span data-ttu-id="58ee0-169">Visual Studio iletişim düzenleyicisini, saatin gitmesini istediğiniz yere bir Win32 STATIK denetimi koymak için kullanabilirsiniz ("saati buraya ekle") ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saatini konumlandırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="58ee0-169">You can use the Visual Studio dialog editor to put a Win32 STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>

<span data-ttu-id="58ee0-170">WM_INITDIALOG nerede işleyeceğinizi kullanırsanız, STATIK yer tutucu için HWND 'yi almak üzere `GetDlgItem` kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="58ee0-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

<span data-ttu-id="58ee0-171">Daha sonra bu yer tutucunun STATIK boyutunu ve konumunu hesaplayabilirsiniz ve bu durumda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati bu yere koyabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="58ee0-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>

<span data-ttu-id="58ee0-172">Dikdörtgen dikdörtgen;</span><span class="sxs-lookup"><span data-stu-id="58ee0-172">RECT rectangle;</span></span>

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

<span data-ttu-id="58ee0-173">Sonra STATIK yer tutucuyu gizlemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="58ee0-173">Then you hide the placeholder STATIC:</span></span>

```cpp
ShowWindow(placeholder, SW_HIDE);
```

<span data-ttu-id="58ee0-174">Ve bu konumda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saat HWND oluşturun:</span><span class="sxs-lookup"><span data-stu-id="58ee0-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

<span data-ttu-id="58ee0-175">Öğreticiyi ilginç hale getirmek ve gerçek bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saat üretmek için, bu noktada bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saat denetimi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="58ee0-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="58ee0-176">Arka plan kod içinde yalnızca birkaç olay işleyicileriyle bu şekilde biçimlendirme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58ee0-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="58ee0-177">Bu öğretici birlikte çalışabilirlik ile ilgili olduğundan ve denetim tasarımı hakkında olmadığından, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saatinin tüm kodu, bu bilgileri oluşturmak için ayrık yönergeler veya her parçanın anlamı olmadan bir kod bloğu olarak sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="58ee0-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="58ee0-178">Denetimin görünümünü ve işlevselliğini değiştirmek için bu kodla denemeler yapın.</span><span class="sxs-lookup"><span data-stu-id="58ee0-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>

<span data-ttu-id="58ee0-179">Biçimlendirme şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="58ee0-179">Here is the markup:</span></span>

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

<span data-ttu-id="58ee0-180">Arka plan kodu aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="58ee0-180">And here is the accompanying code-behind:</span></span>

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

<span data-ttu-id="58ee0-181">Nihai sonuç şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="58ee0-181">The final result looks like:</span></span>

![Son sonuç tarihi ve saati özellikleri iletişim kutusu](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

<span data-ttu-id="58ee0-183">Nihai sonucu bu ekran görüntüsünü üreten kodla karşılaştırmak için bkz. [Win32 saat karşılıklı çalışma örneği](https://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="58ee0-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>

## <a name="see-also"></a><span data-ttu-id="58ee0-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58ee0-184">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="58ee0-185">WPF ve Win32 Birlikte Çalışması</span><span class="sxs-lookup"><span data-stu-id="58ee0-185">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
- [<span data-ttu-id="58ee0-186">Win32 saat birlikte çalışabilirlik örneği</span><span class="sxs-lookup"><span data-stu-id="58ee0-186">Win32 Clock Interoperation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160051)
