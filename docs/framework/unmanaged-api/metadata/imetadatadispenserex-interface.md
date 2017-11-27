---
title: IMetaDataDispenserEx Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx
helpviewer_keywords: IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5ecb4e94c0deed3ed62b2d2eb8b0309ca092abf8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="b2148-102">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2148-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="b2148-103">Genişletir [Imetadatadispenser arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) API meta verileri geçerli meta veri kapsamına nasıl çalıştığını denetleyen yeteneği sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="b2148-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2148-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b2148-104">Methods</span></span>  
  
|<span data-ttu-id="b2148-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b2148-105">Method</span></span>|<span data-ttu-id="b2148-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2148-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2148-107">FindAssembly yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2148-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="b2148-108">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="b2148-108">This method is not implemented.</span></span> <span data-ttu-id="b2148-109">Adlı E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2148-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="b2148-110">FindAssemblyModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2148-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="b2148-111">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="b2148-111">This method is not implemented.</span></span> <span data-ttu-id="b2148-112">Adlı E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2148-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="b2148-113">GetCORSystemDirectory yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2148-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="b2148-114">Geçerli ortak dil çalışma zamanı (CLR) tutan dizinin alır.</span><span class="sxs-lookup"><span data-stu-id="b2148-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="b2148-115">Bu yöntem yalnızca kullanım için işlem dışı hata ayıklayıcıları tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b2148-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="b2148-116">Başka bir bileşen tarafından çağrılan olursa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2148-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="b2148-117">GetOption yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2148-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="b2148-118">Geçerli meta veri kapsam için belirtilen seçenek değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b2148-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="b2148-119">Seçeneği geçerli bir meta veri kapsama çağrıları işlenme denetler.</span><span class="sxs-lookup"><span data-stu-id="b2148-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="b2148-120">Openscopeonıtypeınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2148-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="b2148-121">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="b2148-121">This method is not implemented.</span></span> <span data-ttu-id="b2148-122">Adlı E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2148-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="b2148-123">SetOption yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2148-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="b2148-124">Belirtilen seçenek geçerli meta veri kapsam için belirli bir değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b2148-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="b2148-125">Seçeneği geçerli bir meta veri kapsama çağrıları işlenme denetler.</span><span class="sxs-lookup"><span data-stu-id="b2148-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2148-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2148-126">Requirements</span></span>  
 <span data-ttu-id="b2148-127">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2148-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2148-128">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b2148-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2148-129">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b2148-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2148-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2148-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2148-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2148-131">See Also</span></span>  
 [<span data-ttu-id="b2148-132">Meta veri arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b2148-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="b2148-133">Imetadatadispenser arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2148-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="b2148-134">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2148-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="b2148-135">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2148-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
