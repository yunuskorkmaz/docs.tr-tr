---
title: Uygulama Geliştirme
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: b0bdf49e0bb3d9bfa3fc4e7fd94aa68ee4ea0bb3
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636399"
---
# <a name="application-development"></a><span data-ttu-id="57126-102">Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="57126-102">Application Development</span></span>
<a name="introduction"></a><span data-ttu-id="57126-103">Windows Presentation Foundation (WPF), aşağıdaki uygulama türlerini geliştirmek için kullanılabilen bir sunum çerçevesidir:</span><span class="sxs-lookup"><span data-stu-id="57126-103">Windows Presentation Foundation (WPF) is a presentation framework that can be used to develop the following types of applications:</span></span>  
  
- <span data-ttu-id="57126-104">Tek başına uygulamalar (geleneksel stil Windows uygulamaları, istemci bilgisayara yüklenmiş ve bu bilgisayardan çalıştırılan yürütülebilir derlemeler olarak oluşturulur).</span><span class="sxs-lookup"><span data-stu-id="57126-104">Standalone Applications (traditional style Windows applications built as executable assemblies that are installed to and run from the client computer).</span></span>  
  
- <span data-ttu-id="57126-105">XAML tarayıcı uygulamaları (XBAP 'ler) (yürütülebilir derlemeler olarak oluşturulan ve Microsoft Internet Explorer veya Mozilla Firefox gibi Web tarayıcıları tarafından barındırılan gezinti sayfalarından oluşan uygulamalar).</span><span class="sxs-lookup"><span data-stu-id="57126-105">XAML browser applications (XBAPs) (applications composed of navigation pages that are built as executable assemblies and hosted by Web browsers such as Microsoft Internet Explorer or Mozilla Firefox).</span></span>  
  
- <span data-ttu-id="57126-106">Özel denetim kitaplıkları (yeniden kullanılabilir denetimleri içeren yürütülebilir olmayan derlemeler).</span><span class="sxs-lookup"><span data-stu-id="57126-106">Custom Control Libraries (non-executable assemblies containing reusable controls).</span></span>  
  
- <span data-ttu-id="57126-107">Sınıf kitaplıkları (yeniden kullanılabilir sınıfları içeren yürütülebilir olmayan derlemeler).</span><span class="sxs-lookup"><span data-stu-id="57126-107">Class Libraries (non-executable assemblies that contain reusable classes).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57126-108">Windows hizmetinde WPF türlerinin kullanılması kesinlikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="57126-108">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="57126-109">Bu özellikleri bir Windows hizmetinde kullanmaya çalışırsanız, beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="57126-109">If you attempt to use these features in a Windows service, they may not work as expected.</span></span>  
  
 <span data-ttu-id="57126-110">Bu uygulama kümesini oluşturmak için WPF bir hizmet ana bilgisayarı uygular.</span><span class="sxs-lookup"><span data-stu-id="57126-110">To build this set of applications, WPF implements a host of services.</span></span> <span data-ttu-id="57126-111">Bu konuda bu hizmetlere genel bir bakış sağlanır ve daha fazla bilgi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57126-111">This topic provides an overview of these services and where to find more information.</span></span>  

<a name="Application_Management"></a>   
## <a name="application-management"></a><span data-ttu-id="57126-112">Uygulama Yönetimi</span><span class="sxs-lookup"><span data-stu-id="57126-112">Application Management</span></span>  
 <span data-ttu-id="57126-113">Yürütülebilir WPF uygulamaları, genellikle aşağıdakileri içeren bir çekirdek işlev kümesi gerektirir:</span><span class="sxs-lookup"><span data-stu-id="57126-113">Executable WPF applications commonly require a core set of functionality that includes the following:</span></span>  
  
- <span data-ttu-id="57126-114">Ortak uygulama altyapısını oluşturma ve yönetme (bir giriş noktası yöntemi ve sistem ve giriş iletilerini almak için bir Windows ileti döngüsü oluşturma dahil).</span><span class="sxs-lookup"><span data-stu-id="57126-114">Creating and managing common application infrastructure (including creating an entry point method and a Windows message loop to receive system and input messages).</span></span>  
  
- <span data-ttu-id="57126-115">Bir uygulamanın yaşam süresi ile izleme ve etkileşim kurma.</span><span class="sxs-lookup"><span data-stu-id="57126-115">Tracking and interacting with the lifetime of an application.</span></span>  
  
- <span data-ttu-id="57126-116">Komut satırı parametrelerini alma ve işleme.</span><span class="sxs-lookup"><span data-stu-id="57126-116">Retrieving and processing command-line parameters.</span></span>  
  
- <span data-ttu-id="57126-117">Uygulama kapsamı özelliklerini ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kaynaklarını paylaşma.</span><span class="sxs-lookup"><span data-stu-id="57126-117">Sharing application-scope properties and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] resources.</span></span>  
  
