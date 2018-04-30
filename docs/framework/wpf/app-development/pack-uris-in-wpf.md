---
title: WPF İçinde URI'leri Paketleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
caps.latest.revision: 35
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d90345f6c6e44bfdd98d2a1313a36372cdfe8b06
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="40981-102">WPF İçinde URI'leri Paketleme</span><span class="sxs-lookup"><span data-stu-id="40981-102">Pack URIs in WPF</span></span>
<span data-ttu-id="40981-103">Windows Presentation Foundation (WPF) [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] belirlemek ve aşağıdakiler dahil pek çok yolla dosyaları yüklemek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="40981-103">In Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] are used to identify and load files in many ways, including the following:</span></span>  
  
-   <span data-ttu-id="40981-104">Belirtme [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] göstermek için bir uygulamayı ilk kez başlatıldığında.</span><span class="sxs-lookup"><span data-stu-id="40981-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>  
  
-   <span data-ttu-id="40981-105">Görüntüleri yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="40981-105">Loading images.</span></span>  
  
-   <span data-ttu-id="40981-106">Sayfalara gezinme.</span><span class="sxs-lookup"><span data-stu-id="40981-106">Navigating to pages.</span></span>  
  
-   <span data-ttu-id="40981-107">Yürütülebilir olmayan veri dosyaları yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="40981-107">Loading non-executable data files.</span></span>  
  
 <span data-ttu-id="40981-108">Ayrıca, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] belirlemek ve konumları, aşağıdakiler dahil çeşitli arasından dosyaları yüklemek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="40981-108">Furthermore, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] can be used to identify and load files from a variety of locations, including the following:</span></span>  
  
-   <span data-ttu-id="40981-109">Geçerli derleme.</span><span class="sxs-lookup"><span data-stu-id="40981-109">The current assembly.</span></span>  
  
-   <span data-ttu-id="40981-110">Başvurulan bir derleme.</span><span class="sxs-lookup"><span data-stu-id="40981-110">A referenced assembly.</span></span>  
  
-   <span data-ttu-id="40981-111">Bir derleme göreli bir konum.</span><span class="sxs-lookup"><span data-stu-id="40981-111">A location relative to an assembly.</span></span>  
  
-   <span data-ttu-id="40981-112">Kaynak site uygulama.</span><span class="sxs-lookup"><span data-stu-id="40981-112">The application's site of origin.</span></span>  
  
 <span data-ttu-id="40981-113">Tutarlı bir mekanizma tanımlayan ve bu konumlardan bu tür dosyaları yükleme sağlamak için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] genişletilmesinde yararlanır *paketi URI düzeni*.</span><span class="sxs-lookup"><span data-stu-id="40981-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="40981-114">Bu konuda düzenine genel bakış sağlar, paketi oluşturmak alınmaktadır [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] çeşitli senaryolar için mutlak veya göreli anlatılmaktadır [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] ve [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketini kullanmak nasıl gösteren önce çözümleme [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] hem biçimlendirmeden ve kod.</span><span class="sxs-lookup"><span data-stu-id="40981-114">This topic provides an overview of the scheme, covers how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for a variety of scenarios, discusses absolute and relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] and [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution, before showing how to use pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] from both markup and code.</span></span>  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a><span data-ttu-id="40981-115">URI şeması paketleme</span><span class="sxs-lookup"><span data-stu-id="40981-115">The Pack URI Scheme</span></span>  
 <span data-ttu-id="40981-116">Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] şeması tarafından kullanılıyor [Open Packaging Conventions](http://go.microsoft.com/fwlink/?LinkID=71255) düzenleme ve içerik tanımlayan bir model açıklar (OPC) belirtimi.</span><span class="sxs-lookup"><span data-stu-id="40981-116">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme is used by the [Open Packaging Conventions](http://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="40981-117">Bu model önemli öğelerin paketleri ve bölümleri olan burada bir *paket* bir mantıksal bir veya daha fazla mantıksal bir kapsayıcısıdır *bölümleri*.</span><span class="sxs-lookup"><span data-stu-id="40981-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="40981-118">Aşağıdaki şekil bu kavramı gösterir.</span><span class="sxs-lookup"><span data-stu-id="40981-118">The following figure illustrates this concept.</span></span>  
  
 <span data-ttu-id="40981-119">![Paket ve bölümleri diyagramı](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")</span><span class="sxs-lookup"><span data-stu-id="40981-119">![Package and Parts diagram](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")</span></span>  
  
 <span data-ttu-id="40981-120">Bölümleri tanımlamak için RFC 2396 genişletilebilirlik OPC belirtimi yararlanır (Tekdüzen Kaynak Tanımlayıcıları (URI): genel sözdizimi) paketi tanımlamak için [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] düzeni.</span><span class="sxs-lookup"><span data-stu-id="40981-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme.</span></span>  
  
 <span data-ttu-id="40981-121">Tarafından belirtilen düzeni bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] kendi önekiyle; tanımlanan http, ftp ve dosya bilinen örnekler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="40981-121">The scheme that is specified by a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="40981-122">Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] şema "paketi" kendi şemasını kullanır ve iki bileşenleri içerir: yetkilisi ve yolu.</span><span class="sxs-lookup"><span data-stu-id="40981-122">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="40981-123">Bir paketi biçimi aşağıdaki şekildedir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40981-123">The following is the format for a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 <span data-ttu-id="40981-124">paketi: / /*yetkilisi*/*yolu*</span><span class="sxs-lookup"><span data-stu-id="40981-124">pack://*authority*/*path*</span></span>
  
 <span data-ttu-id="40981-125">*Yetkilisi* bir bölümü, içerdiği paket türünü belirtir. sırada *yolu* bir bölümü bir paket içinde konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="40981-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>  
  
 <span data-ttu-id="40981-126">Bu kavram aşağıdaki şekilde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="40981-126">This concept is illustrated by the following figure:</span></span>  
  
 <span data-ttu-id="40981-127">![Paket, yetkili ve yol arasındaki ilişkiyi](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")</span><span class="sxs-lookup"><span data-stu-id="40981-127">![Relationship among package, authority, and path](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")</span></span>  
  
 <span data-ttu-id="40981-128">Paketler ve bölümleri uygulamaları ve dosyaları, bir uygulama (paketi) dahil olmak üzere bir veya daha fazla dosyaları (parça), burada içerebilir benzer:</span><span class="sxs-lookup"><span data-stu-id="40981-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>  
  
