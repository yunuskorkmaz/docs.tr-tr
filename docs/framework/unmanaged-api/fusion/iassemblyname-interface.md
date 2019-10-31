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
ms.openlocfilehash: de49d66667033dfc6918b139f90cd5523661597f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134323"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="9bfc2-102">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bfc2-102">IAssemblyName Interface</span></span>
<span data-ttu-id="9bfc2-103">Bir derlemenin benzersiz kimliğini tanımlamak ve bunlarla çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bfc2-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9bfc2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9bfc2-104">Methods</span></span>  
  
|<span data-ttu-id="9bfc2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9bfc2-105">Method</span></span>|<span data-ttu-id="9bfc2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bfc2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9bfc2-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bfc2-107">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="9bfc2-108">Bu `IAssemblyName` nesnesinin basit bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9bfc2-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="9bfc2-109">Finalize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bfc2-109">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="9bfc2-110">Bu `IAssemblyName` nesnesinin, yıkıcısı çağrılmadan önce kaynakları serbest bırakmasıyla ve diğer temizleme işlemlerini gerçekleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9bfc2-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="9bfc2-111">GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bfc2-111">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="9bfc2-112">Bu `IAssemblyName` nesnesi tarafından başvurulan derlemenin okunabilir adını alır.</span><span class="sxs-lookup"><span data-stu-id="9bfc2-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="9bfc2-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bfc2-113">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="9bfc2-114">Bu `IAssemblyName` nesnesi tarafından başvurulan derlemenin basit, şifrelenmemiş adını alır.</span><span class="sxs-lookup"><span data-stu-id="9bfc2-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="9bfc2-115">GetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bfc2-115">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="9bfc2-116">Belirtilen `PropertyId`başvurduğu özelliğe bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="9bfc2-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="9bfc2-117">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bfc2-117">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="9bfc2-118">Bu `IAssemblyName` nesnesi tarafından başvurulan derleme için sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="9bfc2-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="9bfc2-119">IsEqual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bfc2-119">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="9bfc2-120">Belirtilen bir `IAssemblyName` nesnesinin, belirtilen karşılaştırma bayraklarını temel alarak bu `IAssemblyName`eşit olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="9bfc2-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="9bfc2-121">SetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bfc2-121">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="9bfc2-122">Belirtilen `PropertyId`başvurduğu özelliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9bfc2-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9bfc2-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9bfc2-123">Requirements</span></span>  
 <span data-ttu-id="9bfc2-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bfc2-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bfc2-125">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="9bfc2-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9bfc2-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bfc2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bfc2-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bfc2-127">See also</span></span>

- [<span data-ttu-id="9bfc2-128">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9bfc2-128">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="9bfc2-129">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bfc2-129">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
