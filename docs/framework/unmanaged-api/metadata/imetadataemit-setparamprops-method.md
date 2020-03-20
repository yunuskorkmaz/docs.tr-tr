---
title: IMetaDataEmit::SetParamProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
ms.openlocfilehash: 13220dcfdd260688494d5aebc50f94abf8a82215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177502"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="60f67-102">IMetaDataEmit::SetParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60f67-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="60f67-103">[IMetaDataEmit::DefineParam'a](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)yapılan bir önceki çağrı yla tanımlanan yöntem parametresinin özelliklerini ayarlar veya değiştirir.</span><span class="sxs-lookup"><span data-stu-id="60f67-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60f67-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60f67-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParamProps (
    [in]  mdParamDef  pd,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60f67-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60f67-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="60f67-106">[içinde] Hedef parametrenin belirteci.</span><span class="sxs-lookup"><span data-stu-id="60f67-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="60f67-107">[içinde] Unicode'daki parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="60f67-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="60f67-108">[içinde] Parametre nin bayrakları.</span><span class="sxs-lookup"><span data-stu-id="60f67-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="60f67-109">[içinde] Sabit değer için ELEMENT_TYPE_\*.</span><span class="sxs-lookup"><span data-stu-id="60f67-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="60f67-110">[içinde] Parametrenin sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="60f67-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="60f67-111">[içinde] (Unicode) karakterlerinin `pValue`boyutu.</span><span class="sxs-lookup"><span data-stu-id="60f67-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60f67-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60f67-112">Requirements</span></span>  
 <span data-ttu-id="60f67-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60f67-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60f67-114">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="60f67-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="60f67-115">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="60f67-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60f67-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60f67-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60f67-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60f67-117">See also</span></span>

- [<span data-ttu-id="60f67-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60f67-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="60f67-119">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60f67-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
