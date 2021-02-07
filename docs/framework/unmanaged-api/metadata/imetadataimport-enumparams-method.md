---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataImport:: Trmparams yöntemi'
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
ms.openlocfilehash: 3402e0277631cb54232269ad96194583cc466c4d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688812"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="63d98-103">IMetaDataImport::EnumParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63d98-103">IMetaDataImport::EnumParams Method</span></span>

<span data-ttu-id="63d98-104">Belirtilen MethodDef belirtecinin başvurduğu metodun parametrelerini temsil eden ParamDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="63d98-104">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63d98-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63d98-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63d98-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63d98-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="63d98-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63d98-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="63d98-108">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="63d98-108">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="63d98-109">'ndaki Numaralandırılacak parametrelere sahip yöntemi temsil eden bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="63d98-109">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="63d98-110">dışı ParamDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="63d98-110">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="63d98-111">'ndaki Dizinin en büyük boyutu `rParams` .</span><span class="sxs-lookup"><span data-stu-id="63d98-111">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="63d98-112">dışı İçinde döndürülen ParamDef belirteçleri sayısı `rParams` .</span><span class="sxs-lookup"><span data-stu-id="63d98-112">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63d98-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="63d98-113">Return Value</span></span>  
  
|<span data-ttu-id="63d98-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63d98-114">HRESULT</span></span>|<span data-ttu-id="63d98-115">Description</span><span class="sxs-lookup"><span data-stu-id="63d98-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="63d98-116">`EnumParams` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="63d98-116">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="63d98-117">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="63d98-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="63d98-118">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="63d98-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63d98-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63d98-119">Requirements</span></span>  

 <span data-ttu-id="63d98-120">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63d98-120">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63d98-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="63d98-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63d98-122">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="63d98-122">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63d98-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63d98-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d98-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63d98-124">See also</span></span>

- [<span data-ttu-id="63d98-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63d98-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="63d98-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63d98-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
