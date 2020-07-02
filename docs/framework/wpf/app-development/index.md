---
title: Uygulama Geliştirme
description: Windows Presentation Foundation (WPF) çerçevesini kullanarak çeşitli uygulamalar oluşturmayı öğrenin.
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: ac4227785f2fc398217b3aa8984176844264bbaa
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613741"
---
# <a name="application-development"></a><span data-ttu-id="ce925-103">Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="ce925-103">Application Development</span></span>
<a name="introduction"></a><span data-ttu-id="ce925-104">Windows Presentation Foundation (WPF), aşağıdaki uygulama türlerini geliştirmek için kullanılabilen bir sunum çerçevesidir:</span><span class="sxs-lookup"><span data-stu-id="ce925-104">Windows Presentation Foundation (WPF) is a presentation framework that can be used to develop the following types of applications:</span></span>  
  
- <span data-ttu-id="ce925-105">Tek başına uygulamalar (geleneksel stil Windows uygulamaları, istemci bilgisayara yüklenmiş ve bu bilgisayardan çalıştırılan yürütülebilir derlemeler olarak oluşturulur).</span><span class="sxs-lookup"><span data-stu-id="ce925-105">Standalone Applications (traditional style Windows applications built as executable assemblies that are installed to and run from the client computer).</span></span>  
  
