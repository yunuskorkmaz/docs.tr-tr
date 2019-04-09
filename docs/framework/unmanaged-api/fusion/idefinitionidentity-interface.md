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
ms.openlocfilehash: 4ff23330f307c10eac134048de39a6e19a67c75b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192673"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="254c8-102">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="254c8-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="254c8-103">Uygulama geçerli kapsamda tanımlar kod benzersiz imzası temsil eder.</span><span class="sxs-lookup"><span data-stu-id="254c8-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="254c8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="254c8-104">Methods</span></span>  
  
|<span data-ttu-id="254c8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="254c8-105">Method</span></span>|<span data-ttu-id="254c8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="254c8-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="254c8-107">Yeni bir arabirim işaretçisi alır `IDefinitionIdentity` için aynı olan nesne `IDefinitionIdentity`, belirtilen öznitelik değişiklikleri dışında.</span><span class="sxs-lookup"><span data-stu-id="254c8-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="254c8-108">Bir arabirim işaretçisi alır bir [Ienumıdentıty_attrıbute](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) bununla ilişkili öznitelikleri içeren nesne `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="254c8-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="254c8-109">Belirtilen ad alanında belirtilen ada sahip bir öznitelik değerini alır.</span><span class="sxs-lookup"><span data-stu-id="254c8-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="254c8-110">Belirtilen değer için belirtilen ad alanında belirtilen ada sahip özniteliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="254c8-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="254c8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="254c8-111">Requirements</span></span>  
 <span data-ttu-id="254c8-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="254c8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="254c8-113">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="254c8-113">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="254c8-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="254c8-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="254c8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="254c8-115">See also</span></span>

- [<span data-ttu-id="254c8-116">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="254c8-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
