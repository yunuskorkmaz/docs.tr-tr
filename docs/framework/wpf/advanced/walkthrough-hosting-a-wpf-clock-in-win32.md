---
title: "İzlenecek yol: Win32'de WPF Saati Barındırma"
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 58e4b1dd311ccd6e1bbab79f4c4dda2207f96eaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549704"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a><span data-ttu-id="4c362-102">İzlenecek yol: Win32'de WPF Saati Barındırma</span><span class="sxs-lookup"><span data-stu-id="4c362-102">Walkthrough: Hosting a WPF Clock in Win32</span></span>
<span data-ttu-id="4c362-103">Yerleştirilecek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamaları, <xref:System.Windows.Interop.HwndSource>, içeren HWND sağlayan, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği.</span><span class="sxs-lookup"><span data-stu-id="4c362-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="4c362-104">Oluşturduğunuz ilk <xref:System.Windows.Interop.HwndSource>, CreateWindow'unkine benzer parametreler vererek.</span><span class="sxs-lookup"><span data-stu-id="4c362-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span>  <span data-ttu-id="4c362-105">Size sonra <xref:System.Windows.Interop.HwndSource> hakkında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde içerik istiyor.</span><span class="sxs-lookup"><span data-stu-id="4c362-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span>  <span data-ttu-id="4c362-106">Son olarak, dışı HWND almak <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="4c362-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="4c362-107">Bu kılavuz karma oluşturma gösterilmektedir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işletim sistemi in uygulama **tarih ve saat özellikleri** iletişim.</span><span class="sxs-lookup"><span data-stu-id="4c362-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application that reimplements the operating system **Date and Time Properties** dialog.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4c362-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="4c362-108">Prerequisites</span></span>  
 <span data-ttu-id="4c362-109">Bkz: [WPF ve Win32 birlikte çalışabilirlik](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="4c362-109">See [WPF and Win32 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span></span>  
  
## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="4c362-110">Bu öğretici nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="4c362-110">How to Use This Tutorial</span></span>  
 <span data-ttu-id="4c362-111">Bu öğretici, birlikte çalışabilirlik uygulama oluşturmanın önemli adımlar yoğunlaşır.</span><span class="sxs-lookup"><span data-stu-id="4c362-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="4c362-112">Öğretici bir örneği tarafından desteklenen [Win32 saati birlikte çalışabilirlik örneği](http://go.microsoft.com/fwlink/?LinkID=160051), ancak bu örnek son ürünün yansıtıcı.</span><span class="sxs-lookup"><span data-stu-id="4c362-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051), but that sample is reflective of the end product.</span></span> <span data-ttu-id="4c362-113">Varolan ile başlayan gibi Bu öğreticide adımları belgeler [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kendi projesi, belki de önceden var olan bir proje ve ekleme barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanıza.</span><span class="sxs-lookup"><span data-stu-id="4c362-113">This tutorial documents the steps as if you were starting with an existing [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="4c362-114">Son ürününüzü karşılaştırabilirsiniz [Win32 saati birlikte çalışabilirlik örneği](http://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="4c362-114">You can compare your end product with [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051).</span></span>  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="4c362-115">İzlenecek yol Win32 içinde Windows Presentation Framework'ün (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="4c362-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>  
 <span data-ttu-id="4c362-116">Aşağıdaki grafikte Bu öğreticinin hedeflediği son ürünü gösterir:</span><span class="sxs-lookup"><span data-stu-id="4c362-116">The following graphic shows the intended end product of this tutorial:</span></span>  
  
 <span data-ttu-id="4c362-117">![Tarih ve Saat Özellikleri iletişim kutusu](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")</span><span class="sxs-lookup"><span data-stu-id="4c362-117">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")</span></span>  
  
 <span data-ttu-id="4c362-118">C++ oluşturarak bu iletişim kutusunu yeniden oluşturabilirsiniz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] proje [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]ve aşağıdaki oluşturmak için iletişim kutusu düzenleyicisini kullanma:</span><span class="sxs-lookup"><span data-stu-id="4c362-118">You can recreate this dialog by creating C++ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and using the dialog editor to create the following:</span></span>  
  
 <span data-ttu-id="4c362-119">![Tarih ve Saat Özellikleri iletişim kutusu](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")</span><span class="sxs-lookup"><span data-stu-id="4c362-119">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")</span></span>  
  
 <span data-ttu-id="4c362-120">(Kullanmak gerekmez [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] kullanmak için <xref:System.Windows.Interop.HwndSource>, ve yazmak için C++ kullanma gerekmez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programları, ancak bunu yapmak için oldukça tipik bir yoludur ve kendisi de bir adım öğretici açıklaması için uygundur).</span><span class="sxs-lookup"><span data-stu-id="4c362-120">(You do not need to use [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>  
  
 <span data-ttu-id="4c362-121">Beş belirli yerleştirmek için gerçekleştirmeniz gereken bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iletişim saati:</span><span class="sxs-lookup"><span data-stu-id="4c362-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>  
  
1.  <span data-ttu-id="4c362-122">Etkinleştirme, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] yönetilen kod projesi (**/CLR**) içinde proje ayarlarını değiştirerek [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4c362-122">Enable your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project to call managed code (**/clr**) by changing project settings in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="4c362-123">Oluşturma bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> ayrı bir DLL içinde.</span><span class="sxs-lookup"><span data-stu-id="4c362-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>  
  
3.  <span data-ttu-id="4c362-124">Put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> içinde bir <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="4c362-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>  
  
4.  <span data-ttu-id="4c362-125">Bunun için bir HWND alın <xref:System.Windows.Controls.Page> kullanarak <xref:System.Windows.Interop.HwndSource.Handle%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4c362-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>  
  
5.  <span data-ttu-id="4c362-126">Kullanım [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HWND büyük içinde nereye yerleştireceğinizi karar vermek için [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulama</span><span class="sxs-lookup"><span data-stu-id="4c362-126">Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] to decide where to place the HWND within the larger [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application</span></span>  
  
## <a name="clr"></a><span data-ttu-id="4c362-127">/ CLR</span><span class="sxs-lookup"><span data-stu-id="4c362-127">/clr</span></span>  
 <span data-ttu-id="4c362-128">Etkinleştirmek için bunu yönetilmeyen ilk adımdır [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] çağırana projeye yönetilen kod.</span><span class="sxs-lookup"><span data-stu-id="4c362-128">The first step is to turn this unmanaged [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project into one that can call managed code.</span></span>  <span data-ttu-id="4c362-129">Kullanın ve Main yöntemi ile kullanmak için ayarlamak istediğiniz gerekli DLL'leri bağlayacak/CLR derleyici seçeneği kullandığınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4c362-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="4c362-130">C++ projesi içinde yönetilen kod kullanımını etkinleştirmek için: win32clock projeye sağ tıklayın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="4c362-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span>  <span data-ttu-id="4c362-131">Üzerinde **genel** özellik sayfası (varsayılan) değiştirmek için ortak dil çalışma zamanı desteğini `/clr`.</span><span class="sxs-lookup"><span data-stu-id="4c362-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>  
  
 <span data-ttu-id="4c362-132">Ardından, DLL'ler için gerekli başvurular ekleyin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll ve UIAutomationTypes.dll.</span><span class="sxs-lookup"><span data-stu-id="4c362-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="4c362-133">(Yönergeleri izleyerek C: sürücüsüne işletim sisteminin yüklü olduğu varsayılır.)</span><span class="sxs-lookup"><span data-stu-id="4c362-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>  
  
1.  <span data-ttu-id="4c362-134">Win32clock projesine sağ tıklatın ve **başvuruları...** ve o iletişim içinde:</span><span class="sxs-lookup"><span data-stu-id="4c362-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>  
  
2.  <span data-ttu-id="4c362-135">Win32clock projesine sağ tıklatın ve **başvuruları...** .</span><span class="sxs-lookup"><span data-stu-id="4c362-135">Right-click win32clock project and select **References...**.</span></span>  
  
3.  <span data-ttu-id="4c362-136">Tıklatın **Yeni Başvuru Ekle**Gözat sekmesini tıklatın, C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll'e girin ve Tamam'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4c362-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>  
  
4.  <span data-ttu-id="4c362-137">PresentationFramework.dll için yineleyin: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span><span class="sxs-lookup"><span data-stu-id="4c362-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>  
  
5.  <span data-ttu-id="4c362-138">WindowsBase.dll için yineleyin: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span><span class="sxs-lookup"><span data-stu-id="4c362-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>  
  
6.  <span data-ttu-id="4c362-139">UIAutomationTypes.dll için yineleyin: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span><span class="sxs-lookup"><span data-stu-id="4c362-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>  
  
7.  <span data-ttu-id="4c362-140">UIAutomationProvider.dll için yineleyin: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span><span class="sxs-lookup"><span data-stu-id="4c362-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>  
  
8.  <span data-ttu-id="4c362-141">Tıklatın **Yeni Başvuru Ekle**System.dll seçin ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="4c362-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>  
  
9. <span data-ttu-id="4c362-142">Tıklatın **Tamam** başvuruları ekleme win32clock özellik sayfalarından çıkmak için.</span><span class="sxs-lookup"><span data-stu-id="4c362-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>  
  
 <span data-ttu-id="4c362-143">Son olarak, ekleme `STAThreadAttribute` için `_tWinMain` ile kullanmak için yöntemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="4c362-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 <span data-ttu-id="4c362-144">Bu öznitelik söyler [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] , ne zaman başlatır [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], için gerekli olan tek iş parçacıklı model (STA) kullanması gereken [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="4c362-144">This attribute tells the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] that when it initializes [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span></span>  
  
## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="4c362-145">Bir Windows Presentation Framework sayfası oluşturun</span><span class="sxs-lookup"><span data-stu-id="4c362-145">Create a Windows Presentation Framework Page</span></span>  
 <span data-ttu-id="4c362-146">Tanımlayan bir DLL ardından, oluşturduğunuz bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="4c362-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="4c362-147">Genellikle oluşturmak en kolay yoludur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> tek başına uygulama ve yazma ve hata ayıklama olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bu şekilde bölümü.</span><span class="sxs-lookup"><span data-stu-id="4c362-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span>  <span data-ttu-id="4c362-148">Bunu yaptıktan sonra bu proje bir DLL'e tıklayarak projeyi sağ tıklatarak açılabilir **özellikleri**, uygulamaya giderek ve çıktı türü Windows Sınıf Kitaplığı'na değiştirme.</span><span class="sxs-lookup"><span data-stu-id="4c362-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>  
  
 <span data-ttu-id="4c362-149">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Dll projesi birleştirilebilir ile [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projesi (iki proje içeren bir çözüm) – çözüm üzerinde select **sağa proje**.</span><span class="sxs-lookup"><span data-stu-id="4c362-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>  
  
 <span data-ttu-id="4c362-150">Bunu kullanmayı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] DLL'den [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] proje, gereken bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4c362-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project, you need to add a reference:</span></span>  
  
1.  <span data-ttu-id="4c362-151">Win32clock projesine sağ tıklatın ve **başvuruları...** .</span><span class="sxs-lookup"><span data-stu-id="4c362-151">Right-click win32clock project and select **References...**.</span></span>  
  
2.  <span data-ttu-id="4c362-152">Tıklatın **Yeni Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="4c362-152">Click **Add New Reference**.</span></span>  
  
3.  <span data-ttu-id="4c362-153">Tıklatın **projeleri** sekmesi.  WPFClock'ı seçin, Tamam'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4c362-153">Click the **Projects** tab.  Select WPFClock, click OK.</span></span>  
  
4.  <span data-ttu-id="4c362-154">Tıklatın **Tamam** başvuruları ekleme win32clock özellik sayfalarından çıkmak için.</span><span class="sxs-lookup"><span data-stu-id="4c362-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>  
  
## <a name="hwndsource"></a><span data-ttu-id="4c362-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="4c362-155">HwndSource</span></span>  
 <span data-ttu-id="4c362-156">Ardından, kullandığınız <xref:System.Windows.Interop.HwndSource> yapmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> HWND gibi arayın.</span><span class="sxs-lookup"><span data-stu-id="4c362-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span>  <span data-ttu-id="4c362-157">Bu kod bloğu bir C++ dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4c362-157">You add this block of code to a C++ file:</span></span>  
  
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
  
 <span data-ttu-id="4c362-158">Bu, bazı açıklamalar kullanan kodu uzun bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="4c362-158">This is a long piece of code that could use some explanation.</span></span>  <span data-ttu-id="4c362-159">İlk bölümü çeşitli yan tümceleri, böylelikle tüm çağrıları tam olarak nitelemek gerekmez:</span><span class="sxs-lookup"><span data-stu-id="4c362-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 <span data-ttu-id="4c362-160">Oluşturan bir işlev tanımlayın sonra [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik, yerleştiren bir <xref:System.Windows.Interop.HwndSource> ve HWND döndürür:</span><span class="sxs-lookup"><span data-stu-id="4c362-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 <span data-ttu-id="4c362-161">Önce oluşturduğunuz bir <xref:System.Windows.Interop.HwndSource>, parametreleri CreateWindow'unkine benzer:</span><span class="sxs-lookup"><span data-stu-id="4c362-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>  
  
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
  
 <span data-ttu-id="4c362-162">Oluşturduğunuz sonra [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfını onun oluşturucusunu çağırarak:</span><span class="sxs-lookup"><span data-stu-id="4c362-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 <span data-ttu-id="4c362-163">Ardından sayfasına bağlanmak <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="4c362-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>  
  
```  
source->RootVisual = page;  
```  
  
 <span data-ttu-id="4c362-164">Ve son satırında için HWND döndürün <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="4c362-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a><span data-ttu-id="4c362-165">Hwnd konumlandırma</span><span class="sxs-lookup"><span data-stu-id="4c362-165">Positioning the Hwnd</span></span>  
 <span data-ttu-id="4c362-166">İçeren bir HWND sahip olduğunuza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati, gereken o HWND içine yerleştirilecek [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] iletişim.</span><span class="sxs-lookup"><span data-stu-id="4c362-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog.</span></span>  <span data-ttu-id="4c362-167">HWND yalnızca nereye koyacağınızı biliyorsanız, yalnızca o boyutunu ve konumunu geçip geçmeyeceğini `GetHwnd` daha önce tanımlanan işlevi.</span><span class="sxs-lookup"><span data-stu-id="4c362-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span>  <span data-ttu-id="4c362-168">Ancak, bir kaynak dosyası Cwnd'lerden hiçbirini nereye konumlandırılır kesinlikle emin; bu nedenle iletişim tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c362-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span>  <span data-ttu-id="4c362-169">Kullanabileceğiniz [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] koymak için iletişim kutusu Düzenleyicisi bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] statik kontrol gitmek için saatin istediğiniz yere ("saati Buraya Ekle") ve konumlandırmak için kullanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saat.</span><span class="sxs-lookup"><span data-stu-id="4c362-169">You can use the [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] dialog editor to put a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>  
  
 <span data-ttu-id="4c362-170">WM_INITDIALOG işlediğiniz yerde, kullandığınız `GetDlgItem` HWND STATIC yer tutucusu için:</span><span class="sxs-lookup"><span data-stu-id="4c362-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 <span data-ttu-id="4c362-171">Koyabilirsiniz şekilde, daha sonra bu yer tutucu statik, konumunu ve boyutunu hesaplayabilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bu yerinde saat:</span><span class="sxs-lookup"><span data-stu-id="4c362-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>  
  
 <span data-ttu-id="4c362-172">RECT dikdörtgeni;</span><span class="sxs-lookup"><span data-stu-id="4c362-172">RECT rectangle;</span></span>  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 <span data-ttu-id="4c362-173">STATİK tutucu Gizle sonra:</span><span class="sxs-lookup"><span data-stu-id="4c362-173">Then you hide the placeholder STATIC:</span></span>  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 <span data-ttu-id="4c362-174">Ve oluşturma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o konumda HWND saat:</span><span class="sxs-lookup"><span data-stu-id="4c362-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 <span data-ttu-id="4c362-175">Öğreticiyi ilginç hale getirmek ve gerçek üretmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati, gerekir oluşturmak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati denetimi bu noktada.</span><span class="sxs-lookup"><span data-stu-id="4c362-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="4c362-176">Arka plan kodu birkaç olay işleyicileri ile çoğunlukla biçimlendirme içinde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c362-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="4c362-177">Bu öğretici denetim tasarımı ile ilgili değildir ve birlikte çalışma hakkında olduğundan için tam kod [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saati sağlanır burada için ayrı yönergeler onu oluşturmak veya her bölümü anlamı olmadan bir kod bloğu olarak.</span><span class="sxs-lookup"><span data-stu-id="4c362-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="4c362-178">Görünüm veya denetim işlevselliğini değiştirmek için bu kodla denemeler çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="4c362-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>  
  
 <span data-ttu-id="4c362-179">Biçimlendirme aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="4c362-179">Here is the markup:</span></span>  
  
 [!code-xaml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 <span data-ttu-id="4c362-180">Ve eşlik eden arka plan kod şöyledir:</span><span class="sxs-lookup"><span data-stu-id="4c362-180">And here is the accompanying code-behind:</span></span>  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 <span data-ttu-id="4c362-181">Nihai sonucu şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="4c362-181">The final result looks like:</span></span>  
  
 <span data-ttu-id="4c362-182">![Tarih ve Saat Özellikleri iletişim kutusu](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")</span><span class="sxs-lookup"><span data-stu-id="4c362-182">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")</span></span>  
  
 <span data-ttu-id="4c362-183">Bu ekran görüntüsünde üretilen kod için sonuç karşılaştırmak için bkz: [Win32 saati birlikte çalışabilirlik örneği](http://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="4c362-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c362-184">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4c362-184">See Also</span></span>  
 <xref:System.Windows.Interop.HwndSource>  
 [<span data-ttu-id="4c362-185">WPF ve Win32 Birlikte Çalışması</span><span class="sxs-lookup"><span data-stu-id="4c362-185">WPF and Win32 Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [<span data-ttu-id="4c362-186">Win32 saati birlikte çalışabilirlik örneği</span><span class="sxs-lookup"><span data-stu-id="4c362-186">Win32 Clock Interoperation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160051)
