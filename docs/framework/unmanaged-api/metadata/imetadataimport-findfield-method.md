---
title: IMetaDataImport::FindField Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1baee71b5b8575f51eb54fbc8a037a5dddd24500
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782532"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="551be-102">IMetaDataImport::FindField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="551be-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="551be-103">Bir işaretçi için fieldDef simgesi alınmış bir alan için belirteç alır tarafından belirtilen <xref:System.Type> ve belirtilen adı ve meta verileri imza sahip.</span><span class="sxs-lookup"><span data-stu-id="551be-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="551be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="551be-104">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="551be-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="551be-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="551be-106">[in] Sınıf veya aramak için alan kapsayan arabirimi TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="551be-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="551be-107">Bu değer ise `mdTokenNil`, genel bir değişken için arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="551be-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="551be-108">[in] Aranacak alan adı.</span><span class="sxs-lookup"><span data-stu-id="551be-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="551be-109">[in] Alan ikili meta veri imzası bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="551be-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="551be-110">[in] Bayt cinsinden boyutu `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="551be-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="551be-111">[out] Eşleşen fieldDef simgesi belirteç için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="551be-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="551be-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="551be-112">Remarks</span></span>  
 <span data-ttu-id="551be-113">Kapsayan sınıfı veya arabirimi kullanarak alanı belirtin (`td`), adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="551be-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="551be-114">İmza geçirilen `FindField` imzaları belirli bir kapsama bağlı oldukları için geçerli kapsamda oluşturulan gerekir.</span><span class="sxs-lookup"><span data-stu-id="551be-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="551be-115">İmza kapsayan sınıf veya değer türü tanımlayan bir belirteç ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="551be-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="551be-116">(Belirteç yerel TypeDef tabloya dizinidir).</span><span class="sxs-lookup"><span data-stu-id="551be-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="551be-117">Geçerli kapsam bağlamında dışında bir çalışma zamanı imza oluşturun ve bu imza, giriş olarak kullanmak `FindField`.</span><span class="sxs-lookup"><span data-stu-id="551be-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="551be-118">`FindField` sınıf veya arabirim içinde tanımlanmış olan alanlar bulur; devralınan alanları bulmaz.</span><span class="sxs-lookup"><span data-stu-id="551be-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="551be-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="551be-119">Requirements</span></span>  
 <span data-ttu-id="551be-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="551be-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="551be-121">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="551be-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="551be-122">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="551be-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="551be-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="551be-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="551be-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="551be-124">See also</span></span>

- [<span data-ttu-id="551be-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="551be-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="551be-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="551be-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
