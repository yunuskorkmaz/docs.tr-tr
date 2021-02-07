---
description: ': IMetaDataTables:: GetColumn metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4c4cec7216f93783b34b594330358d1e6036ed40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688279"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="7ffb2-103">IMetaDataTables::GetColumn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ffb2-103">IMetaDataTables::GetColumn Method</span></span>

<span data-ttu-id="7ffb2-104">Verilen tablodaki belirtilen sütun ve satır hücresinde bulunan değere bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-104">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ffb2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ffb2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ffb2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ffb2-106">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="7ffb2-107">'ndaki Tablonun dizini.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-107">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="7ffb2-108">'ndaki Tablodaki sütunun dizini.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-108">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="7ffb2-109">'ndaki Tablodaki satırın dizini.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-109">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="7ffb2-110">dışı Hücredeki değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-110">[out] A pointer to the value in the cell.</span></span>  

## <a name="remarks"></a><span data-ttu-id="7ffb2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ffb2-111">Remarks</span></span>

<span data-ttu-id="7ffb2-112">Üzerinden döndürülen değerin `pVal` yorumlandığına sütunun türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-112">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="7ffb2-113">Sütun türü, [IMetaDataTables. GetColumnInfo](imetadatatables-getcolumninfo-method.md)çağırarak belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-113">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="7ffb2-114">**GetColumn** yöntemi, **RID** veya **codedtoken** türündeki sütunları otomatik olarak tam 32-bit değerlere dönüştürür `mdToken` .</span><span class="sxs-lookup"><span data-stu-id="7ffb2-114">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="7ffb2-115">Ayrıca, 8 bit veya 16 bit değerleri otomatik olarak tam 32-bit değerlerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-115">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span>
- <span data-ttu-id="7ffb2-116">*Yığın* türü sütunlarında, döndürülen *Pval* karşılık gelen yığında bir dizin olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-116">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="7ffb2-117">Sütun türü</span><span class="sxs-lookup"><span data-stu-id="7ffb2-117">Column type</span></span>              | <span data-ttu-id="7ffb2-118">pVal içerir</span><span class="sxs-lookup"><span data-stu-id="7ffb2-118">pVal contains</span></span> | <span data-ttu-id="7ffb2-119">Yorum</span><span class="sxs-lookup"><span data-stu-id="7ffb2-119">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="7ffb2-120">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="7ffb2-120">`0`..`iRidMax`</span></span><br><span data-ttu-id="7ffb2-121">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="7ffb2-121">(0..63)</span></span>  | <span data-ttu-id="7ffb2-122">mdToken</span><span class="sxs-lookup"><span data-stu-id="7ffb2-122">mdToken</span></span>     | <span data-ttu-id="7ffb2-123">*Pval* , tam bir belirteç içerir.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-123">*pVal* will contain a full Token.</span></span> <span data-ttu-id="7ffb2-124">İşlevi, RID 'yi otomatik olarak tam belirtece dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-124">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="7ffb2-125">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="7ffb2-125">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="7ffb2-126">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="7ffb2-126">(64..95)</span></span> | <span data-ttu-id="7ffb2-127">mdToken</span><span class="sxs-lookup"><span data-stu-id="7ffb2-127">mdToken</span></span> | <span data-ttu-id="7ffb2-128">Dönüş sonrasında *Pval* bir tam belirteç içerecektir.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-128">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="7ffb2-129">İşlevi CodedToken 'ı otomatik olarak tam belirtece açar.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-129">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="7ffb2-130">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="7ffb2-130">`iSHORT` (96)</span></span>            | <span data-ttu-id="7ffb2-131">Int16</span><span class="sxs-lookup"><span data-stu-id="7ffb2-131">Int16</span></span>         | <span data-ttu-id="7ffb2-132">Otomatik olarak 32 bit olarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-132">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="7ffb2-133">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="7ffb2-133">`iUSHORT` (97)</span></span>           | <span data-ttu-id="7ffb2-134">UInt16</span><span class="sxs-lookup"><span data-stu-id="7ffb2-134">UInt16</span></span>        | <span data-ttu-id="7ffb2-135">Otomatik olarak 32 bit olarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-135">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="7ffb2-136">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="7ffb2-136">`iLONG` (98)</span></span>             | <span data-ttu-id="7ffb2-137">Int32</span><span class="sxs-lookup"><span data-stu-id="7ffb2-137">Int32</span></span>         |                                        |
| <span data-ttu-id="7ffb2-138">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="7ffb2-138">`iULONG` (99)</span></span>            | <span data-ttu-id="7ffb2-139">UInt32</span><span class="sxs-lookup"><span data-stu-id="7ffb2-139">UInt32</span></span>        |                                        |
| <span data-ttu-id="7ffb2-140">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="7ffb2-140">`iBYTE` (100)</span></span>            | <span data-ttu-id="7ffb2-141">Bayt</span><span class="sxs-lookup"><span data-stu-id="7ffb2-141">Byte</span></span>          | <span data-ttu-id="7ffb2-142">Otomatik olarak 32 bit olarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-142">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="7ffb2-143">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="7ffb2-143">`iSTRING` (101)</span></span>          | <span data-ttu-id="7ffb2-144">Dize yığın dizini</span><span class="sxs-lookup"><span data-stu-id="7ffb2-144">String heap index</span></span> | <span data-ttu-id="7ffb2-145">*Pval* , dize yığınında bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-145">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="7ffb2-146">Gerçek sütun dize değerini almak için [IMetaDataTables:: GetString](imetadatatables-getstring-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-146">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="7ffb2-147">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="7ffb2-147">`iGUID` (102)</span></span>            | <span data-ttu-id="7ffb2-148">GUID yığın dizini</span><span class="sxs-lookup"><span data-stu-id="7ffb2-148">Guid heap index</span></span> | <span data-ttu-id="7ffb2-149">*Pval* , GUID yığınının bir dizinidir.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-149">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="7ffb2-150">Gerçek sütun GUID değerini almak için [IMetaDataTables:: GetGuid](imetadatatables-getguid-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-150">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="7ffb2-151">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="7ffb2-151">`iBLOB` (103)</span></span>            | <span data-ttu-id="7ffb2-152">Blob yığın dizini</span><span class="sxs-lookup"><span data-stu-id="7ffb2-152">Blob heap index</span></span> | <span data-ttu-id="7ffb2-153">*Pval* , blob yığınında bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-153">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="7ffb2-154">Gerçek sütun blobu değerini almak için [IMetaDataTables:: GetBlob](imetadatatables-getblob-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-154">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="7ffb2-155">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ffb2-155">Requirements</span></span>  

 <span data-ttu-id="7ffb2-156">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ffb2-156">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ffb2-157">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7ffb2-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7ffb2-158">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7ffb2-158">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ffb2-159">**.NET Framework sürümleri**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ffb2-159">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ffb2-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ffb2-160">See also</span></span>

- [<span data-ttu-id="7ffb2-161">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ffb2-161">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="7ffb2-162">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ffb2-162">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
