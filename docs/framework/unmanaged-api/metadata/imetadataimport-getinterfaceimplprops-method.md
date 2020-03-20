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
ms.openlocfilehash: 4b8ddf7fec12d175f030c0ea0ed982c6fb334aee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175388"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="366af-102">IMetaDataImport::GetInterfaceImplProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="366af-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="366af-103">Belirtilen yöntemi uygulayanlar ve bu yöntemi <xref:System.Type> bildiren arabirim için meta veri belirteçleri için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="366af-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="366af-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="366af-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="366af-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="366af-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="366af-106">[içinde] Sınıf ve arabirim belirteçlerini döndürme yöntemini temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="366af-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="366af-107">[çıkış] Yöntemi uygulayan sınıfı temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="366af-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="366af-108">[çıkış] Uygulanan yöntemi tanımlayan arabirimi temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="366af-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="366af-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="366af-109">Remarks</span></span>

 <span data-ttu-id="366af-110">`iImpl` [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) yöntemini arayarak değer elde elabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="366af-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>

 <span data-ttu-id="366af-111">Örneğin, bir sınıfın 0x02000007 `mdTypeDef` belirteç değerine sahip olduğunu ve türleri belirteçleri olan üç arabirim uyguladığını varsayalım:</span><span class="sxs-lookup"><span data-stu-id="366af-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span>

- <span data-ttu-id="366af-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="366af-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="366af-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="366af-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="366af-114">0x020001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="366af-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="366af-115">Kavramsal olarak, bu bilgiler bir arayüz uygulama tablosunda şu şekilde depolanır:</span><span class="sxs-lookup"><span data-stu-id="366af-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="366af-116">Satır numarası</span><span class="sxs-lookup"><span data-stu-id="366af-116">Row number</span></span> | <span data-ttu-id="366af-117">Sınıf belirteci</span><span class="sxs-lookup"><span data-stu-id="366af-117">Class token</span></span> | <span data-ttu-id="366af-118">Arabirim belirteci</span><span class="sxs-lookup"><span data-stu-id="366af-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="366af-119">4</span><span class="sxs-lookup"><span data-stu-id="366af-119">4</span></span>          |             |                 |
| <span data-ttu-id="366af-120">5</span><span class="sxs-lookup"><span data-stu-id="366af-120">5</span></span>          | <span data-ttu-id="366af-121">02000007</span><span class="sxs-lookup"><span data-stu-id="366af-121">02000007</span></span>    | <span data-ttu-id="366af-122">02000003</span><span class="sxs-lookup"><span data-stu-id="366af-122">02000003</span></span>        |
| <span data-ttu-id="366af-123">6</span><span class="sxs-lookup"><span data-stu-id="366af-123">6</span></span>          | <span data-ttu-id="366af-124">02000007</span><span class="sxs-lookup"><span data-stu-id="366af-124">02000007</span></span>    | <span data-ttu-id="366af-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="366af-125">0100000A</span></span>        |
| <span data-ttu-id="366af-126">7</span><span class="sxs-lookup"><span data-stu-id="366af-126">7</span></span>          |             |                 |
| <span data-ttu-id="366af-127">8</span><span class="sxs-lookup"><span data-stu-id="366af-127">8</span></span>          | <span data-ttu-id="366af-128">02000007</span><span class="sxs-lookup"><span data-stu-id="366af-128">02000007</span></span>    | <span data-ttu-id="366af-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="366af-129">0200001C</span></span>        |

<span data-ttu-id="366af-130">Geri çağırma, belirteç 4 bayt lık bir değerdir:</span><span class="sxs-lookup"><span data-stu-id="366af-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="366af-131">Alt 3 bayt satır numarasını veya RID'yi tutar.</span><span class="sxs-lookup"><span data-stu-id="366af-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="366af-132">Üst bayt belirteç türünü tutar – `mdtInterfaceImpl`0x09 için .</span><span class="sxs-lookup"><span data-stu-id="366af-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="366af-133">`GetInterfaceImplProps`satırda tutulan ve bağımsız değişkende belirteç verdiğiniz bilgileri döndürür. `iImpl`</span><span class="sxs-lookup"><span data-stu-id="366af-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="366af-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="366af-134">Requirements</span></span>  
 <span data-ttu-id="366af-135">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="366af-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="366af-136">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="366af-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="366af-137">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="366af-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="366af-138">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="366af-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="366af-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="366af-139">See also</span></span>

- [<span data-ttu-id="366af-140">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="366af-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="366af-141">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="366af-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
