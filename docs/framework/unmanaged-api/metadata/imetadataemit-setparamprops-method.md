---
description: ': Imetadatayayma:: SetParamProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 35e839b05b3671c6c09f315ac636971c386e766e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772033"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="a392b-103">IMetaDataEmit::SetParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a392b-103">IMetaDataEmit::SetParamProps Method</span></span>

<span data-ttu-id="a392b-104">Imetadatayayma için önceki bir çağrı tarafından tanımlanan bir yöntem parametresinin özelliklerini ayarlar veya değiştirir [::D efineParam](imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="a392b-104">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a392b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a392b-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a392b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a392b-106">Parameters</span></span>  

 `pd`  
 <span data-ttu-id="a392b-107">'ndaki Hedef parametrenin belirteci.</span><span class="sxs-lookup"><span data-stu-id="a392b-107">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="a392b-108">'ndaki Parametrenin Unicode olarak adı.</span><span class="sxs-lookup"><span data-stu-id="a392b-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="a392b-109">'ndaki Parametresinin bayrakları.</span><span class="sxs-lookup"><span data-stu-id="a392b-109">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="a392b-110">'ndaki Sabit değer için ELEMENT_TYPE_ \*.</span><span class="sxs-lookup"><span data-stu-id="a392b-110">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="a392b-111">'ndaki Parametrenin sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="a392b-111">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="a392b-112">'ndaki (Unicode) karakter boyutu `pValue` .</span><span class="sxs-lookup"><span data-stu-id="a392b-112">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a392b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a392b-113">Requirements</span></span>  

 <span data-ttu-id="a392b-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a392b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a392b-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a392b-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a392b-116">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a392b-116">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a392b-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a392b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a392b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a392b-118">See also</span></span>

- [<span data-ttu-id="a392b-119">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a392b-119">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a392b-120">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a392b-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
