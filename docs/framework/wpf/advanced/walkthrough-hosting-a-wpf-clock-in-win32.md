---
title: "İzlenecek yol: Win32'de WPF saati barındırma"
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: a58d7e5848ccd62b889b8a7645c08a35822b3352
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352730"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a><span data-ttu-id="bbcce-102">İzlenecek yol: Win32'de WPF saati barındırma</span><span class="sxs-lookup"><span data-stu-id="bbcce-102">Walkthrough: Hosting a WPF Clock in Win32</span></span>
<span data-ttu-id="bbcce-103">Yerleştirmenin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamaları kullanın <xref:System.Windows.Interop.HwndSource>, içeren HWND sağlar, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği.</span><span class="sxs-lookup"><span data-stu-id="bbcce-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="bbcce-104">Oluşturduğunuz ilk <xref:System.Windows.Interop.HwndSource>, parametreler için CreateWindow benzer vererek.</span><span class="sxs-lookup"><span data-stu-id="bbcce-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span>  <span data-ttu-id="bbcce-105">Size daha sonra <xref:System.Windows.Interop.HwndSource> hakkında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik içinde olmasını istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="bbcce-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span>  <span data-ttu-id="bbcce-106">Son olarak, / HWND elde <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="bbcce-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="bbcce-107">Bu izlenecek yol karma oluşturma işlemini gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işletim sistemi in uygulama **tarih ve saat özellikleri** iletişim.</span><span class="sxs-lookup"><span data-stu-id="bbcce-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application that reimplements the operating system **Date and Time Properties** dialog.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bbcce-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="bbcce-108">Prerequisites</span></span>  
 <span data-ttu-id="bbcce-109">Bkz: [WPF ve Win32 birlikte çalışması](wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="bbcce-109">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>  
  
## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="bbcce-110">Bu öğreticide kullanma</span><span class="sxs-lookup"><span data-stu-id="bbcce-110">How to Use This Tutorial</span></span>  
 <span data-ttu-id="bbcce-111">Bu öğreticide, birlikte çalışabilirlik uygulama oluşturmanın önemli adımlar yoğunlaşır.</span><span class="sxs-lookup"><span data-stu-id="bbcce-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="bbcce-112">Öğretici, bir örnek tarafından yedeklenen [Win32 saati birlikte çalışma örneği](https://go.microsoft.com/fwlink/?LinkID=160051), ancak bu örnek son ürünün yansıtıcı.</span><span class="sxs-lookup"><span data-stu-id="bbcce-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051), but that sample is reflective of the end product.</span></span> <span data-ttu-id="bbcce-113">Varolan ile başlayan gibi Bu öğreticide adımları belgeler [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kendi proje, belki de önceden mevcut olan bir proje ve, ekleme barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanıza.</span><span class="sxs-lookup"><span data-stu-id="bbcce-113">This tutorial documents the steps as if you were starting with an existing [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="bbcce-114">Son ürününüzü ile karşılaştırabileceğiniz [Win32 saati birlikte çalışma örneği](https://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="bbcce-114">You can compare your end product with [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="bbcce-115">Bir kılavuz içinde Win32 Windows Presentation Framework (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="bbcce-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>  
 <span data-ttu-id="bbcce-116">Aşağıdaki grafikte, bu öğreticinin hedeflenen son ürün gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bbcce-116">The following graphic shows the intended end product of this tutorial:</span></span>  
  
 <span data-ttu-id="bbcce-117">![Tarih ve Saat Özellikleri iletişim kutusu](./media/interoparch06.PNG "InteropArch06")</span><span class="sxs-lookup"><span data-stu-id="bbcce-117">![Date and Time Properties dialog box](./media/interoparch06.PNG "InteropArch06")</span></span>  
  
 <span data-ttu-id="bbcce-118">C++ oluşturarak bu iletişim kutusunu yeniden oluşturabileceğinizi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projesi [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]ve aşağıdaki oluşturmak için iletişim kutusu düzenleyicisini kullanma:</span><span class="sxs-lookup"><span data-stu-id="bbcce-118">You can recreate this dialog by creating C++ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and using the dialog editor to create the following:</span></span>  
  
 <span data-ttu-id="bbcce-119">![Tarih ve Saat Özellikleri iletişim kutusu](./media/interoparch07.PNG "InteropArch07")</span><span class="sxs-lookup"><span data-stu-id="bbcce-119">![Date and Time Properties dialog box](./media/interoparch07.PNG "InteropArch07")</span></span>  
  
 <span data-ttu-id="bbcce-120">(Kullanın gerekmez [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] kullanılacak <xref:System.Windows.Interop.HwndSource>, ve yazmak için C++ kullanın gerekmez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlar, ancak bunu yapmak için oldukça tipik bir yoludur ve kendisi de adım öğretici açıklaması için uygundur).</span><span class="sxs-lookup"><span data-stu-id="bbcce-120">(You do not need to use [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>  
  
 <span data-ttu-id="bbcce-121">Beş belirli yerleştirmek için gerçekleştirmeniz gereken bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iletişim saati:</span><span class="sxs-lookup"><span data-stu-id="bbcce-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>  
  
1.  <span data-ttu-id="bbcce-122">Etkinleştirme, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] yönetilen kodu çağırmak için proje (**/CLR**) proje ayarlarını değiştirerek [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bbcce-122">Enable your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project to call managed code (**/clr**) by changing project settings in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="bbcce-123">Oluşturma bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> ayrı bir DLL içinde.</span><span class="sxs-lookup"><span data-stu-id="bbcce-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>  
  
3.  <span data-ttu-id="bbcce-124">Yerleştirme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> içinde bir <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="bbcce-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>  
  
4.  <span data-ttu-id="bbcce-125">HWND için alma <xref:System.Windows.Controls.Page> kullanarak <xref:System.Windows.Interop.HwndSource.Handle%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="bbcce-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>  
  
5.  <span data-ttu-id="bbcce-126">Kullanım [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HWND büyük içinde yerleştirileceği yeri karar [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulama</span><span class="sxs-lookup"><span data-stu-id="bbcce-126">Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] to decide where to place the HWND within the larger [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application</span></span>  
  
## <a name="clr"></a><span data-ttu-id="bbcce-127">/ CLR</span><span class="sxs-lookup"><span data-stu-id="bbcce-127">/clr</span></span>  
 <span data-ttu-id="bbcce-128">İlk adım, bu yönetilmeyen olarak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] çağırana projeye yönetilen kod.</span><span class="sxs-lookup"><span data-stu-id="bbcce-128">The first step is to turn this unmanaged [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project into one that can call managed code.</span></span>  <span data-ttu-id="bbcce-129">Gerekli DLL'leri kullanma ve ile kullanmak için ana yöntemi ayarlamak istediğiniz bağlanacağı/CLR derleyici seçeneği kullanmanız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bbcce-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="bbcce-130">Yönetilen kod C++ projesi içinde kullanımını etkinleştirmek için: Win32clock proje üzerinde sağ tıklayıp **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="bbcce-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span>  <span data-ttu-id="bbcce-131">Üzerinde **genel** özellik sayfası (varsayılan) değiştirmek için ortak dil çalışma zamanı desteği `/clr`.</span><span class="sxs-lookup"><span data-stu-id="bbcce-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>  
  
 <span data-ttu-id="bbcce-132">Ardından, DLL'ler için gerekli başvuruları eklemek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll ve UIAutomationTypes.dll.</span><span class="sxs-lookup"><span data-stu-id="bbcce-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="bbcce-133">(Yönergeleri izleyerek, C: sürücüsünde işletim sisteminin yüklü varsayılır.)</span><span class="sxs-lookup"><span data-stu-id="bbcce-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>  
  
1.  <span data-ttu-id="bbcce-134">Win32clock projesine sağ tıklayıp **başvuruları...** , söz konusu iletişim içindeydi ve:</span><span class="sxs-lookup"><span data-stu-id="bbcce-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>  
  
2.  <span data-ttu-id="bbcce-135">Win32clock projesine sağ tıklayıp **başvuruları...** .</span><span class="sxs-lookup"><span data-stu-id="bbcce-135">Right-click win32clock project and select **References...**.</span></span>  
  
3.  <span data-ttu-id="bbcce-136">Tıklayın **Yeni Başvuru Ekle**Gözat sekmesini tıklatın, C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll'e girin ve Tamam'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bbcce-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>  
  
4.  <span data-ttu-id="bbcce-137">PresentationFramework.dll için yineleyin: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span><span class="sxs-lookup"><span data-stu-id="bbcce-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>  
  
5.  <span data-ttu-id="bbcce-138">WindowsBase.dll için yineleyin: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span><span class="sxs-lookup"><span data-stu-id="bbcce-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>  
  
6.  <span data-ttu-id="bbcce-139">UIAutomationTypes.dll için yineleyin: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span><span class="sxs-lookup"><span data-stu-id="bbcce-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>  
  
7.  <span data-ttu-id="bbcce-140">UIAutomationProvider.dll için yineleyin: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span><span class="sxs-lookup"><span data-stu-id="bbcce-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>  
  
8.  <span data-ttu-id="bbcce-141">Tıklayın **Yeni Başvuru Ekle**System.dll seçin ve tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="bbcce-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>  
  
9. <span data-ttu-id="bbcce-142">Tıklayın **Tamam** başvuruları eklemek için win32clock özellik sayfaları'ndan çıkmak için.</span><span class="sxs-lookup"><span data-stu-id="bbcce-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>  
  
 <span data-ttu-id="bbcce-143">Son olarak, ekleme `STAThreadAttribute` için `_tWinMain` ile kullanmak için yöntemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="bbcce-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 <span data-ttu-id="bbcce-144">Bu öznitelik söyler [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] , ne zaman başlatır [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], için gerekli olan bir tek iş parçacıklı model (STA) kullanması gereken [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="bbcce-144">This attribute tells the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] that when it initializes [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span></span>  
  
## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="bbcce-145">Windows Presentation Framework sayfası oluşturma</span><span class="sxs-lookup"><span data-stu-id="bbcce-145">Create a Windows Presentation Framework Page</span></span>  
 <span data-ttu-id="bbcce-146">Tanımlayan bir DLL ardından, oluşturduğunuz bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="bbcce-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="bbcce-147">Genellikle oluşturmak en kolay yöntemdir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> bir tek başına uygulama yazma ve hata ayıklama olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] böylece kısmını.</span><span class="sxs-lookup"><span data-stu-id="bbcce-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span>  <span data-ttu-id="bbcce-148">Bunu yaptıktan sonra bu proje bir DLL içine tıklayarak projeyi sağ tıklatarak kapatılabilir **özellikleri**, uygulamaya gidip ve Windows sınıf kitaplığı için çıktı türünü değiştirme.</span><span class="sxs-lookup"><span data-stu-id="bbcce-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>  
  
 <span data-ttu-id="bbcce-149">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Dll projesi ardından ile birleştirilebilir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projesi (iki proje içeren bir çözüm) – sağ tıklayın, çözümü, select **sağa proje**.</span><span class="sxs-lookup"><span data-stu-id="bbcce-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>  
  
 <span data-ttu-id="bbcce-150">Bunu kullanmayı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] DLL'den [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projesi, bir başvuru eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="bbcce-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project, you need to add a reference:</span></span>  
  
1.  <span data-ttu-id="bbcce-151">Win32clock projesine sağ tıklayıp **başvuruları...** .</span><span class="sxs-lookup"><span data-stu-id="bbcce-151">Right-click win32clock project and select **References...**.</span></span>  
  
2.  <span data-ttu-id="bbcce-152">Tıklayın **Yeni Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="bbcce-152">Click **Add New Reference**.</span></span>  
  
3.  <span data-ttu-id="bbcce-153">Tıklayın **projeleri** sekmesi.  WPFClock'ı seçin, Tamam'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bbcce-153">Click the **Projects** tab.  Select WPFClock, click OK.</span></span>  
  
4.  <span data-ttu-id="bbcce-154">Tıklayın **Tamam** başvuruları eklemek için win32clock özellik sayfaları'ndan çıkmak için.</span><span class="sxs-lookup"><span data-stu-id="bbcce-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>  
  
## <a name="hwndsource"></a><span data-ttu-id="bbcce-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="bbcce-155">HwndSource</span></span>  
 <span data-ttu-id="bbcce-156">Ardından, kullandığınız <xref:System.Windows.Interop.HwndSource> yapmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> HWND gibi arayın.</span><span class="sxs-lookup"><span data-stu-id="bbcce-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span>  <span data-ttu-id="bbcce-157">Bu kod bloğu bir C++ dosyaya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bbcce-157">You add this block of code to a C++ file:</span></span>  
  
```  
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
  
 <span data-ttu-id="bbcce-158">Bu bazı açıklamalar kullanan kod uzun bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="bbcce-158">This is a long piece of code that could use some explanation.</span></span>  <span data-ttu-id="bbcce-159">İlk bölümü çeşitli yan tümceleri olduğundan tüm çağrıları tam olarak nitelemek gerekmez:</span><span class="sxs-lookup"><span data-stu-id="bbcce-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 <span data-ttu-id="bbcce-160">Oluşturan bir işlev tanımlayın ardından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik, yerleştiren bir <xref:System.Windows.Interop.HwndSource> ve HWND döndürür:</span><span class="sxs-lookup"><span data-stu-id="bbcce-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 <span data-ttu-id="bbcce-161">İlk olarak, oluşturun bir <xref:System.Windows.Interop.HwndSource>, parametreleri için CreateWindow benzerdir:</span><span class="sxs-lookup"><span data-stu-id="bbcce-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>  
  
```  
HwndSource^ source = gcnew HwndSource(  
    0, // class style  
    WS_VISIBLE | WS_CHILD, // style  
    0, // exstyle  
    x, y, width, height,  
    "hi", // NAME  
    IntPtr(parent) // parent window   
    );  
```  
  
 <span data-ttu-id="bbcce-162">Oluşturduğunuz sonra [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıf oluşturucusuna çağrı yaparak içerik:</span><span class="sxs-lookup"><span data-stu-id="bbcce-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 <span data-ttu-id="bbcce-163">Sayfaya bağlandıktan sonra <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="bbcce-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>  
  
```  
source->RootVisual = page;  
```  
  
 <span data-ttu-id="bbcce-164">Ve son satırında HWND döndürür <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="bbcce-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a><span data-ttu-id="bbcce-165">Hwnd konumlandırma</span><span class="sxs-lookup"><span data-stu-id="bbcce-165">Positioning the Hwnd</span></span>  
 <span data-ttu-id="bbcce-166">İçeren bir HWND sahip olduğunuza göre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzende, getirmeniz gerekir bu HWND içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] iletişim.</span><span class="sxs-lookup"><span data-stu-id="bbcce-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog.</span></span>  <span data-ttu-id="bbcce-167">HWND yalnızca nereye koyacağınızı ise, yalnızca o boyutunu ve konumunu geçip geçmeyeceğini `GetHwnd` önceden tanımladığınız işlevi.</span><span class="sxs-lookup"><span data-stu-id="bbcce-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span>  <span data-ttu-id="bbcce-168">Ancak, bir kaynak dosyası iletişim Cwnd'lerden hiçbirini nerede konumlandırılacağını tam olarak emin olacak şekilde tanımlamak için kullanılan.</span><span class="sxs-lookup"><span data-stu-id="bbcce-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span>  <span data-ttu-id="bbcce-169">Kullanabileceğiniz [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] koymak için iletişim kutusu Düzenleyicisi bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] statik denetim, Git saati istediğiniz ("Ekle düzende burada") ve konumlandırmak için kullanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati.</span><span class="sxs-lookup"><span data-stu-id="bbcce-169">You can use the [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] dialog editor to put a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>  
  
 <span data-ttu-id="bbcce-170">WM_INITDIALOG işlediğiniz burada kullandığınız `GetDlgItem` HWND yer tutucusu için almak için:</span><span class="sxs-lookup"><span data-stu-id="bbcce-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 <span data-ttu-id="bbcce-171">Böylece, ardından bu yer tutucu statik konumunu ve boyutunu hesaplayabilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , yerinde saati:</span><span class="sxs-lookup"><span data-stu-id="bbcce-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>  
  
 <span data-ttu-id="bbcce-172">RECT dikdörtgeni;</span><span class="sxs-lookup"><span data-stu-id="bbcce-172">RECT rectangle;</span></span>  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 <span data-ttu-id="bbcce-173">Ardından statik yer tutucu Gizle:</span><span class="sxs-lookup"><span data-stu-id="bbcce-173">Then you hide the placeholder STATIC:</span></span>  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 <span data-ttu-id="bbcce-174">Oluşturup [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND o konumda saati:</span><span class="sxs-lookup"><span data-stu-id="bbcce-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 <span data-ttu-id="bbcce-175">Öğreticiyi ilginç hale getirmek ve gerçek üretmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzende, oluşturmanız gerekir bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati denetimi bu noktada.</span><span class="sxs-lookup"><span data-stu-id="bbcce-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="bbcce-176">Arka plan kod yalnızca birkaç olay işleyicileri ile çoğunlukla biçimlendirme içinde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbcce-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="bbcce-177">Bu öğreticide, birlikte çalışabilirlik ve denetimi tasarım hakkında değil olduğundan, için kod tamamlama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saat sağlanır için ayrı yönergeler onu oluşturmak veya her bir parçası olarak ne anlama geldiğini olmadan bir kod bloğu olarak burada.</span><span class="sxs-lookup"><span data-stu-id="bbcce-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="bbcce-178">Görünüm veya denetimi işlevlerini değiştirmek için bu kodla denemeler çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="bbcce-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>  
  
 <span data-ttu-id="bbcce-179">Biçimlendirme şöyledir:</span><span class="sxs-lookup"><span data-stu-id="bbcce-179">Here is the markup:</span></span>  
  
 [!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 <span data-ttu-id="bbcce-180">Ve eşlik eden arka plan kod şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="bbcce-180">And here is the accompanying code-behind:</span></span>  
  
 [!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 <span data-ttu-id="bbcce-181">Nihai sonucu şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="bbcce-181">The final result looks like:</span></span>  
  
 <span data-ttu-id="bbcce-182">![Tarih ve Saat Özellikleri iletişim kutusu](./media/interoparch08.PNG "InteropArch08")</span><span class="sxs-lookup"><span data-stu-id="bbcce-182">![Date and Time Properties dialog box](./media/interoparch08.PNG "InteropArch08")</span></span>  
  
 <span data-ttu-id="bbcce-183">Sonuç şu ekran üretilen kod için karşılaştırmak için bkz [Win32 saati birlikte çalışma örneği](https://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="bbcce-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbcce-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbcce-184">See also</span></span>
- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="bbcce-185">WPF ve Win32 Birlikte Çalışması</span><span class="sxs-lookup"><span data-stu-id="bbcce-185">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
- [<span data-ttu-id="bbcce-186">Win32 saati birlikte çalışabilirlik örneği</span><span class="sxs-lookup"><span data-stu-id="bbcce-186">Win32 Clock Interoperation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160051)
