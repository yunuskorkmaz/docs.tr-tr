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
ms.openlocfilehash: e5eb735acac73d694a0719c206bd22711a8c0333
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437544"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="145c0-102">IMetaDataImport::GetInterfaceImplProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="145c0-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="145c0-103">Belirtilen yöntemi uygulayan <xref:System.Type> için meta veri belirteçleri ve bu yöntemi bildiren arabirim için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="145c0-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="145c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="145c0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="145c0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="145c0-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="145c0-106">'ndaki İçin sınıfı ve arabirim belirteçlerini döndürme yöntemini temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="145c0-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="145c0-107">dışı Yöntemi uygulayan sınıfı temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="145c0-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="145c0-108">dışı Uygulanan yöntemi tanımlayan arabirimi temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="145c0-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="145c0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="145c0-109">Remarks</span></span>

 <span data-ttu-id="145c0-110">[EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) yöntemini çağırarak `iImpl` değerini elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="145c0-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>
 
 <span data-ttu-id="145c0-111">Örneğin, bir sınıfın 0x02000007 `mdTypeDef` belirteç değerine sahip olduğunu ve türleri belirteçleri olan üç arabirim uyguladığını varsayalım:</span><span class="sxs-lookup"><span data-stu-id="145c0-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span> 

- <span data-ttu-id="145c0-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="145c0-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="145c0-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="145c0-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="145c0-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="145c0-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="145c0-115">Kavramsal olarak, bu bilgiler bir arabirim uygulama tablosunda şu şekilde depolanır:</span><span class="sxs-lookup"><span data-stu-id="145c0-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="145c0-116">Satır numarası</span><span class="sxs-lookup"><span data-stu-id="145c0-116">Row number</span></span> | <span data-ttu-id="145c0-117">Sınıf belirteci</span><span class="sxs-lookup"><span data-stu-id="145c0-117">Class token</span></span> | <span data-ttu-id="145c0-118">Arabirim belirteci</span><span class="sxs-lookup"><span data-stu-id="145c0-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="145c0-119">4</span><span class="sxs-lookup"><span data-stu-id="145c0-119">4</span></span>          |             |                 |
| <span data-ttu-id="145c0-120">5</span><span class="sxs-lookup"><span data-stu-id="145c0-120">5</span></span>          | <span data-ttu-id="145c0-121">02000007</span><span class="sxs-lookup"><span data-stu-id="145c0-121">02000007</span></span>    | <span data-ttu-id="145c0-122">02000003</span><span class="sxs-lookup"><span data-stu-id="145c0-122">02000003</span></span>        |
| <span data-ttu-id="145c0-123">6</span><span class="sxs-lookup"><span data-stu-id="145c0-123">6</span></span>          | <span data-ttu-id="145c0-124">02000007</span><span class="sxs-lookup"><span data-stu-id="145c0-124">02000007</span></span>    | <span data-ttu-id="145c0-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="145c0-125">0100000A</span></span>        |
| <span data-ttu-id="145c0-126">7</span><span class="sxs-lookup"><span data-stu-id="145c0-126">7</span></span>          |             |                 |
| <span data-ttu-id="145c0-127">8</span><span class="sxs-lookup"><span data-stu-id="145c0-127">8</span></span>          | <span data-ttu-id="145c0-128">02000007</span><span class="sxs-lookup"><span data-stu-id="145c0-128">02000007</span></span>    | <span data-ttu-id="145c0-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="145c0-129">0200001C</span></span>        |

<span data-ttu-id="145c0-130">Geri çağır, belirteç 4 baytlık bir değerdir:</span><span class="sxs-lookup"><span data-stu-id="145c0-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="145c0-131">Alt 3 bayt satır numarasını veya RID 'yi tutar.</span><span class="sxs-lookup"><span data-stu-id="145c0-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="145c0-132">Üst bayt `mdtInterfaceImpl`için 0x09 belirteç türünü tutar.</span><span class="sxs-lookup"><span data-stu-id="145c0-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="145c0-133">`GetInterfaceImplProps`, belirtecini `iImpl` bağımsız değişkeninde sağladığınız satırda tutulan bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="145c0-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="145c0-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="145c0-134">Requirements</span></span>  
 <span data-ttu-id="145c0-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="145c0-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="145c0-136">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="145c0-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="145c0-137">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="145c0-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="145c0-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="145c0-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="145c0-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="145c0-139">See also</span></span>

- [<span data-ttu-id="145c0-140">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="145c0-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="145c0-141">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="145c0-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
