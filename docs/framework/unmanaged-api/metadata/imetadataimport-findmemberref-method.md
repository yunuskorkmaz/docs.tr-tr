---
title: IMetaDataImport::FindMemberRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: 0ba25c981cc389baf06ecca0db543d48ac60317b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711409"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="069e2-102">IMetaDataImport::FindMemberRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="069e2-102">IMetaDataImport::FindMemberRef Method</span></span>

<span data-ttu-id="069e2-103">Belirtilen <xref:System.Type> ve belirtilen ad ve meta veri imzasına sahip olan üye başvurusu Için MemberRef belirtecine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="069e2-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="069e2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="069e2-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="069e2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="069e2-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="069e2-106">'ndaki Arama için üye başvurusunu kapsayan sınıf veya arabirim için TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="069e2-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="069e2-107">Bu değer ise `mdTokenNil` , arama genel bir değişken veya genel işlev başvurusu için yapılır.</span><span class="sxs-lookup"><span data-stu-id="069e2-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="069e2-108">'ndaki Arama yapılacak üye başvurusunun adı.</span><span class="sxs-lookup"><span data-stu-id="069e2-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="069e2-109">'ndaki Üye başvurusunun ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="069e2-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="069e2-110">'ndaki Bayt cinsinden boyut `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="069e2-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="069e2-111">dışı Eşleşen MemberRef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="069e2-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="069e2-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="069e2-112">Remarks</span></span>  

 <span data-ttu-id="069e2-113">Üyeyi kapsayan sınıfını veya arabirimini ( `td` ), adını ( `szName` ) ve isteğe bağlı olarak imzasını () kullanarak belirtirsiniz `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="069e2-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="069e2-114">`FindMemberRef`İmzaların belirli bir kapsama bağlandığı için, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="069e2-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="069e2-115">İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="069e2-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="069e2-116">Belirteç, yerel TypeDef tablosunun bir dizinidir.</span><span class="sxs-lookup"><span data-stu-id="069e2-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="069e2-117">Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı giriş olarak kullanabilirsiniz `FindMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="069e2-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="069e2-118">`FindMemberRef` yalnızca sınıfta veya arabirimde doğrudan tanımlanmış üye başvurularını bulur; devralınan üye başvurularını bulmaz.</span><span class="sxs-lookup"><span data-stu-id="069e2-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="069e2-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="069e2-119">Requirements</span></span>  

 <span data-ttu-id="069e2-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="069e2-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="069e2-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="069e2-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="069e2-122">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="069e2-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="069e2-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="069e2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="069e2-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="069e2-124">See also</span></span>

- [<span data-ttu-id="069e2-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="069e2-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="069e2-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="069e2-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
