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
ms.openlocfilehash: aee9b986c1e26c1b2e34dac7151a00172451bbad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796557"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="ed85b-102">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed85b-102">IAssemblyName Interface</span></span>
<span data-ttu-id="ed85b-103">Bir derlemenin benzersiz kimliğini tanımlamak ve bunlarla çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed85b-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ed85b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ed85b-104">Methods</span></span>  
  
|<span data-ttu-id="ed85b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ed85b-105">Method</span></span>|<span data-ttu-id="ed85b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed85b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ed85b-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed85b-107">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="ed85b-108">Bu `IAssemblyName` nesnenin basit bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ed85b-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="ed85b-109">Finalize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed85b-109">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="ed85b-110">Bu `IAssemblyName` nesnenin, yıkıcısı çağrılmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="ed85b-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="ed85b-111">GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed85b-111">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="ed85b-112">Bu `IAssemblyName` nesne tarafından başvurulan derlemenin okunabilir adını alır.</span><span class="sxs-lookup"><span data-stu-id="ed85b-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="ed85b-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed85b-113">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="ed85b-114">Bu `IAssemblyName` nesnenin başvurduğu derlemenin basit, şifrelenmemiş adını alır.</span><span class="sxs-lookup"><span data-stu-id="ed85b-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="ed85b-115">GetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed85b-115">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="ed85b-116">Belirtilen `PropertyId`özelliğin başvurduğu özelliğe bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ed85b-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="ed85b-117">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed85b-117">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="ed85b-118">Bu `IAssemblyName` nesne tarafından başvurulan derleme için sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="ed85b-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="ed85b-119">IsEqual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed85b-119">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="ed85b-120">Belirtilen karşılaştırma bayraklarını temel `IAssemblyName` alarak belirtilen bir nesnenin bu `IAssemblyName`değere eşit olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="ed85b-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="ed85b-121">SetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed85b-121">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="ed85b-122">Belirtilen `PropertyId`öğesinin başvurduğu özelliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ed85b-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed85b-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed85b-123">Requirements</span></span>  
 <span data-ttu-id="ed85b-124">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed85b-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed85b-125">**Üst bilgi** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ed85b-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ed85b-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed85b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed85b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed85b-127">See also</span></span>

- [<span data-ttu-id="ed85b-128">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ed85b-128">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="ed85b-129">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed85b-129">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
