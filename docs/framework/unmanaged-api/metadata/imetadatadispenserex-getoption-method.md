---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatadağıtıserex:: GetOption yöntemi'
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
ms.openlocfilehash: cf52a251c3c0e0485558a150b727d58eeae81995
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753555"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="c3d3e-103">IMetaDataDispenserEx::GetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3d3e-103">IMetaDataDispenserEx::GetOption Method</span></span>

<span data-ttu-id="c3d3e-104">Geçerli meta veri kapsamı için belirtilen seçeneğin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="c3d3e-104">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="c3d3e-105">Seçeneği, geçerli meta veri kapsamına yapılan çağrıların işlenme biçimini denetler.</span><span class="sxs-lookup"><span data-stu-id="c3d3e-105">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3d3e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3d3e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3d3e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3d3e-107">Parameters</span></span>  

 `optionId`  
 <span data-ttu-id="c3d3e-108">'ndaki Alınacak seçeneği belirten bir GUID işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c3d3e-108">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="c3d3e-109">Desteklenen GUID 'lerin listesi için açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c3d3e-109">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="c3d3e-110">dışı Döndürülen seçeneğin değeri.</span><span class="sxs-lookup"><span data-stu-id="c3d3e-110">[out] The value of the returned option.</span></span> <span data-ttu-id="c3d3e-111">Bu değerin türü, belirtilen seçeneğin türünün bir değişkeni olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c3d3e-111">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3d3e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3d3e-112">Remarks</span></span>  

 <span data-ttu-id="c3d3e-113">Aşağıdaki liste, bu yöntem için desteklenen GUID 'Leri gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3d3e-113">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="c3d3e-114">Açıklamalar için, bkz. [ımetadatadağıtıserex:: SetOption](imetadatadispenserex-setoption-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c3d3e-114">For descriptions, see the [IMetaDataDispenserEx::SetOption](imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="c3d3e-115">`optionId`Bu listede yoksa, bu yöntem, `E_INVALIDARG` yanlış bir parametre belirten hresult döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3d3e-115">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="c3d3e-116">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="c3d3e-116">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="c3d3e-117">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="c3d3e-117">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="c3d3e-118">Metadadtanocertificate Ationfortokentaşıması</span><span class="sxs-lookup"><span data-stu-id="c3d3e-118">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="c3d3e-119">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="c3d3e-119">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="c3d3e-120">Metadataerrorifemıtoutoforder</span><span class="sxs-lookup"><span data-stu-id="c3d3e-120">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="c3d3e-121">Metadatageneratetcebağdaştırıcıları</span><span class="sxs-lookup"><span data-stu-id="c3d3e-121">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="c3d3e-122">Metaveriveri ınkeroptions</span><span class="sxs-lookup"><span data-stu-id="c3d3e-122">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3d3e-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3d3e-123">Requirements</span></span>  

 <span data-ttu-id="c3d3e-124">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3d3e-124">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3d3e-125">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c3d3e-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3d3e-126">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c3d3e-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c3d3e-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3d3e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d3e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3d3e-128">See also</span></span>

- [<span data-ttu-id="c3d3e-129">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3d3e-129">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="c3d3e-130">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3d3e-130">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
