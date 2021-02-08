---
description: ': IMetaDataImport:: Trmevents yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::EnumEvents Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: e944c15a19314b315e01493836ce078fccc917eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799414"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="3faf7-103">IMetaDataImport::EnumEvents Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3faf7-103">IMetaDataImport::EnumEvents Method</span></span>

<span data-ttu-id="3faf7-104">Belirtilen TypeDef belirtecinin olay tanımı belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="3faf7-104">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3faf7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3faf7-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3faf7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3faf7-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="3faf7-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3faf7-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="3faf7-108">'ndaki Olay tanımları Numaralandırılacak olan TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="3faf7-108">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="3faf7-109">dışı Döndürülen olayların dizisi.</span><span class="sxs-lookup"><span data-stu-id="3faf7-109">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3faf7-110">'ndaki Dizinin en büyük boyutu `rEvents` .</span><span class="sxs-lookup"><span data-stu-id="3faf7-110">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="3faf7-111">dışı ' De döndürülen olayların gerçek sayısı `rEvents` .</span><span class="sxs-lookup"><span data-stu-id="3faf7-111">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3faf7-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3faf7-112">Return Value</span></span>  
  
|<span data-ttu-id="3faf7-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3faf7-113">HRESULT</span></span>|<span data-ttu-id="3faf7-114">Description</span><span class="sxs-lookup"><span data-stu-id="3faf7-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3faf7-115">`EnumEvents` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3faf7-115">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3faf7-116">Numaralandırılacak olay yok.</span><span class="sxs-lookup"><span data-stu-id="3faf7-116">There are no events to enumerate.</span></span> <span data-ttu-id="3faf7-117">Bu durumda, `pcEvents` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="3faf7-117">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3faf7-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3faf7-118">Requirements</span></span>  

 <span data-ttu-id="3faf7-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3faf7-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3faf7-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3faf7-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3faf7-121">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3faf7-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3faf7-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3faf7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3faf7-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3faf7-123">See also</span></span>

- [<span data-ttu-id="3faf7-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3faf7-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3faf7-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3faf7-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
