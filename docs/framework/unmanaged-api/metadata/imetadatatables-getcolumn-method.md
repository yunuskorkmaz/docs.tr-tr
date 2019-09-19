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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 853f137d91e1b3eb4f3f65a06522618f8441dcb3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053671"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="2c0f1-102">IMetaDataTables::GetColumn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c0f1-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="2c0f1-103">Verilen tablodaki belirtilen sütun ve satır hücresinde bulunan değere bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c0f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c0f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c0f1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c0f1-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="2c0f1-106">'ndaki Tablonun dizini.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="2c0f1-107">'ndaki Tablodaki sütunun dizini.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="2c0f1-108">'ndaki Tablodaki satırın dizini.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="2c0f1-109">dışı Hücredeki değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-109">[out] A pointer to the value in the cell.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="2c0f1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c0f1-110">Remarks</span></span>

<span data-ttu-id="2c0f1-111">Üzerinden `pVal` döndürülen değerin yorumlandığına sütunun türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="2c0f1-112">Sütun türü, [IMetaDataTables. GetColumnInfo](imetadatatables-getcolumninfo-method.md)çağırarak belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="2c0f1-113">**GetColumn** yöntemi, **RID** veya **codedtoken** türündeki sütunları otomatik olarak tam 32-bit `mdToken` değerlere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="2c0f1-114">Ayrıca, 8 bit veya 16 bit değerleri otomatik olarak tam 32-bit değerlerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span> 
- <span data-ttu-id="2c0f1-115">*Yığın* türü sütunlarında, döndürülen *Pval* karşılık gelen yığında bir dizin olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="2c0f1-116">Sütun türü</span><span class="sxs-lookup"><span data-stu-id="2c0f1-116">Column type</span></span>              | <span data-ttu-id="2c0f1-117">pVal içerir</span><span class="sxs-lookup"><span data-stu-id="2c0f1-117">pVal contains</span></span> | <span data-ttu-id="2c0f1-118">Yorum</span><span class="sxs-lookup"><span data-stu-id="2c0f1-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="2c0f1-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="2c0f1-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="2c0f1-120">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="2c0f1-120">(0..63)</span></span>  | <span data-ttu-id="2c0f1-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="2c0f1-121">mdToken</span></span>     | <span data-ttu-id="2c0f1-122">*Pval* , tam bir belirteç içerir.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="2c0f1-123">İşlevi, RID 'yi otomatik olarak tam belirtece dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="2c0f1-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="2c0f1-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="2c0f1-125">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="2c0f1-125">(64..95)</span></span> | <span data-ttu-id="2c0f1-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="2c0f1-126">mdToken</span></span> | <span data-ttu-id="2c0f1-127">Dönüş sonrasında *Pval* bir tam belirteç içerecektir.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="2c0f1-128">İşlevi CodedToken 'ı otomatik olarak tam belirtece açar.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="2c0f1-129">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="2c0f1-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="2c0f1-130">Int16</span><span class="sxs-lookup"><span data-stu-id="2c0f1-130">Int16</span></span>         | <span data-ttu-id="2c0f1-131">Otomatik olarak 32 bit olarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="2c0f1-132">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="2c0f1-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="2c0f1-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="2c0f1-133">UInt16</span></span>        | <span data-ttu-id="2c0f1-134">Otomatik olarak 32 bit olarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="2c0f1-135">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="2c0f1-135">`iLONG` (98)</span></span>             | <span data-ttu-id="2c0f1-136">Int32</span><span class="sxs-lookup"><span data-stu-id="2c0f1-136">Int32</span></span>         |                                        | 
| <span data-ttu-id="2c0f1-137">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="2c0f1-137">`iULONG` (99)</span></span>            | <span data-ttu-id="2c0f1-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="2c0f1-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="2c0f1-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="2c0f1-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="2c0f1-140">Bayt</span><span class="sxs-lookup"><span data-stu-id="2c0f1-140">Byte</span></span>          | <span data-ttu-id="2c0f1-141">Otomatik olarak 32 bit olarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="2c0f1-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="2c0f1-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="2c0f1-143">Dize yığın dizini</span><span class="sxs-lookup"><span data-stu-id="2c0f1-143">String heap index</span></span> | <span data-ttu-id="2c0f1-144">*Pval* , dize yığınında bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="2c0f1-145">Gerçek sütun dize değerini almak için [IMetaDataTables:: GetString](imetadatatables-getstring-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="2c0f1-146">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="2c0f1-146">`iGUID` (102)</span></span>            | <span data-ttu-id="2c0f1-147">GUID yığın dizini</span><span class="sxs-lookup"><span data-stu-id="2c0f1-147">Guid heap index</span></span> | <span data-ttu-id="2c0f1-148">*Pval* , GUID yığınının bir dizinidir.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="2c0f1-149">Gerçek sütun GUID değerini almak için [IMetaDataTables:: GetGuid](imetadatatables-getguid-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="2c0f1-150">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="2c0f1-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="2c0f1-151">Blob yığın dizini</span><span class="sxs-lookup"><span data-stu-id="2c0f1-151">Blob heap index</span></span> | <span data-ttu-id="2c0f1-152">*Pval* , blob yığınında bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="2c0f1-153">Gerçek sütun blobu değerini almak için [IMetaDataTables:: GetBlob](imetadatatables-getblob-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="2c0f1-154">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c0f1-154">Requirements</span></span>  
 <span data-ttu-id="2c0f1-155">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c0f1-155">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c0f1-156">**Üst bilgi** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2c0f1-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c0f1-157">**Kitaplığı** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2c0f1-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c0f1-158">**.NET Framework sürümleri**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c0f1-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0f1-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c0f1-159">See also</span></span>

- [<span data-ttu-id="2c0f1-160">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c0f1-160">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="2c0f1-161">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c0f1-161">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
