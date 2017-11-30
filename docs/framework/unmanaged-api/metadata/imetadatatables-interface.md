---
title: IMetaDataTables Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables
helpviewer_keywords: IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c89d615fbeeff4a60eb386d58c573ee7905f538d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="23ba8-102">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23ba8-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="23ba8-103">Depolama ve meta veri bilgileri tablolardaki alınması için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="23ba8-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23ba8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="23ba8-104">Methods</span></span>  
  
|<span data-ttu-id="23ba8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="23ba8-105">Method</span></span>|<span data-ttu-id="23ba8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23ba8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23ba8-107">GetBlob yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-107">GetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|<span data-ttu-id="23ba8-108">Bir işaretçi ikili büyük nesne (BLOB) için belirtilen sütun dizininde alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="23ba8-109">GetBlobHeapSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-109">GetBlobHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="23ba8-110">BLOB yığın bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="23ba8-111">Getcodedtokenınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-111">GetCodedTokenInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="23ba8-112">Belirtilen satır dizini ile ilişkili belirteçleri dizisi için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="23ba8-113">GetColumn yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-113">GetColumn Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|<span data-ttu-id="23ba8-114">Belirtilen sütun dizininde tablonun belirtilen tablo dizinindeki sütunda bulunan değerlerin için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="23ba8-115">GetColumnInfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-115">GetColumnInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="23ba8-116">Belirtilen tabloda belirtilen sütun hakkındaki verileri alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="23ba8-117">GetGuid yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-117">GetGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|<span data-ttu-id="23ba8-118">Belirtilen dizindeki satırdan bir GUID alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="23ba8-119">GetGuidHeapSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-119">GetGuidHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="23ba8-120">GUID yığın bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="23ba8-121">GetNextBlob yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-121">GetNextBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|<span data-ttu-id="23ba8-122">Tabloda sonraki BLOB dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="23ba8-123">GetNextGuid yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-123">GetNextGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|<span data-ttu-id="23ba8-124">Geçerli bir tablo sütununda sonraki GUID değeri dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="23ba8-125">GetNextString yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-125">GetNextString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|<span data-ttu-id="23ba8-126">Sonraki dizenin dizini geçerli bir tablo sütununda alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="23ba8-127">GetNextUserString yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-127">GetNextUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="23ba8-128">Sonraki sabit kodlanmış dize geçerli tablo sütununda içeren satırın dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="23ba8-129">GetNumTables yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-129">GetNumTables Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|<span data-ttu-id="23ba8-130">Geçerli kapsamda tablo sayısını alır `IMetaDataTables` örneği.</span><span class="sxs-lookup"><span data-stu-id="23ba8-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="23ba8-131">GetRow yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-131">GetRow Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|<span data-ttu-id="23ba8-132">Belirtilen satır dizininde belirtilen tablo dizinindeki tablosundaki satır alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="23ba8-133">GetString yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-133">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|<span data-ttu-id="23ba8-134">Dize belirtilen dizindeki geçerli başvuru kapsamda tablo sütunuyla bağlantısı alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="23ba8-135">GetStringHeapSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-135">GetStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="23ba8-136">Dize yığın bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="23ba8-137">Gettableındex yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-137">GetTableIndex Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|<span data-ttu-id="23ba8-138">Belirtilen belirteç tarafından başvurulan tablo için dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="23ba8-139">Gettableınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-139">GetTableInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|<span data-ttu-id="23ba8-140">Ad, satır boyutu, satır sayısı, sütun sayısı ve tablo anahtar sütun dizini belirtilen tablo dizininde alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="23ba8-141">GetUserString yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-141">GetUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|<span data-ttu-id="23ba8-142">Geçerli kapsamdaki dize sütununda belirtilen dizindeki sabit kodlanmış dize alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="23ba8-143">GetUserStringHeapSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ba8-143">GetUserStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="23ba8-144">Kullanıcı dize yığın bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="23ba8-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23ba8-145">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23ba8-145">Requirements</span></span>  
 <span data-ttu-id="23ba8-146">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23ba8-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23ba8-147">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="23ba8-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23ba8-148">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="23ba8-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="23ba8-149">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23ba8-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ba8-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23ba8-150">See Also</span></span>  
 [<span data-ttu-id="23ba8-151">Meta veri arabirimleri</span><span class="sxs-lookup"><span data-stu-id="23ba8-151">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="23ba8-152">Imetadatatables2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="23ba8-152">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
