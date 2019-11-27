---
title: IMetaDataTables Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
ms.openlocfilehash: 17305f2c088dd6f479da4c823d3db0fd50c0b3d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443226"
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="f30d0-102">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f30d0-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="f30d0-103">Tablolarda meta veri bilgilerinin depolanması ve alınması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f30d0-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f30d0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f30d0-104">Methods</span></span>  
  
|<span data-ttu-id="f30d0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f30d0-105">Method</span></span>|<span data-ttu-id="f30d0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f30d0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f30d0-107">GetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-107">GetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|<span data-ttu-id="f30d0-108">Belirtilen sütun dizininde ikili büyük nesne (BLOB) için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="f30d0-109">GetBlobHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-109">GetBlobHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="f30d0-110">BLOB yığınının boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="f30d0-111">GetCodedTokenInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-111">GetCodedTokenInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="f30d0-112">Belirtilen satır diziniyle ilişkili bir belirteç dizisine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="f30d0-113">GetColumn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-113">GetColumn Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|<span data-ttu-id="f30d0-114">Belirtilen tablo dizinindeki tabloda belirtilen sütun dizinindeki sütunda bulunan değerlere yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="f30d0-115">GetColumnInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-115">GetColumnInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="f30d0-116">Belirtilen tabloda belirtilen sütunla ilgili verileri alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="f30d0-117">GetGuid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-117">GetGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|<span data-ttu-id="f30d0-118">Belirtilen dizindeki satırdan bir GUID alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="f30d0-119">GetGuidHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-119">GetGuidHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="f30d0-120">GUID yığınının boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="f30d0-121">GetNextBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-121">GetNextBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|<span data-ttu-id="f30d0-122">Tablodaki sonraki BLOBUN dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="f30d0-123">GetNextGuid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-123">GetNextGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|<span data-ttu-id="f30d0-124">Geçerli tablo sütunundaki sonraki GUID değerinin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="f30d0-125">GetNextString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-125">GetNextString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|<span data-ttu-id="f30d0-126">Geçerli tablo sütunundaki sonraki dizenin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="f30d0-127">GetNextUserString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-127">GetNextUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="f30d0-128">Geçerli tablo sütunundaki bir sonraki sabit kodlanmış dizeyi içeren satırın dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="f30d0-129">GetNumTables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-129">GetNumTables Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|<span data-ttu-id="f30d0-130">Geçerli `IMetaDataTables` örneğinin kapsamındaki tablo sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="f30d0-131">GetRow Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-131">GetRow Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|<span data-ttu-id="f30d0-132">Belirtilen tablo dizinindeki tabloda belirtilen satır dizinindeki satırı alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="f30d0-133">GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-133">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|<span data-ttu-id="f30d0-134">Geçerli başvuru kapsamındaki tablo sütunundan belirtilen dizindeki dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="f30d0-135">GetStringHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-135">GetStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="f30d0-136">Dize yığınının boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="f30d0-137">GetTableIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-137">GetTableIndex Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|<span data-ttu-id="f30d0-138">Belirtilen belirteç tarafından başvurulan tablonun dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="f30d0-139">GetTableInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-139">GetTableInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|<span data-ttu-id="f30d0-140">Belirtilen tablo dizinindeki tablonun adını, satır boyutunu, satır sayısını, sütun sayısını ve anahtar sütun dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="f30d0-141">GetUserString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-141">GetUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|<span data-ttu-id="f30d0-142">Geçerli kapsamdaki dize sütununda belirtilen dizinde sabit kodlanmış dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="f30d0-143">GetUserStringHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f30d0-143">GetUserStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="f30d0-144">Kullanıcı dizesi yığınının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="f30d0-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f30d0-145">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f30d0-145">Requirements</span></span>  
 <span data-ttu-id="f30d0-146">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f30d0-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f30d0-147">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f30d0-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f30d0-148">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f30d0-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f30d0-149">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f30d0-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f30d0-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f30d0-150">See also</span></span>

- [<span data-ttu-id="f30d0-151">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f30d0-151">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="f30d0-152">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f30d0-152">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
