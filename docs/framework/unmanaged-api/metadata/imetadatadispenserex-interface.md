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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4fa4830756ee6ac896611dbc243207739151d3f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547325"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="c6668-102">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6668-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="c6668-103">Genişletir [Imetadatadispenser arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) API meta verileri geçerli meta veri kapsamına nasıl çalıştığını denetleyen olanağı sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="c6668-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c6668-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c6668-104">Methods</span></span>  
  
|<span data-ttu-id="c6668-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c6668-105">Method</span></span>|<span data-ttu-id="c6668-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6668-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c6668-107">FindAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6668-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="c6668-108">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="c6668-108">This method is not implemented.</span></span> <span data-ttu-id="c6668-109">Çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6668-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="c6668-110">FindAssemblyModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6668-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="c6668-111">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="c6668-111">This method is not implemented.</span></span> <span data-ttu-id="c6668-112">Çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6668-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="c6668-113">GetCORSystemDirectory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6668-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="c6668-114">Geçerli ortak dil çalışma zamanının (CLR) tutan dizinin alır.</span><span class="sxs-lookup"><span data-stu-id="c6668-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="c6668-115">Bu yöntemi kullanmak için yalnızca işlem dışı hata ayıklayıcıları tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c6668-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="c6668-116">Başka bir bileşenden çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6668-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="c6668-117">GetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6668-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="c6668-118">Geçerli meta veri kapsam için belirtilen seçenek değerini alır.</span><span class="sxs-lookup"><span data-stu-id="c6668-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="c6668-119">Geçerli bir meta veri kapsama çağrıları nasıl işleneceğini seçeneği denetler.</span><span class="sxs-lookup"><span data-stu-id="c6668-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="c6668-120">OpenScopeOnITypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6668-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="c6668-121">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="c6668-121">This method is not implemented.</span></span> <span data-ttu-id="c6668-122">Çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6668-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="c6668-123">SetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6668-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="c6668-124">Belirtilen seçeneği geçerli meta veri kapsam için belirli bir değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c6668-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="c6668-125">Geçerli bir meta veri kapsama çağrıları nasıl işleneceğini seçeneği denetler.</span><span class="sxs-lookup"><span data-stu-id="c6668-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6668-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6668-126">Requirements</span></span>  
 <span data-ttu-id="c6668-127">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6668-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6668-128">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c6668-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c6668-129">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="c6668-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6668-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6668-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6668-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6668-131">See also</span></span>
- [<span data-ttu-id="c6668-132">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c6668-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="c6668-133">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6668-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="c6668-134">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6668-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c6668-135">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6668-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
