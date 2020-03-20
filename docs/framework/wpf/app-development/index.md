---
title: Uygulama Geliştirme
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: 5ff9f58b72982f79e70b80f60c10828c3b54e5bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185997"
---
# <a name="application-development"></a><span data-ttu-id="e2e26-102">Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="e2e26-102">Application Development</span></span>
<a name="introduction"></a><span data-ttu-id="e2e26-103">Windows Sunu Temeli (WPF), aşağıdaki uygulama türlerini geliştirmek için kullanılabilecek bir sunu çerçevesidir:</span><span class="sxs-lookup"><span data-stu-id="e2e26-103">Windows Presentation Foundation (WPF) is a presentation framework that can be used to develop the following types of applications:</span></span>  
  
- <span data-ttu-id="e2e26-104">Bağımsız Uygulamalar (istemci bilgisayara yüklenen ve istemci bilgisayardan çalıştırılan yürütülebilir derlemeler olarak oluşturulmuş geleneksel stil Windows uygulamaları).</span><span class="sxs-lookup"><span data-stu-id="e2e26-104">Standalone Applications (traditional style Windows applications built as executable assemblies that are installed to and run from the client computer).</span></span>  
  
- <span data-ttu-id="e2e26-105">XAML tarayıcı uygulamaları (XBAPs) (yürütülebilir derlemeler olarak oluşturulan ve Microsoft Internet Explorer veya Mozilla Firefox gibi Web tarayıcıları tarafından barındırılan gezinti sayfalarından oluşan uygulamalar).</span><span class="sxs-lookup"><span data-stu-id="e2e26-105">XAML browser applications (XBAPs) (applications composed of navigation pages that are built as executable assemblies and hosted by Web browsers such as Microsoft Internet Explorer or Mozilla Firefox).</span></span>  
  
- <span data-ttu-id="e2e26-106">Özel Denetim Kitaplıkları (yeniden kullanılabilir denetimler içeren yürütülemez derlemeler).</span><span class="sxs-lookup"><span data-stu-id="e2e26-106">Custom Control Libraries (non-executable assemblies containing reusable controls).</span></span>  
  
- <span data-ttu-id="e2e26-107">Sınıf Kitaplıkları (yeniden kullanılabilir sınıflar içeren yürütülemeyen derlemeler).</span><span class="sxs-lookup"><span data-stu-id="e2e26-107">Class Libraries (non-executable assemblies that contain reusable classes).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2e26-108">Bir Windows hizmetinde WPF türlerinin kullanılması nın önerilmesi kuvvetle yapılır.</span><span class="sxs-lookup"><span data-stu-id="e2e26-108">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="e2e26-109">Bu özellikleri bir Windows hizmetinde kullanmaya çalışırsanız, bunlar beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e2e26-109">If you attempt to use these features in a Windows service, they may not work as expected.</span></span>  
  
 <span data-ttu-id="e2e26-110">Bu uygulama kümesini oluşturmak için WPF bir dizi hizmet uygular.</span><span class="sxs-lookup"><span data-stu-id="e2e26-110">To build this set of applications, WPF implements a host of services.</span></span> <span data-ttu-id="e2e26-111">Bu konu, bu hizmetlere genel bir bakış sağlar ve nerede daha fazla bilgi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2e26-111">This topic provides an overview of these services and where to find more information.</span></span>  

<a name="Application_Management"></a>
## <a name="application-management"></a><span data-ttu-id="e2e26-112">Uygulama Yönetimi</span><span class="sxs-lookup"><span data-stu-id="e2e26-112">Application Management</span></span>  
 <span data-ttu-id="e2e26-113">Çalıştırılabilir WPF uygulamaları genellikle aşağıdakileri içeren bir temel işlevsellik kümesi gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e2e26-113">Executable WPF applications commonly require a core set of functionality that includes the following:</span></span>  
  