-   <span data-ttu-id="40981-129">Yerel bütünleştirilmiş koda derlenmiş kaynak dosyaları.</span><span class="sxs-lookup"><span data-stu-id="40981-129">Resource files that are compiled into the local assembly.</span></span>  
  
-   <span data-ttu-id="40981-130">Başvurulan bütünleştirilmiş koda derlenmiş kaynak dosyaları.</span><span class="sxs-lookup"><span data-stu-id="40981-130">Resource files that are compiled into a referenced assembly.</span></span>  
  
-   <span data-ttu-id="40981-131">Başvuruda bulunan bir bütünleştirilmiş koda derlenmiş kaynak dosyaları.</span><span class="sxs-lookup"><span data-stu-id="40981-131">Resource files that are compiled into a referencing assembly.</span></span>  
  
-   <span data-ttu-id="40981-132">İçerik dosyaları.</span><span class="sxs-lookup"><span data-stu-id="40981-132">Content files.</span></span>  
  
-   <span data-ttu-id="40981-133">Kaynak dosyaları sitesi.</span><span class="sxs-lookup"><span data-stu-id="40981-133">Site of origin files.</span></span>  
  
 <span data-ttu-id="40981-134">Bu tür dosyaları, erişmek için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] iki yetkilileri destekler: uygulama: / / / ve siteoforigin: / / /.</span><span class="sxs-lookup"><span data-stu-id="40981-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="40981-135">Uygulama: / / / yetkilisi içerik ve kaynak dosyaları dahil olmak üzere derleme zamanında bilinen uygulama verileri dosyaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="40981-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="40981-136">Siteoforigin: / / / yetkilisi kaynak dosyaları sitesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="40981-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="40981-137">Her yetki kapsamını aşağıdaki çizimde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="40981-137">The scope of each authority is shown in the following figure.</span></span>  
  
 <span data-ttu-id="40981-138">![Paket URI diyagramı](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")</span><span class="sxs-lookup"><span data-stu-id="40981-138">![Pack URI diagram](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40981-139">Bir paketi yetkilisi bileşeninin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] katıştırılmış olan [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] noktalarını bir pakete ve RFC 2396 uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40981-139">The authority component of a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is an embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="40981-140">Ayrıca, "/" karakter "," karakteri ile değiştirilmelidir ve ayrılmış "%" gibi karakterler ve "?" kaçış uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40981-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="40981-141">OPC Ayrıntılar için bkz.</span><span class="sxs-lookup"><span data-stu-id="40981-141">See the OPC for details.</span></span>  
  
 <span data-ttu-id="40981-142">Aşağıdaki bölümlerde, paketi oluşturmak açıklanmaktadır [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kaynak, içerik ve kaynak dosyaları sitesi tanımlamak için bu iki yetkililerine uygun yolları ile birlikte kullanma.</span><span class="sxs-lookup"><span data-stu-id="40981-142">The following sections explain how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a><span data-ttu-id="40981-143">Kaynak dosya Pack URI</span><span class="sxs-lookup"><span data-stu-id="40981-143">Resource File Pack URIs</span></span>  
 <span data-ttu-id="40981-144">Kaynak dosyaları olarak yapılandırılmış [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` öğeleri ve derlemelerine derlenir.</span><span class="sxs-lookup"><span data-stu-id="40981-144">Resource files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource` items and are compiled into assemblies.</span></span> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="40981-145"> Paketi yapımı destekleyen [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] yerel bütünleştirilmiş koda derlenmiş ya da yerel derlemesinden başvuruda bulunulan bir bütünleştirilmiş koda derlenmiş kaynak dosyaları belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40981-145"> supports the construction of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a><span data-ttu-id="40981-146">Yerel derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-146">Local Assembly Resource File</span></span>  
 <span data-ttu-id="40981-147">Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] aşağıdaki yetkilisi ve yol için bir kaynak yerel bütünleştirilmiş koda derlenmiş dosyasını kullanır:</span><span class="sxs-lookup"><span data-stu-id="40981-147">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="40981-148">**Yetkilisi**: uygulama: / / /.</span><span class="sxs-lookup"><span data-stu-id="40981-148">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="40981-149">**Yol**: yerel derleme projesi klasörü köküne göre yolunu da içeren kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="40981-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>  
  
 <span data-ttu-id="40981-150">Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel derlemenin proje klasörünü kök dizininde bulunan kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="40981-150">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 <span data-ttu-id="40981-151">Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel derlemenin proje klasörünün alt klasöründe bulunan kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="40981-151">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="40981-152">Başvurulan derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-152">Referenced Assembly Resource File</span></span>  
 <span data-ttu-id="40981-153">Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] aşağıdaki yetkilisi ve yol için bir kaynak başvurulan bütünleştirilmiş koda derlenmiş dosyasını kullanır:</span><span class="sxs-lookup"><span data-stu-id="40981-153">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="40981-154">**Yetkilisi**: uygulama: / / /.</span><span class="sxs-lookup"><span data-stu-id="40981-154">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="40981-155">**Yol**: başvurulan bütünleştirilmiş koda derlenmiş bir kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="40981-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="40981-156">Yol aşağıdaki biçime uygun olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="40981-156">The path must conform to the following format:</span></span>  
  
     <span data-ttu-id="40981-157">*AssemblyShortName*{*; Sürüm*] {*; PublicKey*]; bileşen /*yolu*</span><span class="sxs-lookup"><span data-stu-id="40981-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>  
  
    -   <span data-ttu-id="40981-158">**AssemblyShortName**: başvurulan derlemeyi için kısa bir ad.</span><span class="sxs-lookup"><span data-stu-id="40981-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>  
  
    -   <span data-ttu-id="40981-159">**; Sürüm** [isteğe bağlı]: kaynak dosyası içeren başvurulan bütünleştirilmiş kod sürümü.</span><span class="sxs-lookup"><span data-stu-id="40981-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="40981-160">Bu, iki veya daha fazla başvurulan derlemeleri aynı kısa adı ile yüklü olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40981-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>  
  
    -   <span data-ttu-id="40981-161">**; PublicKey** [isteğe bağlı]: başvurulan derlemeyi imzalamak için kullanılan ortak anahtar.</span><span class="sxs-lookup"><span data-stu-id="40981-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="40981-162">Bu, iki veya daha fazla başvurulan derlemeleri aynı kısa adı ile yüklü olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40981-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>  
  
    -   <span data-ttu-id="40981-163">**; bileşeni**: yerel derlemesinden başvuruda bulunulan derleme başvuruluyor belirtir.</span><span class="sxs-lookup"><span data-stu-id="40981-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>  
  
    -   <span data-ttu-id="40981-164">**/ Yol**:, başvurulan derlemenin proje klasörünü kök göreli yolunu da içeren kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="40981-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>  
  
 <span data-ttu-id="40981-165">Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurulan derlemenin proje klasörünü kök dizininde bulunan kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="40981-165">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 <span data-ttu-id="40981-166">Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurulan derlemenin proje klasörünün alt klasöründe bulunan kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="40981-166">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 <span data-ttu-id="40981-167">Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurulan, sürüme özgü derlemenin proje klasörünü kök klasöründe yer alan kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="40981-167">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 <span data-ttu-id="40981-168">Unutmayın paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvurulan derleme kaynak dosyaları için sözdizimi yalnızca uygulamayla birlikte kullanılabilir: / / / yetkilisi.</span><span class="sxs-lookup"><span data-stu-id="40981-168">Note that the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="40981-169">Örneğin, aşağıdaki desteklenmeyen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40981-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a><span data-ttu-id="40981-170">İçerik dosyası Pack URI</span><span class="sxs-lookup"><span data-stu-id="40981-170">Content File Pack URIs</span></span>  
 <span data-ttu-id="40981-171">Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bir içerik dosyası aşağıdaki yetkilisi ve yolunu kullanır:</span><span class="sxs-lookup"><span data-stu-id="40981-171">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a content file uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="40981-172">**Yetkilisi**: uygulama: / / /.</span><span class="sxs-lookup"><span data-stu-id="40981-172">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="40981-173">**Yol**: dosya sistemi konumu uygulamanın ana yürütülebilir derlemenin göreli yolunu da içeren içerik dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="40981-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>  
  
 <span data-ttu-id="40981-174">Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içerik dosyası, yürütülebilir derleme ile aynı klasörde bulunur.</span><span class="sxs-lookup"><span data-stu-id="40981-174">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 <span data-ttu-id="40981-175">Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulamanın yürütülebilir derleme göreli bir alt klasöründe bulunan içeriği dosyası.</span><span class="sxs-lookup"><span data-stu-id="40981-175">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]<span data-ttu-id="40981-176"> İçerik dosyaları için erişilemeyeceğini.</span><span class="sxs-lookup"><span data-stu-id="40981-176"> content files cannot be navigated to.</span></span> <span data-ttu-id="40981-177">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Düzeni yalnızca gezinme destekler [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] kaynak sitede bulunan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="40981-177">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme only supports navigation to [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] files that are located at the site of origin.</span></span>  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="40981-178">Kaynak Paketi URI'ler site</span><span class="sxs-lookup"><span data-stu-id="40981-178">Site of Origin Pack URIs</span></span>  
 <span data-ttu-id="40981-179">Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bir kaynak sitesi için dosya aşağıdaki yetkilisi ve yolu kullanır:</span><span class="sxs-lookup"><span data-stu-id="40981-179">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a site of origin file uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="40981-180">**Yetkilisi**: siteoforigin: / / /.</span><span class="sxs-lookup"><span data-stu-id="40981-180">**Authority**: siteoforigin:///.</span></span>  
  
