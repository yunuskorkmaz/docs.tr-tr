---
title: "IMetaDataImport::FindField Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindField
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2178f8738ca510fb2163c1043dd94ebcb7043904
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="83d53-102">IMetaDataImport::FindField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83d53-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="83d53-103">Bir işaretçi fieldDef simgesi için içine alan için belirteç alır belirtilen tarafından <xref:System.Type> ve belirtilen adı ve meta veri imza sahip.</span><span class="sxs-lookup"><span data-stu-id="83d53-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83d53-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83d53-104">Syntax</span></span>  
  
```  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83d53-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83d53-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="83d53-106">[in] Sınıf veya aramak için alan barındırır arabirimi için TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="83d53-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="83d53-107">Bu değer ise `mdTokenNil`, arama için genel bir değişkendir yapılır.</span><span class="sxs-lookup"><span data-stu-id="83d53-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="83d53-108">[in] Aranacak alan adı.</span><span class="sxs-lookup"><span data-stu-id="83d53-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="83d53-109">[in] Alanın ikili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="83d53-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="83d53-110">[in] Bayt cinsinden boyutu `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="83d53-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="83d53-111">[out] Eşleşen fieldDef simgesi belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="83d53-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83d53-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83d53-112">Remarks</span></span>  
 <span data-ttu-id="83d53-113">Kapsayan sınıf ya da arabirimi kullanarak alanı belirtin (`td`), kendi adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="83d53-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="83d53-114">İmza geçirilen `FindField` imzalar için belirli bir kapsam bağlı olduğundan geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83d53-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="83d53-115">İmza kapsayan sınıfı veya değer türünü tanımlayan bir belirteç eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="83d53-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="83d53-116">(Belirteç yerel TypeDef tabloya bir dizin olur).</span><span class="sxs-lookup"><span data-stu-id="83d53-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="83d53-117">Geçerli kapsam bağlamında dışında bir çalışma zamanı imzası oluşturmak ve girdi olarak bu imza kullanmak `FindField`.</span><span class="sxs-lookup"><span data-stu-id="83d53-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="83d53-118">`FindField`doğrudan sınıfta veya arabirimde tanımlanan alanları bulur; devralınan alanları bulmaz.</span><span class="sxs-lookup"><span data-stu-id="83d53-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83d53-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83d53-119">Requirements</span></span>  
 <span data-ttu-id="83d53-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83d53-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83d53-121">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="83d53-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83d53-122">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="83d53-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83d53-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83d53-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d53-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83d53-124">See Also</span></span>  
 [<span data-ttu-id="83d53-125">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="83d53-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="83d53-126">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="83d53-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
