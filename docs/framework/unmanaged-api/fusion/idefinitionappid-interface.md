---
title: IDefinitionAppId Arabirimi
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bd705ef549de3a8018efe731ef8735ef7b6b915
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083185"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="08277-102">IDefinitionAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08277-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="08277-103">Uygulama geçerli kapsamda tanımlar kod için benzersiz bir tanımlayıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="08277-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08277-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="08277-104">Methods</span></span>  
  
|<span data-ttu-id="08277-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="08277-105">Method</span></span>|<span data-ttu-id="08277-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08277-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="08277-107">Bu kod temsil eden bir biçimlendirilmiş dize alır `IDefinitionAppId` nesne.</span><span class="sxs-lookup"><span data-stu-id="08277-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="08277-108">Bu kod ayarlar `IDefinitionAppId` belirtilen nesneye biçimlendirilmiş dize değeri.</span><span class="sxs-lookup"><span data-stu-id="08277-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="08277-109">Bir arabirim işaretçisi alır bir [Ienumdefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) geçerli uygulama yolu derlemeleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="08277-109">Gets an interface pointer to an [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="08277-110">Uygulama yolu geçerli kapsamda belirtilen tarafından başvurulan değer derleme için ayarlar [Idefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="08277-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="08277-111">Abonelik için bu belirteci tanımlayıcı bir dize gösterimini bir işaretçi alır `IDefinitionAppId` nesne.</span><span class="sxs-lookup"><span data-stu-id="08277-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="08277-112">Bir abonelik için belirteç tanımlayıcısı için ayarlar `IDefinitionAppId` nesne belirtilen dize değeri.</span><span class="sxs-lookup"><span data-stu-id="08277-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08277-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08277-113">Requirements</span></span>  
 <span data-ttu-id="08277-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08277-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08277-115">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="08277-115">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="08277-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="08277-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="08277-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08277-117">See also</span></span>

- [<span data-ttu-id="08277-118">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="08277-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
