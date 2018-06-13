---
title: IAssemblyName Arabirimi
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa12252c4f2a8e710a4a880af103aa324f8118ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432406"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="aaf3a-102">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aaf3a-102">IAssemblyName Interface</span></span>
<span data-ttu-id="aaf3a-103">Açıklayan ve bir derlemenin benzersiz kimliği ile çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="aaf3a-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aaf3a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aaf3a-104">Methods</span></span>  
  
|<span data-ttu-id="aaf3a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="aaf3a-105">Method</span></span>|<span data-ttu-id="aaf3a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aaf3a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aaf3a-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aaf3a-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|<span data-ttu-id="aaf3a-108">Bu basit bir kopyasını oluşturur `IAssemblyName` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="aaf3a-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="aaf3a-109">Finalize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aaf3a-109">Finalize Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|<span data-ttu-id="aaf3a-110">Böylece `IAssemblyName` kaynakları serbest bırakır ve onun yıkıcı çağrılmadan önce diğer temizleme işlemleri gerçekleştirmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="aaf3a-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="aaf3a-111">GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aaf3a-111">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|<span data-ttu-id="aaf3a-112">Bu tarafından başvurulan derleme okunabilir adını alır `IAssemblyName` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="aaf3a-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="aaf3a-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aaf3a-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|<span data-ttu-id="aaf3a-114">Bu tarafından başvurulan derleme basit, şifrelenmemiş adını alır `IAssemblyName` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="aaf3a-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="aaf3a-115">GetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aaf3a-115">GetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|<span data-ttu-id="aaf3a-116">Belirtilen tarafından başvurulan özelliği için bir işaretçi alır `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="aaf3a-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="aaf3a-117">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aaf3a-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|<span data-ttu-id="aaf3a-118">Bu tarafından başvurulan derlemenin sürüm bilgisi alır `IAssemblyName` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="aaf3a-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="aaf3a-119">IsEqual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aaf3a-119">IsEqual Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|<span data-ttu-id="aaf3a-120">Belirtilen bir olup olmadığını belirleyen `IAssemblyName` nesnesidir için eşit `IAssemblyName`, belirtilen karşılaştırma bayrakları göre.</span><span class="sxs-lookup"><span data-stu-id="aaf3a-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="aaf3a-121">SetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aaf3a-121">SetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|<span data-ttu-id="aaf3a-122">Belirtilen tarafından başvurulan özelliğinin değeri ayarlar `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="aaf3a-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aaf3a-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aaf3a-123">Requirements</span></span>  
 <span data-ttu-id="aaf3a-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaf3a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaf3a-125">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="aaf3a-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="aaf3a-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaf3a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaf3a-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aaf3a-127">See Also</span></span>  
 [<span data-ttu-id="aaf3a-128">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aaf3a-128">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="aaf3a-129">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aaf3a-129">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
