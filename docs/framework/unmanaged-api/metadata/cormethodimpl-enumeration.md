---
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
ms.openlocfilehash: 40e82997e58292a10f5e960cc9d9785d9ea8946a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676991"
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="e9367-102">CorMethodImpl Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e9367-102">CorMethodImpl Enumeration</span></span>

<span data-ttu-id="e9367-103">Yöntem uygulama özelliklerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e9367-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9367-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e9367-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="e9367-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e9367-105">Members</span></span>  
  
|<span data-ttu-id="e9367-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e9367-106">Member</span></span>|<span data-ttu-id="e9367-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9367-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="e9367-108">Kod türünü tanımlayan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="e9367-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="e9367-109">Yöntem uygulamasının Microsoft ara dil (MSIL) olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9367-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="e9367-110">Yöntem uygulamasının yerel olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9367-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="e9367-111">Yöntem uygulamasının OPTIL olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9367-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="e9367-112">Yöntem uygulamasının ortak dil çalışma zamanı tarafından sağlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9367-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="e9367-113">Kodun yönetilip yönetilmediğini belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="e9367-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="e9367-114">Yöntem uygulamasının yönetilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9367-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="e9367-115">Yöntem uygulamasının yönetileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9367-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="e9367-116">Yöntemin tanımlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9367-116">Specifies that the method is defined.</span></span> <span data-ttu-id="e9367-117">Bu bayrak birincil olarak birleştirme senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9367-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="e9367-118">Bir HRESULT dönüştürmesi için yöntem imzasının karıştırılamıyor olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9367-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="e9367-119">Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e9367-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="e9367-120">Yöntemin gövdesinde tek iş parçacıklı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9367-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="e9367-121">Metodun satır içine alınamıyor olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9367-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="e9367-122">Mümkünse yöntemin satır içine alınmış olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9367-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="e9367-123">Yöntemin iyileştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="e9367-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="e9367-124">İçin geçerli en büyük değer `CorMethodImpl` .</span><span class="sxs-lookup"><span data-stu-id="e9367-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e9367-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9367-125">Requirements</span></span>  

 <span data-ttu-id="e9367-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9367-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9367-127">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="e9367-127">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e9367-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9367-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9367-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9367-129">See also</span></span>

- [<span data-ttu-id="e9367-130">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="e9367-130">Metadata Enumerations</span></span>](metadata-enumerations.md)
