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
ms.openlocfilehash: f9ea4acfc7ba86d3424bb11af0de685651f99c61
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796747"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="eb0a6-102">WPF İçinde URI'leri Paketleme</span><span class="sxs-lookup"><span data-stu-id="eb0a6-102">Pack URIs in WPF</span></span>

<span data-ttu-id="eb0a6-103">Windows Presentation Foundation (WPF) ' [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] de, aşağıdaki gibi çeşitli yollarla dosya tanımlamak ve yüklemek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="eb0a6-103">In Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] are used to identify and load files in many ways, including the following:</span></span>

- <span data-ttu-id="eb0a6-104">Uygulamanın ilk başladığı zaman göstermek içinöğesinibelirtme.[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb0a6-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>

- <span data-ttu-id="eb0a6-105">Görüntüler yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-105">Loading images.</span></span>

- <span data-ttu-id="eb0a6-106">Sayfalara gitme.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-106">Navigating to pages.</span></span>

- <span data-ttu-id="eb0a6-107">Yürütülebilir olmayan veri dosyaları yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-107">Loading non-executable data files.</span></span>

<span data-ttu-id="eb0a6-108">Ayrıca, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] aşağıdakiler de dahil olmak üzere çeşitli konumlardan dosyaları tanımlamak ve yüklemek için de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="eb0a6-108">Furthermore, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] can be used to identify and load files from a variety of locations, including the following:</span></span>

- <span data-ttu-id="eb0a6-109">Geçerli derleme.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-109">The current assembly.</span></span>

- <span data-ttu-id="eb0a6-110">Başvurulan bir derleme.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-110">A referenced assembly.</span></span>

- <span data-ttu-id="eb0a6-111">Bir derlemeye göre bir konum.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-111">A location relative to an assembly.</span></span>

- <span data-ttu-id="eb0a6-112">Uygulamanın kaynak sitesi.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-112">The application's site of origin.</span></span>

<span data-ttu-id="eb0a6-113">Bu konumlardan bu dosya türlerini tanımlamaya ve yüklemeye yönelik tutarlı bir mekanizma sağlamak için, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] *paket URI düzeninin*genişletilebilirliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="eb0a6-114">Bu konu, şemaya genel bir bakış sunar, çeşitli senaryolar [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] için paketin nasıl oluşturulacağını ele alır, her iki biçimlendirmeden da Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 'in [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] nasıl [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] kullanılacağını göstermeden önce mutlak ve göreli ve çözünürlüğe sahiptir ve kod.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-114">This topic provides an overview of the scheme, covers how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for a variety of scenarios, discusses absolute and relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] and [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution, before showing how to use pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] from both markup and code.</span></span>

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a><span data-ttu-id="eb0a6-115">Paket URI şeması</span><span class="sxs-lookup"><span data-stu-id="eb0a6-115">The Pack URI Scheme</span></span>

<span data-ttu-id="eb0a6-116">Paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] şeması, içeriği düzenlemek ve tanımlamak için bir model tanımlayan [Açık paketleme kuralları](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) belirtimi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-116">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme is used by the [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="eb0a6-117">Bu modelin anahtar öğeleri, bir *paketin* bir veya daha fazla mantıksal *bölüm*için mantıksal bir kapsayıcı olduğu paket ve parçalardır.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="eb0a6-118">Aşağıdaki şekil bu kavramı gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-118">The following figure illustrates this concept.</span></span>

![Paket ve parçalar diyagramı](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

<span data-ttu-id="eb0a6-120">Bileşenleri tanımlamak için OPC belirtimi, RFC 2396 ' in genişletilebilirliği kullanır (Tekdüzen Kaynak tanımlayıcıları (URI): Genel sözdizimi), paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] düzenini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme.</span></span>

<span data-ttu-id="eb0a6-121">Tarafından [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] belirtilen düzen ön eki tarafından tanımlanır; http, FTP ve File iyi bilinen örneklerdir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-121">The scheme that is specified by a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="eb0a6-122">Paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] şeması, düzeni olarak "Pack" kullanır ve iki bileşen içerir: yetkili ve yol.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-122">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="eb0a6-123">Bir paketin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]biçimi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-123">The following is the format for a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

<span data-ttu-id="eb0a6-124">Pack://*yetkilisi*/*yolu*</span><span class="sxs-lookup"><span data-stu-id="eb0a6-124">pack://*authority*/*path*</span></span>

