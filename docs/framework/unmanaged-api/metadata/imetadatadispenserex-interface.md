---
title: IMetaDataDispenserEx Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4cf062029647d4834118a459db378c8535182daf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="15274-102">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15274-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="15274-103">Genişletir [Imetadatadispenser arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) API meta verileri geçerli meta veri kapsamına nasıl çalıştığını denetleyen yeteneği sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="15274-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15274-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="15274-104">Methods</span></span>  
  
|<span data-ttu-id="15274-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="15274-105">Method</span></span>|<span data-ttu-id="15274-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15274-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15274-107">FindAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15274-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="15274-108">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="15274-108">This method is not implemented.</span></span> <span data-ttu-id="15274-109">Adlı E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="15274-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="15274-110">FindAssemblyModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15274-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="15274-111">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="15274-111">This method is not implemented.</span></span> <span data-ttu-id="15274-112">Adlı E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="15274-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="15274-113">GetCORSystemDirectory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15274-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="15274-114">Geçerli ortak dil çalışma zamanı (CLR) tutan dizinin alır.</span><span class="sxs-lookup"><span data-stu-id="15274-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="15274-115">Bu yöntem yalnızca kullanım için işlem dışı hata ayıklayıcıları tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="15274-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="15274-116">Başka bir bileşen tarafından çağrılan olursa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="15274-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="15274-117">GetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15274-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="15274-118">Geçerli meta veri kapsam için belirtilen seçenek değerini alır.</span><span class="sxs-lookup"><span data-stu-id="15274-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="15274-119">Seçeneği geçerli bir meta veri kapsama çağrıları işlenme denetler.</span><span class="sxs-lookup"><span data-stu-id="15274-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="15274-120">OpenScopeOnITypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15274-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="15274-121">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="15274-121">This method is not implemented.</span></span> <span data-ttu-id="15274-122">Adlı E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="15274-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="15274-123">SetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15274-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="15274-124">Belirtilen seçenek geçerli meta veri kapsam için belirli bir değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="15274-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="15274-125">Seçeneği geçerli bir meta veri kapsama çağrıları işlenme denetler.</span><span class="sxs-lookup"><span data-stu-id="15274-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15274-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15274-126">Requirements</span></span>  
 <span data-ttu-id="15274-127">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15274-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15274-128">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="15274-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15274-129">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="15274-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15274-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15274-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15274-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15274-131">See Also</span></span>  
 [<span data-ttu-id="15274-132">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="15274-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="15274-133">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15274-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="15274-134">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15274-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="15274-135">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15274-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
