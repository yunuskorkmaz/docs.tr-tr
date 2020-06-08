---
title: Meta Veri Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 4d947388afb8d7f8f935ae3b8e8aff81efaf2ee4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489604"
---
# <a name="metadata-interfaces"></a><span data-ttu-id="203d5-102">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="203d5-102">Metadata Interfaces</span></span>
<span data-ttu-id="203d5-103">Bu bölümde, .NET Framework türler, Yöntemler, alanlar vb. tarafından sunulan meta verilere erişim sağlayan yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="203d5-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="203d5-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="203d5-104">In This Section</span></span>  
 [<span data-ttu-id="203d5-105">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-105">ICeeGen Interface</span></span>](iceegen-interface.md)  
 <span data-ttu-id="203d5-106">Dinamik kod derleme için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="203d5-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="203d5-107">IHostFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-107">IHostFilter Interface</span></span>](ihostfilter-interface.md)  
 <span data-ttu-id="203d5-108">Çalışma zamanı ana bilgisayarı için meta veri belirteçlerini işlemek üzere işaretlemek üzere bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="203d5-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="203d5-109">IMapToken Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-109">IMapToken Interface</span></span>](imaptoken-interface.md)  
 <span data-ttu-id="203d5-110">İçeri aktarılan ve verilmiş meta veri imzaları arasında eşleme özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="203d5-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="203d5-111">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-111">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)  
 <span data-ttu-id="203d5-112">Kaynakları çözümlemek ve tüketmek için ortak dil çalışma zamanı (CLR) tarafından kullanılan kendi kendine tanımlama modelini destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="203d5-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="203d5-113">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-113">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)  
 <span data-ttu-id="203d5-114">Bir derleme bildiriminin içeriğine erişmek ve bunları incelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="203d5-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="203d5-115">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-115">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)  
 <span data-ttu-id="203d5-116">Tür kitaplıklarını meta veri imzalarına eşlemek ve birinden diğerine dönüştürmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="203d5-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="203d5-117">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="203d5-117">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)  
 <span data-ttu-id="203d5-118">`IMetaDataDispenser`artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="203d5-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="203d5-119">Bunun yerine `IMetaDataDispenserEx` kullanın.</span><span class="sxs-lookup"><span data-stu-id="203d5-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="203d5-120">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)  
 <span data-ttu-id="203d5-121">Meta veri oluşturmak veya değiştirmek için bellek alanını eşleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="203d5-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="203d5-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)  
 <span data-ttu-id="203d5-123">Tanımlı olan kapsamda derleme hakkında meta veriler oluşturma, değiştirme ve depolama için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="203d5-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="203d5-124">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-124">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)  
 <span data-ttu-id="203d5-125">Yöntemlerin ve oluşturucuların tür parametreleri ile tanımlanması ve değiştirilmesi için yöntemler sağlar <xref:System.Type?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="203d5-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="203d5-126">IMetaDataError Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-126">IMetaDataError Interface</span></span>](imetadataerror-interface.md)  
 <span data-ttu-id="203d5-127">Bir derlemenin meta veri imzasının çözümlenmesi sırasında hataları raporlamak için bir geri çağırma mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="203d5-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="203d5-128">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-128">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)  
 <span data-ttu-id="203d5-129">Zaten alınmış olan işlemleri önlemek için meta veri belirteçleri işaretlemek ve filtrelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="203d5-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="203d5-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)  
 <span data-ttu-id="203d5-131">Diğer derlemelerden türleri içeri ve düzenleme için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="203d5-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="203d5-132">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-132">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)  
 <span data-ttu-id="203d5-133">`IMetaDataImport`, Genel türlerle çalışma yeteneği sağlamak için genişletir.</span><span class="sxs-lookup"><span data-stu-id="203d5-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="203d5-134">IMetaDataInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-134">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)  
 <span data-ttu-id="203d5-135">Diskteki bir dosyadaki meta verilerin belleğe eşlenmesiyle ilgili bilgileri alan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="203d5-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="203d5-136">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-136">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)  
 <span data-ttu-id="203d5-137">Tablolarda meta veri bilgilerinin depolanması ve alınması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="203d5-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="203d5-138">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-138">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)  
 <span data-ttu-id="203d5-139">`IMetaDataTables`Meta veri akışlarıyla çalışmaya yönelik yöntemleri içerecek şekilde genişletir.</span><span class="sxs-lookup"><span data-stu-id="203d5-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="203d5-140">IMetaDataValidate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="203d5-140">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)  
 <span data-ttu-id="203d5-141">Meta veri imzalarının doğrulanması için kullanılacak yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="203d5-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="203d5-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="203d5-142">Related Sections</span></span>  
 [<span data-ttu-id="203d5-143">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="203d5-143">Metadata Global Static Functions</span></span>](metadata-global-static-functions.md)  
  
 [<span data-ttu-id="203d5-144">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="203d5-144">Metadata Enumerations</span></span>](metadata-enumerations.md)  
  
 [<span data-ttu-id="203d5-145">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="203d5-145">Metadata Structures</span></span>](metadata-structures.md)  
  
 [<span data-ttu-id="203d5-146">Meta Veri Birleşimleri</span><span class="sxs-lookup"><span data-stu-id="203d5-146">Metadata Unions</span></span>](metadata-unions.md)
