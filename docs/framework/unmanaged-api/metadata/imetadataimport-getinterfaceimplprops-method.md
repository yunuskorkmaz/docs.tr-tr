---
description: ': IMetaDataImport:: GetInterfaceImplProps Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6b3c9394bcf37f700c84e1fda0b785dc0c3f4713
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783917"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="f8dbc-103">IMetaDataImport::GetInterfaceImplProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8dbc-103">IMetaDataImport::GetInterfaceImplProps Method</span></span>

<span data-ttu-id="f8dbc-104">Belirtilen yöntemi uygulayan için meta veri belirteçlerine <xref:System.Type> ve bu yöntemi bildiren arabirime yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f8dbc-104">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="f8dbc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f8dbc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8dbc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f8dbc-106">Parameters</span></span>  

 `iiImpl`  
 <span data-ttu-id="f8dbc-107">'ndaki İçin sınıfı ve arabirim belirteçlerini döndürme yöntemini temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="f8dbc-107">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="f8dbc-108">dışı Yöntemi uygulayan sınıfı temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="f8dbc-108">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="f8dbc-109">dışı Uygulanan yöntemi tanımlayan arabirimi temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="f8dbc-109">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="f8dbc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8dbc-110">Remarks</span></span>

 <span data-ttu-id="f8dbc-111">`iImpl` [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) metodunu çağırarak değerini elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="f8dbc-111">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>

 <span data-ttu-id="f8dbc-112">Örneğin, bir sınıfın `mdTypeDef` 0x02000007 belirteç değerine sahip olduğunu ve türleri belirteçleri olan üç arabirim uyguladığını varsayalım:</span><span class="sxs-lookup"><span data-stu-id="f8dbc-112">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span>

- <span data-ttu-id="f8dbc-113">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="f8dbc-113">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="f8dbc-114">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="f8dbc-114">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="f8dbc-115">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="f8dbc-115">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="f8dbc-116">Kavramsal olarak, bu bilgiler bir arabirim uygulama tablosunda şu şekilde depolanır:</span><span class="sxs-lookup"><span data-stu-id="f8dbc-116">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="f8dbc-117">Satır numarası</span><span class="sxs-lookup"><span data-stu-id="f8dbc-117">Row number</span></span> | <span data-ttu-id="f8dbc-118">Sınıf belirteci</span><span class="sxs-lookup"><span data-stu-id="f8dbc-118">Class token</span></span> | <span data-ttu-id="f8dbc-119">Arabirim belirteci</span><span class="sxs-lookup"><span data-stu-id="f8dbc-119">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="f8dbc-120">4</span><span class="sxs-lookup"><span data-stu-id="f8dbc-120">4</span></span>          |             |                 |
| <span data-ttu-id="f8dbc-121">5</span><span class="sxs-lookup"><span data-stu-id="f8dbc-121">5</span></span>          | <span data-ttu-id="f8dbc-122">02000007</span><span class="sxs-lookup"><span data-stu-id="f8dbc-122">02000007</span></span>    | <span data-ttu-id="f8dbc-123">02000003</span><span class="sxs-lookup"><span data-stu-id="f8dbc-123">02000003</span></span>        |
| <span data-ttu-id="f8dbc-124">6</span><span class="sxs-lookup"><span data-stu-id="f8dbc-124">6</span></span>          | <span data-ttu-id="f8dbc-125">02000007</span><span class="sxs-lookup"><span data-stu-id="f8dbc-125">02000007</span></span>    | <span data-ttu-id="f8dbc-126">0100000A</span><span class="sxs-lookup"><span data-stu-id="f8dbc-126">0100000A</span></span>        |
| <span data-ttu-id="f8dbc-127">7</span><span class="sxs-lookup"><span data-stu-id="f8dbc-127">7</span></span>          |             |                 |
| <span data-ttu-id="f8dbc-128">8</span><span class="sxs-lookup"><span data-stu-id="f8dbc-128">8</span></span>          | <span data-ttu-id="f8dbc-129">02000007</span><span class="sxs-lookup"><span data-stu-id="f8dbc-129">02000007</span></span>    | <span data-ttu-id="f8dbc-130">0200001C</span><span class="sxs-lookup"><span data-stu-id="f8dbc-130">0200001C</span></span>        |

<span data-ttu-id="f8dbc-131">Geri çağır, belirteç 4 baytlık bir değerdir:</span><span class="sxs-lookup"><span data-stu-id="f8dbc-131">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="f8dbc-132">Alt 3 bayt satır numarasını veya RID 'yi tutar.</span><span class="sxs-lookup"><span data-stu-id="f8dbc-132">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="f8dbc-133">Üst bayt, için – 0x09 belirteç türünü tutar `mdtInterfaceImpl` .</span><span class="sxs-lookup"><span data-stu-id="f8dbc-133">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="f8dbc-134">`GetInterfaceImplProps` bağımsız değişkeninde sağladığınız satırı içeren satırda tutulan bilgileri döndürür `iImpl` .</span><span class="sxs-lookup"><span data-stu-id="f8dbc-134">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="f8dbc-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8dbc-135">Requirements</span></span>  

 <span data-ttu-id="f8dbc-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8dbc-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8dbc-137">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f8dbc-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f8dbc-138">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f8dbc-138">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8dbc-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8dbc-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8dbc-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8dbc-140">See also</span></span>

- [<span data-ttu-id="f8dbc-141">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f8dbc-141">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f8dbc-142">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f8dbc-142">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
