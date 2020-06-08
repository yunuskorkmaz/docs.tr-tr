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
ms.openlocfilehash: 76d23fe9221ae5a07d79b8c5c1a7ad297922b003
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501254"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="0b28b-102">IMetaDataTables::GetColumn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b28b-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="0b28b-103">Verilen tablodaki belirtilen sütun ve satır hücresinde bulunan değere bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="0b28b-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b28b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0b28b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b28b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b28b-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="0b28b-106">'ndaki Tablonun dizini.</span><span class="sxs-lookup"><span data-stu-id="0b28b-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="0b28b-107">'ndaki Tablodaki sütunun dizini.</span><span class="sxs-lookup"><span data-stu-id="0b28b-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="0b28b-108">'ndaki Tablodaki satırın dizini.</span><span class="sxs-lookup"><span data-stu-id="0b28b-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="0b28b-109">dışı Hücredeki değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0b28b-109">[out] A pointer to the value in the cell.</span></span>  

## <a name="remarks"></a><span data-ttu-id="0b28b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b28b-110">Remarks</span></span>

<span data-ttu-id="0b28b-111">Üzerinden döndürülen değerin `pVal` yorumlandığına sütunun türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0b28b-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="0b28b-112">Sütun türü, [IMetaDataTables. GetColumnInfo](imetadatatables-getcolumninfo-method.md)çağırarak belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="0b28b-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="0b28b-113">**GetColumn** yöntemi, **RID** veya **codedtoken** türündeki sütunları otomatik olarak tam 32-bit değerlere dönüştürür `mdToken` .</span><span class="sxs-lookup"><span data-stu-id="0b28b-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="0b28b-114">Ayrıca, 8 bit veya 16 bit değerleri otomatik olarak tam 32-bit değerlerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0b28b-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span>
- <span data-ttu-id="0b28b-115">*Yığın* türü sütunlarında, döndürülen *Pval* karşılık gelen yığında bir dizin olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0b28b-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="0b28b-116">Sütun türü</span><span class="sxs-lookup"><span data-stu-id="0b28b-116">Column type</span></span>              | <span data-ttu-id="0b28b-117">pVal içerir</span><span class="sxs-lookup"><span data-stu-id="0b28b-117">pVal contains</span></span> | <span data-ttu-id="0b28b-118">Yorum</span><span class="sxs-lookup"><span data-stu-id="0b28b-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="0b28b-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="0b28b-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="0b28b-120">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="0b28b-120">(0..63)</span></span>  | <span data-ttu-id="0b28b-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="0b28b-121">mdToken</span></span>     | <span data-ttu-id="0b28b-122">*Pval* , tam bir belirteç içerir.</span><span class="sxs-lookup"><span data-stu-id="0b28b-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="0b28b-123">İşlevi, RID 'yi otomatik olarak tam belirtece dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0b28b-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="0b28b-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="0b28b-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="0b28b-125">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="0b28b-125">(64..95)</span></span> | <span data-ttu-id="0b28b-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="0b28b-126">mdToken</span></span> | <span data-ttu-id="0b28b-127">Dönüş sonrasında *Pval* bir tam belirteç içerecektir.</span><span class="sxs-lookup"><span data-stu-id="0b28b-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="0b28b-128">İşlevi CodedToken 'ı otomatik olarak tam belirtece açar.</span><span class="sxs-lookup"><span data-stu-id="0b28b-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="0b28b-129">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="0b28b-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="0b28b-130">Int16</span><span class="sxs-lookup"><span data-stu-id="0b28b-130">Int16</span></span>         | <span data-ttu-id="0b28b-131">Otomatik olarak 32 bit olarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="0b28b-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="0b28b-132">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="0b28b-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="0b28b-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="0b28b-133">UInt16</span></span>        | <span data-ttu-id="0b28b-134">Otomatik olarak 32 bit olarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="0b28b-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="0b28b-135">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="0b28b-135">`iLONG` (98)</span></span>             | <span data-ttu-id="0b28b-136">Int32</span><span class="sxs-lookup"><span data-stu-id="0b28b-136">Int32</span></span>         |                                        |
| <span data-ttu-id="0b28b-137">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="0b28b-137">`iULONG` (99)</span></span>            | <span data-ttu-id="0b28b-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="0b28b-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="0b28b-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="0b28b-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="0b28b-140">Bayt</span><span class="sxs-lookup"><span data-stu-id="0b28b-140">Byte</span></span>          | <span data-ttu-id="0b28b-141">Otomatik olarak 32 bit olarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="0b28b-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="0b28b-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="0b28b-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="0b28b-143">Dize yığın dizini</span><span class="sxs-lookup"><span data-stu-id="0b28b-143">String heap index</span></span> | <span data-ttu-id="0b28b-144">*Pval* , dize yığınında bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="0b28b-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="0b28b-145">Gerçek sütun dize değerini almak için [IMetaDataTables:: GetString](imetadatatables-getstring-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0b28b-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="0b28b-146">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="0b28b-146">`iGUID` (102)</span></span>            | <span data-ttu-id="0b28b-147">GUID yığın dizini</span><span class="sxs-lookup"><span data-stu-id="0b28b-147">Guid heap index</span></span> | <span data-ttu-id="0b28b-148">*Pval* , GUID yığınının bir dizinidir.</span><span class="sxs-lookup"><span data-stu-id="0b28b-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="0b28b-149">Gerçek sütun GUID değerini almak için [IMetaDataTables:: GetGuid](imetadatatables-getguid-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0b28b-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="0b28b-150">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="0b28b-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="0b28b-151">Blob yığın dizini</span><span class="sxs-lookup"><span data-stu-id="0b28b-151">Blob heap index</span></span> | <span data-ttu-id="0b28b-152">*Pval* , blob yığınında bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="0b28b-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="0b28b-153">Gerçek sütun blobu değerini almak için [IMetaDataTables:: GetBlob](imetadatatables-getblob-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0b28b-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="0b28b-154">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b28b-154">Requirements</span></span>  
 <span data-ttu-id="0b28b-155">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b28b-155">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b28b-156">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0b28b-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b28b-157">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0b28b-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b28b-158">**.NET Framework sürümleri**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b28b-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b28b-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b28b-159">See also</span></span>

- [<span data-ttu-id="0b28b-160">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b28b-160">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="0b28b-161">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b28b-161">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
