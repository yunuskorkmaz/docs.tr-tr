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
ms.openlocfilehash: ab74b02df959fe6e6457273e67ba3b82ae6a015c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435997"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="4955f-102">IMetaDataDispenserEx::GetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4955f-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="4955f-103">Gets the value of the specified option for the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="4955f-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="4955f-104">The option controls how calls to the current metadata scope are handled.</span><span class="sxs-lookup"><span data-stu-id="4955f-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4955f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4955f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4955f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4955f-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="4955f-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span><span class="sxs-lookup"><span data-stu-id="4955f-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="4955f-108">See the Remarks section for a list of supported GUIDs.</span><span class="sxs-lookup"><span data-stu-id="4955f-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="4955f-109">[out] The value of the returned option.</span><span class="sxs-lookup"><span data-stu-id="4955f-109">[out] The value of the returned option.</span></span> <span data-ttu-id="4955f-110">The type of this value will be a variant of the specified option's type.</span><span class="sxs-lookup"><span data-stu-id="4955f-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4955f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4955f-111">Remarks</span></span>  
 <span data-ttu-id="4955f-112">The following list shows the GUIDs that are supported for this method.</span><span class="sxs-lookup"><span data-stu-id="4955f-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="4955f-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="4955f-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="4955f-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span><span class="sxs-lookup"><span data-stu-id="4955f-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="4955f-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="4955f-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="4955f-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="4955f-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="4955f-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="4955f-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="4955f-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="4955f-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="4955f-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="4955f-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="4955f-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="4955f-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="4955f-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="4955f-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4955f-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4955f-122">Requirements</span></span>  
 <span data-ttu-id="4955f-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4955f-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4955f-124">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4955f-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4955f-125">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4955f-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4955f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4955f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4955f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4955f-127">See also</span></span>

- [<span data-ttu-id="4955f-128">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4955f-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="4955f-129">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4955f-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
