---
description: ': IMetaDataImport:: GetParamProps Yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::GetParamProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: 2c48215836dfb3ae44edc9a2bf10d4028fd82bb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728125"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="17795-103">IMetaDataImport::GetParamProps Metodu</span><span class="sxs-lookup"><span data-stu-id="17795-103">IMetaDataImport::GetParamProps Method</span></span>

<span data-ttu-id="17795-104">Belirtilen ParamDef belirtecinin başvurduğu parametreye ait meta veri değerlerini alır.</span><span class="sxs-lookup"><span data-stu-id="17795-104">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17795-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17795-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17795-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17795-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="17795-107">'ndaki Meta verilerini döndürecek parametreyi temsil eden ParamDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="17795-107">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="17795-108">dışı Parametreyi alan yöntemi temsil eden bir MethodDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="17795-108">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="17795-109">dışı Yöntem bağımsız değişken listesindeki parametresinin sıra konumu.</span><span class="sxs-lookup"><span data-stu-id="17795-109">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="17795-110">dışı Parametrenin adını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="17795-110">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="17795-111">'ndaki Geniş karakterdeki istenen boyut `szName` .</span><span class="sxs-lookup"><span data-stu-id="17795-111">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="17795-112">dışı Geniş karakter olarak döndürülen boyut `szName` .</span><span class="sxs-lookup"><span data-stu-id="17795-112">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="17795-113">dışı Parametresiyle ilişkili öznitelik bayraklarının bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="17795-113">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="17795-114">Bu bir değer bit değeridir `CorParamAttr` .</span><span class="sxs-lookup"><span data-stu-id="17795-114">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="17795-115">dışı Parametresinin bir olduğunu belirten bayrak işaretçisi <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="17795-115">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="17795-116">dışı Parametresi tarafından döndürülen sabit dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="17795-116">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="17795-117">dışı `ppValue` Geniş karakter veya dize yoksa sıfır olan boyut `ppValue` .</span><span class="sxs-lookup"><span data-stu-id="17795-117">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17795-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17795-118">Remarks</span></span>

<span data-ttu-id="17795-119">İçindeki sıra değerleri, `pulSequence` Parametreler için 1 ile başlar.</span><span class="sxs-lookup"><span data-stu-id="17795-119">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="17795-120">Dönüş değerinin sıra numarası 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="17795-120">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="17795-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17795-121">Requirements</span></span>  

 <span data-ttu-id="17795-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17795-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17795-123">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="17795-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17795-124">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="17795-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="17795-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17795-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17795-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17795-126">See also</span></span>

- [<span data-ttu-id="17795-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17795-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="17795-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17795-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