- <span data-ttu-id="e2e26-114">Ortak uygulama altyapısı oluşturma ve yönetme (sistem ve giriş iletileri almak için bir giriş noktası yöntemi ve Windows ileti döngüsü oluşturma dahil).</span><span class="sxs-lookup"><span data-stu-id="e2e26-114">Creating and managing common application infrastructure (including creating an entry point method and a Windows message loop to receive system and input messages).</span></span>  
  
- <span data-ttu-id="e2e26-115">Bir uygulamanın kullanım ömrü boyunca izleme ve etkileşimde</span><span class="sxs-lookup"><span data-stu-id="e2e26-115">Tracking and interacting with the lifetime of an application.</span></span>  
  
- <span data-ttu-id="e2e26-116">Komut satırı parametrelerini alma ve işleme.</span><span class="sxs-lookup"><span data-stu-id="e2e26-116">Retrieving and processing command-line parameters.</span></span>  
  
- <span data-ttu-id="e2e26-117">Uygulama kapsamı özelliklerini [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve kaynaklarını paylaşma.</span><span class="sxs-lookup"><span data-stu-id="e2e26-117">Sharing application-scope properties and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] resources.</span></span>  
  
- <span data-ttu-id="e2e26-118">İşlenmemiş özel durumları algılama ve işleme.</span><span class="sxs-lookup"><span data-stu-id="e2e26-118">Detecting and processing unhandled exceptions.</span></span>  
  
- <span data-ttu-id="e2e26-119">Çıkış kodlarını iade ediyor.</span><span class="sxs-lookup"><span data-stu-id="e2e26-119">Returning exit codes.</span></span>  
  
- <span data-ttu-id="e2e26-120">Bağımsız uygulamalarda pencereleri yönetme.</span><span class="sxs-lookup"><span data-stu-id="e2e26-120">Managing windows in standalone applications.</span></span>  
  
