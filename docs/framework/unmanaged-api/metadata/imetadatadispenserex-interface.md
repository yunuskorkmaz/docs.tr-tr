---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatadağıtıserex arabirimi'
title: IMetaDataDispenserEx Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
ms.openlocfilehash: d940ac20eaad4b930ab17fb2d194d3b03bd4cf3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753542"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="151b6-103">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="151b6-103">IMetaDataDispenserEx Interface</span></span>

<span data-ttu-id="151b6-104">Meta veri API 'Lerinin geçerli meta veri kapsamında nasıl çalıştığını denetleme yeteneğini sağlamak için [ımetadatadağıtıcı arabirim](imetadatadispenser-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="151b6-104">Extends the [IMetaDataDispenser Interface](imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="151b6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="151b6-105">Methods</span></span>  
  
|<span data-ttu-id="151b6-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="151b6-106">Method</span></span>|<span data-ttu-id="151b6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="151b6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="151b6-108">FindAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="151b6-108">FindAssembly Method</span></span>](imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="151b6-109">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="151b6-109">This method is not implemented.</span></span> <span data-ttu-id="151b6-110">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="151b6-110">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="151b6-111">FindAssemblyModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="151b6-111">FindAssemblyModule Method</span></span>](imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="151b6-112">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="151b6-112">This method is not implemented.</span></span> <span data-ttu-id="151b6-113">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="151b6-113">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="151b6-114">GetCORSystemDirectory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="151b6-114">GetCORSystemDirectory Method</span></span>](imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="151b6-115">Geçerli ortak dil çalışma zamanını (CLR) tutan dizini alır.</span><span class="sxs-lookup"><span data-stu-id="151b6-115">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="151b6-116">Bu yöntem yalnızca işlem dışı hata ayıklayıcıları tarafından kullanılmak üzere desteklenir.</span><span class="sxs-lookup"><span data-stu-id="151b6-116">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="151b6-117">Başka bir bileşenden çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="151b6-117">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="151b6-118">GetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="151b6-118">GetOption Method</span></span>](imetadatadispenserex-getoption-method.md)|<span data-ttu-id="151b6-119">Geçerli meta veri kapsamı için belirtilen seçeneğin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="151b6-119">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="151b6-120">Seçeneği, geçerli meta veri kapsamına yapılan çağrıların işlenme biçimini denetler.</span><span class="sxs-lookup"><span data-stu-id="151b6-120">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="151b6-121">OpenScopeOnITypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="151b6-121">OpenScopeOnITypeInfo Method</span></span>](imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="151b6-122">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="151b6-122">This method is not implemented.</span></span> <span data-ttu-id="151b6-123">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="151b6-123">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="151b6-124">SetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="151b6-124">SetOption Method</span></span>](imetadatadispenserex-setoption-method.md)|<span data-ttu-id="151b6-125">Belirtilen seçeneği geçerli meta veri kapsamı için verilen bir değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="151b6-125">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="151b6-126">Seçeneği, geçerli meta veri kapsamına yapılan çağrıların işlenme biçimini denetler.</span><span class="sxs-lookup"><span data-stu-id="151b6-126">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="151b6-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="151b6-127">Requirements</span></span>  

 <span data-ttu-id="151b6-128">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="151b6-128">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="151b6-129">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="151b6-129">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="151b6-130">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="151b6-130">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="151b6-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="151b6-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="151b6-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="151b6-132">See also</span></span>

- [<span data-ttu-id="151b6-133">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="151b6-133">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="151b6-134">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="151b6-134">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="151b6-135">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="151b6-135">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="151b6-136">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="151b6-136">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
