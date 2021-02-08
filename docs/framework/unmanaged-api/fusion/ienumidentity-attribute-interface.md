---
description: 'Hakkında daha fazla bilgi edinin: IEnumIDENTITY_ATTRIBUTE arabirimi'
title: IEnumIDENTITY_ATTRIBUTE Arabirimi
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
ms.openlocfilehash: b621a722e35d5b31f487e8823b1627fdfe1e7888
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800155"
---
# <a name="ienumidentity_attribute-interface"></a><span data-ttu-id="7e0f2-103">IEnumIDENTITY_ATTRIBUTE Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e0f2-103">IEnumIDENTITY_ATTRIBUTE Interface</span></span>

<span data-ttu-id="7e0f2-104">Geçerli kapsamdaki kod nesnesinin öznitelikleri için bir Numaralandırıcı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="7e0f2-104">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e0f2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7e0f2-105">Methods</span></span>  
  
|<span data-ttu-id="7e0f2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7e0f2-106">Method</span></span>|<span data-ttu-id="7e0f2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e0f2-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="7e0f2-108">İle aynı üyeleri içeren yeni bir arabirim işaretçisi alır `IEnumIDENTITY_ATTRIBUTE` `IEnumIDENTITY_ATTRIBUTE` .</span><span class="sxs-lookup"><span data-stu-id="7e0f2-108">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="7e0f2-109">Bu öğelerin içerdiği verileri `IEnumIDENTITY_ATTRIBUTE` belirtilen veri arabelleğine yazar.</span><span class="sxs-lookup"><span data-stu-id="7e0f2-109">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="7e0f2-110">Geçerli konumdan başlayarak belirtilen sayıda öznitelik alır.</span><span class="sxs-lookup"><span data-stu-id="7e0f2-110">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="7e0f2-111">Yönerge işaretçisini bunun başlangıcına taşıdır `IEnumIDENTITY_ATTRIBUTE` .</span><span class="sxs-lookup"><span data-stu-id="7e0f2-111">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="7e0f2-112">Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.</span><span class="sxs-lookup"><span data-stu-id="7e0f2-112">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7e0f2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e0f2-113">Requirements</span></span>  

 <span data-ttu-id="7e0f2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e0f2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e0f2-115">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="7e0f2-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="7e0f2-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e0f2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e0f2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e0f2-117">See also</span></span>

- [<span data-ttu-id="7e0f2-118">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7e0f2-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