- <span data-ttu-id="57126-118">İşlenmeyen özel durumları algılama ve işleme.</span><span class="sxs-lookup"><span data-stu-id="57126-118">Detecting and processing unhandled exceptions.</span></span>  
  
- <span data-ttu-id="57126-119">Çıkış kodları döndürülüyor.</span><span class="sxs-lookup"><span data-stu-id="57126-119">Returning exit codes.</span></span>  
  
- <span data-ttu-id="57126-120">Windows 'ı tek başına uygulamalarda yönetme.</span><span class="sxs-lookup"><span data-stu-id="57126-120">Managing windows in standalone applications.</span></span>  
  
- <span data-ttu-id="57126-121">XAML tarayıcı uygulamalarında (XBAP) ve gezinti pencereleri ve çerçevelerle tek başına uygulamalarda gezinmeyi izleme.</span><span class="sxs-lookup"><span data-stu-id="57126-121">Tracking navigation in XAML browser applications (XBAPs), and standalone applications with navigation windows and frames.</span></span>  
  
 <span data-ttu-id="57126-122">Bu yetenekler, *uygulama tanımı*kullanarak uygulamalarınıza ekleyeceğiniz <xref:System.Windows.Application> sınıfı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="57126-122">These capabilities are implemented by the <xref:System.Windows.Application> class, which you add to your applications using an *application definition*.</span></span>  
  
 <span data-ttu-id="57126-123">Daha fazla bilgi için bkz. [uygulama yönetimine genel bakış](application-management-overview.md).</span><span class="sxs-lookup"><span data-stu-id="57126-123">For more information, see [Application Management Overview](application-management-overview.md).</span></span>  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="57126-124">WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları</span><span class="sxs-lookup"><span data-stu-id="57126-124">WPF Application Resource, Content, and Data Files</span></span>  
 <span data-ttu-id="57126-125">WPF, ekli kaynaklar için Microsoft .NET çerçevesindeki temel desteği üç tür yürütülebilir olmayan veri dosyası desteğiyle genişletir: kaynak, içerik ve veri.</span><span class="sxs-lookup"><span data-stu-id="57126-125">WPF extends the core support in the Microsoft .NET Framework for embedded resources with support for three kinds of non-executable data files: resource, content, and data.</span></span> <span data-ttu-id="57126-126">Daha fazla bilgi için bkz. [WPF uygulama kaynağı, içerik ve veri dosyaları](wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="57126-126">For more information, see [WPF Application Resource, Content, and Data Files](wpf-application-resource-content-and-data-files.md).</span></span>  
  
 <span data-ttu-id="57126-127">WPF yürütülebilir olmayan veri dosyaları desteğinin temel bileşeni, benzersiz bir URI kullanarak bunları belirleyip yükleyebilme olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="57126-127">A key component of the support for WPF non-executable data files is the ability to identify and load them using a unique URI.</span></span> <span data-ttu-id="57126-128">Daha fazla bilgi için bkz. [WPF 'de paket URI 'leri](pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="57126-128">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a><span data-ttu-id="57126-129">Pencereler ve Iletişim kutuları</span><span class="sxs-lookup"><span data-stu-id="57126-129">Windows and Dialog Boxes</span></span>  
 <span data-ttu-id="57126-130">Kullanıcılar Windows aracılığıyla WPF tek başına uygulamalarıyla etkileşime geçer.</span><span class="sxs-lookup"><span data-stu-id="57126-130">Users interact with WPF standalone applications through windows.</span></span> <span data-ttu-id="57126-131">Bir pencerenin amacı, uygulama içeriğini barındırmak ve genellikle kullanıcıların içerikle etkileşime geçmesini sağlayan uygulama işlevlerini kullanıma sunmasıdır.</span><span class="sxs-lookup"><span data-stu-id="57126-131">The purpose of a window is to host application content and expose application functionality that usually allows users to interact with the content.</span></span> <span data-ttu-id="57126-132">WPF 'de, Windows şunları destekleyen <xref:System.Windows.Window> sınıfıyla kapsüllenir:</span><span class="sxs-lookup"><span data-stu-id="57126-132">In WPF, windows are encapsulated by the <xref:System.Windows.Window> class, which supports:</span></span>  
  
- <span data-ttu-id="57126-133">Windows oluşturuluyor ve gösteriliyor.</span><span class="sxs-lookup"><span data-stu-id="57126-133">Creating and showing windows.</span></span>  
  
- <span data-ttu-id="57126-134">Sahip/sahip pencere ilişkileri oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="57126-134">Establishing owner/owned window relationships.</span></span>  
  
- <span data-ttu-id="57126-135">Pencere görünümünü yapılandırma (örneğin, boyut, konum, simgeler, başlık çubuğu metni, kenarlık).</span><span class="sxs-lookup"><span data-stu-id="57126-135">Configuring window appearance (for example, size, location, icons, title bar text, border).</span></span>  
  
- <span data-ttu-id="57126-136">Bir pencerenin ömrü ile izleme ve etkileşim kurma.</span><span class="sxs-lookup"><span data-stu-id="57126-136">Tracking and interacting with the lifetime of a window.</span></span>  
  
 <span data-ttu-id="57126-137">Daha fazla bilgi için bkz. [WPF Windows 'A genel bakış](wpf-windows-overview.md).</span><span class="sxs-lookup"><span data-stu-id="57126-137">For more information, see [WPF Windows Overview](wpf-windows-overview.md).</span></span>  
  
 <span data-ttu-id="57126-138"><xref:System.Windows.Window>, iletişim kutusu olarak bilinen özel bir pencere türü oluşturma yeteneğini destekler.</span><span class="sxs-lookup"><span data-stu-id="57126-138"><xref:System.Windows.Window> supports the ability to create a special type of window known as a dialog box.</span></span> <span data-ttu-id="57126-139">Hem kalıcı hem de kalıcı olmayan iletişim kutusu türleri oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="57126-139">Both modal and modeless types of dialog boxes can be created.</span></span>  
  
 <span data-ttu-id="57126-140">WPF, daha kolay ve uygulamalar arasında tutarlı bir kullanıcı deneyimi sağlamak için, yaygın Windows iletişim kutularından üçünü kullanıma sunar: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>ve <xref:System.Windows.Controls.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="57126-140">For convenience, and the benefits of reusability and a consistent user experience across applications, WPF exposes three of the common Windows dialog boxes: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, and <xref:System.Windows.Controls.PrintDialog>.</span></span>  
  
 <span data-ttu-id="57126-141">İleti kutusu, kullanıcılara önemli metin bilgileri göstermek ve basit Evet/Hayır/Tamam/Iptal soruları sormak için özel bir iletişim kutusu türüdür.</span><span class="sxs-lookup"><span data-stu-id="57126-141">A message box is a special type of dialog box for showing important textual information to users, and for asking simple Yes/No/OK/Cancel questions.</span></span> <span data-ttu-id="57126-142">İleti kutularını oluşturmak ve göstermek için <xref:System.Windows.MessageBox> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="57126-142">You use the <xref:System.Windows.MessageBox> class to create and show message boxes.</span></span>  
  
 <span data-ttu-id="57126-143">Daha fazla bilgi için bkz. [Iletişim kutularına genel bakış](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="57126-143">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
<a name="Navigation"></a>   
## <a name="navigation"></a><span data-ttu-id="57126-144">Gezinti</span><span class="sxs-lookup"><span data-stu-id="57126-144">Navigation</span></span>  
 <span data-ttu-id="57126-145">WPF, sayfaları (<xref:System.Windows.Controls.Page>) ve köprüleri (<xref:System.Windows.Documents.Hyperlink>) kullanarak Web stili gezintiyi destekler.</span><span class="sxs-lookup"><span data-stu-id="57126-145">WPF supports Web-style navigation using pages (<xref:System.Windows.Controls.Page>) and hyperlinks (<xref:System.Windows.Documents.Hyperlink>).</span></span> <span data-ttu-id="57126-146">Gezinti, aşağıdakiler dahil olmak üzere çeşitli yollarla uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="57126-146">Navigation can be implemented in a variety of ways that include the following:</span></span>  
  
- <span data-ttu-id="57126-147">Bir Web tarayıcısında barındırılan tek başına sayfalar.</span><span class="sxs-lookup"><span data-stu-id="57126-147">Standalone pages that are hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="57126-148">Bir Web tarayıcısında barındırılan bir XBAP 'ye derlenen sayfalar.</span><span class="sxs-lookup"><span data-stu-id="57126-148">Pages compiled into an XBAP that is hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="57126-149">Tek başına bir uygulamaya derlenen ve bir gezinti penceresi (<xref:System.Windows.Navigation.NavigationWindow>) tarafından barındırılan sayfalar.</span><span class="sxs-lookup"><span data-stu-id="57126-149">Pages compiled into a standalone application and hosted by a navigation window (<xref:System.Windows.Navigation.NavigationWindow>).</span></span>  
  
- <span data-ttu-id="57126-150">Tek başına bir sayfada veya bir XBAP ya da tek başına uygulama olarak derlenen bir sayfada barındırılan bir çerçeve (<xref:System.Windows.Controls.Frame>) tarafından barındırılan sayfalar.</span><span class="sxs-lookup"><span data-stu-id="57126-150">Pages that are hosted by a frame (<xref:System.Windows.Controls.Frame>), which may be hosted in a standalone page, or a page compiled into either an XBAP or a standalone application.</span></span>  
  
 <span data-ttu-id="57126-151">Gezintiyi kolaylaştırmak için WPF aşağıdakileri uygular:</span><span class="sxs-lookup"><span data-stu-id="57126-151">To facilitate navigation, WPF implements the following:</span></span>  
  
- <span data-ttu-id="57126-152"><xref:System.Windows.Navigation.NavigationService>, <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>ve XBAP 'ler tarafından uygulama içi gezintiyi desteklemek için kullanılan gezinti isteklerini işlemeye yönelik paylaşılan gezinti motoru.</span><span class="sxs-lookup"><span data-stu-id="57126-152"><xref:System.Windows.Navigation.NavigationService>, the shared navigation engine for processing navigation requests that is used by <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, and XBAPs to support intra-application navigation.</span></span>  
  
- <span data-ttu-id="57126-153">Gezinmeyi başlatmak için gezinti yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="57126-153">Navigation methods to initiate navigation.</span></span>  
  
- <span data-ttu-id="57126-154">Gezinti ömrünü izlemek ve bunlarla etkileşime geçmek için gezinti olayları.</span><span class="sxs-lookup"><span data-stu-id="57126-154">Navigation events to track and interact with navigation lifetime.</span></span>  
  
- <span data-ttu-id="57126-155">Bir günlük kullanarak geri ve ileri gezinmesini hatırlayıp, aynı zamanda incelenebilir ve işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="57126-155">Remembering back and forward navigation using a journal, which can also be inspected and manipulated.</span></span>  
  
 <span data-ttu-id="57126-156">Daha fazla bilgi için bkz. [gezintiye genel bakış](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="57126-156">For information, see [Navigation Overview](navigation-overview.md).</span></span>  
  
 <span data-ttu-id="57126-157">WPF, yapılandırılmış gezinti olarak bilinen özel bir gezinti türünü de destekler.</span><span class="sxs-lookup"><span data-stu-id="57126-157">WPF also supports a special type of navigation known as structured navigation.</span></span> <span data-ttu-id="57126-158">Yapılandırılmış gezinti, çağırma işlevleriyle tutarlı yapılandırılmış ve öngörülebilir bir şekilde veri döndüren bir veya daha fazla sayfayı çağırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57126-158">Structured navigation can be used to call one or more pages that return data in a structured and predictable way that is consistent with calling functions.</span></span> <span data-ttu-id="57126-159">Bu özellik, [yapılandırılmış gezintiye genel bakış](structured-navigation-overview.md)bölümünde açıklanan <xref:System.Windows.Navigation.PageFunction%601> sınıfına bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="57126-159">This capability depends on the <xref:System.Windows.Navigation.PageFunction%601> class, which is described further in [Structured Navigation Overview](structured-navigation-overview.md).</span></span> <span data-ttu-id="57126-160"><xref:System.Windows.Navigation.PageFunction%601> Ayrıca, [gezinti topolojilerine genel bakış](navigation-topologies-overview.md)bölümünde açıklanan karmaşık gezinti topolojileri oluşturmayı basitleştirmeye de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="57126-160"><xref:System.Windows.Navigation.PageFunction%601> also serves to simplify the creation of complex navigation topologies, which are described in [Navigation Topologies Overview](navigation-topologies-overview.md).</span></span>  
  
<a name="Hosting"></a>   
## <a name="hosting"></a><span data-ttu-id="57126-161">Barındırma</span><span class="sxs-lookup"><span data-stu-id="57126-161">Hosting</span></span>  
 <span data-ttu-id="57126-162">XBAP 'ler, Microsoft Internet Explorer veya Firefox içinde barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="57126-162">XBAPs can be hosted in Microsoft Internet Explorer or Firefox.</span></span> <span data-ttu-id="57126-163">Her barındırma modelinin, [barındırma](hosting-wpf-applications.md)kapsamında yer alan kendi konuları ve kısıtlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="57126-163">Each hosting model has its own set of considerations and constraints that are covered in [Hosting](hosting-wpf-applications.md).</span></span>  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a><span data-ttu-id="57126-164">Yapılandırma ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="57126-164">Build and Deploy</span></span>  
 <span data-ttu-id="57126-165">Basit WPF uygulamaları komut satırı derleyicileri kullanılarak bir komut isteminden oluşturulabilir, ancak WPF geliştirme ve oluşturma sürecini basitleştirerek ek destek sağlamak için Visual Studio ile tümleşir.</span><span class="sxs-lookup"><span data-stu-id="57126-165">Although simple WPF applications can be built from a command prompt using command-line compilers, WPF integrates with Visual Studio to provide additional support that simplified the development and build process.</span></span> <span data-ttu-id="57126-166">Daha fazla bilgi için bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="57126-166">For more information, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="57126-167">Oluşturduğunuz uygulamanın türüne bağlı olarak, aralarından seçim yapabileceğiniz bir veya daha fazla dağıtım seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="57126-167">Depending on the type of application you build, there are one or more deployment options to choose from.</span></span> <span data-ttu-id="57126-168">Daha fazla bilgi için bkz. [WPF uygulaması dağıtma](deploying-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="57126-168">For more information, see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="57126-169">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="57126-169">Related Topics</span></span>  
  
|<span data-ttu-id="57126-170">Başlık</span><span class="sxs-lookup"><span data-stu-id="57126-170">Title</span></span>|<span data-ttu-id="57126-171">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57126-171">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="57126-172">Uygulama Yönetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="57126-172">Application Management Overview</span></span>](application-management-overview.md)|<span data-ttu-id="57126-173">Uygulama yaşam süresi, Windows, uygulama kaynakları ve gezinmeyi yönetme dahil <xref:System.Windows.Application> sınıfına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="57126-173">Provides an overview of the <xref:System.Windows.Application> class including managing application lifetime, windows, application resources, and navigation.</span></span>|  
|[<span data-ttu-id="57126-174">WPF’de Windows</span><span class="sxs-lookup"><span data-stu-id="57126-174">Windows in WPF</span></span>](windows-in-wpf-applications.md)|<span data-ttu-id="57126-175">Uygulamanızda, <xref:System.Windows.Window> sınıfı ve iletişim kutularının kullanımı dahil olmak üzere yönetme hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="57126-175">Provides details of managing windows in your application including how to use the <xref:System.Windows.Window> class and dialog boxes.</span></span>|  
|[<span data-ttu-id="57126-176">Gezintiye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="57126-176">Navigation Overview</span></span>](navigation-overview.md)|<span data-ttu-id="57126-177">Uygulamanızın sayfaları arasında gezinmeyi yönetmeye ilişkin bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="57126-177">Provides an overview of managing navigation between pages of your application.</span></span>|  
|[<span data-ttu-id="57126-178">Barındırma</span><span class="sxs-lookup"><span data-stu-id="57126-178">Hosting</span></span>](hosting-wpf-applications.md)|<span data-ttu-id="57126-179">XAML tarayıcı uygulamalarına (XBAP 'ler) genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="57126-179">Provides an overview of XAML browser applications (XBAPs).</span></span>|  
|[<span data-ttu-id="57126-180">Derleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="57126-180">Build and Deploy</span></span>](building-and-deploying-wpf-applications.md)|<span data-ttu-id="57126-181">WPF uygulamanızı derleyip dağıtmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="57126-181">Describes how to build and deploy your WPF application.</span></span>|  
|[<span data-ttu-id="57126-182">Visual Studio’da WPF’ye Giriş</span><span class="sxs-lookup"><span data-stu-id="57126-182">Introduction to WPF in Visual Studio</span></span>](../getting-started/introduction-to-wpf-in-vs.md)|<span data-ttu-id="57126-183">WPF 'nin ana özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="57126-183">Describes the main features of WPF.</span></span>|  
|[<span data-ttu-id="57126-184">İzlenecek Yol: İlk WPF masaüstü uygulamam</span><span class="sxs-lookup"><span data-stu-id="57126-184">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|<span data-ttu-id="57126-185">Sayfa gezintisi, düzen, denetimler, görüntüler, stiller ve bağlamayı kullanarak bir WPF uygulamasının nasıl oluşturulduğunu gösteren bir izlenecek yol.</span><span class="sxs-lookup"><span data-stu-id="57126-185">A walkthrough that shows how to create a WPF application using page navigation, layout, controls, images, styles, and binding.</span></span>|
