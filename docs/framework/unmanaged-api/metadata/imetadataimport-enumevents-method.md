---
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
ms.openlocfilehash: 53b1234a176cade5876d70da0cb4eadc18802c69
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492310"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="fe8b6-102">IMetaDataImport::EnumEvents Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe8b6-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="fe8b6-103">Belirtilen TypeDef belirtecinin olay tanımı belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="fe8b6-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe8b6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fe8b6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe8b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe8b6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="fe8b6-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fe8b6-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="fe8b6-107">'ndaki Olay tanımları Numaralandırılacak olan TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="fe8b6-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="fe8b6-108">dışı Döndürülen olayların dizisi.</span><span class="sxs-lookup"><span data-stu-id="fe8b6-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fe8b6-109">'ndaki Dizinin en büyük boyutu `rEvents` .</span><span class="sxs-lookup"><span data-stu-id="fe8b6-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="fe8b6-110">dışı ' De döndürülen olayların gerçek sayısı `rEvents` .</span><span class="sxs-lookup"><span data-stu-id="fe8b6-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe8b6-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fe8b6-111">Return Value</span></span>  
  
|<span data-ttu-id="fe8b6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe8b6-112">HRESULT</span></span>|<span data-ttu-id="fe8b6-113">Description</span><span class="sxs-lookup"><span data-stu-id="fe8b6-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="fe8b6-114">`EnumEvents`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fe8b6-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="fe8b6-115">Numaralandırılacak olay yok.</span><span class="sxs-lookup"><span data-stu-id="fe8b6-115">There are no events to enumerate.</span></span> <span data-ttu-id="fe8b6-116">Bu durumda, `pcEvents` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="fe8b6-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe8b6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe8b6-117">Requirements</span></span>  
 <span data-ttu-id="fe8b6-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe8b6-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe8b6-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fe8b6-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe8b6-120">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="fe8b6-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe8b6-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe8b6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe8b6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe8b6-122">See also</span></span>

- [<span data-ttu-id="fe8b6-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe8b6-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="fe8b6-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe8b6-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
