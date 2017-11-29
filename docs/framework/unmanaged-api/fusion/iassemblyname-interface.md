---
title: IAssemblyName Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName
helpviewer_keywords: IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1d11889ab9db408b6e703bbaec17fd0487f142a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="c715f-102">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c715f-102">IAssemblyName Interface</span></span>
<span data-ttu-id="c715f-103">Açıklayan ve bir derlemenin benzersiz kimliği ile çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c715f-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c715f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c715f-104">Methods</span></span>  
  
|<span data-ttu-id="c715f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c715f-105">Method</span></span>|<span data-ttu-id="c715f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c715f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c715f-107">Clone yöntemi</span><span class="sxs-lookup"><span data-stu-id="c715f-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|<span data-ttu-id="c715f-108">Bu basit bir kopyasını oluşturur `IAssemblyName` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c715f-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="c715f-109">Finalize yöntemi</span><span class="sxs-lookup"><span data-stu-id="c715f-109">Finalize Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|<span data-ttu-id="c715f-110">Böylece `IAssemblyName` kaynakları serbest bırakır ve onun yıkıcı çağrılmadan önce diğer temizleme işlemleri gerçekleştirmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="c715f-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="c715f-111">GetDisplayName yöntemi</span><span class="sxs-lookup"><span data-stu-id="c715f-111">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|<span data-ttu-id="c715f-112">Bu tarafından başvurulan derleme okunabilir adını alır `IAssemblyName` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c715f-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="c715f-113">GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="c715f-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|<span data-ttu-id="c715f-114">Bu tarafından başvurulan derleme basit, şifrelenmemiş adını alır `IAssemblyName` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c715f-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="c715f-115">GetProperty yöntemi</span><span class="sxs-lookup"><span data-stu-id="c715f-115">GetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|<span data-ttu-id="c715f-116">Belirtilen tarafından başvurulan özelliği için bir işaretçi alır `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="c715f-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="c715f-117">GetVersion yöntemi</span><span class="sxs-lookup"><span data-stu-id="c715f-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|<span data-ttu-id="c715f-118">Bu tarafından başvurulan derlemenin sürüm bilgisi alır `IAssemblyName` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c715f-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="c715f-119">Isequal yöntemi</span><span class="sxs-lookup"><span data-stu-id="c715f-119">IsEqual Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|<span data-ttu-id="c715f-120">Belirtilen bir olup olmadığını belirleyen `IAssemblyName` nesnesidir için eşit `IAssemblyName`, belirtilen karşılaştırma bayrakları göre.</span><span class="sxs-lookup"><span data-stu-id="c715f-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="c715f-121">SetProperty yöntemi</span><span class="sxs-lookup"><span data-stu-id="c715f-121">SetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|<span data-ttu-id="c715f-122">Belirtilen tarafından başvurulan özelliğinin değeri ayarlar `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="c715f-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c715f-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c715f-123">Requirements</span></span>  
 <span data-ttu-id="c715f-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c715f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c715f-125">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c715f-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c715f-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c715f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c715f-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c715f-127">See Also</span></span>  
 [<span data-ttu-id="c715f-128">Fusion arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c715f-128">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="c715f-129">Iassemblyenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="c715f-129">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
