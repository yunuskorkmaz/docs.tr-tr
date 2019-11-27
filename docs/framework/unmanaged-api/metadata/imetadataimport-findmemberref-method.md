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
ms.openlocfilehash: 59512cc1c1b280d7fe6deb2f9d721ad53547e356
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437962"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="62ade-102">IMetaDataImport::FindMemberRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62ade-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="62ade-103">Belirtilen <xref:System.Type> içine alınmış ve belirtilen ad ve meta veri imzasına sahip olan üye başvurusunun MemberRef belirtecine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="62ade-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ade-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62ade-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62ade-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62ade-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="62ade-106">'ndaki Arama için üye başvurusunu kapsayan sınıf veya arabirim için TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="62ade-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="62ade-107">Bu değer `mdTokenNil`, arama genel bir değişken veya genel işlev başvurusu için yapılır.</span><span class="sxs-lookup"><span data-stu-id="62ade-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="62ade-108">'ndaki Arama yapılacak üye başvurusunun adı.</span><span class="sxs-lookup"><span data-stu-id="62ade-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="62ade-109">'ndaki Üye başvurusunun ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="62ade-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="62ade-110">'ndaki `pvSigBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="62ade-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="62ade-111">dışı Eşleşen MemberRef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="62ade-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62ade-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62ade-112">Remarks</span></span>  
 <span data-ttu-id="62ade-113">Üyeyi kapsayan sınıfını veya arabirimini (`td`), adını (`szName`) ve isteğe bağlı olarak imzasını (`pvSigBlob`) kullanarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62ade-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="62ade-114">İmzaların belirli bir kapsama bağlandığı için `FindMemberRef` geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62ade-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="62ade-115">İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="62ade-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="62ade-116">Belirteç, yerel TypeDef tablosunun bir dizinidir.</span><span class="sxs-lookup"><span data-stu-id="62ade-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="62ade-117">Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı `FindMemberRef`giriş olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62ade-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="62ade-118">`FindMemberRef` yalnızca sınıfta veya arabirimde doğrudan tanımlanmış üye başvurularını bulur; devralınan üye başvurularını bulmaz.</span><span class="sxs-lookup"><span data-stu-id="62ade-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62ade-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62ade-119">Requirements</span></span>  
 <span data-ttu-id="62ade-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62ade-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62ade-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="62ade-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="62ade-122">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="62ade-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="62ade-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62ade-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ade-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62ade-124">See also</span></span>

- [<span data-ttu-id="62ade-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="62ade-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="62ade-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="62ade-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
