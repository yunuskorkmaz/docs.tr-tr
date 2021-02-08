---
description: 'Daha fazla bilgi edinin: CorMethodImpl numaralandırması'
title: CorMethodImpl Numaralandırması
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
ms.openlocfilehash: 157db81a72742f1f2aae7e95249b819b2396ef4b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784398"
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="42cf9-103">CorMethodImpl Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="42cf9-103">CorMethodImpl Enumeration</span></span>

<span data-ttu-id="42cf9-104">Yöntem uygulama özelliklerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="42cf9-104">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42cf9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="42cf9-105">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a><span data-ttu-id="42cf9-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="42cf9-106">Members</span></span>  
  
|<span data-ttu-id="42cf9-107">Üye</span><span class="sxs-lookup"><span data-stu-id="42cf9-107">Member</span></span>|<span data-ttu-id="42cf9-108">Description</span><span class="sxs-lookup"><span data-stu-id="42cf9-108">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="42cf9-109">Kod türünü tanımlayan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="42cf9-109">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="42cf9-110">Yöntem uygulamasının Microsoft ara dil (MSIL) olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="42cf9-110">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="42cf9-111">Yöntem uygulamasının yerel olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="42cf9-111">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="42cf9-112">Yöntem uygulamasının OPTIL olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="42cf9-112">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="42cf9-113">Yöntem uygulamasının ortak dil çalışma zamanı tarafından sağlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="42cf9-113">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="42cf9-114">Kodun yönetilip yönetilmediğini belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="42cf9-114">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="42cf9-115">Yöntem uygulamasının yönetilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="42cf9-115">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="42cf9-116">Yöntem uygulamasının yönetileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="42cf9-116">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="42cf9-117">Yöntemin tanımlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="42cf9-117">Specifies that the method is defined.</span></span> <span data-ttu-id="42cf9-118">Bu bayrak birincil olarak birleştirme senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42cf9-118">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="42cf9-119">Bir HRESULT dönüştürmesi için yöntem imzasının karıştırılamıyor olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="42cf9-119">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="42cf9-120">Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="42cf9-120">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="42cf9-121">Yöntemin gövdesinde tek iş parçacıklı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="42cf9-121">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="42cf9-122">Metodun satır içine alınamıyor olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="42cf9-122">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="42cf9-123">Mümkünse yöntemin satır içine alınmış olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="42cf9-123">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="42cf9-124">Yöntemin iyileştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="42cf9-124">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="42cf9-125">İçin geçerli en büyük değer `CorMethodImpl` .</span><span class="sxs-lookup"><span data-stu-id="42cf9-125">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42cf9-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42cf9-126">Requirements</span></span>  

 <span data-ttu-id="42cf9-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42cf9-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42cf9-128">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="42cf9-128">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="42cf9-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42cf9-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42cf9-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42cf9-130">See also</span></span>

- [<span data-ttu-id="42cf9-131">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="42cf9-131">Metadata Enumerations</span></span>](metadata-enumerations.md)
