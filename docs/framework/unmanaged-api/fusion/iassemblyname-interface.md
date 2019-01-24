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
ms.openlocfilehash: 22276e543e8eeb9c6cf9aeee7a9af92c503d3a7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549021"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="4c7be-102">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c7be-102">IAssemblyName Interface</span></span>
<span data-ttu-id="4c7be-103">Açıklayan ve bir derlemenin benzersiz kimliği ile çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c7be-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c7be-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4c7be-104">Methods</span></span>  
  
|<span data-ttu-id="4c7be-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4c7be-105">Method</span></span>|<span data-ttu-id="4c7be-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c7be-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c7be-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c7be-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|<span data-ttu-id="4c7be-108">Bu basit bir kopyasını oluşturur `IAssemblyName` nesne.</span><span class="sxs-lookup"><span data-stu-id="4c7be-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="4c7be-109">Finalize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c7be-109">Finalize Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|<span data-ttu-id="4c7be-110">Böylece `IAssemblyName` kaynakları serbest bırakmak ve yok edici çağrılmadan önce diğer temizleme işlemleri gerçekleştirmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="4c7be-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="4c7be-111">GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c7be-111">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|<span data-ttu-id="4c7be-112">Okunabilir bu başvurduğu derlemenin adını alır `IAssemblyName` nesne.</span><span class="sxs-lookup"><span data-stu-id="4c7be-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="4c7be-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c7be-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|<span data-ttu-id="4c7be-114">Basit, şifrelenmemiş bu başvurduğu derlemenin adını alır `IAssemblyName` nesne.</span><span class="sxs-lookup"><span data-stu-id="4c7be-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="4c7be-115">GetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c7be-115">GetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|<span data-ttu-id="4c7be-116">Başvurulan tarafından belirtilen özellik için bir işaretçi alır `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="4c7be-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="4c7be-117">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c7be-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|<span data-ttu-id="4c7be-118">Bu tarafından başvurulan derlemenin sürüm bilgilerini alır `IAssemblyName` nesne.</span><span class="sxs-lookup"><span data-stu-id="4c7be-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="4c7be-119">IsEqual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c7be-119">IsEqual Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|<span data-ttu-id="4c7be-120">Belirtilen bir olup olmadığını belirler `IAssemblyName` nesnedir şuna eşit `IAssemblyName`bağlı olarak belirtilen karşılaştırma bayrakları.</span><span class="sxs-lookup"><span data-stu-id="4c7be-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="4c7be-121">SetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c7be-121">SetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|<span data-ttu-id="4c7be-122">Belirtilen tarafından başvurulan özelliğin değerini ayarlar `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="4c7be-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4c7be-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c7be-123">Requirements</span></span>  
 <span data-ttu-id="4c7be-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c7be-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c7be-125">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4c7be-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4c7be-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c7be-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c7be-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c7be-127">See also</span></span>
- [<span data-ttu-id="4c7be-128">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4c7be-128">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="4c7be-129">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c7be-129">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
