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
ms.openlocfilehash: 7e6bc57fb470a5c12549bb5f9445ecf1551425a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107836"
---
# <a name="ienumidentity_attribute-interface"></a><span data-ttu-id="98649-102">IEnumIDENTITY_ATTRIBUTE Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98649-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="98649-103">Geçerli kapsamdaki kod nesnesinin öznitelikleri için bir Numaralandırıcı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="98649-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98649-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="98649-104">Methods</span></span>  
  
|<span data-ttu-id="98649-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="98649-105">Method</span></span>|<span data-ttu-id="98649-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98649-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="98649-107">Bu `IEnumIDENTITY_ATTRIBUTE`aynı üyeleri içeren yeni bir `IEnumIDENTITY_ATTRIBUTE` yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="98649-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="98649-108">Bu `IEnumIDENTITY_ATTRIBUTE` öğelerinde içerilen verileri belirtilen veri arabelleğine yazar.</span><span class="sxs-lookup"><span data-stu-id="98649-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="98649-109">Geçerli konumdan başlayarak belirtilen sayıda öznitelik alır.</span><span class="sxs-lookup"><span data-stu-id="98649-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="98649-110">Yönerge işaretçisini bu `IEnumIDENTITY_ATTRIBUTE`başına kaydırır.</span><span class="sxs-lookup"><span data-stu-id="98649-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="98649-111">Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.</span><span class="sxs-lookup"><span data-stu-id="98649-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98649-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98649-112">Requirements</span></span>  
 <span data-ttu-id="98649-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98649-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98649-114">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="98649-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="98649-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98649-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98649-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98649-116">See also</span></span>

- [<span data-ttu-id="98649-117">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="98649-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
