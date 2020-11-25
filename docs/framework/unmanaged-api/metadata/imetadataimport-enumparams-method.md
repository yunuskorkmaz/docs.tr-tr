---
title: IMetaDataImport::EnumParams Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
ms.openlocfilehash: b41f9bb05a43ac4c6dd8a89c45ef4826741e5679
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728270"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="130b6-102">IMetaDataImport::EnumParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="130b6-102">IMetaDataImport::EnumParams Method</span></span>

<span data-ttu-id="130b6-103">Belirtilen MethodDef belirtecinin başvurduğu metodun parametrelerini temsil eden ParamDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="130b6-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="130b6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="130b6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="130b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="130b6-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="130b6-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="130b6-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="130b6-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="130b6-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="130b6-108">'ndaki Numaralandırılacak parametrelere sahip yöntemi temsil eden bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="130b6-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="130b6-109">dışı ParamDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="130b6-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="130b6-110">'ndaki Dizinin en büyük boyutu `rParams` .</span><span class="sxs-lookup"><span data-stu-id="130b6-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="130b6-111">dışı İçinde döndürülen ParamDef belirteçleri sayısı `rParams` .</span><span class="sxs-lookup"><span data-stu-id="130b6-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="130b6-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="130b6-112">Return Value</span></span>  
  
|<span data-ttu-id="130b6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="130b6-113">HRESULT</span></span>|<span data-ttu-id="130b6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="130b6-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="130b6-115">`EnumParams` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="130b6-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="130b6-116">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="130b6-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="130b6-117">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="130b6-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="130b6-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="130b6-118">Requirements</span></span>  

 <span data-ttu-id="130b6-119">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="130b6-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="130b6-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="130b6-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="130b6-121">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="130b6-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="130b6-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="130b6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="130b6-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="130b6-123">See also</span></span>

- [<span data-ttu-id="130b6-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="130b6-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="130b6-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="130b6-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
