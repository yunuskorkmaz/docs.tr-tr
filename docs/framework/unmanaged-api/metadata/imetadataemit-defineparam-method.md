---
title: IMetaDataEmit::DefineParam Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 2807458549db02598ba05f2aa80fa6ea6fbc5a13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177700"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="d8be3-102">IMetaDataEmit::DefineParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8be3-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="d8be3-103">Belirtilen belirteç tarafından başvurulan yöntem için belirtilen imzaile bir parametre tanımı oluşturur ve bu parametre tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="d8be3-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8be3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8be3-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,
    [in]  ULONG       ulParamSeq,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,
    [out] mdParamDef  *ppd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8be3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8be3-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="d8be3-106">[içinde] Parametresi tanımlanan yöntemin belirteci.</span><span class="sxs-lookup"><span data-stu-id="d8be3-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="d8be3-107">[içinde] Parametre sıra numarası.</span><span class="sxs-lookup"><span data-stu-id="d8be3-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="d8be3-108">[içinde] Unicode'daki parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="d8be3-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="d8be3-109">[içinde] Parametre için bayraklar.</span><span class="sxs-lookup"><span data-stu-id="d8be3-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="d8be3-110">Bu `CorParamAttr` değerlerin bir bitmask olduğunu.</span><span class="sxs-lookup"><span data-stu-id="d8be3-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="d8be3-111">[içinde] `ELEMENT_TYPE_` sabit değer *\** için.</span><span class="sxs-lookup"><span data-stu-id="d8be3-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d8be3-112">[içinde] Parametrenin sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="d8be3-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="d8be3-113">[içinde] Unicode karakterlerinin boyutu. `pValue`</span><span class="sxs-lookup"><span data-stu-id="d8be3-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="d8be3-114">[çıkış] Atanan `mdParamDef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="d8be3-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8be3-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8be3-115">Remarks</span></span>  
 <span data-ttu-id="d8be3-116">Parametreler için `ulParamSeq` 1 ile başlarda sıra değerleri.</span><span class="sxs-lookup"><span data-stu-id="d8be3-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="d8be3-117">İade değerinin sıra numarası 0'dır.</span><span class="sxs-lookup"><span data-stu-id="d8be3-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8be3-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8be3-118">Requirements</span></span>  
 <span data-ttu-id="d8be3-119">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8be3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8be3-120">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d8be3-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8be3-121">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d8be3-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8be3-122">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8be3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8be3-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8be3-123">See also</span></span>

- [<span data-ttu-id="d8be3-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8be3-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d8be3-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8be3-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