<span data-ttu-id="eb0a6-125">*Yetkili* , bir bölümün içerdiği paketin türünü belirtir. *yol* , bir paket içindeki bir bölümün konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>

<span data-ttu-id="eb0a6-126">Bu kavram aşağıdaki şekilde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="eb0a6-126">This concept is illustrated by the following figure:</span></span>

![Paket, yetkili ve yol arasındaki ilişki](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

<span data-ttu-id="eb0a6-128">Paketler ve parçalar, uygulamalar ve dosyalarla benzerdir; burada bir uygulama (paket) bir veya daha fazla dosya (parça) içerebilir:</span><span class="sxs-lookup"><span data-stu-id="eb0a6-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>

- <span data-ttu-id="eb0a6-129">Yerel derlemeye derlenen kaynak dosyaları.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-129">Resource files that are compiled into the local assembly.</span></span>

- <span data-ttu-id="eb0a6-130">Başvurulan bir derlemeye derlenen kaynak dosyaları.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-130">Resource files that are compiled into a referenced assembly.</span></span>

- <span data-ttu-id="eb0a6-131">Başvurulan bir derlemeye derlenen kaynak dosyaları.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-131">Resource files that are compiled into a referencing assembly.</span></span>

- <span data-ttu-id="eb0a6-132">İçerik dosyaları.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-132">Content files.</span></span>

- <span data-ttu-id="eb0a6-133">Kaynak dosyalarının sitesi.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-133">Site of origin files.</span></span>

<span data-ttu-id="eb0a6-134">Bu dosya [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] türlerine erişmek için iki kaynakçayı destekler: Application:///ve siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="eb0a6-135">Application:///yetkilisi, kaynak ve içerik dosyaları dahil olmak üzere derleme zamanında bilinen uygulama verileri dosyalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="eb0a6-136">Siteoforigin:///yetkilisi, kaynak dosyalarının sitesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="eb0a6-137">Her bir yetkilinin kapsamı aşağıdaki şekilde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-137">The scope of each authority is shown in the following figure.</span></span>

![Paket URI diyagramı](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> <span data-ttu-id="eb0a6-139">Bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketin yetkili bileşeni, bir pakete işaret eden [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ve RFC 2396 ile uyumlu olması gereken bir katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-139">The authority component of a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is an embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="eb0a6-140">Ek olarak, "/" karakteri "," karakteriyle değiştirilmelidir ve "%" ve "?" gibi ayrılmış karakterlerle kaçışlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="eb0a6-141">Ayrıntılar için bkz. OPC.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-141">See the OPC for details.</span></span>

<span data-ttu-id="eb0a6-142">Aşağıdaki bölümlerde, bu iki yetkilinin kaynak [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , içerik ve kaynak dosyalarının sitesini tanımlamaya yönelik uygun yollarla birlikte nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-142">The following sections explain how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a><span data-ttu-id="eb0a6-143">Kaynak dosya paketi URI 'Leri</span><span class="sxs-lookup"><span data-stu-id="eb0a6-143">Resource File Pack URIs</span></span>

<span data-ttu-id="eb0a6-144">Kaynak dosyaları öğeler olarak [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` yapılandırılır ve derlemelere derlenir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-144">Resource files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource` items and are compiled into assemblies.</span></span> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="eb0a6-145">yerel derlemeye derlenen ya da [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] yerel derlemeden başvurulan bir derlemeye derlenen kaynak dosyalarını tanımlamak için kullanılabilen paketin oluşturulmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-145">supports the construction of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a><span data-ttu-id="eb0a6-146">Yerel derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-146">Local Assembly Resource File</span></span>

<span data-ttu-id="eb0a6-147">Yerel derlemeye [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] derlenen bir kaynak dosyası paketi şu yetkiyi ve yolu kullanır:</span><span class="sxs-lookup"><span data-stu-id="eb0a6-147">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>

- <span data-ttu-id="eb0a6-148">**Yetkili**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-148">**Authority**: application:///.</span></span>

- <span data-ttu-id="eb0a6-149">**Yol**: Kaynak dosyasının, yolu da dahil olmak üzere, yerel derleme proje klasörü köküne göreli adı.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>

<span data-ttu-id="eb0a6-150">Aşağıdaki örnek, yerel derlemenin proje [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] klasörünün kökünde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bulunan bir kaynak dosyası paketini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-150">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="eb0a6-151">Aşağıdaki örnek, yerel derlemenin proje [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] klasörünün bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] alt klasöründe bulunan bir kaynak dosyası paketini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-151">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="eb0a6-152">Başvurulan derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-152">Referenced Assembly Resource File</span></span>

<span data-ttu-id="eb0a6-153">Başvurulan bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] derlemeye derlenen bir kaynak dosyası paketi şu yetkiyi ve yolu kullanır:</span><span class="sxs-lookup"><span data-stu-id="eb0a6-153">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>

- <span data-ttu-id="eb0a6-154">**Yetkili**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-154">**Authority**: application:///.</span></span>

- <span data-ttu-id="eb0a6-155">**Yol**: Başvurulan bir derlemeye derlenen kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="eb0a6-156">Yolun aşağıdaki biçime uyması gerekir:</span><span class="sxs-lookup"><span data-stu-id="eb0a6-156">The path must conform to the following format:</span></span>

  <span data-ttu-id="eb0a6-157">*AssemblyShortName* { *; Sürüm*] { *; PublicKey*]; bileşen/*yol*</span><span class="sxs-lookup"><span data-stu-id="eb0a6-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>

  - <span data-ttu-id="eb0a6-158">**AssemblyShortName**: başvurulan derlemenin kısa adı.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>

  - <span data-ttu-id="eb0a6-159">**; Sürüm** [isteğe bağlı]: kaynak dosyasını içeren başvurulan derlemenin sürümü.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="eb0a6-160">Bu, aynı kısa ada sahip iki veya daha fazla başvurulan derleme yüklendiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="eb0a6-161">**; PublicKey** [isteğe bağlı]: başvurulan derlemeyi imzalamak için kullanılan ortak anahtar.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="eb0a6-162">Bu, aynı kısa ada sahip iki veya daha fazla başvurulan derleme yüklendiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="eb0a6-163">**; bileşen**: başvurulan derlemenin yerel derlemeden başvurulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>

  - <span data-ttu-id="eb0a6-164">**/Path**: kaynak dosyasının, yolu da dahil olmak üzere, başvurulan derlemenin proje klasörünün köküne göre adı.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>

<span data-ttu-id="eb0a6-165">Aşağıdaki örnek, başvurulan derlemenin proje [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] klasörünün kökünde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bulunan bir kaynak dosyası paketini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-165">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

<span data-ttu-id="eb0a6-166">Aşağıdaki örnek, başvurulan derlemenin proje [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] klasörünün bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] alt klasöründe bulunan bir kaynak dosyası paketini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-166">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

<span data-ttu-id="eb0a6-167">Aşağıdaki örnek, başvurulan, sürüme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] özgü derlemenin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] proje klasörünün kök klasöründe bulunan bir kaynak dosyası paketini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-167">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

<span data-ttu-id="eb0a6-168">Başvurulan derleme kaynak dosyalarının [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paket sözdiziminin yalnızca Application:///yetkilisi ile kullanılabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-168">Note that the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="eb0a6-169">Örneğin, aşağıdaki ' de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a><span data-ttu-id="eb0a6-170">İçerik dosyası paketi URI 'Leri</span><span class="sxs-lookup"><span data-stu-id="eb0a6-170">Content File Pack URIs</span></span>

<span data-ttu-id="eb0a6-171">Bir içerik [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dosyası paketi aşağıdaki yetkili ve yolu kullanır:</span><span class="sxs-lookup"><span data-stu-id="eb0a6-171">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a content file uses the following authority and path:</span></span>

- <span data-ttu-id="eb0a6-172">**Yetkili**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-172">**Authority**: application:///.</span></span>

- <span data-ttu-id="eb0a6-173">**Yol**: Uygulamanın ana yürütülebilir dosyasının dosya sistemi konumuna göreli yolu da dahil olmak üzere içerik dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>

<span data-ttu-id="eb0a6-174">Aşağıdaki örnek, çalıştırılabilir derleme ile [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] aynı klasörde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bulunan bir içerik dosyası paketini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-174">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>

`pack://application:,,,/ContentFile.xaml`

<span data-ttu-id="eb0a6-175">Aşağıdaki örnek, uygulamanın yürütülebilir derlemesine [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] göre bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] alt klasörde bulunan bir içerik dosyası paketini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-175">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> <span data-ttu-id="eb0a6-176">HTML içerik dosyalarına gidilemez.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-176">HTML content files cannot be navigated to.</span></span> <span data-ttu-id="eb0a6-177">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Düzen yalnızca kaynak sitesinde bulunan HTML dosyalarına gezinmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-177">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme only supports navigation to HTML files that are located at the site of origin.</span></span>

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="eb0a6-178">Kaynak Paketi URI 'Leri sitesi</span><span class="sxs-lookup"><span data-stu-id="eb0a6-178">Site of Origin Pack URIs</span></span>

<span data-ttu-id="eb0a6-179">Kaynak dosyanın [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bir sitesi paketi aşağıdaki yetkili ve yolu kullanır:</span><span class="sxs-lookup"><span data-stu-id="eb0a6-179">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a site of origin file uses the following authority and path:</span></span>

- <span data-ttu-id="eb0a6-180">**Yetkili**: siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-180">**Authority**: siteoforigin:///.</span></span>

- <span data-ttu-id="eb0a6-181">**Yol**: Yürütülebilir dosyanın başlatıldığı konuma göre yolu da dahil olmak üzere, kaynak dosya sitesinin adı.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>

<span data-ttu-id="eb0a6-182">Aşağıdaki örnek, çalıştırılabilir derlemenin başlatıldığı [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] konumda depolanan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir kaynak dosyası sitesinin paketini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-182">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

<span data-ttu-id="eb0a6-183">Aşağıdaki örnek, uygulamanın yürütülebilir dosyasının [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başlatıldığı konuma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] göre alt klasörde depolanan bir kaynak dosyası sitesinin paketini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-183">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a><span data-ttu-id="eb0a6-184">Sayfa dosyaları</span><span class="sxs-lookup"><span data-stu-id="eb0a6-184">Page Files</span></span>

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="eb0a6-185">öğeler olarak [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` yapılandırılan dosyalar, kaynak dosyalarla aynı şekilde derlemeler halinde derlenir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-185">files that are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="eb0a6-186">Sonuç olarak [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] , `Page` öğeler kaynak dosyaları paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kullanılarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-186">Consequently, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items can be identified using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files.</span></span>

<span data-ttu-id="eb0a6-187">Genellikle öğe olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]yapılandırılandosyatürleri kököğesiolarakaşağıdakilerdenbirinesahiptir`Page` :</span><span class="sxs-lookup"><span data-stu-id="eb0a6-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items have one of the following as their root element:</span></span>

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="eb0a6-188">Mutlak vs. Göreli paket URI 'Leri</span><span class="sxs-lookup"><span data-stu-id="eb0a6-188">Absolute vs. Relative Pack URIs</span></span>

<span data-ttu-id="eb0a6-189">Tam nitelikli paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , düzeni, yetkiyi ve yolu içerir ve mutlak bir paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-189">A fully qualified pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] includes the scheme, the authority, and the path, and it is considered an absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="eb0a6-190">Geliştiriciler için bir basitleştirme olarak, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeler genellikle yalnızca yolu içeren göreli bir paketle [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]birlikte uygun öznitelikleri ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], which includes only the path.</span></span>

<span data-ttu-id="eb0a6-191">Örneğin, yerel derlemedeki bir kaynak dosyası için [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] aşağıdaki mutlak paketi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-191">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file in the local assembly.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="eb0a6-192">Bu kaynak dosyasına [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvuran göreli paket aşağıdaki gibi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-192">The relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that refers to this resource file would be the following.</span></span>

`/ResourceFile.xaml`

> [!NOTE]
> <span data-ttu-id="eb0a6-193">Kaynak dosyalarının sitesi Derlemelerle ilişkili olmadığından, yalnızca mutlak paketle [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span></span>

<span data-ttu-id="eb0a6-194">Varsayılan olarak, göreli bir paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , başvuruyu içeren biçimlendirmenin veya kodun konumuna göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-194">By default, a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="eb0a6-195">Bununla birlikte, önde gelen ters eğik çizgi kullanılırsa, göreli paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvurusu uygulamanın köküne göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-195">If a leading backslash is used, however, the relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="eb0a6-196">Örneğin, aşağıdaki proje yapısını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-196">For example, consider the following project structure.</span></span>

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

<span data-ttu-id="eb0a6-197">Sayfa1. xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] *kök*\SubFolder\Page2.xaml 'e başvuran bir içeriyorsa, başvuru aşağıdaki göreli paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-197">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`Page2.xaml`

<span data-ttu-id="eb0a6-198">Sayfa1. xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] *kök*\ Page2.xaml 'e başvuran bir içeriyorsa, başvuru aşağıdaki göreli paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-198">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a><span data-ttu-id="eb0a6-199">Paket URI 'SI çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="eb0a6-199">Pack URI Resolution</span></span>

<span data-ttu-id="eb0a6-200">Paketin [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] biçimi, farklı dosya türleri için paketin [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] aynı görünmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-200">The format of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] makes it possible for pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for different types of files to look the same.</span></span> <span data-ttu-id="eb0a6-201">Örneğin, aşağıdaki mutlak paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-201">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`pack://application:,,,/ResourceOrContentFile.xaml`

<span data-ttu-id="eb0a6-202">Bu mutlak paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , yerel derlemedeki veya bir içerik dosyasındaki bir kaynak dosyasına başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-202">This absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="eb0a6-203">Aynı, aşağıdaki göreli [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-203">The same is true for the following relative [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`/ResourceOrContentFile.xaml`

<span data-ttu-id="eb0a6-204">Bir paketin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvurduğu dosya türünü tespit etmek için, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aşağıdaki buluşsal yöntemleri kullanarak yerel derlemelerde [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] ve içerik dosyalarında kaynak dosyaları için çözümler:</span><span class="sxs-lookup"><span data-stu-id="eb0a6-204">In order to determine the type of file that a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files in local assemblies and content files by using the following heuristics:</span></span>

1. <span data-ttu-id="eb0a6-205"><xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Paketle[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]eşleşen bir özniteliğin derleme meta verilerini araştırma.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

2. <span data-ttu-id="eb0a6-206">Öznitelik bulunursa, paketin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] yolu bir içerik dosyasına başvurur. <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute></span><span class="sxs-lookup"><span data-stu-id="eb0a6-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a content file.</span></span>

3. <span data-ttu-id="eb0a6-207"><xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Özniteliği bulunamazsa, yerel derlemeye derlenen küme kaynak dosyalarını araştırın.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>

4. <span data-ttu-id="eb0a6-208">Paketin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] yoluyla eşleşen bir kaynak dosyası bulunursa, paketin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] yolu bir kaynak dosyasına başvurur.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-208">If a resource file that matches the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a resource file.</span></span>

5. <span data-ttu-id="eb0a6-209">Kaynak bulunamazsa, dahili olarak oluşturulan <xref:System.Uri> geçersiz olur.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>

[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]<span data-ttu-id="eb0a6-210">Aşağıdaki öğesine başvuran için [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] çözümleme uygulanmaz:</span><span class="sxs-lookup"><span data-stu-id="eb0a6-210">resolution does not apply for [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that refer to the following:</span></span>

- <span data-ttu-id="eb0a6-211">Başvurulan derlemelerdeki içerik dosyaları: Bu dosya türleri tarafından [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

- <span data-ttu-id="eb0a6-212">Başvurulan derlemelerdeki gömülü dosyalar: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] bu değerler, başvurulan derlemenin `;component` ve sonekin her ikisi de dahil olduklarından benzersiz olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-212">Embedded files in referenced assemblies: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>

- <span data-ttu-id="eb0a6-213">Kaynak dosyalarının sitesi: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] siteoforigin:///yetkilisini içeren paket [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] tarafından tanımlanabilecek tek dosya olduklarından bunların benzersiz olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-213">Site of origin files: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they are the only files that can be identified by pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that contain the siteoforigin:/// authority.</span></span>

<span data-ttu-id="eb0a6-214">Paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] çözümlemenin izin verdiği bir basitleştirme, kodun kaynak ve içerik dosyalarının konumlarından çok bağımsız olmasına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-214">One simplification that pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="eb0a6-215">Örneğin, yerel derlemede bir içerik dosyası olarak yeniden yapılandırılmış bir kaynak dosyanız varsa, paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]kullanan kodla aynı şekilde kaynak paketi aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the resource remains the same, as does the code that uses the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a><span data-ttu-id="eb0a6-216">Paket URI 'Leri ile programlama</span><span class="sxs-lookup"><span data-stu-id="eb0a6-216">Programming with Pack URIs</span></span>

<span data-ttu-id="eb0a6-217">Birçok [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sınıf, paketiyle [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]birlikte ayarlanabilir özellikleri uygular, örneğin:</span><span class="sxs-lookup"><span data-stu-id="eb0a6-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including:</span></span>

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

<span data-ttu-id="eb0a6-218">Bu özellikler, hem biçimlendirmeden hem de koddan ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="eb0a6-219">Bu bölümde her ikisi için temel kurulumlarını ve ardından yaygın senaryolar örnekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="eb0a6-220">Biçimlendirmede paket URI 'Leri kullanma</span><span class="sxs-lookup"><span data-stu-id="eb0a6-220">Using Pack URIs in Markup</span></span>

<span data-ttu-id="eb0a6-221">Bir özniteliğin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] öğesi paketle [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]ayarlanarak biçimlendirme içinde bir paket belirtilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-221">A pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is specified in markup by setting the element of an attribute with the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="eb0a6-222">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="eb0a6-222">For example:</span></span>

`<element attribute="pack://application:,,,/File.xaml" />`

<span data-ttu-id="eb0a6-223">Tablo 1, biçimlendirmede belirtebileceğiniz çeşitli mutlak [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] paketi gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-223">Table 1 illustrates the various absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>

<span data-ttu-id="eb0a6-224">Tablo 1: Işaretlemede mutlak paket URI 'Leri</span><span class="sxs-lookup"><span data-stu-id="eb0a6-224">Table 1: Absolute Pack URIs in Markup</span></span>

|<span data-ttu-id="eb0a6-225">Dosya</span><span class="sxs-lookup"><span data-stu-id="eb0a6-225">File</span></span>|<span data-ttu-id="eb0a6-226">Mutlak paket[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb0a6-226">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="eb0a6-227">Kaynak dosya-yerel derleme</span><span class="sxs-lookup"><span data-stu-id="eb0a6-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|
|<span data-ttu-id="eb0a6-228">Alt klasör-yerel derlemede kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="eb0a6-229">Kaynak dosyası ile başvurulan derleme</span><span class="sxs-lookup"><span data-stu-id="eb0a6-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="eb0a6-230">Başvurulan derlemenin alt klasöründeki kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="eb0a6-231">Sürümlü başvurulan derlemede kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|<span data-ttu-id="eb0a6-232">İçerik dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|
|<span data-ttu-id="eb0a6-233">Alt klasördeki içerik dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|<span data-ttu-id="eb0a6-234">Kaynak dosyanın sitesi</span><span class="sxs-lookup"><span data-stu-id="eb0a6-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|<span data-ttu-id="eb0a6-235">Alt klasördeki kaynak dosyanın sitesi</span><span class="sxs-lookup"><span data-stu-id="eb0a6-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

<span data-ttu-id="eb0a6-236">Tablo 2 ' de, İşaretlemede [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] belirtebileceğiniz çeşitli göreli paket gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-236">Table 2 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>

<span data-ttu-id="eb0a6-237">Tablo 2: Işaretlemede göreli paket URI 'Leri</span><span class="sxs-lookup"><span data-stu-id="eb0a6-237">Table 2: Relative Pack URIs in Markup</span></span>

|<span data-ttu-id="eb0a6-238">Dosya</span><span class="sxs-lookup"><span data-stu-id="eb0a6-238">File</span></span>|<span data-ttu-id="eb0a6-239">Göreli paket[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb0a6-239">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="eb0a6-240">Yerel derlemede kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|
|<span data-ttu-id="eb0a6-241">Yerel derlemenin alt klasöründeki kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="eb0a6-242">Başvurulan derlemedeki kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="eb0a6-243">Başvurulan derlemenin alt klasöründeki kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="eb0a6-244">İçerik dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-244">Content file</span></span>|`"/ContentFile.xaml"`|
|<span data-ttu-id="eb0a6-245">Alt klasördeki içerik dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a><span data-ttu-id="eb0a6-246">Kodda paket URI 'Leri kullanma</span><span class="sxs-lookup"><span data-stu-id="eb0a6-246">Using Pack URIs in Code</span></span>

<span data-ttu-id="eb0a6-247">Sınıfı örnekleyerek ve [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] oluşturucuya bir parametre olarak geçirerek kodda bir paket belirtirsiniz. <xref:System.Uri></span><span class="sxs-lookup"><span data-stu-id="eb0a6-247">You specify a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] in code by instantiating the <xref:System.Uri> class and passing the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] as a parameter to the constructor.</span></span> <span data-ttu-id="eb0a6-248">Bu, aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-248">This is demonstrated in the following example.</span></span>

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

<span data-ttu-id="eb0a6-249">Varsayılan olarak, <xref:System.Uri> sınıfı paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] mutlak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-249">By default, the <xref:System.Uri> class considers pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to be absolute.</span></span> <span data-ttu-id="eb0a6-250">Sonuç olarak, bir <xref:System.Uri> sınıf örneği bir göreli paketle [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]oluşturulduğunda bir özel durum tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

