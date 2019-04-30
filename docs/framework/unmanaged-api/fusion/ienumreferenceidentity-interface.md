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
ms.openlocfilehash: 766b17bae0c58d9872ff9c118f330ebc3220257e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697257"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="4e4d0-102">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e4d0-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="4e4d0-103">Bir koleksiyonu için bir numaralandırıcı görevi gören `IReferenceIdentity` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4e4d0-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e4d0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4e4d0-104">Methods</span></span>  
  
|<span data-ttu-id="4e4d0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4e4d0-105">Method</span></span>|<span data-ttu-id="4e4d0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e4d0-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="4e4d0-107">Yeni bir arabirim işaretçisi alır `IEnumReferenceIdentity` bu aynı üyeleri içeren `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="4e4d0-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="4e4d0-108">Belirtilen sayıda alır `IReferenceIdentity` nesneleri, geçerli konumdan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="4e4d0-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="4e4d0-109">Yönerge işaretçisini bu başlangıcına taşır `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="4e4d0-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="4e4d0-110">Öğe, geçerli konumdan başlayarak belirtilen sayıda yönerge işaretçisini ileriye taşır.</span><span class="sxs-lookup"><span data-stu-id="4e4d0-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e4d0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e4d0-111">Requirements</span></span>  
 <span data-ttu-id="4e4d0-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e4d0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e4d0-113">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="4e4d0-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="4e4d0-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e4d0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e4d0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e4d0-115">See also</span></span>

- [<span data-ttu-id="4e4d0-116">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4e4d0-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="4e4d0-117">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e4d0-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
