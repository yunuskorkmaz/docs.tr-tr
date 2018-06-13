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
ms.openlocfilehash: 7d930088d6e621885d14fc4bdab2475aa27594e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448706"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="4bcac-102">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bcac-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="4bcac-103">Genişletir [Imetadatadispenser arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) API meta verileri geçerli meta veri kapsamına nasıl çalıştığını denetleyen yeteneği sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="4bcac-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4bcac-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4bcac-104">Methods</span></span>  
  
|<span data-ttu-id="4bcac-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4bcac-105">Method</span></span>|<span data-ttu-id="4bcac-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4bcac-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4bcac-107">FindAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bcac-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="4bcac-108">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="4bcac-108">This method is not implemented.</span></span> <span data-ttu-id="4bcac-109">Adlı E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bcac-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="4bcac-110">FindAssemblyModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bcac-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="4bcac-111">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="4bcac-111">This method is not implemented.</span></span> <span data-ttu-id="4bcac-112">Adlı E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bcac-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="4bcac-113">GetCORSystemDirectory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bcac-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="4bcac-114">Geçerli ortak dil çalışma zamanı (CLR) tutan dizinin alır.</span><span class="sxs-lookup"><span data-stu-id="4bcac-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="4bcac-115">Bu yöntem yalnızca kullanım için işlem dışı hata ayıklayıcıları tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4bcac-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="4bcac-116">Başka bir bileşen tarafından çağrılan olursa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bcac-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="4bcac-117">GetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bcac-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="4bcac-118">Geçerli meta veri kapsam için belirtilen seçenek değerini alır.</span><span class="sxs-lookup"><span data-stu-id="4bcac-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="4bcac-119">Seçeneği geçerli bir meta veri kapsama çağrıları işlenme denetler.</span><span class="sxs-lookup"><span data-stu-id="4bcac-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="4bcac-120">OpenScopeOnITypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bcac-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="4bcac-121">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="4bcac-121">This method is not implemented.</span></span> <span data-ttu-id="4bcac-122">Adlı E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bcac-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="4bcac-123">SetOption Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bcac-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="4bcac-124">Belirtilen seçenek geçerli meta veri kapsam için belirli bir değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4bcac-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="4bcac-125">Seçeneği geçerli bir meta veri kapsama çağrıları işlenme denetler.</span><span class="sxs-lookup"><span data-stu-id="4bcac-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4bcac-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4bcac-126">Requirements</span></span>  
 <span data-ttu-id="4bcac-127">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bcac-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bcac-128">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4bcac-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4bcac-129">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4bcac-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4bcac-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bcac-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bcac-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4bcac-131">See Also</span></span>  
 [<span data-ttu-id="4bcac-132">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4bcac-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="4bcac-133">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bcac-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="4bcac-134">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bcac-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4bcac-135">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bcac-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
