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
ms.openlocfilehash: 11ea6e468909ea42e38bdc7b76c60c460c98025e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503673"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="20227-102">IMetaDataImport::FindField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20227-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="20227-103">Belirtilen <xref:System.Type> ve belirtilen ad ve meta veri imzasına sahip olan alan Için FieldDef belirtecine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="20227-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20227-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="20227-104">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20227-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20227-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="20227-106">'ndaki Aranacak alanı kapsayan sınıf veya arabirim için TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="20227-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="20227-107">Bu değer ise `mdTokenNil` , arama genel bir değişken için yapılır.</span><span class="sxs-lookup"><span data-stu-id="20227-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="20227-108">'ndaki Aranacak alanın adı.</span><span class="sxs-lookup"><span data-stu-id="20227-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="20227-109">'ndaki Alanın ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="20227-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="20227-110">'ndaki Bayt cinsinden boyut `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="20227-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="20227-111">dışı Eşleşen FieldDef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="20227-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20227-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20227-112">Remarks</span></span>  
 <span data-ttu-id="20227-113">Alanı kapsayan sınıfını veya arabirimini ( `td` ), adını ( `szName` ) ve isteğe bağlı olarak imzasını () kullanarak belirtirsiniz `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="20227-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="20227-114">`FindField`İmzaların belirli bir kapsama bağlandığı için, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20227-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="20227-115">İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="20227-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="20227-116">(Belirteç yerel TypeDef tablosunun bir dizinidir).</span><span class="sxs-lookup"><span data-stu-id="20227-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="20227-117">Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı giriş olarak kullanabilirsiniz `FindField` .</span><span class="sxs-lookup"><span data-stu-id="20227-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="20227-118">`FindField`yalnızca sınıfta veya arabirimde doğrudan tanımlanmış alanları bulur; devralınan alanları bulamaz.</span><span class="sxs-lookup"><span data-stu-id="20227-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20227-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20227-119">Requirements</span></span>  
 <span data-ttu-id="20227-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20227-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20227-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="20227-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="20227-122">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="20227-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="20227-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20227-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20227-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20227-124">See also</span></span>

- [<span data-ttu-id="20227-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20227-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="20227-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20227-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
