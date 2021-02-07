---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyEmit::D efineExportedType yöntemi'
title: IMetaDataAssemblyEmit::DefineExportedType Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 0da1b1eb0880b0ba9df0ba9ad70b460163dffc39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671119"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="169c1-103">IMetaDataAssemblyEmit::DefineExportedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="169c1-103">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>

<span data-ttu-id="169c1-104">`ExportedType`Belirtilen içe aktarılmış tür için meta veri içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="169c1-104">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="169c1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="169c1-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="169c1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="169c1-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="169c1-107">'ndaki Aktarılacak türün adı.</span><span class="sxs-lookup"><span data-stu-id="169c1-107">[in] The name of type to be exported.</span></span> <span data-ttu-id="169c1-108">Ortak dil çalışma zamanının 1,1 sürümü için, verilen türün adı, türü için verilen adla tam olarak eşleşmelidir `TypeDef` .</span><span class="sxs-lookup"><span data-stu-id="169c1-108">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="169c1-109">'ndaki İçe aktarılmış türün nerede uygulandığını belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="169c1-109">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="169c1-110">Geçerli değerler ve bunlarla ilişkili anlamları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="169c1-110">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="169c1-111">`mdFile` Bu derleme içindeki farklı bir dosyada tür uygulandı.</span><span class="sxs-lookup"><span data-stu-id="169c1-111">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="169c1-112">`mdAssemblyRef` Tür, farklı bir derlemede uygulanır.</span><span class="sxs-lookup"><span data-stu-id="169c1-112">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="169c1-113">`mdExportedTYpe` Tür başka bir tür içinde iç içe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="169c1-113">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="169c1-114">`mdFileNil` Tür, bildirimle aynı dosyada ve iç içe geçmiş bir tür değil.</span><span class="sxs-lookup"><span data-stu-id="169c1-114">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="169c1-115">'ndaki Meta veriye aktarılacak türü belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="169c1-115">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="169c1-116">Bu değer `TypeDef` , türü uygulayan dosyanın tablosuna girilir ve yalnızca söz konusu dosya bu derlemede olduğunda ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="169c1-116">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="169c1-117">'ndaki İçe aktarılmış tür için özellik ayarlarını tanımlayan [CorTypeAttr](cortypeattr-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="169c1-117">[in] A bitwise combination of [CorTypeAttr](cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="169c1-118">dışı Verilen türü gösteren döndürülen meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="169c1-118">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="169c1-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="169c1-119">Remarks</span></span>  

 <span data-ttu-id="169c1-120">`ExportedType`Bu derleme tarafından sunulan ve bildirimi içeren bir modülde uygulanan her tür için bir meta veri yapısı tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="169c1-120">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="169c1-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="169c1-121">Requirements</span></span>  

 <span data-ttu-id="169c1-122">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="169c1-122">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="169c1-123">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="169c1-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="169c1-124">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="169c1-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="169c1-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="169c1-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="169c1-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="169c1-126">See also</span></span>

- [<span data-ttu-id="169c1-127">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="169c1-127">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
