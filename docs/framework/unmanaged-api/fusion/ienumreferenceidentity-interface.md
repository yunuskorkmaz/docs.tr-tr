---
title: IEnumReferenceIdentity Arabirimi
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
ms.openlocfilehash: 1305b9ebe3cd87ba002ee87610ff309d015a44e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131741"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="d3110-102">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3110-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="d3110-103">`IReferenceIdentity` nesnelerinin bir koleksiyonu için bir Numaralandırıcı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="d3110-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3110-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d3110-104">Methods</span></span>  
  
|<span data-ttu-id="d3110-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d3110-105">Method</span></span>|<span data-ttu-id="d3110-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3110-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="d3110-107">Bu `IEnumReferenceIdentity`aynı üyeleri içeren yeni bir `IEnumReferenceIdentity` yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="d3110-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="d3110-108">Geçerli konumdan başlayarak belirtilen sayıda `IReferenceIdentity` nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="d3110-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="d3110-109">Yönerge işaretçisini bu `IEnumReferenceIdentity`başına kaydırır.</span><span class="sxs-lookup"><span data-stu-id="d3110-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="d3110-110">Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.</span><span class="sxs-lookup"><span data-stu-id="d3110-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3110-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3110-111">Requirements</span></span>  
 <span data-ttu-id="d3110-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3110-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3110-113">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="d3110-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="d3110-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3110-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3110-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3110-115">See also</span></span>

- [<span data-ttu-id="d3110-116">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d3110-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="d3110-117">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3110-117">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
