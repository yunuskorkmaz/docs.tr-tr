---
title: IReferenceIdentity Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceIdentity
helpviewer_keywords: IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 35c6152836adf02d541bacd149ed9ac053765ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="e5e4a-102">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5e4a-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="e5e4a-103">Bir kod nesnesinin benzersiz imza başvuru temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e5e4a-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5e4a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e5e4a-104">Methods</span></span>  
  
|<span data-ttu-id="e5e4a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e5e4a-105">Method</span></span>|<span data-ttu-id="e5e4a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5e4a-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="e5e4a-107">Arabirim işaretçisi yeni bir alır `IReferenceIdentity` için aynı olan örneği `IReferenceIdentity`, belirtilen öznitelik değişikliklerini dışında.</span><span class="sxs-lookup"><span data-stu-id="e5e4a-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="e5e4a-108">Bir arabirim işaretçisi alır bir `IEnumIDENTITY_ATTRIBUTE` bu ile ilişkili öznitelikleri içeren örneği `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="e5e4a-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="e5e4a-109">Belirtilen ada sahip belirtilen ad alanında özniteliğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="e5e4a-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="e5e4a-110">Belirtilen ad ve belirtilen değeri belirtilen ada sahip öznitelik ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e5e4a-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5e4a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5e4a-111">Requirements</span></span>  
 <span data-ttu-id="e5e4a-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5e4a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5e4a-113">**Başlık:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="e5e4a-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="e5e4a-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5e4a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e4a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5e4a-115">See Also</span></span>  
 [<span data-ttu-id="e5e4a-116">Fusion arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e5e4a-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="e5e4a-117">Ienumıdentıty_attrıbute arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5e4a-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
