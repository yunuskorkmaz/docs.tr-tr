---
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
ms.openlocfilehash: 96f0c0c254ce255581ac2937c805096918ab29e8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008059"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="6a5b5-102">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a5b5-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="6a5b5-103">Meta veri API 'Lerinin geçerli meta veri kapsamında nasıl çalıştığını denetleme yeteneğini sağlamak için [ımetadatadağıtıcı arabirim](imetadatadispenser-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-103">Extends the [IMetaDataDispenser Interface](imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6a5b5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6a5b5-104">Methods</span></span>  
  
|<span data-ttu-id="6a5b5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6a5b5-105">Method</span></span>|<span data-ttu-id="6a5b5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a5b5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6a5b5-107">FindAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a5b5-107">FindAssembly Method</span></span>](imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="6a5b5-108">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-108">This method is not implemented.</span></span> <span data-ttu-id="6a5b5-109">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="6a5b5-110">FindAssemblyModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a5b5-110">FindAssemblyModule Method</span></span>](imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="6a5b5-111">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-111">This method is not implemented.</span></span> <span data-ttu-id="6a5b5-112">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="6a5b5-113">GetCORSystemDirectory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a5b5-113">GetCORSystemDirectory Method</span></span>](imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="6a5b5-114">Geçerli ortak dil çalışma zamanını (CLR) tutan dizini alır.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="6a5b5-115">Bu yöntem yalnızca işlem dışı hata ayıklayıcıları tarafından kullanılmak üzere desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="6a5b5-116">Başka bir bileşenden çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="6a5b5-117">GetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a5b5-117">GetOption Method</span></span>](imetadatadispenserex-getoption-method.md)|<span data-ttu-id="6a5b5-118">Geçerli meta veri kapsamı için belirtilen seçeneğin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="6a5b5-119">Seçeneği, geçerli meta veri kapsamına yapılan çağrıların işlenme biçimini denetler.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="6a5b5-120">OpenScopeOnITypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a5b5-120">OpenScopeOnITypeInfo Method</span></span>](imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="6a5b5-121">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-121">This method is not implemented.</span></span> <span data-ttu-id="6a5b5-122">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="6a5b5-123">SetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a5b5-123">SetOption Method</span></span>](imetadatadispenserex-setoption-method.md)|<span data-ttu-id="6a5b5-124">Belirtilen seçeneği geçerli meta veri kapsamı için verilen bir değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="6a5b5-125">Seçeneği, geçerli meta veri kapsamına yapılan çağrıların işlenme biçimini denetler.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a5b5-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a5b5-126">Requirements</span></span>  
 <span data-ttu-id="6a5b5-127">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a5b5-127">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a5b5-128">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6a5b5-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a5b5-129">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6a5b5-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6a5b5-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a5b5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a5b5-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a5b5-131">See also</span></span>

- [<span data-ttu-id="6a5b5-132">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6a5b5-132">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="6a5b5-133">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a5b5-133">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="6a5b5-134">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a5b5-134">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="6a5b5-135">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a5b5-135">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
