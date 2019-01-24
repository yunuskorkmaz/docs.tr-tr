---
title: IReferenceIdentity Arabirimi
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb8686342b20bd6afe0a4c4803d64428ed95c98b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665779"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="675a7-102">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="675a7-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="675a7-103">Kod nesnesi benzersiz imzası bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="675a7-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="675a7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="675a7-104">Methods</span></span>  
  
|<span data-ttu-id="675a7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="675a7-105">Method</span></span>|<span data-ttu-id="675a7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="675a7-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="675a7-107">Yeni bir arabirim işaretçisi alır `IReferenceIdentity` için aynı olan örneği `IReferenceIdentity`, belirtilen öznitelik değişiklikleri dışında.</span><span class="sxs-lookup"><span data-stu-id="675a7-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="675a7-108">Bir arabirim işaretçisi alır bir `IEnumIDENTITY_ATTRIBUTE` bununla ilişkili öznitelikleri içeren örneğini `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="675a7-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="675a7-109">Belirtilen ada sahip belirtilen ad alanı özniteliğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="675a7-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="675a7-110">Belirtilen ad alanı ve belirtilen değere belirtilen ada sahip özniteliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="675a7-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="675a7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="675a7-111">Requirements</span></span>  
 <span data-ttu-id="675a7-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="675a7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="675a7-113">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="675a7-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="675a7-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="675a7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="675a7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="675a7-115">See also</span></span>
- [<span data-ttu-id="675a7-116">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="675a7-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="675a7-117">IEnumIDENTITY_ATTRIBUTE Arabirimi</span><span class="sxs-lookup"><span data-stu-id="675a7-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
