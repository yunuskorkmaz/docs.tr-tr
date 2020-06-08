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
ms.openlocfilehash: 1c9d9647084aa729817eeeb17ee3f5cd320c0d29
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491255"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="33a78-102">IMetaDataImport::GetInterfaceImplProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33a78-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="33a78-103">Belirtilen yöntemi uygulayan için meta veri belirteçlerine <xref:System.Type> ve bu yöntemi bildiren arabirime yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="33a78-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="33a78-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="33a78-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33a78-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="33a78-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="33a78-106">'ndaki İçin sınıfı ve arabirim belirteçlerini döndürme yöntemini temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="33a78-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="33a78-107">dışı Yöntemi uygulayan sınıfı temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="33a78-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="33a78-108">dışı Uygulanan yöntemi tanımlayan arabirimi temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="33a78-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="33a78-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33a78-109">Remarks</span></span>

 <span data-ttu-id="33a78-110">`iImpl` [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) metodunu çağırarak değerini elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="33a78-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>

 <span data-ttu-id="33a78-111">Örneğin, bir sınıfın `mdTypeDef` 0x02000007 belirteç değerine sahip olduğunu ve türleri belirteçleri olan üç arabirim uyguladığını varsayalım:</span><span class="sxs-lookup"><span data-stu-id="33a78-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span>

- <span data-ttu-id="33a78-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="33a78-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="33a78-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="33a78-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="33a78-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="33a78-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="33a78-115">Kavramsal olarak, bu bilgiler bir arabirim uygulama tablosunda şu şekilde depolanır:</span><span class="sxs-lookup"><span data-stu-id="33a78-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="33a78-116">Satır numarası</span><span class="sxs-lookup"><span data-stu-id="33a78-116">Row number</span></span> | <span data-ttu-id="33a78-117">Sınıf belirteci</span><span class="sxs-lookup"><span data-stu-id="33a78-117">Class token</span></span> | <span data-ttu-id="33a78-118">Arabirim belirteci</span><span class="sxs-lookup"><span data-stu-id="33a78-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="33a78-119">4</span><span class="sxs-lookup"><span data-stu-id="33a78-119">4</span></span>          |             |                 |
| <span data-ttu-id="33a78-120">5</span><span class="sxs-lookup"><span data-stu-id="33a78-120">5</span></span>          | <span data-ttu-id="33a78-121">02000007</span><span class="sxs-lookup"><span data-stu-id="33a78-121">02000007</span></span>    | <span data-ttu-id="33a78-122">02000003</span><span class="sxs-lookup"><span data-stu-id="33a78-122">02000003</span></span>        |
| <span data-ttu-id="33a78-123">6</span><span class="sxs-lookup"><span data-stu-id="33a78-123">6</span></span>          | <span data-ttu-id="33a78-124">02000007</span><span class="sxs-lookup"><span data-stu-id="33a78-124">02000007</span></span>    | <span data-ttu-id="33a78-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="33a78-125">0100000A</span></span>        |
| <span data-ttu-id="33a78-126">7</span><span class="sxs-lookup"><span data-stu-id="33a78-126">7</span></span>          |             |                 |
| <span data-ttu-id="33a78-127">8</span><span class="sxs-lookup"><span data-stu-id="33a78-127">8</span></span>          | <span data-ttu-id="33a78-128">02000007</span><span class="sxs-lookup"><span data-stu-id="33a78-128">02000007</span></span>    | <span data-ttu-id="33a78-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="33a78-129">0200001C</span></span>        |

<span data-ttu-id="33a78-130">Geri çağır, belirteç 4 baytlık bir değerdir:</span><span class="sxs-lookup"><span data-stu-id="33a78-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="33a78-131">Alt 3 bayt satır numarasını veya RID 'yi tutar.</span><span class="sxs-lookup"><span data-stu-id="33a78-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="33a78-132">Üst bayt, için – 0x09 belirteç türünü tutar `mdtInterfaceImpl` .</span><span class="sxs-lookup"><span data-stu-id="33a78-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="33a78-133">`GetInterfaceImplProps`bağımsız değişkeninde sağladığınız satırı içeren satırda tutulan bilgileri döndürür `iImpl` .</span><span class="sxs-lookup"><span data-stu-id="33a78-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="33a78-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33a78-134">Requirements</span></span>  
 <span data-ttu-id="33a78-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33a78-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33a78-136">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="33a78-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33a78-137">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="33a78-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="33a78-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33a78-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a78-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33a78-139">See also</span></span>

- [<span data-ttu-id="33a78-140">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33a78-140">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="33a78-141">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33a78-141">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
