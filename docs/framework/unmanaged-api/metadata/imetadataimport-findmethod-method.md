---
title: IMetaDataImport::FindMethod Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 857ea06ad8aba2a6de87bdf670ad0462a2f7dde1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487297"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="54d87-102">IMetaDataImport::FindMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54d87-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="54d87-103">Bir işaretçi için MethodDef alınmış yöntemi için belirteç alır tarafından belirtilen <xref:System.Type> ve belirtilen adı ve meta verileri imza sahip.</span><span class="sxs-lookup"><span data-stu-id="54d87-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54d87-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54d87-104">Syntax</span></span>  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54d87-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54d87-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="54d87-106">[in] `mdTypeDef` Belirteci aranacak üye kapsayan türü için (bir sınıf veya arabirim).</span><span class="sxs-lookup"><span data-stu-id="54d87-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="54d87-107">Bu değer ise `mdTokenNil`, genel bir işlev için arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="54d87-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="54d87-108">[in] Aranacak yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="54d87-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="54d87-109">[in] İkili meta veri imzası yöntem bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="54d87-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="54d87-110">[in] Bayt cinsinden boyutu `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="54d87-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="54d87-111">[out] Eşleşen MethodDef belirteç için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="54d87-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54d87-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54d87-112">Remarks</span></span>  
 <span data-ttu-id="54d87-113">Kapsayan sınıfı veya arabirimi kullanarak yöntemini belirtin (`td`), adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="54d87-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="54d87-114">Bir sınıfı veya arabirimi aynı ada sahip birden çok yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="54d87-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="54d87-115">Bu durumda, benzersiz bir eşleşme bulmak için yöntemin imzasını geçirin.</span><span class="sxs-lookup"><span data-stu-id="54d87-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="54d87-116">İmza geçirilen `FindMethod` imzaları belirli bir kapsama bağlı oldukları için geçerli kapsamda oluşturulan gerekir.</span><span class="sxs-lookup"><span data-stu-id="54d87-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="54d87-117">İmza kapsayan sınıf veya değer türü tanımlayan bir belirteç ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="54d87-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="54d87-118">Belirteç, yerel TypeDef tablosuna bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="54d87-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="54d87-119">Geçerli kapsam bağlamında dışında bir çalışma zamanı imza oluşturun ve bu imza olarak giriş için giriş kullanmasına `FindMethod`.</span><span class="sxs-lookup"><span data-stu-id="54d87-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="54d87-120">`FindMethod` sınıf veya arabirim içinde tanımlanmış olan yöntemleri bulur; devralınan yöntemleri bulmaz.</span><span class="sxs-lookup"><span data-stu-id="54d87-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54d87-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54d87-121">Requirements</span></span>  
 <span data-ttu-id="54d87-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54d87-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54d87-123">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="54d87-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54d87-124">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="54d87-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="54d87-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54d87-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d87-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54d87-126">See also</span></span>
- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="54d87-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54d87-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="54d87-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54d87-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
