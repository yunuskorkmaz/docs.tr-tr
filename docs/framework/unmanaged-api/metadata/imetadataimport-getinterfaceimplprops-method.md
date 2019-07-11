---
title: IMetaDataImport::GetInterfaceImplProps Yöntemi
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a4305b94d785a764671a2d73f43facefd0da0e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782367"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="4cf50-102">IMetaDataImport::GetInterfaceImplProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cf50-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="4cf50-103">Meta veri belirteçleri için bir işaretçi alır <xref:System.Type> belirtilen yöntemini uygulayan ve arabirim için bu yöntem bildirir.</span><span class="sxs-lookup"><span data-stu-id="4cf50-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="4cf50-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cf50-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cf50-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4cf50-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="4cf50-106">[in] Sınıf ve arabirim belirteçleri için döndürülecek yöntemi temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="4cf50-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="4cf50-107">[out] Yöntemini uygulayan bir sınıfı temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="4cf50-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="4cf50-108">[out] Uygulanan yöntemi tanımlar arabirimi temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="4cf50-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="4cf50-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cf50-109">Remarks</span></span>

 <span data-ttu-id="4cf50-110">Değeri elde `iImpl` çağırarak [Enumınterfaceımpls](imetadataimport-enuminterfaceimpls-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4cf50-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>
 
 <span data-ttu-id="4cf50-111">Örneğin, bir sınıf olduğunu varsayalım. bir `mdTypeDef` belirteç 0x02000007 değeri ile eşleşen türleri belirteçleri sahip üç arabirimi uygular:</span><span class="sxs-lookup"><span data-stu-id="4cf50-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span> 

- <span data-ttu-id="4cf50-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="4cf50-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="4cf50-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="4cf50-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="4cf50-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="4cf50-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="4cf50-115">Kavramsal olarak, bu bilgileri, bir arabirim uygulaması tablosuna depolanır:</span><span class="sxs-lookup"><span data-stu-id="4cf50-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="4cf50-116">Satır numarası</span><span class="sxs-lookup"><span data-stu-id="4cf50-116">Row number</span></span> | <span data-ttu-id="4cf50-117">Sınıf simgesi</span><span class="sxs-lookup"><span data-stu-id="4cf50-117">Class token</span></span> | <span data-ttu-id="4cf50-118">Belirteç arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cf50-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="4cf50-119">4</span><span class="sxs-lookup"><span data-stu-id="4cf50-119">4</span></span>          |             |                 |
| <span data-ttu-id="4cf50-120">5</span><span class="sxs-lookup"><span data-stu-id="4cf50-120">5</span></span>          | <span data-ttu-id="4cf50-121">02000007</span><span class="sxs-lookup"><span data-stu-id="4cf50-121">02000007</span></span>    | <span data-ttu-id="4cf50-122">02000003</span><span class="sxs-lookup"><span data-stu-id="4cf50-122">02000003</span></span>        |
| <span data-ttu-id="4cf50-123">6</span><span class="sxs-lookup"><span data-stu-id="4cf50-123">6</span></span>          | <span data-ttu-id="4cf50-124">02000007</span><span class="sxs-lookup"><span data-stu-id="4cf50-124">02000007</span></span>    | <span data-ttu-id="4cf50-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="4cf50-125">0100000A</span></span>        |
| <span data-ttu-id="4cf50-126">7</span><span class="sxs-lookup"><span data-stu-id="4cf50-126">7</span></span>          |             |                 |
| <span data-ttu-id="4cf50-127">8</span><span class="sxs-lookup"><span data-stu-id="4cf50-127">8</span></span>          | <span data-ttu-id="4cf50-128">02000007</span><span class="sxs-lookup"><span data-stu-id="4cf50-128">02000007</span></span>    | <span data-ttu-id="4cf50-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="4cf50-129">0200001C</span></span>        |

<span data-ttu-id="4cf50-130">Geri çağırırsanız, belirteç bir 4 baytlık değerdir:</span><span class="sxs-lookup"><span data-stu-id="4cf50-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="4cf50-131">Daha düşük 3 baytlar satır numarasına tutun veya RID.</span><span class="sxs-lookup"><span data-stu-id="4cf50-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="4cf50-132">Belirteç türü – 0x09 için üst bayt tutar `mdtInterfaceImpl`.</span><span class="sxs-lookup"><span data-stu-id="4cf50-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="4cf50-133">`GetInterfaceImplProps` bilgi tutulan belirteç tarafınıza sıradaki döndürür `iImpl` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="4cf50-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="4cf50-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4cf50-134">Requirements</span></span>  
 <span data-ttu-id="4cf50-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cf50-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cf50-136">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4cf50-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4cf50-137">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4cf50-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4cf50-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cf50-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf50-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cf50-139">See also</span></span>

- [<span data-ttu-id="4cf50-140">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cf50-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4cf50-141">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cf50-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
