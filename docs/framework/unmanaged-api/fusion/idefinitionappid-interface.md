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
ms.openlocfilehash: 5114f74e80da925c7a153b9e481c54067152eaec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108209"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="b51ca-102">IDefinitionAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b51ca-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="b51ca-103">Geçerli kapsamda uygulamayı tanımlayan kod için benzersiz tanımlayıcıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b51ca-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b51ca-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b51ca-104">Methods</span></span>  
  
|<span data-ttu-id="b51ca-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b51ca-105">Method</span></span>|<span data-ttu-id="b51ca-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b51ca-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="b51ca-107">Bu `IDefinitionAppId` nesnesindeki kodu temsil eden biçimli bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="b51ca-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="b51ca-108">Bu `IDefinitionAppId` nesnesinin kodunu belirtilen biçimli dize değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b51ca-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="b51ca-109">Geçerli uygulama yolundaki derlemeleri içeren bir [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) nesnesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="b51ca-109">Gets an interface pointer to an [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="b51ca-110">Geçerli kapsamdaki derleme için uygulama yolunu, belirtilen [IDefinitionIdentity](idefinitionidentity-interface.md) nesnesinin başvurduğu değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b51ca-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="b51ca-111">Bu `IDefinitionAppId` nesnesine bir abonelik için belirteç tanımlayıcısının dize gösterimine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="b51ca-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="b51ca-112">Bu `IDefinitionAppId` nesnesine yönelik bir aboneliğin Belirteç tanımlayıcısını belirtilen dize değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b51ca-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b51ca-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b51ca-113">Requirements</span></span>  
 <span data-ttu-id="b51ca-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b51ca-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b51ca-115">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="b51ca-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b51ca-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b51ca-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b51ca-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b51ca-117">See also</span></span>

- [<span data-ttu-id="b51ca-118">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b51ca-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
