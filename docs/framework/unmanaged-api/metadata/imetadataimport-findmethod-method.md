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
ms.openlocfilehash: 111e42a6d8f413c616779bc44e0722ab38781588
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711344"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="8cf3f-102">IMetaDataImport::FindMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8cf3f-102">IMetaDataImport::FindMethod Method</span></span>

<span data-ttu-id="8cf3f-103">Belirtilen <xref:System.Type> ve belirtilen ad ve meta veri imzasına sahip olan yöntemi Için MethodDef belirtecine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="8cf3f-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cf3f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8cf3f-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cf3f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8cf3f-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="8cf3f-106">'ndaki `mdTypeDef` Aramak için üyeyi kapsayan türün belirteci (bir sınıf veya arabirim).</span><span class="sxs-lookup"><span data-stu-id="8cf3f-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="8cf3f-107">Bu değer ise `mdTokenNil` , genel bir işlev için arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="8cf3f-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="8cf3f-108">'ndaki Aranacak yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="8cf3f-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8cf3f-109">'ndaki Metodun ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8cf3f-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8cf3f-110">'ndaki Bayt cinsinden boyut `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="8cf3f-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="8cf3f-111">dışı Eşleşen MethodDef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8cf3f-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cf3f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8cf3f-112">Remarks</span></span>  

 <span data-ttu-id="8cf3f-113">Yöntemi kapsayan sınıfını veya arabirimini ( `td` ), adını ( `szName` ) ve isteğe bağlı olarak imzasını () kullanarak belirtirsiniz `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="8cf3f-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="8cf3f-114">Bir sınıfta veya arabirimde aynı ada sahip birden çok yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="8cf3f-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="8cf3f-115">Bu durumda, benzersiz eşleşmeyi bulmak için yöntemin imzasını geçirin.</span><span class="sxs-lookup"><span data-stu-id="8cf3f-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="8cf3f-116">`FindMethod`İmzaların belirli bir kapsama bağlandığı için, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8cf3f-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="8cf3f-117">İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8cf3f-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="8cf3f-118">Belirteç, yerel TypeDef tablosunun bir dizinidir.</span><span class="sxs-lookup"><span data-stu-id="8cf3f-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="8cf3f-119">Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı girişi yapılacak girdi olarak kullanabilirsiniz `FindMethod` .</span><span class="sxs-lookup"><span data-stu-id="8cf3f-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="8cf3f-120">`FindMethod` yalnızca sınıfta veya arabirimde doğrudan tanımlanmış yöntemleri bulur; devralınan yöntemleri bulmaz.</span><span class="sxs-lookup"><span data-stu-id="8cf3f-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cf3f-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8cf3f-121">Requirements</span></span>  

 <span data-ttu-id="8cf3f-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cf3f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cf3f-123">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8cf3f-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8cf3f-124">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8cf3f-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8cf3f-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cf3f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cf3f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cf3f-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="8cf3f-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cf3f-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8cf3f-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cf3f-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
