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
ms.openlocfilehash: d8b8bfd0e70e75c702f32555c10f433a1ff4ae10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175427"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="6e822-102">IMetaDataImport::FindMemberRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e822-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="6e822-103">Belirtilen <xref:System.Type> ad ve meta veri imzasına sahip üye başvurusu için Üye Ref belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="6e822-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e822-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e822-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e822-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e822-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="6e822-106">[içinde] Arama için üye başvuruyu içine alan sınıf veya arabirim için TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="6e822-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="6e822-107">Bu değer `mdTokenNil`ise, arama genel değişken veya genel işlev başvurusu için yapılır.</span><span class="sxs-lookup"><span data-stu-id="6e822-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="6e822-108">[içinde] Aranacak üye nin adı.</span><span class="sxs-lookup"><span data-stu-id="6e822-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="6e822-109">[içinde] Üye başvurunun ikili meta veri imzasına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6e822-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="6e822-110">[içinde] `pvSigBlob`Baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="6e822-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="6e822-111">[çıkış] Eşleşen ÜyeRef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6e822-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e822-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e822-112">Remarks</span></span>  
 <span data-ttu-id="6e822-113">Üyeyi çevreleyen sınıfını veya arayüzünü`td`( ),`szName`adını ( ),`pvSigBlob`ve isteğe bağlı olarak imzasını ( ) kullanarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e822-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="6e822-114">İmzalar belirli `FindMemberRef` bir kapsama bağlı olduğundan, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6e822-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="6e822-115">İmza, çevreleyen sınıfı veya değer türünü tanımlayan bir belirteç katıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="6e822-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="6e822-116">Belirteç, yerel TypeDef tablosuna bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="6e822-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="6e822-117">Geçerli kapsam bağlamının dışında bir çalışma zamanı imzası oluşturamazsınız ve `FindMemberRef`bu imzayı 'ye giriş olarak kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="6e822-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="6e822-118">`FindMemberRef`yalnızca doğrudan sınıf veya arabirimde tanımlanmış üye başvuruları bulur; devralınan üye referansları bulamaz.</span><span class="sxs-lookup"><span data-stu-id="6e822-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e822-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e822-119">Requirements</span></span>  
 <span data-ttu-id="6e822-120">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e822-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e822-121">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6e822-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e822-122">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="6e822-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6e822-123">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e822-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e822-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e822-124">See also</span></span>

- [<span data-ttu-id="6e822-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e822-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6e822-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e822-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
