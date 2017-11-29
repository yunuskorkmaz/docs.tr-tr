---
title: IMetaDataDispenserEx::GetOption Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.GetOption
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fa9db222c81c2d6536b782c3e047e24c773bd018
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="32a2c-102">IMetaDataDispenserEx::GetOption Metodu</span><span class="sxs-lookup"><span data-stu-id="32a2c-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="32a2c-103">Geçerli meta veri kapsam için belirtilen seçenek değerini alır.</span><span class="sxs-lookup"><span data-stu-id="32a2c-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="32a2c-104">Seçeneği geçerli bir meta veri kapsama çağrıları işlenme denetler.</span><span class="sxs-lookup"><span data-stu-id="32a2c-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32a2c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32a2c-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32a2c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32a2c-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="32a2c-107">[in] Bir işaretçi alınması seçeneğine belirten bir GUID.</span><span class="sxs-lookup"><span data-stu-id="32a2c-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="32a2c-108">Desteklenen GUID'lerin listesini için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="32a2c-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="32a2c-109">[out] Döndürülen seçeneği değeri.</span><span class="sxs-lookup"><span data-stu-id="32a2c-109">[out] The value of the returned option.</span></span> <span data-ttu-id="32a2c-110">Bu değerin türü belirtilen seçeneğin türünde bir değişken olacaktır.</span><span class="sxs-lookup"><span data-stu-id="32a2c-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32a2c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32a2c-111">Remarks</span></span>  
 <span data-ttu-id="32a2c-112">Aşağıdaki liste, bu yöntem için desteklenen GUID'ler gösterir.</span><span class="sxs-lookup"><span data-stu-id="32a2c-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="32a2c-113">Açıklamaları için bkz: [Imetadatadispenserex::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32a2c-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="32a2c-114">Varsa `optionId` olduğundan bu listede değil, bu yöntem HRESULT döndürür `E_INVALIDARG`, hatalı bir parametre belirten.</span><span class="sxs-lookup"><span data-stu-id="32a2c-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
-   <span data-ttu-id="32a2c-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="32a2c-115">MetaDataCheckDuplicatesFor</span></span>  
  
-   <span data-ttu-id="32a2c-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="32a2c-116">MetaDataRefToDefCheck</span></span>  
  
-   <span data-ttu-id="32a2c-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="32a2c-117">MetaDataNotificationForTokenMovement</span></span>  
  
-   <span data-ttu-id="32a2c-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="32a2c-118">MetaDataSetENC</span></span>  
  
-   <span data-ttu-id="32a2c-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="32a2c-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
-   <span data-ttu-id="32a2c-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="32a2c-120">MetaDataGenerateTCEAdapters</span></span>  
  
-   <span data-ttu-id="32a2c-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="32a2c-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32a2c-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32a2c-122">Requirements</span></span>  
 <span data-ttu-id="32a2c-123">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32a2c-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32a2c-124">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="32a2c-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="32a2c-125">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="32a2c-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="32a2c-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32a2c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a2c-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32a2c-127">See Also</span></span>  
 [<span data-ttu-id="32a2c-128">Imetadatadispenserex arabirimi</span><span class="sxs-lookup"><span data-stu-id="32a2c-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="32a2c-129">Imetadatadispenser arabirimi</span><span class="sxs-lookup"><span data-stu-id="32a2c-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
