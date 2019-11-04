---
title: WPF İçinde URI'leri Paketleme
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: efaf55220a41526b8952f01b8225f8336a4e8657
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459672"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="f4d36-102">WPF İçinde URI'leri Paketleme</span><span class="sxs-lookup"><span data-stu-id="f4d36-102">Pack URIs in WPF</span></span>

<span data-ttu-id="f4d36-103">Windows Presentation Foundation (WPF) içinde, aşağıdaki gibi çeşitli yollarla dosya tanımlamak ve yüklemek için Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanılır:</span><span class="sxs-lookup"><span data-stu-id="f4d36-103">In Windows Presentation Foundation (WPF), uniform resource identifiers (URIs) are used to identify and load files in many ways, including the following:</span></span>

- <span data-ttu-id="f4d36-104">Bir uygulamanın ilk kez başladığı zaman gösterilecek [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] belirtme.</span><span class="sxs-lookup"><span data-stu-id="f4d36-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>

- <span data-ttu-id="f4d36-105">Görüntüler yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="f4d36-105">Loading images.</span></span>

- <span data-ttu-id="f4d36-106">Sayfalara gitme.</span><span class="sxs-lookup"><span data-stu-id="f4d36-106">Navigating to pages.</span></span>

- <span data-ttu-id="f4d36-107">Yürütülebilir olmayan veri dosyaları yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="f4d36-107">Loading non-executable data files.</span></span>

<span data-ttu-id="f4d36-108">Ayrıca, URI 'Ler aşağıdakiler de dahil olmak üzere çeşitli konumlardan dosyaları tanımlamak ve yüklemek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="f4d36-108">Furthermore, URIs can be used to identify and load files from a variety of locations, including the following:</span></span>

- <span data-ttu-id="f4d36-109">Geçerli derleme.</span><span class="sxs-lookup"><span data-stu-id="f4d36-109">The current assembly.</span></span>

- <span data-ttu-id="f4d36-110">Başvurulan bir derleme.</span><span class="sxs-lookup"><span data-stu-id="f4d36-110">A referenced assembly.</span></span>

- <span data-ttu-id="f4d36-111">Bir derlemeye göre bir konum.</span><span class="sxs-lookup"><span data-stu-id="f4d36-111">A location relative to an assembly.</span></span>

- <span data-ttu-id="f4d36-112">Uygulamanın kaynak sitesi.</span><span class="sxs-lookup"><span data-stu-id="f4d36-112">The application's site of origin.</span></span>

<span data-ttu-id="f4d36-113">Bu konumlardan bu dosya türlerini tanımlamaya ve yüklemeye yönelik tutarlı bir mekanizma sağlamak için, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] *Pack URI düzeninin*genişletilebilirliğine yararlanır.</span><span class="sxs-lookup"><span data-stu-id="f4d36-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="f4d36-114">Bu konu, şemaya genel bir bakış sağlar ve çeşitli senaryolar için paket URI 'Lerinin nasıl kullanılacağını ele alır. her iki biçimlendirme ve koddan paket URI 'Lerinin nasıl kullanılacağını göstermeden önce mutlak ve göreli URI 'Ler ve URI çözümlemesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f4d36-114">This topic provides an overview of the scheme, covers how to construct pack URIs for a variety of scenarios, discusses absolute and relative URIs and URI resolution, before showing how to use pack URIs from both markup and code.</span></span>

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a><span data-ttu-id="f4d36-115">Paket URI şeması</span><span class="sxs-lookup"><span data-stu-id="f4d36-115">The Pack URI Scheme</span></span>

<span data-ttu-id="f4d36-116">Paket URI şeması, içeriği düzenlemek ve tanımlamak için bir model tanımlayan [Açık paketleme kuralları](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) belirtimi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4d36-116">The pack URI scheme is used by the [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="f4d36-117">Bu modelin anahtar öğeleri, bir *paketin* bir veya daha fazla mantıksal *bölüm*için mantıksal bir kapsayıcı olduğu paket ve parçalardır.</span><span class="sxs-lookup"><span data-stu-id="f4d36-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="f4d36-118">Aşağıdaki şekil bu kavramı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-118">The following figure illustrates this concept.</span></span>

