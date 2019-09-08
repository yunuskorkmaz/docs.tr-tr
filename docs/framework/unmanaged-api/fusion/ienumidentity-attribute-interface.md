---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbb3ac150ebfe9fe3698427d8bb2bfb3e3347c07
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796458"
---
# <a name="ienumidentity_attribute-interface"></a><span data-ttu-id="823e3-102">IEnumIDENTITY_ATTRIBUTE Arabirimi</span><span class="sxs-lookup"><span data-stu-id="823e3-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="823e3-103">Geçerli kapsamdaki kod nesnesinin öznitelikleri için bir Numaralandırıcı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="823e3-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="823e3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="823e3-104">Methods</span></span>  
  
|<span data-ttu-id="823e3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="823e3-105">Method</span></span>|<span data-ttu-id="823e3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="823e3-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="823e3-107">İle aynı üyeleri `IEnumIDENTITY_ATTRIBUTE` `IEnumIDENTITY_ATTRIBUTE`içeren yeni bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="823e3-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="823e3-108">Bu `IEnumIDENTITY_ATTRIBUTE` öğelerin içerdiği verileri belirtilen veri arabelleğine yazar.</span><span class="sxs-lookup"><span data-stu-id="823e3-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="823e3-109">Geçerli konumdan başlayarak belirtilen sayıda öznitelik alır.</span><span class="sxs-lookup"><span data-stu-id="823e3-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="823e3-110">Yönerge işaretçisini bunun `IEnumIDENTITY_ATTRIBUTE`başlangıcına taşıdır.</span><span class="sxs-lookup"><span data-stu-id="823e3-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="823e3-111">Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.</span><span class="sxs-lookup"><span data-stu-id="823e3-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="823e3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="823e3-112">Requirements</span></span>  
 <span data-ttu-id="823e3-113">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="823e3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="823e3-114">**Üst bilgi** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="823e3-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="823e3-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="823e3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="823e3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="823e3-116">See also</span></span>

- [<span data-ttu-id="823e3-117">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="823e3-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
