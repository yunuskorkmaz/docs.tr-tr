---
title: "CorMethodImpl Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodImpl
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodImpl
helpviewer_keywords: CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85ee55c0d4ec0d3fb8c18dff570afefeb2eaf25e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="0f34b-102">CorMethodImpl Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0f34b-102">CorMethodImpl Enumeration</span></span>
<span data-ttu-id="0f34b-103">Yöntem uygulaması özellikleri açıklanmaktadır değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0f34b-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f34b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f34b-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="0f34b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0f34b-105">Members</span></span>  
  
|<span data-ttu-id="0f34b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0f34b-106">Member</span></span>|<span data-ttu-id="0f34b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f34b-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="0f34b-108">Kod türünü açıklayan bayrakları.</span><span class="sxs-lookup"><span data-stu-id="0f34b-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="0f34b-109">Yöntem uygulaması Microsoft Ara dili (MSIL) olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f34b-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="0f34b-110">Yöntem uygulaması yerel olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f34b-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="0f34b-111">Yöntem uygulaması OPTIL olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f34b-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="0f34b-112">Yöntem uygulaması ortak dil çalışma zamanı tarafından sağlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f34b-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="0f34b-113">Kod yönetilen veya yönetilmeyen olup olmadığını belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="0f34b-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="0f34b-114">Yöntem uygulaması yönetilmeyen olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f34b-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="0f34b-115">Yöntem uygulaması yönetilip yönetilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f34b-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="0f34b-116">Yöntemi tanımlanır belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f34b-116">Specifies that the method is defined.</span></span> <span data-ttu-id="0f34b-117">Bu bayrak, öncelikle birleştirme senaryolarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f34b-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="0f34b-118">Yöntem imzası HRESULT dönüştürme için karıştırılmış belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f34b-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="0f34b-119">İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="0f34b-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="0f34b-120">Yöntemi, tek kendi gövde iş parçacıklı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f34b-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="0f34b-121">Yöntem içermesinden olamaz belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f34b-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="0f34b-122">Yöntemi, mümkünse içermesinden olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f34b-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="0f34b-123">Yöntem getirilmemiş belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f34b-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="0f34b-124">Geçerli değeri en fazla bir `CorMethodImpl`.</span><span class="sxs-lookup"><span data-stu-id="0f34b-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f34b-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f34b-125">Requirements</span></span>  
 <span data-ttu-id="0f34b-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f34b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f34b-127">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="0f34b-127">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0f34b-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f34b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f34b-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f34b-129">See Also</span></span>  
 [<span data-ttu-id="0f34b-130">Meta veri numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="0f34b-130">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