-   <span data-ttu-id="40981-181">**Yol**: site içinden yürütülebilir derleme başlatılmış konumu göreli yolunu da içeren kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="40981-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>  
  
 <span data-ttu-id="40981-182">Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site yürütülebilir derleme başlatıldığı konumunda depolanan kaynak dosya.</span><span class="sxs-lookup"><span data-stu-id="40981-182">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 <span data-ttu-id="40981-183">Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site uygulamanın yürütülebilir derleme başlatıldığı konumuna göre alt depolanan kaynak dosya.</span><span class="sxs-lookup"><span data-stu-id="40981-183">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a><span data-ttu-id="40981-184">Sayfa dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-184">Page Files</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="40981-185"> olarak yapılandırılmış dosyalar [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` öğeleri kaynak dosyaları aynı şekilde derlemelerine derlenir.</span><span class="sxs-lookup"><span data-stu-id="40981-185"> files that are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="40981-186">Sonuç olarak, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` öğeleri paketi kullanarak belirlenebilir [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kaynak dosyaları için.</span><span class="sxs-lookup"><span data-stu-id="40981-186">Consequently, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items can be identified using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files.</span></span>  
  
 <span data-ttu-id="40981-187">Türlerini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yaygın olarak yapılandırılmış dosyalar [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` öğeleriniz kendi kök öğesi olarak şunlardan biri:</span><span class="sxs-lookup"><span data-stu-id="40981-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items have one of the following as their root element:</span></span>  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="40981-188">Mutlak vs. Göreli Pack URI</span><span class="sxs-lookup"><span data-stu-id="40981-188">Absolute vs. Relative Pack URIs</span></span>  
 <span data-ttu-id="40981-189">Tam bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] şema, yetkili ve yol içerir ve bir mutlak paketi kabul edilen [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40981-189">A fully qualified pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] includes the scheme, the authority, and the path, and it is considered an absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="40981-190">Geliştiriciler, basitleştirme olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeleri genellikle izin göreli paketiyle uygun özniteliklere ayarlamanızı [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], yalnızca yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="40981-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], which includes only the path.</span></span>  
  
 <span data-ttu-id="40981-191">Örneğin, aşağıdaki mutlak paketi göz önünde bulundurun [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] yerel derleme kaynak dosyası için.</span><span class="sxs-lookup"><span data-stu-id="40981-191">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file in the local assembly.</span></span>  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 <span data-ttu-id="40981-192">Göreli paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bu kaynağa başvuruyor dosya, aşağıdaki olacaktır.</span><span class="sxs-lookup"><span data-stu-id="40981-192">The relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that refers to this resource file would be the following.</span></span>  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  <span data-ttu-id="40981-193">Kaynak dosyaları sitesi olmadığından derlemeler ile ilişkilendirilmiş, bunlar yalnızca mutlak paketiyle başvurulabilen [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40981-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span></span>  
  
 <span data-ttu-id="40981-194">Varsayılan olarak, göreli bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] işaretleme veya başvuru içeren kodu konumuna göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="40981-194">By default, a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="40981-195">Başında bir eğik çizgi kullanılırsa, ancak göreli paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvuru sonra uygulama kök göreli olarak kabul.</span><span class="sxs-lookup"><span data-stu-id="40981-195">If a leading backslash is used, however, the relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="40981-196">Örneğin, aşağıdaki proje yapısını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="40981-196">For example, consider the following project structure.</span></span>  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 <span data-ttu-id="40981-197">Page1.XAML içeriyorsa bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvuran *kök*\SubFolder\Page2.xaml, başvuru aşağıdaki göreli paketi kullanabilirsiniz [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40981-197">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `Page2.xaml`  
  
 <span data-ttu-id="40981-198">Page1.XAML içeriyorsa bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvuran *kök*\Page2.xaml, başvuru aşağıdaki göreli paketi kullanabilirsiniz [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40981-198">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a><span data-ttu-id="40981-199">Paketi URI çözümleme</span><span class="sxs-lookup"><span data-stu-id="40981-199">Pack URI Resolution</span></span>  
 <span data-ttu-id="40981-200">Paketi biçimi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] paketi mümkündür yapar [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] aynı aramak için dosyalarını farklı türde.</span><span class="sxs-lookup"><span data-stu-id="40981-200">The format of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] makes it is possible for pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for different types of files to look the same.</span></span> <span data-ttu-id="40981-201">Örneğin, aşağıdaki mutlak paketi göz önünde bulundurun [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40981-201">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 <span data-ttu-id="40981-202">Bu mutlak paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] yerel derlemede bir kaynak dosyası veya içerik dosyasına başvuruyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="40981-202">This absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="40981-203">Aynı için aşağıdaki göreli geçerlidir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40981-203">The same is true for the following relative [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `/ResourceOrContentFile.xaml`  
  
 <span data-ttu-id="40981-204">Belirlemek için, dosya türü, bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvurduğu, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çözümler [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] yerel derlemeler ve aşağıdaki buluşsal yöntemlerini kullanarak içerik dosyaları kaynak dosyaları:</span><span class="sxs-lookup"><span data-stu-id="40981-204">In order to determine the type of file that a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files in local assemblies and content files by using the following heuristics:</span></span>  
  
1.  <span data-ttu-id="40981-205">Derleme meta verilerini araştırma bir <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> paketi eşleşen öznitelik [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40981-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
2.  <span data-ttu-id="40981-206">Varsa <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> özniteliği bulunduğunda, yolun paketinin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] içerik dosyasına başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="40981-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a content file.</span></span>  
  
3.  <span data-ttu-id="40981-207">Varsa <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> özniteliği bulunamadı, yerel bütünleştirilmiş koda derlenmiş kümesi kaynak dosyalarını araştırma.</span><span class="sxs-lookup"><span data-stu-id="40981-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>  
  
4.  <span data-ttu-id="40981-208">Yolun paketinin eşleşen bir kaynak dosya [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bulunursa, yolun paketinin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] kaynak dosyasına başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="40981-208">If a resource file that matches the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a resource file.</span></span>  
  
5.  <span data-ttu-id="40981-209">Kaynak bulunmazsa, dahili olarak oluşturulan <xref:System.Uri> geçersiz.</span><span class="sxs-lookup"><span data-stu-id="40981-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]<span data-ttu-id="40981-210"> çözümleme için geçerli olmayan [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] aşağıdaki bakın:</span><span class="sxs-lookup"><span data-stu-id="40981-210"> resolution does not apply for [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that refer to the following:</span></span>  
  
-   <span data-ttu-id="40981-211">İçerik başvurulan derlemelerin dosyalarında: Bu dosya türlerini tarafından desteklenmeyen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40981-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>  
  
-   <span data-ttu-id="40981-212">Başvurulan derlemeleri gömülü dosyalar: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , tanımlamak bunları hem başvurulan bütünleştirilmiş kodun adını içerdiğinden benzersizdir ve `;component` soneki.</span><span class="sxs-lookup"><span data-stu-id="40981-212">Embedded files in referenced assemblies: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>  
  
-   <span data-ttu-id="40981-213">Kaynak dosyaları sitesi: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , tanımlamak bunları paketi tarafından tanımlanan yalnızca dosyaları olduklarından benzersizdir [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] siteoforigin içerir: / / / yetkilisi.</span><span class="sxs-lookup"><span data-stu-id="40981-213">Site of origin files: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they are the only files that can be identified by pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that contain the siteoforigin:/// authority.</span></span>  
  
 <span data-ttu-id="40981-214">Paketi bir basitleştirme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] çözümleme sağlar ve içerik kaynak dosyaları konumlarını biraz bağımsız olması için kodu.</span><span class="sxs-lookup"><span data-stu-id="40981-214">One simplification that pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="40981-215">Örneğin, bir içerik dosyası paketi olacak şekilde yeniden yerel derleme kaynak dosyası varsa [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketi kullanan kodu yaptığı gibi kaynak aynı kalır [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40981-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the resource remains the same, as does the code that uses the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a><span data-ttu-id="40981-216">Pack URI ile programlama</span><span class="sxs-lookup"><span data-stu-id="40981-216">Programming with Pack URIs</span></span>  
 <span data-ttu-id="40981-217">Birçok [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sınıfları uygulama paketi ayarlanabilir özellikleri [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]dahil:</span><span class="sxs-lookup"><span data-stu-id="40981-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including:</span></span>  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="40981-218">Bu özellikler, biçimlendirme ve kodun ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="40981-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="40981-219">Bu bölümde her ikisi için de temel kurulumlarını gösterir ve yaygın senaryolar örnekleri gösterilir.</span><span class="sxs-lookup"><span data-stu-id="40981-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="40981-220">Biçimlendirme Pack URI kullanma</span><span class="sxs-lookup"><span data-stu-id="40981-220">Using Pack URIs in Markup</span></span>  
 <span data-ttu-id="40981-221">Bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketi olan bir öznitelik öğesi ayarlayarak biçimlendirme içinde belirtilen [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40981-221">A pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is specified in markup by setting the element of an attribute with the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="40981-222">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="40981-222">For example:</span></span>  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 <span data-ttu-id="40981-223">Tablo 1 gösterilmektedir çeşitli mutlak paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , biçimlendirme belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40981-223">Table 1 illustrates the various absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>  
  
 <span data-ttu-id="40981-224">Tablo 1: Mutlak Pack URI biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="40981-224">Table 1: Absolute Pack URIs in Markup</span></span>  
  
|<span data-ttu-id="40981-225">Dosya</span><span class="sxs-lookup"><span data-stu-id="40981-225">File</span></span>|<span data-ttu-id="40981-226">Mutlak paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40981-226">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="40981-227">Kaynak dosya - yerel derleme</span><span class="sxs-lookup"><span data-stu-id="40981-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|  
|<span data-ttu-id="40981-228">Alt - yerel derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="40981-229">Kaynak dosya - başvurulan derleme</span><span class="sxs-lookup"><span data-stu-id="40981-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|<span data-ttu-id="40981-230">Alt başvurulan derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="40981-231">Sürümü tutulan başvurulan derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|<span data-ttu-id="40981-232">İçerik dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|  
|<span data-ttu-id="40981-233">İçerik dosyası alt</span><span class="sxs-lookup"><span data-stu-id="40981-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|<span data-ttu-id="40981-234">Kaynak dosya site</span><span class="sxs-lookup"><span data-stu-id="40981-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|<span data-ttu-id="40981-235">Kaynak dosya alt site</span><span class="sxs-lookup"><span data-stu-id="40981-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 <span data-ttu-id="40981-236">Tablo 2 gösterilmektedir çeşitli göreli paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , biçimlendirme belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40981-236">Table 2 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>  
  
 <span data-ttu-id="40981-237">Tablo 2: Göreli Pack URI biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="40981-237">Table 2: Relative Pack URIs in Markup</span></span>  
  
|<span data-ttu-id="40981-238">Dosya</span><span class="sxs-lookup"><span data-stu-id="40981-238">File</span></span>|<span data-ttu-id="40981-239">Göreli paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40981-239">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="40981-240">Yerel derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|  
|<span data-ttu-id="40981-241">Yerel derleme alt kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="40981-242">Başvurulan derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|<span data-ttu-id="40981-243">Alt başvurulan derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="40981-244">İçerik dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-244">Content file</span></span>|`"/ContentFile.xaml"`|  
|<span data-ttu-id="40981-245">İçerik dosyası alt</span><span class="sxs-lookup"><span data-stu-id="40981-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a><span data-ttu-id="40981-246">Pack URI kod içinde kullanma</span><span class="sxs-lookup"><span data-stu-id="40981-246">Using Pack URIs in Code</span></span>  
 <span data-ttu-id="40981-247">Bir paketi belirtmeniz [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] örneği tarafından kodda <xref:System.Uri> sınıfı ve paketi geçirme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Oluşturucusu parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="40981-247">You specify a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] in code by instantiating the <xref:System.Uri> class and passing the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] as a parameter to the constructor.</span></span> <span data-ttu-id="40981-248">Bu, aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="40981-248">This is demonstrated in the following example.</span></span>  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 <span data-ttu-id="40981-249">Varsayılan olarak, <xref:System.Uri> sınıfı, paketi göz önünde bulundurur [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] mutlak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40981-249">By default, the <xref:System.Uri> class considers pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to be absolute.</span></span> <span data-ttu-id="40981-250">Sonuç olarak, bir özel durum örneği tetiklenir <xref:System.Uri> sınıfı göreli bir paketi ile oluşturulan [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40981-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 <span data-ttu-id="40981-251">Neyse ki, <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> , aşırı <xref:System.Uri> sınıfı oluşturucusu türünde bir parametre kabul eden <xref:System.UriKind> belirtmek izin vermek için bir paket olup olmadığını [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] mutlak veya göreli.</span><span class="sxs-lookup"><span data-stu-id="40981-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is either absolute or relative.</span></span>  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 <span data-ttu-id="40981-252">Yalnızca belirtmelisiniz <xref:System.UriKind.Absolute> veya <xref:System.UriKind.Relative> olduğunuzda belirli, sağlanan paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] biri veya diğer.</span><span class="sxs-lookup"><span data-stu-id="40981-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is one or the other.</span></span> <span data-ttu-id="40981-253">Paketi türünü bilmiyorsanız [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] kullanılan, bir kullanıcı bir paketi girdiğinde gibi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] çalışma zamanında <xref:System.UriKind.RelativeOrAbsolute> yerine.</span><span class="sxs-lookup"><span data-stu-id="40981-253">If you don't know the type of pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that is used, such as when a user enters a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 <span data-ttu-id="40981-254">Tablo 3 gösterilmektedir çeşitli göreli paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kullanarak kod içinde belirtebileceğiniz <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="40981-254">Table 3 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="40981-255">Tablo 3: Mutlak Pack URI kodu</span><span class="sxs-lookup"><span data-stu-id="40981-255">Table 3: Absolute Pack URIs in Code</span></span>  
  
|<span data-ttu-id="40981-256">Dosya</span><span class="sxs-lookup"><span data-stu-id="40981-256">File</span></span>|<span data-ttu-id="40981-257">Mutlak paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40981-257">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="40981-258">Kaynak dosya - yerel derleme</span><span class="sxs-lookup"><span data-stu-id="40981-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="40981-259">Alt - yerel derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="40981-260">Kaynak dosya - başvurulan derleme</span><span class="sxs-lookup"><span data-stu-id="40981-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="40981-261">Alt başvurulan derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="40981-262">Sürümü tutulan başvurulan derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="40981-263">İçerik dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="40981-264">İçerik dosyası alt</span><span class="sxs-lookup"><span data-stu-id="40981-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="40981-265">Kaynak dosya site</span><span class="sxs-lookup"><span data-stu-id="40981-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="40981-266">Kaynak dosya alt site</span><span class="sxs-lookup"><span data-stu-id="40981-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 <span data-ttu-id="40981-267">Tablo 4 gösterilmektedir çeşitli göreli paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kodu kullanarak belirttiğiniz <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="40981-267">Table 4 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="40981-268">Tablo 4: Göreli Pack URI kodu</span><span class="sxs-lookup"><span data-stu-id="40981-268">Table 4: Relative Pack URIs in Code</span></span>  
  
|<span data-ttu-id="40981-269">Dosya</span><span class="sxs-lookup"><span data-stu-id="40981-269">File</span></span>|<span data-ttu-id="40981-270">Göreli paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40981-270">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="40981-271">Kaynak dosya - yerel derleme</span><span class="sxs-lookup"><span data-stu-id="40981-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="40981-272">Alt - yerel derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="40981-273">Kaynak dosya - başvurulan derleme</span><span class="sxs-lookup"><span data-stu-id="40981-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="40981-274">Alt - başvurulan derleme kaynak dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="40981-275">İçerik dosyası</span><span class="sxs-lookup"><span data-stu-id="40981-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="40981-276">İçerik dosyası alt</span><span class="sxs-lookup"><span data-stu-id="40981-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="40981-277">Paketi URI senaryoları</span><span class="sxs-lookup"><span data-stu-id="40981-277">Common Pack URI Scenarios</span></span>  
 <span data-ttu-id="40981-278">Önceki bölümlerde paketi oluşturmak nasıl ele alınan [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kaynak, içerik ve kaynak dosyaları sitesi tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="40981-278">The preceding sections have discussed how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="40981-279">İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]bu kurulumlarını çeşitli şekillerde kullanılır ve aşağıdaki bölümler birkaç genel kullanımları kapsar.</span><span class="sxs-lookup"><span data-stu-id="40981-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="40981-280">Bir uygulama başlatıldığında göstermek için kullanıcı Arabirimi belirtme</span><span class="sxs-lookup"><span data-stu-id="40981-280">Specifying the UI to Show When an Application Starts</span></span>  
 <span data-ttu-id="40981-281"><xref:System.Windows.Application.StartupUri%2A> ilk belirtir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ne zaman göstermek için bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama başlatıldığında.</span><span class="sxs-lookup"><span data-stu-id="40981-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="40981-282">Bağımsız uygulamalar için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] penceresinde, aşağıdaki örnekte gösterildiği gibi olabilir.</span><span class="sxs-lookup"><span data-stu-id="40981-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 <span data-ttu-id="40981-283">Bağımsız uygulamalar ve [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] ayrıca bir sayfa ilk kullanıcı Arabirimi, aşağıdaki örnekte gösterildiği gibi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40981-283">Standalone applications and [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] can also specify a page as the initial UI, as shown in the following example.</span></span>  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 <span data-ttu-id="40981-284">Uygulama başına bir uygulamadır ve bir sayfa ile belirtilen <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] açılır bir <xref:System.Windows.Navigation.NavigationWindow> sayfası barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="40981-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="40981-285">İçin [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], ana bilgisayar tarayıcıda sayfası gösterilir.</span><span class="sxs-lookup"><span data-stu-id="40981-285">For [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], the page is shown in the host browser.</span></span>  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a><span data-ttu-id="40981-286">Bir sayfaya gezinme</span><span class="sxs-lookup"><span data-stu-id="40981-286">Navigating to a Page</span></span>  
 <span data-ttu-id="40981-287">Aşağıdaki örnek, bir sayfaya gitmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="40981-287">The following example shows how to navigate to a page.</span></span>  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 <span data-ttu-id="40981-288">Gezinme için çeşitli yollar hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bkz: [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="40981-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span>  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a><span data-ttu-id="40981-289">Pencereyi simge belirtme</span><span class="sxs-lookup"><span data-stu-id="40981-289">Specifying a Window Icon</span></span>  
 <span data-ttu-id="40981-290">Aşağıdaki örnekte bir URI pencerenin simge belirtmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="40981-290">The following example shows how to use a URI to specify a window's icon.</span></span>  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 <span data-ttu-id="40981-291">Daha fazla bilgi için bkz. <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="40981-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="40981-292">Görüntü, ses ve Video dosyaları yükleniyor</span><span class="sxs-lookup"><span data-stu-id="40981-292">Loading Image, Audio, and Video Files</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="40981-293"> uygulamaların her biri algılanabilir ve paketiyle yüklenen medya türleri, çok geniş bir yelpazedeki kullanmasını sağlayan [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]aşağıdaki örneklerde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="40981-293"> allows applications to use a wide variety of media types, all of which can be identified and loaded with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], as shown in the following examples.</span></span>  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 <span data-ttu-id="40981-294">Medya içeriği ile çalışma hakkında daha fazla bilgi için bkz: [grafik ve çoklu ortam](../../../../docs/framework/wpf/graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="40981-294">For more information on working with media content, see [Graphics and Multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md).</span></span>  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="40981-295">Kaynak sitesinden bir kaynak sözlüğü yükleniyor</span><span class="sxs-lookup"><span data-stu-id="40981-295">Loading a Resource Dictionary from the Site of Origin</span></span>  
 <span data-ttu-id="40981-296">Kaynak sözlüklerindeki (<xref:System.Windows.ResourceDictionary>) uygulama temaları desteklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40981-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="40981-297">Oluşturun ve Temalar yönetmek için bir yol, bir uygulamanın kaynak sitede bulunan kaynak sözlüklerindeki olarak birden çok tema oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="40981-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="40981-298">Bu eklenmesi ve güncelleştirilmiş yeniden derlenmesi ve bir uygulama dağıtarak Temalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="40981-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="40981-299">Bu kaynak sözlüklerindeki tanımlanabilir ve paketi kullanılarak yüklenen [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], aşağıdaki örnekte gösterilen.</span><span class="sxs-lookup"><span data-stu-id="40981-299">These resource dictionaries can be identified and loaded using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], which is shown in the following example.</span></span>  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 <span data-ttu-id="40981-300">Temalar da genel bir bakış için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="40981-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40981-301">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40981-301">See Also</span></span>  
 [<span data-ttu-id="40981-302">WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları</span><span class="sxs-lookup"><span data-stu-id="40981-302">WPF Application Resource, Content, and Data Files</span></span>](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
