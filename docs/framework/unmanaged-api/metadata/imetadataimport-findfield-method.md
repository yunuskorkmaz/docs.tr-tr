---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataImport:: FindField yöntemi'
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
ms.openlocfilehash: b8041a37b91f22722a05aec99c92c4f17c2b0610
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799310"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="db244-103">IMetaDataImport::FindField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db244-103">IMetaDataImport::FindField Method</span></span>

<span data-ttu-id="db244-104">Belirtilen <xref:System.Type> ve belirtilen ad ve meta veri imzasına sahip olan alan Için FieldDef belirtecine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="db244-104">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db244-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db244-105">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db244-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db244-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="db244-107">'ndaki Aranacak alanı kapsayan sınıf veya arabirim için TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="db244-107">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="db244-108">Bu değer ise `mdTokenNil` , arama genel bir değişken için yapılır.</span><span class="sxs-lookup"><span data-stu-id="db244-108">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="db244-109">'ndaki Aranacak alanın adı.</span><span class="sxs-lookup"><span data-stu-id="db244-109">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="db244-110">'ndaki Alanın ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db244-110">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="db244-111">'ndaki Bayt cinsinden boyut `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="db244-111">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="db244-112">dışı Eşleşen FieldDef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db244-112">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db244-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db244-113">Remarks</span></span>  

 <span data-ttu-id="db244-114">Alanı kapsayan sınıfını veya arabirimini ( `td` ), adını ( `szName` ) ve isteğe bağlı olarak imzasını () kullanarak belirtirsiniz `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="db244-114">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="db244-115">`FindField`İmzaların belirli bir kapsama bağlandığı için, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db244-115">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="db244-116">İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="db244-116">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="db244-117">(Belirteç yerel TypeDef tablosunun bir dizinidir).</span><span class="sxs-lookup"><span data-stu-id="db244-117">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="db244-118">Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı giriş olarak kullanabilirsiniz `FindField` .</span><span class="sxs-lookup"><span data-stu-id="db244-118">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="db244-119">`FindField` yalnızca sınıfta veya arabirimde doğrudan tanımlanmış alanları bulur; devralınan alanları bulamaz.</span><span class="sxs-lookup"><span data-stu-id="db244-119">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db244-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db244-120">Requirements</span></span>  

 <span data-ttu-id="db244-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db244-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db244-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="db244-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db244-123">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="db244-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db244-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db244-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db244-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db244-125">See also</span></span>

- [<span data-ttu-id="db244-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db244-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="db244-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db244-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
