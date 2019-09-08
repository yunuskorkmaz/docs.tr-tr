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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c5d4bc1fa82f7623168050f4ee36f0ea3cd171e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796438"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="8b405-102">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b405-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="8b405-103">Bir `IReferenceIdentity` nesne koleksiyonu için bir Numaralandırıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="8b405-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b405-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8b405-104">Methods</span></span>  
  
|<span data-ttu-id="8b405-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8b405-105">Method</span></span>|<span data-ttu-id="8b405-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b405-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="8b405-107">İle aynı üyeleri `IEnumReferenceIdentity` `IEnumReferenceIdentity`içeren yeni bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="8b405-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="8b405-108">Geçerli konumdan başlayarak belirtilen sayıda `IReferenceIdentity` nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="8b405-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="8b405-109">Yönerge işaretçisini bunun `IEnumReferenceIdentity`başlangıcına taşıdır.</span><span class="sxs-lookup"><span data-stu-id="8b405-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="8b405-110">Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.</span><span class="sxs-lookup"><span data-stu-id="8b405-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b405-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b405-111">Requirements</span></span>  
 <span data-ttu-id="8b405-112">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b405-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b405-113">**Üst bilgi** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="8b405-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="8b405-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b405-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b405-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b405-115">See also</span></span>

- [<span data-ttu-id="8b405-116">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8b405-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="8b405-117">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b405-117">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
