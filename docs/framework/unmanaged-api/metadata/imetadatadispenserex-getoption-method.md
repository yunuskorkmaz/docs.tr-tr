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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5512c503d8b4048c613ab88c2b4d9d19cdbb9dca
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479040"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="3f84c-102">IMetaDataDispenserEx::GetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f84c-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="3f84c-103">Geçerli meta veri kapsam için belirtilen seçenek değerini alır.</span><span class="sxs-lookup"><span data-stu-id="3f84c-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="3f84c-104">Geçerli bir meta veri kapsama çağrıları nasıl işleneceğini seçeneği denetler.</span><span class="sxs-lookup"><span data-stu-id="3f84c-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f84c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f84c-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f84c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f84c-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="3f84c-107">[in] Alınacak seçeneğini belirten bir GUID için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f84c-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="3f84c-108">Desteklenen GUID'lerinin listesi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3f84c-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="3f84c-109">[out] Döndürülen seçeneği değeri.</span><span class="sxs-lookup"><span data-stu-id="3f84c-109">[out] The value of the returned option.</span></span> <span data-ttu-id="3f84c-110">Bu değerin türü, belirtilen seçeneğin türünde bir değişken olacaktır.</span><span class="sxs-lookup"><span data-stu-id="3f84c-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f84c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f84c-111">Remarks</span></span>  
 <span data-ttu-id="3f84c-112">Aşağıdaki liste, bu yöntem için desteklenen GUID'leri gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f84c-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="3f84c-113">Açıklamaları için bkz. [Imetadatadispenserex::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3f84c-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="3f84c-114">Varsa `optionId` olduğundan bu listede değil, bu yöntem HRESULT döndürür. `E_INVALIDARG`, hatalı bir parametre belirten.</span><span class="sxs-lookup"><span data-stu-id="3f84c-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
-   <span data-ttu-id="3f84c-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="3f84c-115">MetaDataCheckDuplicatesFor</span></span>  
  
-   <span data-ttu-id="3f84c-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="3f84c-116">MetaDataRefToDefCheck</span></span>  
  
-   <span data-ttu-id="3f84c-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="3f84c-117">MetaDataNotificationForTokenMovement</span></span>  
  
-   <span data-ttu-id="3f84c-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="3f84c-118">MetaDataSetENC</span></span>  
  
-   <span data-ttu-id="3f84c-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="3f84c-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
-   <span data-ttu-id="3f84c-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="3f84c-120">MetaDataGenerateTCEAdapters</span></span>  
  
-   <span data-ttu-id="3f84c-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="3f84c-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f84c-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f84c-122">Requirements</span></span>  
 <span data-ttu-id="3f84c-123">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f84c-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f84c-124">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3f84c-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f84c-125">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="3f84c-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f84c-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f84c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f84c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f84c-127">See also</span></span>
- [<span data-ttu-id="3f84c-128">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f84c-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="3f84c-129">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f84c-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
