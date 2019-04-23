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
ms.openlocfilehash: d725228f2a7359d415673fdcb90d0cabae1a40be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175532"
---
# <a name="ienumidentityattribute-interface"></a><span data-ttu-id="23b9c-102">IEnumIDENTITY_ATTRIBUTE Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23b9c-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="23b9c-103">Geçerli kapsam içinde kod nesnesinin öznitelikleri için bir numaralandırıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="23b9c-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23b9c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="23b9c-104">Methods</span></span>  
  
|<span data-ttu-id="23b9c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="23b9c-105">Method</span></span>|<span data-ttu-id="23b9c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23b9c-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="23b9c-107">Yeni bir arabirim işaretçisi alır `IEnumIDENTITY_ATTRIBUTE` bu aynı üyeleri içeren `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="23b9c-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="23b9c-108">Bu öğe içinde yer alan verileri Yazar `IEnumIDENTITY_ATTRIBUTE` belirtilen veri arabelleği için.</span><span class="sxs-lookup"><span data-stu-id="23b9c-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="23b9c-109">Öznitelikler, geçerli konumdan başlayarak belirtilen sayıda alır.</span><span class="sxs-lookup"><span data-stu-id="23b9c-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="23b9c-110">Yönerge işaretçisini bu başlangıcına taşır `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="23b9c-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="23b9c-111">Öğe, geçerli konumdan başlayarak belirtilen sayıda yönerge işaretçisini ileriye taşır.</span><span class="sxs-lookup"><span data-stu-id="23b9c-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23b9c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23b9c-112">Requirements</span></span>  
 <span data-ttu-id="23b9c-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23b9c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23b9c-114">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="23b9c-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="23b9c-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23b9c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b9c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23b9c-116">See also</span></span>

- [<span data-ttu-id="23b9c-117">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="23b9c-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