- <span data-ttu-id="ce925-106">XAML tarayıcı uygulamaları (XBAP 'ler) (yürütülebilir derlemeler olarak oluşturulan ve Microsoft Internet Explorer veya Mozilla Firefox gibi Web tarayıcıları tarafından barındırılan gezinti sayfalarından oluşan uygulamalar).</span><span class="sxs-lookup"><span data-stu-id="ce925-106">XAML browser applications (XBAPs) (applications composed of navigation pages that are built as executable assemblies and hosted by Web browsers such as Microsoft Internet Explorer or Mozilla Firefox).</span></span>  
  
- <span data-ttu-id="ce925-107">Özel denetim kitaplıkları (yeniden kullanılabilir denetimleri içeren yürütülebilir olmayan derlemeler).</span><span class="sxs-lookup"><span data-stu-id="ce925-107">Custom Control Libraries (non-executable assemblies containing reusable controls).</span></span>  
  
- <span data-ttu-id="ce925-108">Sınıf kitaplıkları (yeniden kullanılabilir sınıfları içeren yürütülebilir olmayan derlemeler).</span><span class="sxs-lookup"><span data-stu-id="ce925-108">Class Libraries (non-executable assemblies that contain reusable classes).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce925-109">Windows hizmetinde WPF türlerinin kullanılması kesinlikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="ce925-109">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="ce925-110">Bu özellikleri bir Windows hizmetinde kullanmaya çalışırsanız, beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ce925-110">If you attempt to use these features in a Windows service, they may not work as expected.</span></span>  
  
 <span data-ttu-id="ce925-111">Bu uygulama kümesini oluşturmak için WPF bir hizmet ana bilgisayarı uygular.</span><span class="sxs-lookup"><span data-stu-id="ce925-111">To build this set of applications, WPF implements a host of services.</span></span> <span data-ttu-id="ce925-112">Bu konuda bu hizmetlere genel bir bakış sağlanır ve daha fazla bilgi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce925-112">This topic provides an overview of these services and where to find more information.</span></span>  

<a name="Application_Management"></a>
## <a name="application-management"></a><span data-ttu-id="ce925-113">Uygulama Yönetimi</span><span class="sxs-lookup"><span data-stu-id="ce925-113">Application Management</span></span>  
 <span data-ttu-id="ce925-114">Yürütülebilir WPF uygulamaları, genellikle aşağıdakileri içeren bir çekirdek işlev kümesi gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ce925-114">Executable WPF applications commonly require a core set of functionality that includes the following:</span></span>  
  
- <span data-ttu-id="ce925-115">Ortak uygulama altyapısını oluşturma ve yönetme (bir giriş noktası yöntemi ve sistem ve giriş iletilerini almak için bir Windows ileti döngüsü oluşturma dahil).</span><span class="sxs-lookup"><span data-stu-id="ce925-115">Creating and managing common application infrastructure (including creating an entry point method and a Windows message loop to receive system and input messages).</span></span>  
  
- <span data-ttu-id="ce925-116">Bir uygulamanın yaşam süresi ile izleme ve etkileşim kurma.</span><span class="sxs-lookup"><span data-stu-id="ce925-116">Tracking and interacting with the lifetime of an application.</span></span>  
  
- <span data-ttu-id="ce925-117">Komut satırı parametrelerini alma ve işleme.</span><span class="sxs-lookup"><span data-stu-id="ce925-117">Retrieving and processing command-line parameters.</span></span>  
  
- <span data-ttu-id="ce925-118">Uygulama kapsamı özelliklerini ve kaynaklarını paylaşma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ce925-118">Sharing application-scope properties and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] resources.</span></span>  
  
- <span data-ttu-id="ce925-119">İşlenmeyen özel durumları algılama ve işleme.</span><span class="sxs-lookup"><span data-stu-id="ce925-119">Detecting and processing unhandled exceptions.</span></span>  
  
- <span data-ttu-id="ce925-120">Çıkış kodları döndürülüyor.</span><span class="sxs-lookup"><span data-stu-id="ce925-120">Returning exit codes.</span></span>  
  
- <span data-ttu-id="ce925-121">Windows 'ı tek başına uygulamalarda yönetme.</span><span class="sxs-lookup"><span data-stu-id="ce925-121">Managing windows in standalone applications.</span></span>  
  
- <span data-ttu-id="ce925-122">XAML tarayıcı uygulamalarında (XBAP) ve gezinti pencereleri ve çerçevelerle tek başına uygulamalarda gezinmeyi izleme.</span><span class="sxs-lookup"><span data-stu-id="ce925-122">Tracking navigation in XAML browser applications (XBAPs), and standalone applications with navigation windows and frames.</span></span>  
  
 <span data-ttu-id="ce925-123">Bu yetenekler <xref:System.Windows.Application> , *uygulama tanımı*kullanarak uygulamalarınıza eklediğiniz sınıfı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ce925-123">These capabilities are implemented by the <xref:System.Windows.Application> class, which you add to your applications using an *application definition*.</span></span>  
  
 <span data-ttu-id="ce925-124">Daha fazla bilgi için bkz. [uygulama yönetimine genel bakış](application-management-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ce925-124">For more information, see [Application Management Overview](application-management-overview.md).</span></span>  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="ce925-125">WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları</span><span class="sxs-lookup"><span data-stu-id="ce925-125">WPF Application Resource, Content, and Data Files</span></span>  
 <span data-ttu-id="ce925-126">WPF, ekli kaynaklar için Microsoft .NET çerçevesindeki temel desteği üç tür yürütülebilir olmayan veri dosyası desteğiyle genişletir: kaynak, içerik ve veri.</span><span class="sxs-lookup"><span data-stu-id="ce925-126">WPF extends the core support in the Microsoft .NET Framework for embedded resources with support for three kinds of non-executable data files: resource, content, and data.</span></span> <span data-ttu-id="ce925-127">Daha fazla bilgi için bkz. [WPF uygulama kaynağı, içerik ve veri dosyaları](wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="ce925-127">For more information, see [WPF Application Resource, Content, and Data Files](wpf-application-resource-content-and-data-files.md).</span></span>  
  
 <span data-ttu-id="ce925-128">WPF yürütülebilir olmayan veri dosyaları desteğinin temel bileşeni, benzersiz bir URI kullanarak bunları belirleyip yükleyebilme olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="ce925-128">A key component of the support for WPF non-executable data files is the ability to identify and load them using a unique URI.</span></span> <span data-ttu-id="ce925-129">Daha fazla bilgi için bkz. [WPF 'de paket URI 'leri](pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="ce925-129">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a><span data-ttu-id="ce925-130">Pencereler ve Iletişim kutuları</span><span class="sxs-lookup"><span data-stu-id="ce925-130">Windows and Dialog Boxes</span></span>  
 <span data-ttu-id="ce925-131">Kullanıcılar Windows aracılığıyla WPF tek başına uygulamalarıyla etkileşime geçer.</span><span class="sxs-lookup"><span data-stu-id="ce925-131">Users interact with WPF standalone applications through windows.</span></span> <span data-ttu-id="ce925-132">Bir pencerenin amacı, uygulama içeriğini barındırmak ve genellikle kullanıcıların içerikle etkileşime geçmesini sağlayan uygulama işlevlerini kullanıma sunmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ce925-132">The purpose of a window is to host application content and expose application functionality that usually allows users to interact with the content.</span></span> <span data-ttu-id="ce925-133">WPF 'de, Windows şunları destekleyen sınıfı tarafından kapsüllenir <xref:System.Windows.Window> :</span><span class="sxs-lookup"><span data-stu-id="ce925-133">In WPF, windows are encapsulated by the <xref:System.Windows.Window> class, which supports:</span></span>  
  
- <span data-ttu-id="ce925-134">Windows oluşturuluyor ve gösteriliyor.</span><span class="sxs-lookup"><span data-stu-id="ce925-134">Creating and showing windows.</span></span>  
  
- <span data-ttu-id="ce925-135">Sahip/sahip pencere ilişkileri oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="ce925-135">Establishing owner/owned window relationships.</span></span>  
  
- <span data-ttu-id="ce925-136">Pencere görünümünü yapılandırma (örneğin, boyut, konum, simgeler, başlık çubuğu metni, kenarlık).</span><span class="sxs-lookup"><span data-stu-id="ce925-136">Configuring window appearance (for example, size, location, icons, title bar text, border).</span></span>  
  
- <span data-ttu-id="ce925-137">Bir pencerenin ömrü ile izleme ve etkileşim kurma.</span><span class="sxs-lookup"><span data-stu-id="ce925-137">Tracking and interacting with the lifetime of a window.</span></span>  
  
 <span data-ttu-id="ce925-138">Daha fazla bilgi için bkz. [WPF Windows 'A genel bakış](wpf-windows-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ce925-138">For more information, see [WPF Windows Overview](wpf-windows-overview.md).</span></span>  
  
 <span data-ttu-id="ce925-139"><xref:System.Windows.Window>iletişim kutusu olarak bilinen özel bir pencere türü oluşturma yeteneğini destekler.</span><span class="sxs-lookup"><span data-stu-id="ce925-139"><xref:System.Windows.Window> supports the ability to create a special type of window known as a dialog box.</span></span> <span data-ttu-id="ce925-140">Hem kalıcı hem de kalıcı olmayan iletişim kutusu türleri oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="ce925-140">Both modal and modeless types of dialog boxes can be created.</span></span>  
  
 <span data-ttu-id="ce925-141">WPF, daha kolay ve uygulamalar arasında tutarlı bir kullanıcı deneyimi sağlamak için, yaygın Windows iletişim kutularından üçünü kullanıma sunar: <xref:Microsoft.Win32.OpenFileDialog> , <xref:Microsoft.Win32.SaveFileDialog> ve <xref:System.Windows.Controls.PrintDialog> .</span><span class="sxs-lookup"><span data-stu-id="ce925-141">For convenience, and the benefits of reusability and a consistent user experience across applications, WPF exposes three of the common Windows dialog boxes: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, and <xref:System.Windows.Controls.PrintDialog>.</span></span>  
  
 <span data-ttu-id="ce925-142">İleti kutusu, kullanıcılara önemli metin bilgileri göstermek ve basit Evet/Hayır/Tamam/Iptal soruları sormak için özel bir iletişim kutusu türüdür.</span><span class="sxs-lookup"><span data-stu-id="ce925-142">A message box is a special type of dialog box for showing important textual information to users, and for asking simple Yes/No/OK/Cancel questions.</span></span> <span data-ttu-id="ce925-143"><xref:System.Windows.MessageBox>İleti kutuları oluşturmak ve göstermek için sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ce925-143">You use the <xref:System.Windows.MessageBox> class to create and show message boxes.</span></span>  
  
 <span data-ttu-id="ce925-144">Daha fazla bilgi için bkz. [Iletişim kutularına genel bakış](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ce925-144">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
<a name="Navigation"></a>
## <a name="navigation"></a><span data-ttu-id="ce925-145">Gezinti</span><span class="sxs-lookup"><span data-stu-id="ce925-145">Navigation</span></span>  
 <span data-ttu-id="ce925-146">WPF, Pages ( <xref:System.Windows.Controls.Page> ) ve köprüleri () kullanarak Web stili gezintiyi destekler <xref:System.Windows.Documents.Hyperlink> .</span><span class="sxs-lookup"><span data-stu-id="ce925-146">WPF supports Web-style navigation using pages (<xref:System.Windows.Controls.Page>) and hyperlinks (<xref:System.Windows.Documents.Hyperlink>).</span></span> <span data-ttu-id="ce925-147">Gezinti, aşağıdakiler dahil olmak üzere çeşitli yollarla uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="ce925-147">Navigation can be implemented in a variety of ways that include the following:</span></span>  
  
- <span data-ttu-id="ce925-148">Bir Web tarayıcısında barındırılan tek başına sayfalar.</span><span class="sxs-lookup"><span data-stu-id="ce925-148">Standalone pages that are hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="ce925-149">Bir Web tarayıcısında barındırılan bir XBAP 'ye derlenen sayfalar.</span><span class="sxs-lookup"><span data-stu-id="ce925-149">Pages compiled into an XBAP that is hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="ce925-150">Tek başına bir uygulamada derlenen ve bir gezinti penceresi () tarafından barındırılan sayfalar <xref:System.Windows.Navigation.NavigationWindow> .</span><span class="sxs-lookup"><span data-stu-id="ce925-150">Pages compiled into a standalone application and hosted by a navigation window (<xref:System.Windows.Navigation.NavigationWindow>).</span></span>  
  
- <span data-ttu-id="ce925-151"><xref:System.Windows.Controls.Frame>Tek başına bir sayfada veya BIR XBAP ya da tek başına uygulama olarak derlenen bir sayfada barındırılan bir çerçeve () tarafından barındırılan sayfalar.</span><span class="sxs-lookup"><span data-stu-id="ce925-151">Pages that are hosted by a frame (<xref:System.Windows.Controls.Frame>), which may be hosted in a standalone page, or a page compiled into either an XBAP or a standalone application.</span></span>  
  
 <span data-ttu-id="ce925-152">Gezintiyi kolaylaştırmak için WPF aşağıdakileri uygular:</span><span class="sxs-lookup"><span data-stu-id="ce925-152">To facilitate navigation, WPF implements the following:</span></span>  
  
- <span data-ttu-id="ce925-153"><xref:System.Windows.Navigation.NavigationService>, <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.NavigationWindow> ve,, ve XBAP tarafından uygulama içi gezintiyi desteklemek için kullanılan gezinti isteklerini işlemeye yönelik paylaşılan gezinti motoru.</span><span class="sxs-lookup"><span data-stu-id="ce925-153"><xref:System.Windows.Navigation.NavigationService>, the shared navigation engine for processing navigation requests that is used by <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, and XBAPs to support intra-application navigation.</span></span>  
  
- <span data-ttu-id="ce925-154">Gezinmeyi başlatmak için gezinti yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="ce925-154">Navigation methods to initiate navigation.</span></span>  
  
- <span data-ttu-id="ce925-155">Gezinti ömrünü izlemek ve bunlarla etkileşime geçmek için gezinti olayları.</span><span class="sxs-lookup"><span data-stu-id="ce925-155">Navigation events to track and interact with navigation lifetime.</span></span>  
  
- <span data-ttu-id="ce925-156">Bir günlük kullanarak geri ve ileri gezinmesini hatırlayıp, aynı zamanda incelenebilir ve işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="ce925-156">Remembering back and forward navigation using a journal, which can also be inspected and manipulated.</span></span>  
  
 <span data-ttu-id="ce925-157">Daha fazla bilgi için bkz. [gezintiye genel bakış](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ce925-157">For information, see [Navigation Overview](navigation-overview.md).</span></span>  
  
 <span data-ttu-id="ce925-158">WPF, yapılandırılmış gezinti olarak bilinen özel bir gezinti türünü de destekler.</span><span class="sxs-lookup"><span data-stu-id="ce925-158">WPF also supports a special type of navigation known as structured navigation.</span></span> <span data-ttu-id="ce925-159">Yapılandırılmış gezinti, çağırma işlevleriyle tutarlı yapılandırılmış ve öngörülebilir bir şekilde veri döndüren bir veya daha fazla sayfayı çağırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ce925-159">Structured navigation can be used to call one or more pages that return data in a structured and predictable way that is consistent with calling functions.</span></span> <span data-ttu-id="ce925-160">Bu özellik <xref:System.Windows.Navigation.PageFunction%601> , [yapılandırılmış gezintiye genel bakış](structured-navigation-overview.md)bölümünde açıklanan sınıfa bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ce925-160">This capability depends on the <xref:System.Windows.Navigation.PageFunction%601> class, which is described further in [Structured Navigation Overview](structured-navigation-overview.md).</span></span> <span data-ttu-id="ce925-161"><xref:System.Windows.Navigation.PageFunction%601>Ayrıca, [gezinti topolojilerine genel bakış](navigation-topologies-overview.md)bölümünde açıklanan karmaşık gezinti topolojileri oluşturmayı basitleştirmeye de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce925-161"><xref:System.Windows.Navigation.PageFunction%601> also serves to simplify the creation of complex navigation topologies, which are described in [Navigation Topologies Overview](navigation-topologies-overview.md).</span></span>  
  
<a name="Hosting"></a>
## <a name="hosting"></a><span data-ttu-id="ce925-162">Hosting</span><span class="sxs-lookup"><span data-stu-id="ce925-162">Hosting</span></span>  
 <span data-ttu-id="ce925-163">XBAP 'ler, Microsoft Internet Explorer veya Firefox içinde barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ce925-163">XBAPs can be hosted in Microsoft Internet Explorer or Firefox.</span></span> <span data-ttu-id="ce925-164">Her barındırma modelinin, [barındırma](hosting-wpf-applications.md)kapsamında yer alan kendi konuları ve kısıtlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="ce925-164">Each hosting model has its own set of considerations and constraints that are covered in [Hosting](hosting-wpf-applications.md).</span></span>  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a><span data-ttu-id="ce925-165">Yapılandırma ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="ce925-165">Build and Deploy</span></span>  
 <span data-ttu-id="ce925-166">Basit WPF uygulamaları komut satırı derleyicileri kullanılarak bir komut isteminden oluşturulabilir, ancak WPF geliştirme ve oluşturma sürecini basitleştirerek ek destek sağlamak için Visual Studio ile tümleşir.</span><span class="sxs-lookup"><span data-stu-id="ce925-166">Although simple WPF applications can be built from a command prompt using command-line compilers, WPF integrates with Visual Studio to provide additional support that simplified the development and build process.</span></span> <span data-ttu-id="ce925-167">Daha fazla bilgi için bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="ce925-167">For more information, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="ce925-168">Oluşturduğunuz uygulamanın türüne bağlı olarak, aralarından seçim yapabileceğiniz bir veya daha fazla dağıtım seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="ce925-168">Depending on the type of application you build, there are one or more deployment options to choose from.</span></span> <span data-ttu-id="ce925-169">Daha fazla bilgi için bkz. [WPF uygulaması dağıtma](deploying-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="ce925-169">For more information, see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>  
  
<a name="related_topics"></a>
## <a name="related-topics"></a><span data-ttu-id="ce925-170">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="ce925-170">Related Topics</span></span>  
  
|<span data-ttu-id="ce925-171">Başlık</span><span class="sxs-lookup"><span data-stu-id="ce925-171">Title</span></span>|<span data-ttu-id="ce925-172">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce925-172">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ce925-173">Uygulama Yönetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ce925-173">Application Management Overview</span></span>](application-management-overview.md)|<span data-ttu-id="ce925-174"><xref:System.Windows.Application>Uygulama ömrü, Windows, uygulama kaynakları ve gezinmeyi yönetme dahil olmak üzere sınıfa genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce925-174">Provides an overview of the <xref:System.Windows.Application> class including managing application lifetime, windows, application resources, and navigation.</span></span>|  
|[<span data-ttu-id="ce925-175">WPF’de Windows</span><span class="sxs-lookup"><span data-stu-id="ce925-175">Windows in WPF</span></span>](windows-in-wpf-applications.md)|<span data-ttu-id="ce925-176">Uygulamanızda, <xref:System.Windows.Window> sınıfın ve iletişim kutularının kullanımı dahil olmak üzere yönetme hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce925-176">Provides details of managing windows in your application including how to use the <xref:System.Windows.Window> class and dialog boxes.</span></span>|  
|[<span data-ttu-id="ce925-177">Gezintiye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ce925-177">Navigation Overview</span></span>](navigation-overview.md)|<span data-ttu-id="ce925-178">Uygulamanızın sayfaları arasında gezinmeyi yönetmeye ilişkin bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce925-178">Provides an overview of managing navigation between pages of your application.</span></span>|  
|[<span data-ttu-id="ce925-179">Hosting</span><span class="sxs-lookup"><span data-stu-id="ce925-179">Hosting</span></span>](hosting-wpf-applications.md)|<span data-ttu-id="ce925-180">XAML tarayıcı uygulamalarına (XBAP 'ler) genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce925-180">Provides an overview of XAML browser applications (XBAPs).</span></span>|  
|[<span data-ttu-id="ce925-181">Derleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="ce925-181">Build and Deploy</span></span>](building-and-deploying-wpf-applications.md)|<span data-ttu-id="ce925-182">WPF uygulamanızı derleyip dağıtmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce925-182">Describes how to build and deploy your WPF application.</span></span>|  
|[<span data-ttu-id="ce925-183">Visual Studio’da WPF’ye Giriş</span><span class="sxs-lookup"><span data-stu-id="ce925-183">Introduction to WPF in Visual Studio</span></span>](../getting-started/introduction-to-wpf-in-vs.md)|<span data-ttu-id="ce925-184">WPF 'nin ana özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce925-184">Describes the main features of WPF.</span></span>|  
|[<span data-ttu-id="ce925-185">İzlenecek Yol: İlk WPF masaüstü uygulamam</span><span class="sxs-lookup"><span data-stu-id="ce925-185">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|<span data-ttu-id="ce925-186">Sayfa gezintisi, düzen, denetimler, görüntüler, stiller ve bağlamayı kullanarak bir WPF uygulamasının nasıl oluşturulduğunu gösteren bir izlenecek yol.</span><span class="sxs-lookup"><span data-stu-id="ce925-186">A walkthrough that shows how to create a WPF application using page navigation, layout, controls, images, styles, and binding.</span></span>|
