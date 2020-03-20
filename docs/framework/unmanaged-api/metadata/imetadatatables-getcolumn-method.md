---
title: IMetaDataTables::GetColumn Yöntemi
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: f43d4d1547cbe92f325950e1697dada83b42c4f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177133"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="964a3-102">IMetaDataTables::GetColumn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="964a3-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="964a3-103">Verilen tabloda belirtilen sütun ve satırın hücresinde bulunan değeriçin bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="964a3-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="964a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="964a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="964a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="964a3-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="964a3-106">[içinde] Tablonun dizini.</span><span class="sxs-lookup"><span data-stu-id="964a3-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="964a3-107">[içinde] Tablodaki sütunun dizini.</span><span class="sxs-lookup"><span data-stu-id="964a3-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="964a3-108">[içinde] Tablodaki satırın dizini.</span><span class="sxs-lookup"><span data-stu-id="964a3-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="964a3-109">[çıkış] Hücredeki değeriçin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="964a3-109">[out] A pointer to the value in the cell.</span></span>  

## <a name="remarks"></a><span data-ttu-id="964a3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="964a3-110">Remarks</span></span>

<span data-ttu-id="964a3-111">Döndürülen değerin yorumlanması `pVal` sütunun türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="964a3-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="964a3-112">Sütun türü [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md)çağırarak belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="964a3-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="964a3-113">**GetColumn** yöntemi, **Rid** veya **CodedToken** türündeki sütunları otomatik `mdToken` olarak tam 32 bit değerlere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="964a3-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="964a3-114">Ayrıca otomatik olarak 8-bit veya 16-bit değerleri tam 32-bit değerlerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="964a3-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span>
- <span data-ttu-id="964a3-115">*Yığın* türü sütunları için, döndürülen *pVal* ilgili yığına bir dizin olacaktır.</span><span class="sxs-lookup"><span data-stu-id="964a3-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="964a3-116">Sütun türü</span><span class="sxs-lookup"><span data-stu-id="964a3-116">Column type</span></span>              | <span data-ttu-id="964a3-117">pVal içerir</span><span class="sxs-lookup"><span data-stu-id="964a3-117">pVal contains</span></span> | <span data-ttu-id="964a3-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="964a3-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="964a3-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="964a3-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="964a3-120">(0..63)</span><span class="sxs-lookup"><span data-stu-id="964a3-120">(0..63)</span></span>  | <span data-ttu-id="964a3-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="964a3-121">mdToken</span></span>     | <span data-ttu-id="964a3-122">*pVal* tam bir Belirteç içerir.</span><span class="sxs-lookup"><span data-stu-id="964a3-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="964a3-123">İşlev, Rid'i otomatik olarak tam bir belirteci dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="964a3-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="964a3-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="964a3-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="964a3-125">(64..95)</span><span class="sxs-lookup"><span data-stu-id="964a3-125">(64..95)</span></span> | <span data-ttu-id="964a3-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="964a3-126">mdToken</span></span> | <span data-ttu-id="964a3-127">Döndükten sonra, *pVal* tam bir Belirteç içerecektir.</span><span class="sxs-lookup"><span data-stu-id="964a3-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="964a3-128">İşlev, CodedToken'ı otomatik olarak tam bir belirteç haline getirir.</span><span class="sxs-lookup"><span data-stu-id="964a3-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="964a3-129">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="964a3-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="964a3-130">Int16</span><span class="sxs-lookup"><span data-stu-id="964a3-130">Int16</span></span>         | <span data-ttu-id="964a3-131">Otomatik olarak 32 bit'e uzatıldı.</span><span class="sxs-lookup"><span data-stu-id="964a3-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="964a3-132">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="964a3-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="964a3-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="964a3-133">UInt16</span></span>        | <span data-ttu-id="964a3-134">Otomatik olarak 32 bit'e uzatıldı.</span><span class="sxs-lookup"><span data-stu-id="964a3-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="964a3-135">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="964a3-135">`iLONG` (98)</span></span>             | <span data-ttu-id="964a3-136">Int32</span><span class="sxs-lookup"><span data-stu-id="964a3-136">Int32</span></span>         |                                        |
| <span data-ttu-id="964a3-137">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="964a3-137">`iULONG` (99)</span></span>            | <span data-ttu-id="964a3-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="964a3-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="964a3-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="964a3-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="964a3-140">Bayt</span><span class="sxs-lookup"><span data-stu-id="964a3-140">Byte</span></span>          | <span data-ttu-id="964a3-141">Otomatik olarak 32 bit'e uzatıldı.</span><span class="sxs-lookup"><span data-stu-id="964a3-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="964a3-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="964a3-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="964a3-143">String yığın dizini</span><span class="sxs-lookup"><span data-stu-id="964a3-143">String heap index</span></span> | <span data-ttu-id="964a3-144">*pVal* String yığınına bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="964a3-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="964a3-145">Gerçek sütun String değerini almak için [IMetadataTables::GetString'i](imetadatatables-getstring-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="964a3-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="964a3-146">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="964a3-146">`iGUID` (102)</span></span>            | <span data-ttu-id="964a3-147">Kılavuz yığın dizini</span><span class="sxs-lookup"><span data-stu-id="964a3-147">Guid heap index</span></span> | <span data-ttu-id="964a3-148">*pVal* Guid yığınına bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="964a3-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="964a3-149">Gerçek sütun Guid değerini almak için [IMetadataTables kullanın::GetGuid.](imetadatatables-getguid-method.md)</span><span class="sxs-lookup"><span data-stu-id="964a3-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="964a3-150">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="964a3-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="964a3-151">Blob yığın dizini</span><span class="sxs-lookup"><span data-stu-id="964a3-151">Blob heap index</span></span> | <span data-ttu-id="964a3-152">*pVal* Blob yığınıiçine bir indekstir.</span><span class="sxs-lookup"><span data-stu-id="964a3-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="964a3-153">Gerçek sütun Blob değerini almak için [IMetadataTables kullanın::GetBlob.](imetadatatables-getblob-method.md)</span><span class="sxs-lookup"><span data-stu-id="964a3-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="964a3-154">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="964a3-154">Requirements</span></span>  
 <span data-ttu-id="964a3-155">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="964a3-155">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="964a3-156">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="964a3-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="964a3-157">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="964a3-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="964a3-158">**.NET Çerçeve Sürümleri**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="964a3-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="964a3-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="964a3-159">See also</span></span>

- [<span data-ttu-id="964a3-160">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="964a3-160">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="964a3-161">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="964a3-161">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
