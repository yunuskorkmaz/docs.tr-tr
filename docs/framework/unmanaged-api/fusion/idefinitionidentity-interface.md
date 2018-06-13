---
title: IDefinitionIdentity Arabirimi
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 401c23e44cc473d0a27a82a00343852693cb0f2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429351"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="86fc0-102">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86fc0-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="86fc0-103">Uygulama geçerli kapsamda tanımlar kodunun benzersiz imza temsil eder.</span><span class="sxs-lookup"><span data-stu-id="86fc0-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86fc0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="86fc0-104">Methods</span></span>  
  
|<span data-ttu-id="86fc0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="86fc0-105">Method</span></span>|<span data-ttu-id="86fc0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86fc0-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="86fc0-107">Arabirim işaretçisi yeni bir alır `IDefinitionIdentity` için aynı nesne `IDefinitionIdentity`, belirtilen öznitelik değişikliklerini dışında.</span><span class="sxs-lookup"><span data-stu-id="86fc0-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="86fc0-108">Bir arabirim işaretçisi alır bir [Ienumıdentıty_attrıbute](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) bu ile ilişkili öznitelikleri içeren nesne `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="86fc0-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="86fc0-109">Belirtilen ada sahip özniteliğin değerini belirtilen ad alanında alır.</span><span class="sxs-lookup"><span data-stu-id="86fc0-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="86fc0-110">Belirtilen değer için belirtilen ad alanında belirtilen ada sahip öznitelik ayarlar.</span><span class="sxs-lookup"><span data-stu-id="86fc0-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86fc0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86fc0-111">Requirements</span></span>  
 <span data-ttu-id="86fc0-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86fc0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86fc0-113">**Başlık:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="86fc0-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="86fc0-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86fc0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86fc0-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86fc0-115">See Also</span></span>  
 [<span data-ttu-id="86fc0-116">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="86fc0-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
