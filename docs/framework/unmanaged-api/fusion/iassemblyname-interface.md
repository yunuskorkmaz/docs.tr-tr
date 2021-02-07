---
description: 'Daha fazla bilgi edinin: IAssemblyName arabirimi'
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
ms.openlocfilehash: fb5949572adc533bab5ed26ee969267f430f36ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760712"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="60367-103">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60367-103">IAssemblyName Interface</span></span>

<span data-ttu-id="60367-104">Bir derlemenin benzersiz kimliğini tanımlamak ve bunlarla çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="60367-104">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60367-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="60367-105">Methods</span></span>  
  
|<span data-ttu-id="60367-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="60367-106">Method</span></span>|<span data-ttu-id="60367-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60367-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="60367-108">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60367-108">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="60367-109">Bu nesnenin basit bir kopyasını oluşturur `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="60367-109">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="60367-110">Finalize Metodu</span><span class="sxs-lookup"><span data-stu-id="60367-110">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="60367-111">Bu `IAssemblyName` nesnenin, yıkıcısı çağrılmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="60367-111">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="60367-112">GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60367-112">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="60367-113">Bu nesne tarafından başvurulan derlemenin okunabilir adını alır `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="60367-113">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="60367-114">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60367-114">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="60367-115">Bu nesnenin başvurduğu derlemenin basit, şifrelenmemiş adını alır `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="60367-115">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="60367-116">GetProperty yöntemi</span><span class="sxs-lookup"><span data-stu-id="60367-116">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="60367-117">Belirtilen özelliğin başvurduğu özelliğe bir işaretçi alır `PropertyId` .</span><span class="sxs-lookup"><span data-stu-id="60367-117">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="60367-118">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60367-118">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="60367-119">Bu nesne tarafından başvurulan derleme için sürüm bilgilerini alır `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="60367-119">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="60367-120">IsEqual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60367-120">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="60367-121">Belirtilen `IAssemblyName` `IAssemblyName` karşılaştırma bayraklarını temel alarak belirtilen bir nesnenin bu değere eşit olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="60367-121">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="60367-122">SetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60367-122">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="60367-123">Belirtilen öğesinin başvurduğu özelliğin değerini ayarlar `PropertyId` .</span><span class="sxs-lookup"><span data-stu-id="60367-123">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60367-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60367-124">Requirements</span></span>  

 <span data-ttu-id="60367-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60367-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60367-126">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="60367-126">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="60367-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60367-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60367-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60367-128">See also</span></span>

- [<span data-ttu-id="60367-129">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="60367-129">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="60367-130">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60367-130">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