```csharp
Uri uri = new Uri("/File.xaml");
```

<span data-ttu-id="eb0a6-251">Neyse ki, <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> <xref:System.Uri> sınıf oluşturucusunun aşırı yüklemesi, bir paketin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] mutlak ya da <xref:System.UriKind> göreli olduğunu belirtmenize izin vermek için türünde bir parametre kabul eder.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is either absolute or relative.</span></span>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

<span data-ttu-id="eb0a6-252">Yalnızca <xref:System.UriKind.Absolute> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ya <xref:System.UriKind.Relative> da belirtilen paketin bir veya diğeri olduğunu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is one or the other.</span></span> <span data-ttu-id="eb0a6-253">Kullanıcı çalışma zamanında bir paket [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] girdiğinde olduğu gibi kullanılan paketin türünü bilmiyorsanız, bunun yerine kullanın <xref:System.UriKind.RelativeOrAbsolute> .</span><span class="sxs-lookup"><span data-stu-id="eb0a6-253">If you don't know the type of pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that is used, such as when a user enters a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

<span data-ttu-id="eb0a6-254">Tablo 3 ' de kullanarak [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] <xref:System.Uri?displayProperty=nameWithType>kodda belirtebileceğiniz çeşitli göreli paket gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-254">Table 3 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="eb0a6-255">Tablo 3: Koddaki mutlak paket URI 'Leri</span><span class="sxs-lookup"><span data-stu-id="eb0a6-255">Table 3: Absolute Pack URIs in Code</span></span>

