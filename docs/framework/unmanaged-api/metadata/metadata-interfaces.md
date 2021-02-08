---
description: 'Daha fazla bilgi edinin: meta veri arabirimleri'
title: Meta Veri Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 4851fbc93bfa29f1b4b5015c82f05c1b200b9092
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799141"
---
# <a name="metadata-interfaces"></a><span data-ttu-id="5b7c4-103">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5b7c4-103">Metadata Interfaces</span></span>

<span data-ttu-id="5b7c4-104">Bu bölümde, .NET Framework türler, Yöntemler, alanlar vb. tarafından sunulan meta verilere erişim sağlayan yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-104">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b7c4-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5b7c4-105">In This Section</span></span>  

 [<span data-ttu-id="5b7c4-106">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-106">ICeeGen Interface</span></span>](iceegen-interface.md)  
 <span data-ttu-id="5b7c4-107">Dinamik kod derleme için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-107">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="5b7c4-108">IHostFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-108">IHostFilter Interface</span></span>](ihostfilter-interface.md)  
 <span data-ttu-id="5b7c4-109">Çalışma zamanı ana bilgisayarı için meta veri belirteçlerini işlemek üzere işaretlemek üzere bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-109">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="5b7c4-110">IMapToken Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-110">IMapToken Interface</span></span>](imaptoken-interface.md)  
 <span data-ttu-id="5b7c4-111">İçeri aktarılan ve verilmiş meta veri imzaları arasında eşleme özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-111">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="5b7c4-112">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-112">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)  
 <span data-ttu-id="5b7c4-113">Kaynakları çözümlemek ve tüketmek için ortak dil çalışma zamanı (CLR) tarafından kullanılan kendi kendine tanımlama modelini destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-113">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="5b7c4-114">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-114">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)  
 <span data-ttu-id="5b7c4-115">Bir derleme bildiriminin içeriğine erişmek ve bunları incelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-115">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="5b7c4-116">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-116">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)  
 <span data-ttu-id="5b7c4-117">Tür kitaplıklarını meta veri imzalarına eşlemek ve birinden diğerine dönüştürmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-117">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="5b7c4-118">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)  
 <span data-ttu-id="5b7c4-119">`IMetaDataDispenser` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-119">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="5b7c4-120">Bunun yerine `IMetaDataDispenserEx` kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-120">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="5b7c4-121">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)  
 <span data-ttu-id="5b7c4-122">Meta veri oluşturmak veya değiştirmek için bellek alanını eşleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-122">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="5b7c4-123">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-123">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)  
 <span data-ttu-id="5b7c4-124">Tanımlı olan kapsamda derleme hakkında meta veriler oluşturma, değiştirme ve depolama için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-124">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="5b7c4-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)  
 <span data-ttu-id="5b7c4-126">Yöntemlerin ve oluşturucuların tür parametreleri ile tanımlanması ve değiştirilmesi için yöntemler sağlar <xref:System.Type?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5b7c4-126">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="5b7c4-127">IMetaDataError Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-127">IMetaDataError Interface</span></span>](imetadataerror-interface.md)  
 <span data-ttu-id="5b7c4-128">Bir derlemenin meta veri imzasının çözümlenmesi sırasında hataları raporlamak için bir geri çağırma mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-128">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="5b7c4-129">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-129">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)  
 <span data-ttu-id="5b7c4-130">Zaten alınmış olan işlemleri önlemek için meta veri belirteçleri işaretlemek ve filtrelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-130">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="5b7c4-131">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-131">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)  
 <span data-ttu-id="5b7c4-132">Diğer derlemelerden türleri içeri ve düzenleme için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-132">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="5b7c4-133">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-133">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)  
 <span data-ttu-id="5b7c4-134">`IMetaDataImport`, Genel türlerle çalışma yeteneği sağlamak için genişletir.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-134">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="5b7c4-135">IMetaDataInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-135">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)  
 <span data-ttu-id="5b7c4-136">Diskteki bir dosyadaki meta verilerin belleğe eşlenmesiyle ilgili bilgileri alan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-136">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="5b7c4-137">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-137">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)  
 <span data-ttu-id="5b7c4-138">Tablolarda meta veri bilgilerinin depolanması ve alınması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-138">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="5b7c4-139">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-139">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)  
 <span data-ttu-id="5b7c4-140">`IMetaDataTables`Meta veri akışlarıyla çalışmaya yönelik yöntemleri içerecek şekilde genişletir.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-140">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="5b7c4-141">IMetaDataValidate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b7c4-141">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)  
 <span data-ttu-id="5b7c4-142">Meta veri imzalarının doğrulanması için kullanılacak yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c4-142">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5b7c4-143">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="5b7c4-143">Related Sections</span></span>  

 [<span data-ttu-id="5b7c4-144">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5b7c4-144">Metadata Global Static Functions</span></span>](metadata-global-static-functions.md)  
  
 [<span data-ttu-id="5b7c4-145">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="5b7c4-145">Metadata Enumerations</span></span>](metadata-enumerations.md)  
  
 [<span data-ttu-id="5b7c4-146">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="5b7c4-146">Metadata Structures</span></span>](metadata-structures.md)  
  
 [<span data-ttu-id="5b7c4-147">Meta Veri Birleşmeleri</span><span class="sxs-lookup"><span data-stu-id="5b7c4-147">Metadata Unions</span></span>](metadata-unions.md)
