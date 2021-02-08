---
description: ': IMetaDataImport:: FindMethod yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0d2866554fcb4dcf3984310e4da24d501f1fc7b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803561"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="03ad3-103">IMetaDataImport::FindMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03ad3-103">IMetaDataImport::FindMethod Method</span></span>

<span data-ttu-id="03ad3-104">Belirtilen <xref:System.Type> ve belirtilen ad ve meta veri imzasına sahip olan yöntemi Için MethodDef belirtecine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="03ad3-104">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03ad3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03ad3-105">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03ad3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03ad3-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="03ad3-107">'ndaki `mdTypeDef` Aramak için üyeyi kapsayan türün belirteci (bir sınıf veya arabirim).</span><span class="sxs-lookup"><span data-stu-id="03ad3-107">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="03ad3-108">Bu değer ise `mdTokenNil` , genel bir işlev için arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="03ad3-108">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="03ad3-109">'ndaki Aranacak yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="03ad3-109">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="03ad3-110">'ndaki Metodun ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="03ad3-110">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="03ad3-111">'ndaki Bayt cinsinden boyut `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="03ad3-111">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="03ad3-112">dışı Eşleşen MethodDef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="03ad3-112">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03ad3-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03ad3-113">Remarks</span></span>  

 <span data-ttu-id="03ad3-114">Yöntemi kapsayan sınıfını veya arabirimini ( `td` ), adını ( `szName` ) ve isteğe bağlı olarak imzasını () kullanarak belirtirsiniz `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="03ad3-114">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="03ad3-115">Bir sınıfta veya arabirimde aynı ada sahip birden çok yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="03ad3-115">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="03ad3-116">Bu durumda, benzersiz eşleşmeyi bulmak için yöntemin imzasını geçirin.</span><span class="sxs-lookup"><span data-stu-id="03ad3-116">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="03ad3-117">`FindMethod`İmzaların belirli bir kapsama bağlandığı için, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03ad3-117">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="03ad3-118">İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="03ad3-118">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="03ad3-119">Belirteç, yerel TypeDef tablosunun bir dizinidir.</span><span class="sxs-lookup"><span data-stu-id="03ad3-119">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="03ad3-120">Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı girişi yapılacak girdi olarak kullanabilirsiniz `FindMethod` .</span><span class="sxs-lookup"><span data-stu-id="03ad3-120">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="03ad3-121">`FindMethod` yalnızca sınıfta veya arabirimde doğrudan tanımlanmış yöntemleri bulur; devralınan yöntemleri bulmaz.</span><span class="sxs-lookup"><span data-stu-id="03ad3-121">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03ad3-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03ad3-122">Requirements</span></span>  

 <span data-ttu-id="03ad3-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03ad3-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03ad3-124">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="03ad3-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03ad3-125">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="03ad3-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03ad3-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03ad3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03ad3-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03ad3-127">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="03ad3-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03ad3-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="03ad3-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03ad3-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
