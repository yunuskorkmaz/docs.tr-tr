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
ms.openlocfilehash: 832adacac4a6df9ccf21578538a1c557150f3ba1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008787"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="7f016-102">IMetaDataDispenserEx::GetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f016-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="7f016-103">Geçerli meta veri kapsamı için belirtilen seçeneğin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="7f016-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="7f016-104">Seçeneği, geçerli meta veri kapsamına yapılan çağrıların işlenme biçimini denetler.</span><span class="sxs-lookup"><span data-stu-id="7f016-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f016-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7f016-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f016-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f016-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="7f016-107">'ndaki Alınacak seçeneği belirten bir GUID işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7f016-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="7f016-108">Desteklenen GUID 'lerin listesi için açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7f016-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="7f016-109">dışı Döndürülen seçeneğin değeri.</span><span class="sxs-lookup"><span data-stu-id="7f016-109">[out] The value of the returned option.</span></span> <span data-ttu-id="7f016-110">Bu değerin türü, belirtilen seçeneğin türünün bir değişkeni olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7f016-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f016-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f016-111">Remarks</span></span>  
 <span data-ttu-id="7f016-112">Aşağıdaki liste, bu yöntem için desteklenen GUID 'Leri gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f016-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="7f016-113">Açıklamalar için, bkz. [ımetadatadağıtıserex:: SetOption](imetadatadispenserex-setoption-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7f016-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="7f016-114">`optionId`Bu listede yoksa, bu yöntem, `E_INVALIDARG` yanlış bir parametre belirten hresult döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f016-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="7f016-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="7f016-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="7f016-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="7f016-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="7f016-117">Metadadtanocertificate Ationfortokentaşıması</span><span class="sxs-lookup"><span data-stu-id="7f016-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="7f016-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="7f016-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="7f016-119">Metadataerrorifemıtoutoforder</span><span class="sxs-lookup"><span data-stu-id="7f016-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="7f016-120">Metadatageneratetcebağdaştırıcıları</span><span class="sxs-lookup"><span data-stu-id="7f016-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="7f016-121">Metaveriveri ınkeroptions</span><span class="sxs-lookup"><span data-stu-id="7f016-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f016-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f016-122">Requirements</span></span>  
 <span data-ttu-id="7f016-123">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f016-123">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f016-124">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7f016-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f016-125">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7f016-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f016-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f016-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f016-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f016-127">See also</span></span>

- [<span data-ttu-id="7f016-128">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f016-128">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="7f016-129">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f016-129">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
