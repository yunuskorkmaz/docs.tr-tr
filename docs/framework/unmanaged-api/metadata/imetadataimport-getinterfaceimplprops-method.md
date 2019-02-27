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
ms.openlocfilehash: dc16d01d45364d1a17f281f859b27c3e48342ff0
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835726"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="94d8a-102">IMetaDataImport::GetInterfaceImplProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94d8a-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="94d8a-103">Meta veri belirteçleri için bir işaretçi alır <xref:System.Type> belirtilen yöntemini uygulayan ve arabirim için bu yöntem bildirir.</span><span class="sxs-lookup"><span data-stu-id="94d8a-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="94d8a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94d8a-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94d8a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94d8a-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="94d8a-106">[in] Sınıf ve arabirim belirteçleri için döndürülecek yöntemi temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="94d8a-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="94d8a-107">[out] Yöntemini uygulayan bir sınıfı temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="94d8a-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="94d8a-108">[out] Uygulanan yöntemi tanımlar arabirimi temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="94d8a-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="94d8a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94d8a-109">Remarks</span></span>

 <span data-ttu-id="94d8a-110">Değeri elde `iImpl` çağırarak [Enumınterfaceımpls](imetadataimport-enuminterfaceimpls-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="94d8a-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>
 
 <span data-ttu-id="94d8a-111">Örneğin, bir sınıf olduğunu varsayalım. bir `mdTypeDef` belirteç 0x02000007 değeri ile eşleşen türleri belirteçleri sahip üç arabirimi uygular:</span><span class="sxs-lookup"><span data-stu-id="94d8a-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span> 

- <span data-ttu-id="94d8a-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="94d8a-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="94d8a-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="94d8a-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="94d8a-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="94d8a-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="94d8a-115">Kavramsal olarak, bu bilgileri, bir arabirim uygulaması tablosuna depolanır:</span><span class="sxs-lookup"><span data-stu-id="94d8a-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="94d8a-116">Satır numarası</span><span class="sxs-lookup"><span data-stu-id="94d8a-116">Row number</span></span> | <span data-ttu-id="94d8a-117">Sınıf simgesi</span><span class="sxs-lookup"><span data-stu-id="94d8a-117">Class token</span></span> | <span data-ttu-id="94d8a-118">Belirteç arabirimi</span><span class="sxs-lookup"><span data-stu-id="94d8a-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="94d8a-119">4</span><span class="sxs-lookup"><span data-stu-id="94d8a-119">4</span></span>          |             |                 |
| <span data-ttu-id="94d8a-120">5</span><span class="sxs-lookup"><span data-stu-id="94d8a-120">5</span></span>          | <span data-ttu-id="94d8a-121">02000007</span><span class="sxs-lookup"><span data-stu-id="94d8a-121">02000007</span></span>    | <span data-ttu-id="94d8a-122">02000003</span><span class="sxs-lookup"><span data-stu-id="94d8a-122">02000003</span></span>        |
| <span data-ttu-id="94d8a-123">6</span><span class="sxs-lookup"><span data-stu-id="94d8a-123">6</span></span>          | <span data-ttu-id="94d8a-124">02000007</span><span class="sxs-lookup"><span data-stu-id="94d8a-124">02000007</span></span>    | <span data-ttu-id="94d8a-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="94d8a-125">0100000A</span></span>        |
| <span data-ttu-id="94d8a-126">7</span><span class="sxs-lookup"><span data-stu-id="94d8a-126">7</span></span>          |             |                 |
| <span data-ttu-id="94d8a-127">8</span><span class="sxs-lookup"><span data-stu-id="94d8a-127">8</span></span>          | <span data-ttu-id="94d8a-128">02000007</span><span class="sxs-lookup"><span data-stu-id="94d8a-128">02000007</span></span>    | <span data-ttu-id="94d8a-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="94d8a-129">0200001C</span></span>        |

<span data-ttu-id="94d8a-130">Geri çağırırsanız, belirteç bir 4 baytlık değerdir:</span><span class="sxs-lookup"><span data-stu-id="94d8a-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="94d8a-131">Daha düşük 3 baytlar satır numarasına tutun veya RID.</span><span class="sxs-lookup"><span data-stu-id="94d8a-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="94d8a-132">Belirteç türü – 0x09 için üst bayt tutar `mdtInterfaceImpl`.</span><span class="sxs-lookup"><span data-stu-id="94d8a-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="94d8a-133">`GetInterfaceImplProps` bilgi tutulan belirteç tarafınıza sıradaki döndürür `iImpl` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="94d8a-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="94d8a-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94d8a-134">Requirements</span></span>  
 <span data-ttu-id="94d8a-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94d8a-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94d8a-136">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="94d8a-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="94d8a-137">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="94d8a-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="94d8a-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94d8a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94d8a-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94d8a-139">See also</span></span>
- [<span data-ttu-id="94d8a-140">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94d8a-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="94d8a-141">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94d8a-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