![Paket ve parçalar diyagramı](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

<span data-ttu-id="f4d36-120">OPC belirtimi, parçaları belirlemek için, paket URI düzenini tanımlamak üzere RFC 2396 (Tekdüzen Kaynak tanımlayıcıları (URI): genel sözdizimi) genişletilebilirliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4d36-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack URI scheme.</span></span>

<span data-ttu-id="f4d36-121">Bir URI tarafından belirtilen düzen ön eki tarafından tanımlanır; http, FTP ve dosya iyi bilinen örneklerdir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-121">The scheme that is specified by a URI is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="f4d36-122">Paket URI şeması, düzeni olarak "Pack" kullanır ve iki bileşen içerir: yetkili ve yol.</span><span class="sxs-lookup"><span data-stu-id="f4d36-122">The pack URI scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="f4d36-123">Paket URI 'sinin biçimi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-123">The following is the format for a pack URI.</span></span>

<span data-ttu-id="f4d36-124">pack://*authority* /*yolu*</span><span class="sxs-lookup"><span data-stu-id="f4d36-124">pack://*authority*/*path*</span></span>

<span data-ttu-id="f4d36-125">*Yetkili* , bir bölümün içerdiği paketin türünü belirtir. *yol* , bir paket içindeki bir bölümün konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>

<span data-ttu-id="f4d36-126">Bu kavram aşağıdaki şekilde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f4d36-126">This concept is illustrated by the following figure:</span></span>

![Paket, yetkili ve yol arasındaki ilişki](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

<span data-ttu-id="f4d36-128">Paketler ve parçalar, uygulamalar ve dosyalarla benzerdir; burada bir uygulama (paket) bir veya daha fazla dosya (parça) içerebilir:</span><span class="sxs-lookup"><span data-stu-id="f4d36-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>

- <span data-ttu-id="f4d36-129">Yerel derlemeye derlenen kaynak dosyaları.</span><span class="sxs-lookup"><span data-stu-id="f4d36-129">Resource files that are compiled into the local assembly.</span></span>

- <span data-ttu-id="f4d36-130">Başvurulan bir derlemeye derlenen kaynak dosyaları.</span><span class="sxs-lookup"><span data-stu-id="f4d36-130">Resource files that are compiled into a referenced assembly.</span></span>

- <span data-ttu-id="f4d36-131">Başvurulan bir derlemeye derlenen kaynak dosyaları.</span><span class="sxs-lookup"><span data-stu-id="f4d36-131">Resource files that are compiled into a referencing assembly.</span></span>

- <span data-ttu-id="f4d36-132">İçerik dosyaları.</span><span class="sxs-lookup"><span data-stu-id="f4d36-132">Content files.</span></span>

- <span data-ttu-id="f4d36-133">Kaynak dosyalarının sitesi.</span><span class="sxs-lookup"><span data-stu-id="f4d36-133">Site of origin files.</span></span>

<span data-ttu-id="f4d36-134">Bu dosya türlerine erişmek için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] iki kaynakçayı destekler: application:///ve siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="f4d36-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="f4d36-135">Application:///yetkilisi, kaynak ve içerik dosyaları dahil olmak üzere derleme zamanında bilinen uygulama verileri dosyalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4d36-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="f4d36-136">Siteoforigin:///yetkilisi, kaynak dosyalarının sitesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4d36-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="f4d36-137">Her bir yetkilinin kapsamı aşağıdaki şekilde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-137">The scope of each authority is shown in the following figure.</span></span>

![Paket URI diyagramı](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> <span data-ttu-id="f4d36-139">Bir paket URI 'sinin yetkili bileşeni, bir paketi işaret eden ve RFC 2396 ' e uyması gereken gömülü bir URI 'dir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-139">The authority component of a pack URI is an embedded URI that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="f4d36-140">Ek olarak, "/" karakteri "," karakteriyle değiştirilmelidir ve "%" ve "?" gibi ayrılmış karakterlerle kaçışlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4d36-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="f4d36-141">Ayrıntılar için bkz. OPC.</span><span class="sxs-lookup"><span data-stu-id="f4d36-141">See the OPC for details.</span></span>

<span data-ttu-id="f4d36-142">Aşağıdaki bölümlerde, bu iki yetkilinin kaynağını, içeriğini ve kaynak dosyalarının sitesini tanımlamaya yönelik uygun yollarla birlikte kullanarak paket URI 'Lerinin nasıl oluşturulduğu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4d36-142">The following sections explain how to construct pack URIs using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a><span data-ttu-id="f4d36-143">Kaynak dosya paketi URI 'Leri</span><span class="sxs-lookup"><span data-stu-id="f4d36-143">Resource File Pack URIs</span></span>

<span data-ttu-id="f4d36-144">Kaynak dosyaları MSBuild `Resource` öğeleri olarak yapılandırılır ve derlemelere derlenir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-144">Resource files are configured as MSBuild `Resource` items and are compiled into assemblies.</span></span> <span data-ttu-id="f4d36-145">WPF, yerel derlemeye derlenen ya da yerel derlemeden başvurulan bir derlemeye derlenen kaynak dosyalarını tanımlamak için kullanılabilen paket URI 'lerinin oluşturulmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="f4d36-145">WPF supports the construction of pack URIs that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a><span data-ttu-id="f4d36-146">Yerel derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-146">Local Assembly Resource File</span></span>

<span data-ttu-id="f4d36-147">Yerel derlemeye derlenen bir kaynak dosyası için paket URI 'SI aşağıdaki yetkiyi ve yolu kullanır:</span><span class="sxs-lookup"><span data-stu-id="f4d36-147">The pack URI for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>

- <span data-ttu-id="f4d36-148">**Yetkili**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="f4d36-148">**Authority**: application:///.</span></span>

- <span data-ttu-id="f4d36-149">**Yol**: kaynak dosyanın, yolu da dahil olmak üzere yerel derleme proje klasörü köküne göreli adı.</span><span class="sxs-lookup"><span data-stu-id="f4d36-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>

<span data-ttu-id="f4d36-150">Aşağıdaki örnek, yerel derlemenin proje klasörünün kökünde bulunan bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kaynak dosyası için paket URI 'sini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-150">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="f4d36-151">Aşağıdaki örnek, yerel derlemenin proje klasörünün bir alt klasöründe bulunan bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kaynak dosyası için paket URI 'sini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-151">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="f4d36-152">Başvurulan derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-152">Referenced Assembly Resource File</span></span>

<span data-ttu-id="f4d36-153">Başvurulan bir derlemeye derlenen bir kaynak dosyası için paket URI 'SI aşağıdaki yetkiyi ve yolu kullanır:</span><span class="sxs-lookup"><span data-stu-id="f4d36-153">The pack URI for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>

- <span data-ttu-id="f4d36-154">**Yetkili**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="f4d36-154">**Authority**: application:///.</span></span>

- <span data-ttu-id="f4d36-155">**Yol**: başvurulan bir derlemeye derlenen kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="f4d36-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="f4d36-156">Yolun aşağıdaki biçime uyması gerekir:</span><span class="sxs-lookup"><span data-stu-id="f4d36-156">The path must conform to the following format:</span></span>

  <span data-ttu-id="f4d36-157">*AssemblyShortName*{ *; Sürüm*] { *; PublicKey*]; bileşen/*yol*</span><span class="sxs-lookup"><span data-stu-id="f4d36-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>

  - <span data-ttu-id="f4d36-158">**AssemblyShortName**: başvurulan derlemenin kısa adı.</span><span class="sxs-lookup"><span data-stu-id="f4d36-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>

  - <span data-ttu-id="f4d36-159">**; Sürüm** [isteğe bağlı]: kaynak dosyasını içeren başvurulan derlemenin sürümü.</span><span class="sxs-lookup"><span data-stu-id="f4d36-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="f4d36-160">Bu, aynı kısa ada sahip iki veya daha fazla başvurulan derleme yüklendiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4d36-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="f4d36-161">**; PublicKey** [isteğe bağlı]: başvurulan derlemeyi imzalamak için kullanılan ortak anahtar.</span><span class="sxs-lookup"><span data-stu-id="f4d36-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="f4d36-162">Bu, aynı kısa ada sahip iki veya daha fazla başvurulan derleme yüklendiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4d36-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="f4d36-163">**; bileşen**: başvurulan derlemenin yerel derlemeden başvurulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>

  - <span data-ttu-id="f4d36-164">**/Path**: kaynak dosyasının, yolu da dahil olmak üzere, başvurulan derlemenin proje klasörünün köküne göre adı.</span><span class="sxs-lookup"><span data-stu-id="f4d36-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>

<span data-ttu-id="f4d36-165">Aşağıdaki örnek, başvurulan derlemenin proje klasörünün kökünde bulunan bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kaynak dosyası için paket URI 'sini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-165">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

<span data-ttu-id="f4d36-166">Aşağıdaki örnek, başvurulan derlemenin proje klasörünün bir alt klasöründe bulunan bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kaynak dosyası için paket URI 'sini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-166">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

<span data-ttu-id="f4d36-167">Aşağıdaki örnek, başvurulan, sürüme özgü derlemenin proje klasörünün kök klasöründe bulunan bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kaynak dosyası için paket URI 'sini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-167">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

<span data-ttu-id="f4d36-168">Başvurulan derleme kaynak dosyalarının paket URI sözdiziminin yalnızca application:///yetkilisi ile kullanılabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f4d36-168">Note that the pack URI syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="f4d36-169">Örneğin, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]içinde aşağıdakiler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f4d36-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a><span data-ttu-id="f4d36-170">İçerik dosyası paketi URI 'Leri</span><span class="sxs-lookup"><span data-stu-id="f4d36-170">Content File Pack URIs</span></span>

<span data-ttu-id="f4d36-171">Bir içerik dosyası için paket URI 'SI aşağıdaki yetkiyi ve yolu kullanır:</span><span class="sxs-lookup"><span data-stu-id="f4d36-171">The pack URI for a content file uses the following authority and path:</span></span>

- <span data-ttu-id="f4d36-172">**Yetkili**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="f4d36-172">**Authority**: application:///.</span></span>

- <span data-ttu-id="f4d36-173">**Yol**: uygulamanın ana yürütülebilir dosyasının dosya sistemi konumuna göreli yolu da dahil olmak üzere içerik dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="f4d36-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>

<span data-ttu-id="f4d36-174">Aşağıdaki örnek, çalıştırılabilir derleme ile aynı klasörde bulunan bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içerik dosyası için paket URI 'sini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-174">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>

`pack://application:,,,/ContentFile.xaml`

<span data-ttu-id="f4d36-175">Aşağıdaki örnek, uygulamanın yürütülebilir derlemesine göre bir alt klasörde bulunan bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içerik dosyası için paket URI 'sini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-175">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> <span data-ttu-id="f4d36-176">HTML içerik dosyalarına gidilemez.</span><span class="sxs-lookup"><span data-stu-id="f4d36-176">HTML content files cannot be navigated to.</span></span> <span data-ttu-id="f4d36-177">URI şeması yalnızca kaynak sitesinde bulunan HTML dosyalarına gezinmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="f4d36-177">The URI scheme only supports navigation to HTML files that are located at the site of origin.</span></span>

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="f4d36-178">Kaynak Paketi URI 'Leri sitesi</span><span class="sxs-lookup"><span data-stu-id="f4d36-178">Site of Origin Pack URIs</span></span>

<span data-ttu-id="f4d36-179">Kaynak dosyanın bir sitesi için paket URI 'SI aşağıdaki yetkiyi ve yolu kullanır:</span><span class="sxs-lookup"><span data-stu-id="f4d36-179">The pack URI for a site of origin file uses the following authority and path:</span></span>

- <span data-ttu-id="f4d36-180">**Yetkili**: siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="f4d36-180">**Authority**: siteoforigin:///.</span></span>

- <span data-ttu-id="f4d36-181">**Yol**: kaynak dosyanın, yürütülebilir derlemenin başlatıldığı konuma göre yolu da dahil olmak üzere adı.</span><span class="sxs-lookup"><span data-stu-id="f4d36-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>

<span data-ttu-id="f4d36-182">Aşağıdaki örnek, çalıştırılabilir derlemenin başlatıldığı konumda depolanan kaynak dosyanın [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sitesinin paket URI 'sini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-182">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

<span data-ttu-id="f4d36-183">Aşağıdaki örnek, uygulamasının yürütülebilir dosyasının başlatıldığı konuma göre alt klasörde depolanan bir kaynak dosyanın [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sitesinin paket URI 'sini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-183">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a><span data-ttu-id="f4d36-184">Sayfa dosyaları</span><span class="sxs-lookup"><span data-stu-id="f4d36-184">Page Files</span></span>

<span data-ttu-id="f4d36-185">MSBuild `Page` öğesi olarak yapılandırılmış XAML dosyaları, kaynak dosyalarla aynı şekilde derlemeler halinde derlenir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-185">XAML files that are configured as MSBuild `Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="f4d36-186">Sonuç olarak, MSBuild `Page` öğeleri, kaynak dosyaları için Pack URI 'Leri kullanılarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-186">Consequently, MSBuild `Page` items can be identified using pack URIs for resource files.</span></span>

<span data-ttu-id="f4d36-187">Genel olarak MSBuild`Page` öğeleri olarak yapılandırılan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya türleri, kök öğesi olarak aşağıdakilerden birine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f4d36-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as MSBuild`Page` items have one of the following as their root element:</span></span>

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="f4d36-188">Mutlak ve göreli paket URI 'Leri</span><span class="sxs-lookup"><span data-stu-id="f4d36-188">Absolute vs. Relative Pack URIs</span></span>

<span data-ttu-id="f4d36-189">Tam bir paket URI şeması, yetkiyi ve yolu içerir ve mutlak paket URI 'SI olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-189">A fully qualified pack URI includes the scheme, the authority, and the path, and it is considered an absolute pack URI.</span></span> <span data-ttu-id="f4d36-190">Geliştiriciler için basitlik, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeleri genellikle yalnızca yolu içeren göreli bir paket URI 'SI ile uygun öznitelikleri ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4d36-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack URI, which includes only the path.</span></span>

<span data-ttu-id="f4d36-191">Örneğin, yerel derlemedeki bir kaynak dosyası için aşağıdaki mutlak paket URI 'sini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="f4d36-191">For example, consider the following absolute pack URI for a resource file in the local assembly.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="f4d36-192">Bu kaynak dosyasına başvuran göreli paket URI 'SI aşağıdaki gibi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f4d36-192">The relative pack URI that refers to this resource file would be the following.</span></span>

`/ResourceFile.xaml`

> [!NOTE]
> <span data-ttu-id="f4d36-193">Kaynak dosyalarının sitesi Derlemelerle ilişkili olmadığından, yalnızca mutlak paket URI 'Leri ile başvurulabilirler.</span><span class="sxs-lookup"><span data-stu-id="f4d36-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack URIs.</span></span>

<span data-ttu-id="f4d36-194">Varsayılan olarak, göreli bir paket URI 'SI, başvuruyu içeren biçimlendirmenin veya kodun konumuna göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-194">By default, a relative pack URI is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="f4d36-195">Bununla birlikte, önde gelen ters eğik çizgi kullanılırsa, göreli paket URI başvurusu daha sonra uygulamanın köküne göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-195">If a leading backslash is used, however, the relative pack URI reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="f4d36-196">Örneğin, aşağıdaki proje yapısını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="f4d36-196">For example, consider the following project structure.</span></span>

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

<span data-ttu-id="f4d36-197">Sayfa1. xaml *kök*\Subfolder\page2.xaml 'e başvuran bir URI içeriyorsa, başvuru aşağıdaki GÖRELI paket URI 'sini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-197">If Page1.xaml contains a URI that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`Page2.xaml`

<span data-ttu-id="f4d36-198">Sayfa1. xaml, *kök*\ Page2.xaml 'e başvuran bir URI içeriyorsa, başvuru aşağıdaki GÖRELI paket URI 'sini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-198">If Page1.xaml contains a URI that references *Root*\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a><span data-ttu-id="f4d36-199">Paket URI 'SI çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="f4d36-199">Pack URI Resolution</span></span>

<span data-ttu-id="f4d36-200">Paket URI 'Leri biçimi, farklı dosya türleri için paket URI 'Lerinin aynı görünmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f4d36-200">The format of pack URIs makes it possible for pack URIs for different types of files to look the same.</span></span> <span data-ttu-id="f4d36-201">Örneğin, aşağıdaki mutlak paket URI 'sini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="f4d36-201">For example, consider the following absolute pack URI.</span></span>

`pack://application:,,,/ResourceOrContentFile.xaml`

<span data-ttu-id="f4d36-202">Bu mutlak paket URI 'SI, yerel derlemedeki veya bir içerik dosyasındaki bir kaynak dosyasına başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-202">This absolute pack URI could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="f4d36-203">Aynı, aşağıdaki göreli URI için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-203">The same is true for the following relative URI.</span></span>

`/ResourceOrContentFile.xaml`

<span data-ttu-id="f4d36-204">Bir paket URI 'sinin başvurduğu dosya türünü belirleyebilmek için, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aşağıdaki buluşsal yöntemleri kullanarak yerel derlemelerde ve içerik dosyalarındaki kaynak dosyaları için URI 'Leri çözümler:</span><span class="sxs-lookup"><span data-stu-id="f4d36-204">In order to determine the type of file that a pack URI refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves URIs for resource files in local assemblies and content files by using the following heuristics:</span></span>

1. <span data-ttu-id="f4d36-205">Paket URI 'siyle eşleşen bir <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> özniteliği için bütünleştirilmiş kod meta verilerini araştırma.</span><span class="sxs-lookup"><span data-stu-id="f4d36-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack URI.</span></span>

2. <span data-ttu-id="f4d36-206"><xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> özniteliği bulunursa, paket URI 'SI yolu bir içerik dosyası anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack URI refers to a content file.</span></span>

3. <span data-ttu-id="f4d36-207"><xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> özniteliği bulunamazsa, yerel derlemeye derlenen küme kaynak dosyalarını araştırın.</span><span class="sxs-lookup"><span data-stu-id="f4d36-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>

4. <span data-ttu-id="f4d36-208">Paket URI 'SI yoluyla eşleşen bir kaynak dosyası bulunursa, paket URI 'sinin yolu bir kaynak dosyasına başvurur.</span><span class="sxs-lookup"><span data-stu-id="f4d36-208">If a resource file that matches the path of the pack URI is found, the path of the pack URI refers to a resource file.</span></span>

5. <span data-ttu-id="f4d36-209">Kaynak bulunamazsa, dahili olarak oluşturulan <xref:System.Uri> geçersiz olur.</span><span class="sxs-lookup"><span data-stu-id="f4d36-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>

<span data-ttu-id="f4d36-210">URI çözümlemesi, aşağıdakilere başvuran URI 'Ler için uygulanmaz:</span><span class="sxs-lookup"><span data-stu-id="f4d36-210">URI resolution does not apply for URIs that refer to the following:</span></span>

- <span data-ttu-id="f4d36-211">Başvurulan derlemelerdeki içerik dosyaları: Bu dosya türleri [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f4d36-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

- <span data-ttu-id="f4d36-212">Başvurulan derlemelerdeki gömülü dosyalar: başvurulan derlemenin ve `;component` sonekin her ikisi de dahil olduklarından, bunları tanımlayan URI 'Ler benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-212">Embedded files in referenced assemblies: URIs that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>

- <span data-ttu-id="f4d36-213">Kaynak dosyalarının sitesi: siteoforigin:///yetkilisini içeren paket URI 'Leri tarafından tanımlanabilecek tek dosya olduklarından, bunları tanımlayan URI 'Ler benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-213">Site of origin files: URIs that identify them are unique because they are the only files that can be identified by pack URIs that contain the siteoforigin:/// authority.</span></span>

<span data-ttu-id="f4d36-214">Paket URI 'SI çözümlemenin izin verdiği bir basitleştirmeli, kodun kaynak ve içerik dosyalarının konumlarından bağımsız olması için kod içindir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-214">One simplification that pack URI resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="f4d36-215">Örneğin, yerel derlemede bir içerik dosyası olarak yeniden yapılandırılmış bir kaynak dosyanız varsa, paket URI 'sini kullanan kod gibi, kaynağın paket URI 'SI aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="f4d36-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack URI for the resource remains the same, as does the code that uses the pack URI.</span></span>

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a><span data-ttu-id="f4d36-216">Paket URI 'Leri ile programlama</span><span class="sxs-lookup"><span data-stu-id="f4d36-216">Programming with Pack URIs</span></span>

<span data-ttu-id="f4d36-217">Birçok [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sınıfı, paket URI 'Leri ile ayarlanabilir özellikleri uygular, örneğin:</span><span class="sxs-lookup"><span data-stu-id="f4d36-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack URIs, including:</span></span>

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

<span data-ttu-id="f4d36-218">Bu özellikler, hem biçimlendirmeden hem de koddan ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="f4d36-219">Bu bölümde her ikisi için temel kurulumlarını ve ardından yaygın senaryolar örnekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="f4d36-220">Biçimlendirmede paket URI 'Leri kullanma</span><span class="sxs-lookup"><span data-stu-id="f4d36-220">Using Pack URIs in Markup</span></span>

<span data-ttu-id="f4d36-221">Paket URI 'si olan bir özniteliğin öğesi ayarlanarak, biçimlendirmede bir paket URI 'SI belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-221">A pack URI is specified in markup by setting the element of an attribute with the pack URI.</span></span> <span data-ttu-id="f4d36-222">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f4d36-222">For example:</span></span>

`<element attribute="pack://application:,,,/File.xaml" />`

<span data-ttu-id="f4d36-223">Tablo 1 ' de, İşaretlemede belirtebileceğiniz çeşitli mutlak paket URI 'Leri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-223">Table 1 illustrates the various absolute pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="f4d36-224">Tablo 1: biçimlendirmede mutlak paket URI 'Leri</span><span class="sxs-lookup"><span data-stu-id="f4d36-224">Table 1: Absolute Pack URIs in Markup</span></span>

|<span data-ttu-id="f4d36-225">Dosya</span><span class="sxs-lookup"><span data-stu-id="f4d36-225">File</span></span>|<span data-ttu-id="f4d36-226">Mutlak paket URI 'SI</span><span class="sxs-lookup"><span data-stu-id="f4d36-226">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="f4d36-227">Kaynak dosya-yerel derleme</span><span class="sxs-lookup"><span data-stu-id="f4d36-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|
|<span data-ttu-id="f4d36-228">Alt klasör-yerel derlemede kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="f4d36-229">Kaynak dosyası ile başvurulan derleme</span><span class="sxs-lookup"><span data-stu-id="f4d36-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="f4d36-230">Başvurulan derlemenin alt klasöründeki kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="f4d36-231">Sürümlü başvurulan derlemede kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|<span data-ttu-id="f4d36-232">İçerik dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|
|<span data-ttu-id="f4d36-233">Alt klasördeki içerik dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|<span data-ttu-id="f4d36-234">Kaynak dosyanın sitesi</span><span class="sxs-lookup"><span data-stu-id="f4d36-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|<span data-ttu-id="f4d36-235">Alt klasördeki kaynak dosyanın sitesi</span><span class="sxs-lookup"><span data-stu-id="f4d36-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

<span data-ttu-id="f4d36-236">Tablo 2 ' de, biçimlendirmede belirtebileceğiniz çeşitli göreli paket URI 'Leri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-236">Table 2 illustrates the various relative pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="f4d36-237">Tablo 2: biçimlendirmede göreli paket URI 'Leri</span><span class="sxs-lookup"><span data-stu-id="f4d36-237">Table 2: Relative Pack URIs in Markup</span></span>

|<span data-ttu-id="f4d36-238">Dosya</span><span class="sxs-lookup"><span data-stu-id="f4d36-238">File</span></span>|<span data-ttu-id="f4d36-239">Göreli paket URI 'SI</span><span class="sxs-lookup"><span data-stu-id="f4d36-239">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="f4d36-240">Yerel derlemede kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|
|<span data-ttu-id="f4d36-241">Yerel derlemenin alt klasöründeki kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="f4d36-242">Başvurulan derlemedeki kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="f4d36-243">Başvurulan derlemenin alt klasöründeki kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="f4d36-244">İçerik dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-244">Content file</span></span>|`"/ContentFile.xaml"`|
|<span data-ttu-id="f4d36-245">Alt klasördeki içerik dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a><span data-ttu-id="f4d36-246">Kodda paket URI 'Leri kullanma</span><span class="sxs-lookup"><span data-stu-id="f4d36-246">Using Pack URIs in Code</span></span>

<span data-ttu-id="f4d36-247"><xref:System.Uri> sınıfını örnekleyerek ve paketi URI 'sini oluşturucuya bir parametre olarak geçirerek kodda bir paket URI 'SI belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4d36-247">You specify a pack URI in code by instantiating the <xref:System.Uri> class and passing the pack URI as a parameter to the constructor.</span></span> <span data-ttu-id="f4d36-248">Bu, aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-248">This is demonstrated in the following example.</span></span>

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

<span data-ttu-id="f4d36-249">Varsayılan olarak, <xref:System.Uri> sınıfı paket URI 'Lerinin mutlak olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="f4d36-249">By default, the <xref:System.Uri> class considers pack URIs to be absolute.</span></span> <span data-ttu-id="f4d36-250">Sonuç olarak, bir göreli paket URI 'SI ile <xref:System.Uri> sınıfının bir örneği oluşturulduğunda bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="f4d36-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack URI.</span></span>

```csharp
Uri uri = new Uri("/File.xaml");
```

<span data-ttu-id="f4d36-251">Neyse ki, <xref:System.Uri> sınıf oluşturucusunun <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> aşırı yüklemesi, bir paket URI 'sinin mutlak veya göreli olduğunu belirtmenize olanak tanımak için <xref:System.UriKind> türünde bir parametre kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f4d36-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack URI is either absolute or relative.</span></span>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

<span data-ttu-id="f4d36-252">Yalnızca <xref:System.UriKind.Absolute> veya <xref:System.UriKind.Relative>, belirtilen paket URI 'sinin bir veya başka bir değer olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack URI is one or the other.</span></span> <span data-ttu-id="f4d36-253">Bir kullanıcı çalışma zamanında bir paket URI 'SI girdiğinde olduğu gibi, kullanılan paket URI türünü bilmiyorsanız, bunun yerine <xref:System.UriKind.RelativeOrAbsolute> kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4d36-253">If you don't know the type of pack URI that is used, such as when a user enters a pack URI at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

<span data-ttu-id="f4d36-254">Tablo 3 ' <xref:System.Uri?displayProperty=nameWithType> kullanarak kodda belirtebileceğiniz çeşitli göreli paket URI 'Leri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-254">Table 3 illustrates the various relative pack URIs that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f4d36-255">Tablo 3: koddaki mutlak paket URI 'Leri</span><span class="sxs-lookup"><span data-stu-id="f4d36-255">Table 3: Absolute Pack URIs in Code</span></span>

|<span data-ttu-id="f4d36-256">Dosya</span><span class="sxs-lookup"><span data-stu-id="f4d36-256">File</span></span>|<span data-ttu-id="f4d36-257">Mutlak paket URI 'SI</span><span class="sxs-lookup"><span data-stu-id="f4d36-257">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="f4d36-258">Kaynak dosya-yerel derleme</span><span class="sxs-lookup"><span data-stu-id="f4d36-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f4d36-259">Alt klasör-yerel derlemede kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f4d36-260">Kaynak dosyası ile başvurulan derleme</span><span class="sxs-lookup"><span data-stu-id="f4d36-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f4d36-261">Başvurulan derlemenin alt klasöründeki kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f4d36-262">Sürümlü başvurulan derlemede kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f4d36-263">İçerik dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f4d36-264">Alt klasördeki içerik dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f4d36-265">Kaynak dosyanın sitesi</span><span class="sxs-lookup"><span data-stu-id="f4d36-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f4d36-266">Alt klasördeki kaynak dosyanın sitesi</span><span class="sxs-lookup"><span data-stu-id="f4d36-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

<span data-ttu-id="f4d36-267">Tablo 4 ' te <xref:System.Uri?displayProperty=nameWithType> kullanarak kodda belirtebileceğiniz çeşitli göreli paket URI 'Leri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-267">Table 4 illustrates the various relative pack URIs that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f4d36-268">Tablo 4: koddaki göreli paket URI 'Leri</span><span class="sxs-lookup"><span data-stu-id="f4d36-268">Table 4: Relative Pack URIs in Code</span></span>

|<span data-ttu-id="f4d36-269">Dosya</span><span class="sxs-lookup"><span data-stu-id="f4d36-269">File</span></span>|<span data-ttu-id="f4d36-270">Göreli paket URI 'SI</span><span class="sxs-lookup"><span data-stu-id="f4d36-270">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="f4d36-271">Kaynak dosya-yerel derleme</span><span class="sxs-lookup"><span data-stu-id="f4d36-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="f4d36-272">Alt klasör-yerel derlemede kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="f4d36-273">Kaynak dosyası ile başvurulan derleme</span><span class="sxs-lookup"><span data-stu-id="f4d36-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="f4d36-274">Alt klasör ile başvurulan derlemede kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="f4d36-275">İçerik dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="f4d36-276">Alt klasördeki içerik dosyası</span><span class="sxs-lookup"><span data-stu-id="f4d36-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="f4d36-277">Ortak paket URI senaryoları</span><span class="sxs-lookup"><span data-stu-id="f4d36-277">Common Pack URI Scenarios</span></span>

<span data-ttu-id="f4d36-278">Önceki bölümlerde kaynak, içerik ve kaynak dosyalarının kaynağını tanımlamak için paket URI 'Leri oluşturma konusu ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="f4d36-278">The preceding sections have discussed how to construct pack URIs to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="f4d36-279">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bu kurulumlarını çeşitli yollarla kullanılır ve aşağıdaki bölümlerde bazı yaygın kullanımlar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4d36-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="f4d36-280">Uygulamanın başladığı zaman gösterilecek Kullanıcı arabirimini belirtme</span><span class="sxs-lookup"><span data-stu-id="f4d36-280">Specifying the UI to Show When an Application Starts</span></span>

<span data-ttu-id="f4d36-281"><xref:System.Windows.Application.StartupUri%2A>, bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulaması başlatıldığında gösterilecek ilk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="f4d36-282">Tek başına uygulamalar için, aşağıdaki örnekte gösterildiği gibi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir pencere olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

<span data-ttu-id="f4d36-283">Tek başına uygulamalar ve XAML tarayıcı uygulamaları (XBAP 'ler), aşağıdaki örnekte gösterildiği gibi ilk kullanıcı arabirimi olarak bir sayfa da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-283">Standalone applications and XAML browser applications (XBAPs) can also specify a page as the initial UI, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

<span data-ttu-id="f4d36-284">Uygulama tek başına bir uygulamadır ve <xref:System.Windows.Application.StartupUri%2A>ile bir sayfa belirtilirse, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sayfayı barındırmak için bir <xref:System.Windows.Navigation.NavigationWindow> açar.</span><span class="sxs-lookup"><span data-stu-id="f4d36-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="f4d36-285">XBAP 'ler için, sayfa konak tarayıcısında gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-285">For XBAPs, the page is shown in the host browser.</span></span>

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a><span data-ttu-id="f4d36-286">Bir sayfaya gitme</span><span class="sxs-lookup"><span data-stu-id="f4d36-286">Navigating to a Page</span></span>

<span data-ttu-id="f4d36-287">Aşağıdaki örnek, bir sayfaya nasıl gidebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-287">The following example shows how to navigate to a page.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="f4d36-288">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]'de gezinmek için çeşitli yollar hakkında daha fazla bilgi için bkz. [gezintiye genel bakış](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f4d36-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](navigation-overview.md).</span></span>

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a><span data-ttu-id="f4d36-289">Pencere simgesi belirtme</span><span class="sxs-lookup"><span data-stu-id="f4d36-289">Specifying a Window Icon</span></span>

<span data-ttu-id="f4d36-290">Aşağıdaki örnek, bir pencerenin simgesini belirtmek için bir URI 'yi nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-290">The following example shows how to use a URI to specify a window's icon.</span></span>

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

<span data-ttu-id="f4d36-291">Daha fazla bilgi için bkz. <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="f4d36-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="f4d36-292">Görüntü, ses ve video dosyaları yükleniyor</span><span class="sxs-lookup"><span data-stu-id="f4d36-292">Loading Image, Audio, and Video Files</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="f4d36-293">, aşağıdaki örneklerde gösterildiği gibi uygulamaların hepsi, paket URI 'leriyle tanımlanabilecek ve yüklenebilecek çok çeşitli medya türlerini kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4d36-293">allows applications to use a wide variety of media types, all of which can be identified and loaded with pack URIs, as shown in the following examples.</span></span>

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

<span data-ttu-id="f4d36-294">Medya içeriğiyle çalışma hakkında daha fazla bilgi için bkz. [grafik ve multimedya](../graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="f4d36-294">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="f4d36-295">Kaynak sitesinden kaynak sözlüğü yükleme</span><span class="sxs-lookup"><span data-stu-id="f4d36-295">Loading a Resource Dictionary from the Site of Origin</span></span>

<span data-ttu-id="f4d36-296">Kaynak sözlükleri (<xref:System.Windows.ResourceDictionary>), uygulama temalarını desteklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="f4d36-297">Temaları oluşturmanın ve yönetmenin bir yolu, uygulamanın kaynak sitesinde bulunan kaynak sözlükleri olarak birden çok tema oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="f4d36-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="f4d36-298">Bu, bir uygulamayı yeniden derleme ve yeniden dağıtmaya gerek kalmadan temaların eklenmesini ve güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4d36-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="f4d36-299">Bu kaynak sözlükleri, aşağıdaki örnekte gösterilen Pack URI 'Leri kullanılarak tanımlanabilir ve yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f4d36-299">These resource dictionaries can be identified and loaded using pack URIs, which is shown in the following example.</span></span>

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

<span data-ttu-id="f4d36-300">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]temalara genel bakış için bkz. stil oluşturma [ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="f4d36-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4d36-301">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4d36-301">See also</span></span>

- [<span data-ttu-id="f4d36-302">WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları</span><span class="sxs-lookup"><span data-stu-id="f4d36-302">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
