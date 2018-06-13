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
ms.openlocfilehash: 6b68d4e3d51fdb50290319de804a78c1a78a07a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447394"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="0844e-102">IMetaDataImport::FindMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0844e-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="0844e-103">Bir işaretçi MethodDef içine yöntemi için belirteç alır belirtilen tarafından <xref:System.Type> ve belirtilen adı ve meta veri imza sahip.</span><span class="sxs-lookup"><span data-stu-id="0844e-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0844e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0844e-104">Syntax</span></span>  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0844e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0844e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="0844e-106">[in] `mdTypeDef` Aramak için üye kapsayan türü için (bir sınıf veya arabirim) belirteci.</span><span class="sxs-lookup"><span data-stu-id="0844e-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="0844e-107">Bu değer ise `mdTokenNil`, genel bir işlev için arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="0844e-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="0844e-108">[in] Aranacak yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="0844e-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="0844e-109">[in] Yönteminin ikili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0844e-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="0844e-110">[in] Bayt cinsinden boyutu `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="0844e-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="0844e-111">[out] Eşleşen MethodDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0844e-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0844e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0844e-112">Remarks</span></span>  
 <span data-ttu-id="0844e-113">Kapsayan sınıf ya da arabirimi kullanarak yöntemini belirtin (`td`), kendi adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="0844e-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="0844e-114">Bir sınıf ya da arabirimi aynı ada sahip birden çok yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="0844e-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="0844e-115">Bu durumda, benzersiz bir eşleşme bulmak için yöntemin imzası geçirin.</span><span class="sxs-lookup"><span data-stu-id="0844e-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="0844e-116">İmza geçirilen `FindMethod` imzalar için belirli bir kapsam bağlı olduğundan geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0844e-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="0844e-117">İmza kapsayan sınıfı veya değer türünü tanımlayan bir belirteç eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="0844e-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="0844e-118">Belirteç yerel TypeDef tabloya dizinidir.</span><span class="sxs-lookup"><span data-stu-id="0844e-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="0844e-119">Geçerli kapsam bağlamında dışında bir çalışma zamanı imzası oluşturmak ve bu imza olarak giriş için giriş kullanmasına `FindMethod`.</span><span class="sxs-lookup"><span data-stu-id="0844e-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="0844e-120">`FindMethod` doğrudan sınıfta veya arabirimde tanımlanan yöntemler bulur; devralınan yöntemleri bulmaz.</span><span class="sxs-lookup"><span data-stu-id="0844e-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0844e-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0844e-121">Requirements</span></span>  
 <span data-ttu-id="0844e-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0844e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0844e-123">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0844e-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0844e-124">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0844e-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0844e-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0844e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0844e-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0844e-126">See Also</span></span>  
 <xref:System.Reflection.MethodInfo>  
 [<span data-ttu-id="0844e-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0844e-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0844e-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0844e-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