- <span data-ttu-id="e2e26-121">XAML tarayıcı uygulamalarında (XBAP' lar) gezinmeyi ve navigasyon pencerelerini ve çerçevelerini içeren bağımsız uygulamaları izleme.</span><span class="sxs-lookup"><span data-stu-id="e2e26-121">Tracking navigation in XAML browser applications (XBAPs), and standalone applications with navigation windows and frames.</span></span>  
  
 <span data-ttu-id="e2e26-122">Bu özellikler, *uygulama*tanımı <xref:System.Windows.Application> kullanılarak uygulamalarınıza eklediğiniz sınıf tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e2e26-122">These capabilities are implemented by the <xref:System.Windows.Application> class, which you add to your applications using an *application definition*.</span></span>  
  
 <span data-ttu-id="e2e26-123">Daha fazla bilgi için [Uygulama Yönetimine Genel Bakış'a](application-management-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e2e26-123">For more information, see [Application Management Overview](application-management-overview.md).</span></span>  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="e2e26-124">WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları</span><span class="sxs-lookup"><span data-stu-id="e2e26-124">WPF Application Resource, Content, and Data Files</span></span>  
 <span data-ttu-id="e2e26-125">WPF, microsoft .NET Framework'deki temel desteği, yürütülemeyen üç tür veri dosyası için destek le birlikte gömülü kaynaklar için genişletir: kaynak, içerik ve veri.</span><span class="sxs-lookup"><span data-stu-id="e2e26-125">WPF extends the core support in the Microsoft .NET Framework for embedded resources with support for three kinds of non-executable data files: resource, content, and data.</span></span> <span data-ttu-id="e2e26-126">Daha fazla bilgi için [Bkz. WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları.](wpf-application-resource-content-and-data-files.md)</span><span class="sxs-lookup"><span data-stu-id="e2e26-126">For more information, see [WPF Application Resource, Content, and Data Files](wpf-application-resource-content-and-data-files.md).</span></span>  
  
 <span data-ttu-id="e2e26-127">WPF yürütülemeyen veri dosyaları için desteğin önemli bir bileşeni, bunları benzersiz bir URI kullanarak tanımlama ve yükleme yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="e2e26-127">A key component of the support for WPF non-executable data files is the ability to identify and load them using a unique URI.</span></span> <span data-ttu-id="e2e26-128">Daha fazla bilgi için [WPF'deki Paket URI'leri'ne](pack-uris-in-wpf.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e2e26-128">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a><span data-ttu-id="e2e26-129">Windows ve İletişim Kutuları</span><span class="sxs-lookup"><span data-stu-id="e2e26-129">Windows and Dialog Boxes</span></span>  
 <span data-ttu-id="e2e26-130">Kullanıcılar windows üzerinden WPF bağımsız uygulamaları ile etkileşim.</span><span class="sxs-lookup"><span data-stu-id="e2e26-130">Users interact with WPF standalone applications through windows.</span></span> <span data-ttu-id="e2e26-131">Pencerenin amacı, uygulama içeriğini barındırmak ve genellikle kullanıcıların içerikle etkileşimkurmasına olanak tanıyan uygulama işlevselliğini ortaya çıkarmaktır.</span><span class="sxs-lookup"><span data-stu-id="e2e26-131">The purpose of a window is to host application content and expose application functionality that usually allows users to interact with the content.</span></span> <span data-ttu-id="e2e26-132">WPF'de <xref:System.Windows.Window> pencereler, aşağıdakileri destekleyen sınıf tarafından kapsüllenir:</span><span class="sxs-lookup"><span data-stu-id="e2e26-132">In WPF, windows are encapsulated by the <xref:System.Windows.Window> class, which supports:</span></span>  
  
- <span data-ttu-id="e2e26-133">Pencereleroluşturma ve gösterme.</span><span class="sxs-lookup"><span data-stu-id="e2e26-133">Creating and showing windows.</span></span>  
  
- <span data-ttu-id="e2e26-134">Sahip/sahip olunan pencere ilişkilerini kurma.</span><span class="sxs-lookup"><span data-stu-id="e2e26-134">Establishing owner/owned window relationships.</span></span>  
  
- <span data-ttu-id="e2e26-135">Pencere görünümünü yapılandırma (örneğin, boyut, konum, simgeler, başlık çubuğu metni, kenarlık).</span><span class="sxs-lookup"><span data-stu-id="e2e26-135">Configuring window appearance (for example, size, location, icons, title bar text, border).</span></span>  
  
- <span data-ttu-id="e2e26-136">Bir pencerenin ömrü boyunca izleme ve etkileşim.</span><span class="sxs-lookup"><span data-stu-id="e2e26-136">Tracking and interacting with the lifetime of a window.</span></span>  
  
 <span data-ttu-id="e2e26-137">Daha fazla bilgi için Bkz. [WPF Windows Genel Bakış.](wpf-windows-overview.md)</span><span class="sxs-lookup"><span data-stu-id="e2e26-137">For more information, see [WPF Windows Overview](wpf-windows-overview.md).</span></span>  
  
 <span data-ttu-id="e2e26-138"><xref:System.Windows.Window>iletişim kutusu olarak bilinen özel bir pencere türünü oluşturma yeteneğini destekler.</span><span class="sxs-lookup"><span data-stu-id="e2e26-138"><xref:System.Windows.Window> supports the ability to create a special type of window known as a dialog box.</span></span> <span data-ttu-id="e2e26-139">Hem modal hem de modeless iletişim kutuları türleri oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="e2e26-139">Both modal and modeless types of dialog boxes can be created.</span></span>  
  
 <span data-ttu-id="e2e26-140">Kolaylık sağlamak ve yeniden kullanılabilirlik ve uygulamalar arasında tutarlı bir kullanıcı deneyiminin avantajları için WPF, <xref:Microsoft.Win32.SaveFileDialog>ortak <xref:System.Windows.Controls.PrintDialog>Windows iletişim kutularından üçünü ortaya çıkarır: <xref:Microsoft.Win32.OpenFileDialog>, ve .</span><span class="sxs-lookup"><span data-stu-id="e2e26-140">For convenience, and the benefits of reusability and a consistent user experience across applications, WPF exposes three of the common Windows dialog boxes: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, and <xref:System.Windows.Controls.PrintDialog>.</span></span>  
  
 <span data-ttu-id="e2e26-141">İleti kutusu, kullanıcılara önemli metin bilgilerini göstermek ve basit Evet/Hayır/Tamam/İptal soruları sormak için özel bir iletişim kutusu türüdür.</span><span class="sxs-lookup"><span data-stu-id="e2e26-141">A message box is a special type of dialog box for showing important textual information to users, and for asking simple Yes/No/OK/Cancel questions.</span></span> <span data-ttu-id="e2e26-142">İleti kutuları <xref:System.Windows.MessageBox> oluşturmak ve göstermek için sınıfı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e2e26-142">You use the <xref:System.Windows.MessageBox> class to create and show message boxes.</span></span>  
  
 <span data-ttu-id="e2e26-143">Daha fazla bilgi için İletişim [Kutularına Genel Bakış'a](dialog-boxes-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e2e26-143">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
<a name="Navigation"></a>
## <a name="navigation"></a><span data-ttu-id="e2e26-144">Gezinti</span><span class="sxs-lookup"><span data-stu-id="e2e26-144">Navigation</span></span>  
 <span data-ttu-id="e2e26-145">WPF, sayfaları ( )<xref:System.Windows.Controls.Page>ve köprüleri<xref:System.Windows.Documents.Hyperlink>( ) kullanarak Web tarzı gezinmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="e2e26-145">WPF supports Web-style navigation using pages (<xref:System.Windows.Controls.Page>) and hyperlinks (<xref:System.Windows.Documents.Hyperlink>).</span></span> <span data-ttu-id="e2e26-146">Gezinme aşağıdakileri içeren çeşitli şekillerde uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="e2e26-146">Navigation can be implemented in a variety of ways that include the following:</span></span>  
  
- <span data-ttu-id="e2e26-147">Web tarayıcısında barındırılan bağımsız sayfalar.</span><span class="sxs-lookup"><span data-stu-id="e2e26-147">Standalone pages that are hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="e2e26-148">Web tarayıcısında barındırılan bir XBAP'da derlenen sayfalar.</span><span class="sxs-lookup"><span data-stu-id="e2e26-148">Pages compiled into an XBAP that is hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="e2e26-149">Bağımsız bir uygulamada derlenen ve gezinti penceresi<xref:System.Windows.Navigation.NavigationWindow>tarafından barındırılan sayfalar ( ).</span><span class="sxs-lookup"><span data-stu-id="e2e26-149">Pages compiled into a standalone application and hosted by a navigation window (<xref:System.Windows.Navigation.NavigationWindow>).</span></span>  
  
- <span data-ttu-id="e2e26-150">Bağımsız bir sayfada barındırılabilen bir çerçeve (),<xref:System.Windows.Controls.Frame>veya XBAP veya bağımsız bir uygulama olarak derlenmiş bir sayfa tarafından barındırılan sayfalar.</span><span class="sxs-lookup"><span data-stu-id="e2e26-150">Pages that are hosted by a frame (<xref:System.Windows.Controls.Frame>), which may be hosted in a standalone page, or a page compiled into either an XBAP or a standalone application.</span></span>  
  
 <span data-ttu-id="e2e26-151">Gezinmeyi kolaylaştırmak için WPF aşağıdakileri uygular:</span><span class="sxs-lookup"><span data-stu-id="e2e26-151">To facilitate navigation, WPF implements the following:</span></span>  
  
- <span data-ttu-id="e2e26-152"><xref:System.Windows.Navigation.NavigationService>, uygulama içi gezinmeyi desteklemek için <xref:System.Windows.Controls.Frame>XBAP'lar <xref:System.Windows.Navigation.NavigationWindow>ve XBAP'lar tarafından kullanılan gezinti isteklerini işlemek için paylaşılan gezinti motoru.</span><span class="sxs-lookup"><span data-stu-id="e2e26-152"><xref:System.Windows.Navigation.NavigationService>, the shared navigation engine for processing navigation requests that is used by <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, and XBAPs to support intra-application navigation.</span></span>  
  
- <span data-ttu-id="e2e26-153">Gezinmeyi başlatmak için gezinme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e2e26-153">Navigation methods to initiate navigation.</span></span>  
  
- <span data-ttu-id="e2e26-154">Gezinme ömrünü izlemek ve bunlarla etkileşimde kalmak için gezinme olayları.</span><span class="sxs-lookup"><span data-stu-id="e2e26-154">Navigation events to track and interact with navigation lifetime.</span></span>  
  
- <span data-ttu-id="e2e26-155">Ayrıca denetlenebilir ve manipüle edilebilir bir günlük kullanarak ileri ve geri navigasyon hatırlama.</span><span class="sxs-lookup"><span data-stu-id="e2e26-155">Remembering back and forward navigation using a journal, which can also be inspected and manipulated.</span></span>  
  
 <span data-ttu-id="e2e26-156">Daha fazla bilgi için [Gezintiye Genel Bakış'a](navigation-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e2e26-156">For information, see [Navigation Overview](navigation-overview.md).</span></span>  
  
 <span data-ttu-id="e2e26-157">WPF ayrıca yapılandırılmış gezinti olarak bilinen özel bir gezinti türünü de destekler.</span><span class="sxs-lookup"><span data-stu-id="e2e26-157">WPF also supports a special type of navigation known as structured navigation.</span></span> <span data-ttu-id="e2e26-158">Yapılandırılmış gezinti, verileri arama işlevleriyle tutarlı yapılandırılmış ve öngörülebilir bir şekilde döndüren bir veya daha fazla sayfayı çağırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2e26-158">Structured navigation can be used to call one or more pages that return data in a structured and predictable way that is consistent with calling functions.</span></span> <span data-ttu-id="e2e26-159">Bu özellik, Yapılandırılmış <xref:System.Windows.Navigation.PageFunction%601> [Gezintiye Genel Bakış'ta](structured-navigation-overview.md)daha fazla açıklanan sınıfa bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e2e26-159">This capability depends on the <xref:System.Windows.Navigation.PageFunction%601> class, which is described further in [Structured Navigation Overview](structured-navigation-overview.md).</span></span> <span data-ttu-id="e2e26-160"><xref:System.Windows.Navigation.PageFunction%601>ayrıca [Navigasyon Topolojileri Genel Bakış](navigation-topologies-overview.md)açıklanan karmaşık navigasyon topolojileri, oluşturulmasını kolaylaştırmak için hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="e2e26-160"><xref:System.Windows.Navigation.PageFunction%601> also serves to simplify the creation of complex navigation topologies, which are described in [Navigation Topologies Overview](navigation-topologies-overview.md).</span></span>  
  
<a name="Hosting"></a>
## <a name="hosting"></a><span data-ttu-id="e2e26-161">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e2e26-161">Hosting</span></span>  
 <span data-ttu-id="e2e26-162">XBAPs Microsoft Internet Explorer veya Firefox'ta barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2e26-162">XBAPs can be hosted in Microsoft Internet Explorer or Firefox.</span></span> <span data-ttu-id="e2e26-163">Her barındırma [modeli, Barındırma](hosting-wpf-applications.md)kapsamında olan kendi değerlendirmeleri ve kısıtlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="e2e26-163">Each hosting model has its own set of considerations and constraints that are covered in [Hosting](hosting-wpf-applications.md).</span></span>  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a><span data-ttu-id="e2e26-164">Yapılandırma ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="e2e26-164">Build and Deploy</span></span>  
 <span data-ttu-id="e2e26-165">Basit WPF uygulamaları komut satırı derleyicileri kullanılarak komut isteminden oluşturulabilse de, Geliştirme ve oluşturma işlemini basitleştiren ek destek sağlamak için WPF Visual Studio ile tümleşir.</span><span class="sxs-lookup"><span data-stu-id="e2e26-165">Although simple WPF applications can be built from a command prompt using command-line compilers, WPF integrates with Visual Studio to provide additional support that simplified the development and build process.</span></span> <span data-ttu-id="e2e26-166">Daha fazla bilgi için [wpf uygulaması oluşturma](building-a-wpf-application-wpf.md)bilgisine bakın.</span><span class="sxs-lookup"><span data-stu-id="e2e26-166">For more information, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="e2e26-167">Oluşturduğunuz uygulamatürüne bağlı olarak, aralarından seçim yapabileceğiniz bir veya daha fazla dağıtım seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="e2e26-167">Depending on the type of application you build, there are one or more deployment options to choose from.</span></span> <span data-ttu-id="e2e26-168">Daha fazla bilgi için [wpf uygulaması dağıtma'ya](deploying-a-wpf-application-wpf.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e2e26-168">For more information, see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>  
  
<a name="related_topics"></a>
## <a name="related-topics"></a><span data-ttu-id="e2e26-169">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="e2e26-169">Related Topics</span></span>  
  
|<span data-ttu-id="e2e26-170">Başlık</span><span class="sxs-lookup"><span data-stu-id="e2e26-170">Title</span></span>|<span data-ttu-id="e2e26-171">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2e26-171">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e2e26-172">Uygulama Yönetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e2e26-172">Application Management Overview</span></span>](application-management-overview.md)|<span data-ttu-id="e2e26-173">Uygulama ömrü, <xref:System.Windows.Application> windows, uygulama kaynakları ve gezinmeyi yönetme dahil olmak üzere sınıfa genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2e26-173">Provides an overview of the <xref:System.Windows.Application> class including managing application lifetime, windows, application resources, and navigation.</span></span>|  
|[<span data-ttu-id="e2e26-174">WPF’de Windows</span><span class="sxs-lookup"><span data-stu-id="e2e26-174">Windows in WPF</span></span>](windows-in-wpf-applications.md)|<span data-ttu-id="e2e26-175">Uygulamanızda sınıf ve iletişim kutularının nasıl <xref:System.Windows.Window> kullanılacağı nı içeren pencereleri yönetme ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2e26-175">Provides details of managing windows in your application including how to use the <xref:System.Windows.Window> class and dialog boxes.</span></span>|  
|[<span data-ttu-id="e2e26-176">Gezintiye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e2e26-176">Navigation Overview</span></span>](navigation-overview.md)|<span data-ttu-id="e2e26-177">Uygulamanızın sayfaları arasında gezinmeyi yönetmeye genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2e26-177">Provides an overview of managing navigation between pages of your application.</span></span>|  
|[<span data-ttu-id="e2e26-178">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e2e26-178">Hosting</span></span>](hosting-wpf-applications.md)|<span data-ttu-id="e2e26-179">XAML tarayıcı uygulamalarına (XBAP) genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2e26-179">Provides an overview of XAML browser applications (XBAPs).</span></span>|  
|[<span data-ttu-id="e2e26-180">Derleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="e2e26-180">Build and Deploy</span></span>](building-and-deploying-wpf-applications.md)|<span data-ttu-id="e2e26-181">WPF uygulamanızı nasıl oluşturup dağıtılacak yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2e26-181">Describes how to build and deploy your WPF application.</span></span>|  
|[<span data-ttu-id="e2e26-182">Visual Studio’da WPF’ye Giriş</span><span class="sxs-lookup"><span data-stu-id="e2e26-182">Introduction to WPF in Visual Studio</span></span>](../getting-started/introduction-to-wpf-in-vs.md)|<span data-ttu-id="e2e26-183">WPF'nin temel özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2e26-183">Describes the main features of WPF.</span></span>|  
|[<span data-ttu-id="e2e26-184">İzlenecek Yol: İlk WPF masaüstü uygulamam</span><span class="sxs-lookup"><span data-stu-id="e2e26-184">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|<span data-ttu-id="e2e26-185">Sayfa gezintisi, düzen, denetimler, resimler, stiller ve bağlama yı kullanarak wpf uygulamasının nasıl oluşturulurulur' u gösteren bir yol için.</span><span class="sxs-lookup"><span data-stu-id="e2e26-185">A walkthrough that shows how to create a WPF application using page navigation, layout, controls, images, styles, and binding.</span></span>|
