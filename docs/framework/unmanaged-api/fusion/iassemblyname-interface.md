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
ms.openlocfilehash: f6feed9f59715f9a2801cd3a2a99a087957d4377
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715075"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="4f00e-102">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f00e-102">IAssemblyName Interface</span></span>

<span data-ttu-id="4f00e-103">Bir derlemenin benzersiz kimliğini tanımlamak ve bunlarla çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f00e-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4f00e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4f00e-104">Methods</span></span>  
  
|<span data-ttu-id="4f00e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4f00e-105">Method</span></span>|<span data-ttu-id="4f00e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f00e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4f00e-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f00e-107">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="4f00e-108">Bu nesnenin basit bir kopyasını oluşturur `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="4f00e-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="4f00e-109">Finalize Metodu</span><span class="sxs-lookup"><span data-stu-id="4f00e-109">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="4f00e-110">Bu `IAssemblyName` nesnenin, yıkıcısı çağrılmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="4f00e-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="4f00e-111">GetDisplayName Metodu</span><span class="sxs-lookup"><span data-stu-id="4f00e-111">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="4f00e-112">Bu nesne tarafından başvurulan derlemenin okunabilir adını alır `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="4f00e-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="4f00e-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f00e-113">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="4f00e-114">Bu nesnenin başvurduğu derlemenin basit, şifrelenmemiş adını alır `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="4f00e-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="4f00e-115">GetProperty yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f00e-115">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="4f00e-116">Belirtilen özelliğin başvurduğu özelliğe bir işaretçi alır `PropertyId` .</span><span class="sxs-lookup"><span data-stu-id="4f00e-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="4f00e-117">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f00e-117">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="4f00e-118">Bu nesne tarafından başvurulan derleme için sürüm bilgilerini alır `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="4f00e-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="4f00e-119">IsEqual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f00e-119">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="4f00e-120">Belirtilen `IAssemblyName` `IAssemblyName` karşılaştırma bayraklarını temel alarak belirtilen bir nesnenin bu değere eşit olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="4f00e-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="4f00e-121">SetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f00e-121">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="4f00e-122">Belirtilen öğesinin başvurduğu özelliğin değerini ayarlar `PropertyId` .</span><span class="sxs-lookup"><span data-stu-id="4f00e-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4f00e-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f00e-123">Requirements</span></span>  

 <span data-ttu-id="4f00e-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f00e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f00e-125">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="4f00e-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4f00e-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f00e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f00e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f00e-127">See also</span></span>

- [<span data-ttu-id="4f00e-128">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4f00e-128">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="4f00e-129">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f00e-129">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
