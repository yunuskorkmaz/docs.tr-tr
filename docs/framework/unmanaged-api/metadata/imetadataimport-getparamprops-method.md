---
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
ms.openlocfilehash: c2abf2813c6e1a9db4264bded32d9cb9c58a2bcb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491062"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="115b5-102">IMetaDataImport::GetParamProps Metodu</span><span class="sxs-lookup"><span data-stu-id="115b5-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="115b5-103">Belirtilen ParamDef belirtecinin başvurduğu parametreye ait meta veri değerlerini alır.</span><span class="sxs-lookup"><span data-stu-id="115b5-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="115b5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="115b5-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="115b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="115b5-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="115b5-106">'ndaki Meta verilerini döndürecek parametreyi temsil eden ParamDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="115b5-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="115b5-107">dışı Parametreyi alan yöntemi temsil eden bir MethodDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="115b5-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="115b5-108">dışı Yöntem bağımsız değişken listesindeki parametresinin sıra konumu.</span><span class="sxs-lookup"><span data-stu-id="115b5-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="115b5-109">dışı Parametrenin adını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="115b5-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="115b5-110">'ndaki Geniş karakterdeki istenen boyut `szName` .</span><span class="sxs-lookup"><span data-stu-id="115b5-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="115b5-111">dışı Geniş karakter olarak döndürülen boyut `szName` .</span><span class="sxs-lookup"><span data-stu-id="115b5-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="115b5-112">dışı Parametresiyle ilişkili öznitelik bayraklarının bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="115b5-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="115b5-113">Bu bir değer bit değeridir `CorParamAttr` .</span><span class="sxs-lookup"><span data-stu-id="115b5-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="115b5-114">dışı Parametresinin bir olduğunu belirten bayrak işaretçisi <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="115b5-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="115b5-115">dışı Parametresi tarafından döndürülen sabit dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="115b5-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="115b5-116">dışı `ppValue`Geniş karakter veya dize yoksa sıfır olan boyut `ppValue` .</span><span class="sxs-lookup"><span data-stu-id="115b5-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="115b5-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="115b5-117">Remarks</span></span>

<span data-ttu-id="115b5-118">İçindeki sıra değerleri, `pulSequence` Parametreler için 1 ile başlar.</span><span class="sxs-lookup"><span data-stu-id="115b5-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="115b5-119">Dönüş değerinin sıra numarası 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="115b5-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="115b5-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="115b5-120">Requirements</span></span>  
 <span data-ttu-id="115b5-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="115b5-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="115b5-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="115b5-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="115b5-123">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="115b5-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="115b5-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="115b5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="115b5-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="115b5-125">See also</span></span>

- [<span data-ttu-id="115b5-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="115b5-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="115b5-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="115b5-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
