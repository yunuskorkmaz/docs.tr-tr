---
description: 'Daha fazla bilgi edinin: IMetaDataTables Arabirimi'
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
ms.openlocfilehash: c3edf504586bad1252c36d6e8254193eaf9cc26d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799279"
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="2a4a2-103">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-103">IMetaDataTables Interface</span></span>

<span data-ttu-id="2a4a2-104">Tablolarda meta veri bilgilerinin depolanması ve alınması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-104">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a4a2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2a4a2-105">Methods</span></span>  
  
|<span data-ttu-id="2a4a2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2a4a2-106">Method</span></span>|<span data-ttu-id="2a4a2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a4a2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a4a2-108">GetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-108">GetBlob Method</span></span>](imetadatatables-getblob-method.md)|<span data-ttu-id="2a4a2-109">Belirtilen sütun dizininde ikili büyük nesne (BLOB) için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-109">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="2a4a2-110">GetBlobHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-110">GetBlobHeapSize Method</span></span>](imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="2a4a2-111">BLOB yığınının boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-111">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="2a4a2-112">GetCodedTokenInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-112">GetCodedTokenInfo Method</span></span>](imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="2a4a2-113">Belirtilen satır diziniyle ilişkili bir belirteç dizisine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-113">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="2a4a2-114">GetColumn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-114">GetColumn Method</span></span>](imetadatatables-getcolumn-method.md)|<span data-ttu-id="2a4a2-115">Belirtilen tablo dizinindeki tabloda belirtilen sütun dizinindeki sütunda bulunan değerlere yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-115">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="2a4a2-116">GetColumnInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-116">GetColumnInfo Method</span></span>](imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="2a4a2-117">Belirtilen tabloda belirtilen sütunla ilgili verileri alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-117">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="2a4a2-118">GetGuid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-118">GetGuid Method</span></span>](imetadatatables-getguid-method.md)|<span data-ttu-id="2a4a2-119">Belirtilen dizindeki satırdan bir GUID alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-119">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="2a4a2-120">GetGuidHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-120">GetGuidHeapSize Method</span></span>](imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="2a4a2-121">GUID yığınının boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-121">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="2a4a2-122">GetNextBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-122">GetNextBlob Method</span></span>](imetadatatables-getnextblob-method.md)|<span data-ttu-id="2a4a2-123">Tablodaki sonraki BLOBUN dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-123">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="2a4a2-124">GetNextGuid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-124">GetNextGuid Method</span></span>](imetadatatables-getnextguid-method.md)|<span data-ttu-id="2a4a2-125">Geçerli tablo sütunundaki sonraki GUID değerinin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-125">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="2a4a2-126">GetNextString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-126">GetNextString Method</span></span>](imetadatatables-getnextstring-method.md)|<span data-ttu-id="2a4a2-127">Geçerli tablo sütunundaki sonraki dizenin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-127">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="2a4a2-128">GetNextUserString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-128">GetNextUserString Method</span></span>](imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="2a4a2-129">Geçerli tablo sütunundaki bir sonraki sabit kodlanmış dizeyi içeren satırın dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-129">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="2a4a2-130">GetNumTables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-130">GetNumTables Method</span></span>](imetadatatables-getnumtables-method.md)|<span data-ttu-id="2a4a2-131">Geçerli örnek kapsamındaki tablo sayısını alır `IMetaDataTables` .</span><span class="sxs-lookup"><span data-stu-id="2a4a2-131">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="2a4a2-132">GetRow Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-132">GetRow Method</span></span>](imetadatatables-getrow-method.md)|<span data-ttu-id="2a4a2-133">Belirtilen tablo dizinindeki tabloda belirtilen satır dizinindeki satırı alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-133">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="2a4a2-134">GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-134">GetString Method</span></span>](imetadatatables-getstring-method.md)|<span data-ttu-id="2a4a2-135">Geçerli başvuru kapsamındaki tablo sütunundan belirtilen dizindeki dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-135">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="2a4a2-136">GetStringHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-136">GetStringHeapSize Method</span></span>](imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="2a4a2-137">Dize yığınının boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-137">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="2a4a2-138">GetTableIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-138">GetTableIndex Method</span></span>](imetadatatables-gettableindex-method.md)|<span data-ttu-id="2a4a2-139">Belirtilen belirteç tarafından başvurulan tablonun dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-139">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="2a4a2-140">GetTableInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-140">GetTableInfo Method</span></span>](imetadatatables-gettableinfo-method.md)|<span data-ttu-id="2a4a2-141">Belirtilen tablo dizinindeki tablonun adını, satır boyutunu, satır sayısını, sütun sayısını ve anahtar sütun dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-141">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="2a4a2-142">GetUserString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-142">GetUserString Method</span></span>](imetadatatables-getuserstring-method.md)|<span data-ttu-id="2a4a2-143">Geçerli kapsamdaki dize sütununda belirtilen dizinde sabit kodlanmış dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-143">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="2a4a2-144">GetUserStringHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-144">GetUserStringHeapSize Method</span></span>](imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="2a4a2-145">Kullanıcı dizesi yığınının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-145">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a4a2-146">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a4a2-146">Requirements</span></span>  

 <span data-ttu-id="2a4a2-147">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a4a2-147">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a4a2-148">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2a4a2-148">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2a4a2-149">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2a4a2-149">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2a4a2-150">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a4a2-150">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a4a2-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a4a2-151">See also</span></span>

- [<span data-ttu-id="2a4a2-152">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2a4a2-152">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="2a4a2-153">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a4a2-153">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