|<span data-ttu-id="eb0a6-256">Dosya</span><span class="sxs-lookup"><span data-stu-id="eb0a6-256">File</span></span>|<span data-ttu-id="eb0a6-257">Mutlak paket[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb0a6-257">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="eb0a6-258">Kaynak dosya-yerel derleme</span><span class="sxs-lookup"><span data-stu-id="eb0a6-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="eb0a6-259">Alt klasör-yerel derlemede kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="eb0a6-260">Kaynak dosyası ile başvurulan derleme</span><span class="sxs-lookup"><span data-stu-id="eb0a6-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="eb0a6-261">Başvurulan derlemenin alt klasöründeki kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="eb0a6-262">Sürümlü başvurulan derlemede kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="eb0a6-263">İçerik dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="eb0a6-264">Alt klasördeki içerik dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="eb0a6-265">Kaynak dosyanın sitesi</span><span class="sxs-lookup"><span data-stu-id="eb0a6-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="eb0a6-266">Alt klasördeki kaynak dosyanın sitesi</span><span class="sxs-lookup"><span data-stu-id="eb0a6-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

<span data-ttu-id="eb0a6-267">Tablo 4 ' te, kullanarak [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] <xref:System.Uri?displayProperty=nameWithType>kod içinde belirtebileceğiniz çeşitli göreli paket gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-267">Table 4 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="eb0a6-268">Tablo 4: Koddaki göreli paket URI 'Leri</span><span class="sxs-lookup"><span data-stu-id="eb0a6-268">Table 4: Relative Pack URIs in Code</span></span>

|<span data-ttu-id="eb0a6-269">Dosya</span><span class="sxs-lookup"><span data-stu-id="eb0a6-269">File</span></span>|<span data-ttu-id="eb0a6-270">Göreli paket[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb0a6-270">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="eb0a6-271">Kaynak dosya-yerel derleme</span><span class="sxs-lookup"><span data-stu-id="eb0a6-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="eb0a6-272">Alt klasör-yerel derlemede kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="eb0a6-273">Kaynak dosyası ile başvurulan derleme</span><span class="sxs-lookup"><span data-stu-id="eb0a6-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="eb0a6-274">Alt klasör ile başvurulan derlemede kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="eb0a6-275">İçerik dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="eb0a6-276">Alt klasördeki içerik dosyası</span><span class="sxs-lookup"><span data-stu-id="eb0a6-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="eb0a6-277">Ortak paket URI senaryoları</span><span class="sxs-lookup"><span data-stu-id="eb0a6-277">Common Pack URI Scenarios</span></span>

<span data-ttu-id="eb0a6-278">Yukarıdaki bölümlerde kaynak, içerik ve kaynak dosyalarının kaynağını [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] tanımlamak üzere paket oluşturma konusu ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-278">The preceding sections have discussed how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="eb0a6-279">' [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]De, bu kurulumlarını çeşitli yollarla kullanılır ve aşağıdaki bölümlerde birçok yaygın kullanımlar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="eb0a6-280">Uygulamanın başladığı zaman gösterilecek Kullanıcı arabirimini belirtme</span><span class="sxs-lookup"><span data-stu-id="eb0a6-280">Specifying the UI to Show When an Application Starts</span></span>

<span data-ttu-id="eb0a6-281"><xref:System.Windows.Application.StartupUri%2A>[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama başlatıldığında görüntülenecek olan ilkini belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="eb0a6-282">Tek başına uygulamalar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için, aşağıdaki örnekte gösterildiği gibi bir pencere olabilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

<span data-ttu-id="eb0a6-283">Ayrıca, aşağıdaki [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] örnekte gösterildiği gibi, tek başına uygulamalar ve ilk kullanıcı arabirimi olarak bir sayfa da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-283">Standalone applications and [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] can also specify a page as the initial UI, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

<span data-ttu-id="eb0a6-284">Uygulama tek başına bir uygulama ve bir sayfa ile <xref:System.Windows.Application.StartupUri%2A>belirtilirse, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sayfayı barındırmak için bir <xref:System.Windows.Navigation.NavigationWindow> açar.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="eb0a6-285">İçin [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], sayfa konak tarayıcısında gösterilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-285">For [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], the page is shown in the host browser.</span></span>

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a><span data-ttu-id="eb0a6-286">Bir sayfaya gitme</span><span class="sxs-lookup"><span data-stu-id="eb0a6-286">Navigating to a Page</span></span>

<span data-ttu-id="eb0a6-287">Aşağıdaki örnek, bir sayfaya nasıl gidebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-287">The following example shows how to navigate to a page.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="eb0a6-288">İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]gezinmek için çeşitli yollar hakkında daha fazla bilgi için bkz. [gezintiye genel bakış](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="eb0a6-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](navigation-overview.md).</span></span>

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a><span data-ttu-id="eb0a6-289">Pencere simgesi belirtme</span><span class="sxs-lookup"><span data-stu-id="eb0a6-289">Specifying a Window Icon</span></span>

<span data-ttu-id="eb0a6-290">Aşağıdaki örnek, bir pencerenin simgesini belirtmek için bir URI 'yi nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-290">The following example shows how to use a URI to specify a window's icon.</span></span>

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

<span data-ttu-id="eb0a6-291">Daha fazla bilgi için bkz. <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="eb0a6-292">Görüntü, ses ve video dosyaları yükleniyor</span><span class="sxs-lookup"><span data-stu-id="eb0a6-292">Loading Image, Audio, and Video Files</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="eb0a6-293">uygulamaların, aşağıdaki örneklerde gösterildiği gibi, hepsi tarafından [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]tanımlanabilecek ve yüklenebilecek çok çeşitli medya türlerini kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-293">allows applications to use a wide variety of media types, all of which can be identified and loaded with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], as shown in the following examples.</span></span>

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

<span data-ttu-id="eb0a6-294">Medya içeriğiyle çalışma hakkında daha fazla bilgi için bkz. [grafik ve multimedya](../graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="eb0a6-294">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="eb0a6-295">Kaynak sitesinden kaynak sözlüğü yükleme</span><span class="sxs-lookup"><span data-stu-id="eb0a6-295">Loading a Resource Dictionary from the Site of Origin</span></span>

<span data-ttu-id="eb0a6-296">Kaynak sözlükleri (<xref:System.Windows.ResourceDictionary>), uygulama temalarını desteklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="eb0a6-297">Temaları oluşturmanın ve yönetmenin bir yolu, uygulamanın kaynak sitesinde bulunan kaynak sözlükleri olarak birden çok tema oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="eb0a6-298">Bu, bir uygulamayı yeniden derleme ve yeniden dağıtmaya gerek kalmadan temaların eklenmesini ve güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="eb0a6-299">Bu kaynak sözlükleri, aşağıdaki örnekte gösterilen Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]kullanılarak tanımlanabilir ve yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-299">These resource dictionaries can be identified and loaded using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], which is shown in the following example.</span></span>

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

<span data-ttu-id="eb0a6-300">İçindeki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]temalara genel bakış için bkz. [Stil oluşturma ve şablon](../controls/styling-and-templating.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../controls/styling-and-templating.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb0a6-301">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb0a6-301">See also</span></span>

- [<span data-ttu-id="eb0a6-302">WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları</span><span class="sxs-lookup"><span data-stu-id="eb0a6-302">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
