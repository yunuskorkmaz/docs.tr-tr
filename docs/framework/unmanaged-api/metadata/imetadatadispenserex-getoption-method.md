---
title: IMetaDataDispenserEx::GetOption Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
ms.openlocfilehash: 816e2f2dc7d4d00f74f67720ee45d7b3483e57fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177725"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="1ca5c-102">IMetaDataDispenserEx::GetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ca5c-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="1ca5c-103">Geçerli meta veri kapsamı için belirtilen seçeneğin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="1ca5c-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="1ca5c-104">Seçenek, geçerli meta veri kapsamına yapılan çağrıların nasıl işleneceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="1ca5c-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ca5c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ca5c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ca5c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ca5c-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="1ca5c-107">[içinde] Alınacak seçeneği belirten bir GUID işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1ca5c-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="1ca5c-108">Desteklenen GUID'lerin listesi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1ca5c-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="1ca5c-109">[çıkış] Döndürülen seçeneğin değeri.</span><span class="sxs-lookup"><span data-stu-id="1ca5c-109">[out] The value of the returned option.</span></span> <span data-ttu-id="1ca5c-110">Bu değerin türü, belirtilen seçeneğin türünün bir varyantı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1ca5c-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ca5c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ca5c-111">Remarks</span></span>  
 <span data-ttu-id="1ca5c-112">Aşağıdaki liste, bu yöntem için desteklenen GUID'leri gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ca5c-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="1ca5c-113">Açıklamalar için [iMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) yöntemine bakın.</span><span class="sxs-lookup"><span data-stu-id="1ca5c-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="1ca5c-114">Bu `optionId` listede yoksa, bu yöntem yanlış `E_INVALIDARG`bir parametre gösteren HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="1ca5c-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="1ca5c-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="1ca5c-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="1ca5c-116">MetaDataReftodefcheck</span><span class="sxs-lookup"><span data-stu-id="1ca5c-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="1ca5c-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="1ca5c-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="1ca5c-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="1ca5c-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="1ca5c-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="1ca5c-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="1ca5c-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="1ca5c-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="1ca5c-121">MetaDataLinkerSeçenekleri</span><span class="sxs-lookup"><span data-stu-id="1ca5c-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ca5c-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ca5c-122">Requirements</span></span>  
 <span data-ttu-id="1ca5c-123">**Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ca5c-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ca5c-124">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1ca5c-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ca5c-125">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1ca5c-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ca5c-126">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ca5c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca5c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ca5c-127">See also</span></span>

- [<span data-ttu-id="1ca5c-128">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ca5c-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="1ca5c-129">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ca5c-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
