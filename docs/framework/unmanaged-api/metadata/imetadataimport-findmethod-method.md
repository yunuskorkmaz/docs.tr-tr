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
ms.openlocfilehash: 53b3d94e8b1e273fcbc041d25a5bf586a12735c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177258"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="537a5-102">IMetaDataImport::FindMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="537a5-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="537a5-103">Belirtilen <xref:System.Type> tarafından eklenen ve belirtilen ad ve meta veri imzasına sahip yöntem için MethodDef belirteci için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="537a5-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="537a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="537a5-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="537a5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="537a5-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="537a5-106">[içinde] `mdTypeDef` Üyeyi aramak için içine alan tür (sınıf veya arabirim) için belirteç.</span><span class="sxs-lookup"><span data-stu-id="537a5-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="537a5-107">Bu değer `mdTokenNil`ise, arama global bir işlev için yapılır.</span><span class="sxs-lookup"><span data-stu-id="537a5-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="537a5-108">[içinde] Aranacak yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="537a5-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="537a5-109">[içinde] Yöntemin ikili meta veri imzasına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="537a5-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="537a5-110">[içinde] `pvSigBlob`Baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="537a5-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="537a5-111">[çıkış] Eşleşen MethodDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="537a5-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="537a5-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="537a5-112">Remarks</span></span>  
 <span data-ttu-id="537a5-113">Yöntemi çevreleyen sınıf ını veya arabirimini (`td``szName`), adını ( ),`pvSigBlob`ve isteğe bağlı olarak imzasını ( ) kullanarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="537a5-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="537a5-114">Bir sınıfta veya arabirimde aynı ada sahip birden çok yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="537a5-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="537a5-115">Bu durumda, benzersiz eşleşmeyi bulmak için yöntemin imzasını geçirin.</span><span class="sxs-lookup"><span data-stu-id="537a5-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="537a5-116">İmzalar belirli `FindMethod` bir kapsama bağlı olduğundan, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="537a5-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="537a5-117">İmza, çevreleyen sınıfı veya değer türünü tanımlayan bir belirteç katıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="537a5-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="537a5-118">Belirteç, yerel TypeDef tablosuna bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="537a5-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="537a5-119">Geçerli kapsam bağlamının dışında bir çalışma zamanı imzası oluşturamazsınız ve bu imzayı `FindMethod`giriş olarak kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="537a5-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="537a5-120">`FindMethod`yalnızca sınıf veya arabirimde doğrudan tanımlanan yöntemleri bulur; kalıtsal yöntemler bulamaz.</span><span class="sxs-lookup"><span data-stu-id="537a5-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="537a5-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="537a5-121">Requirements</span></span>  
 <span data-ttu-id="537a5-122">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="537a5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="537a5-123">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="537a5-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="537a5-124">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="537a5-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="537a5-125">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="537a5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="537a5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="537a5-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="537a5-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="537a5-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="537a5-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="537a5-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
