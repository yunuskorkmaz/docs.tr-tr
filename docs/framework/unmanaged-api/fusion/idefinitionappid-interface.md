---
description: 'Şu konuda daha fazla bilgi edinin: IDefinitionAppId arabirimi'
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
ms.openlocfilehash: 3c68044e7e747521e190fad404e89d6d0a994611
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760673"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="c73a3-103">IDefinitionAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c73a3-103">IDefinitionAppId Interface</span></span>

<span data-ttu-id="c73a3-104">Geçerli kapsamda uygulamayı tanımlayan kod için benzersiz tanımlayıcıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c73a3-104">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c73a3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c73a3-105">Methods</span></span>  
  
|<span data-ttu-id="c73a3-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c73a3-106">Method</span></span>|<span data-ttu-id="c73a3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c73a3-107">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="c73a3-108">Bu nesnedeki kodu temsil eden biçimli bir dize alır `IDefinitionAppId` .</span><span class="sxs-lookup"><span data-stu-id="c73a3-108">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="c73a3-109">Bu `IDefinitionAppId` nesnenin kodunu belirtilen biçimli dize değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c73a3-109">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="c73a3-110">Geçerli uygulama yolundaki derlemeleri içeren bir [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) nesnesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="c73a3-110">Gets an interface pointer to an [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="c73a3-111">Geçerli kapsamdaki derleme için uygulama yolunu, belirtilen [IDefinitionIdentity](idefinitionidentity-interface.md) nesnesinin başvurduğu değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c73a3-111">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="c73a3-112">Bu nesne için bir abonelik için belirteç tanımlayıcısının dize gösterimine yönelik bir işaretçi alır `IDefinitionAppId` .</span><span class="sxs-lookup"><span data-stu-id="c73a3-112">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="c73a3-113">Bu nesne için bir aboneliğin Belirteç tanımlayıcısını `IDefinitionAppId` belirtilen dize değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c73a3-113">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c73a3-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c73a3-114">Requirements</span></span>  

 <span data-ttu-id="c73a3-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c73a3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c73a3-116">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="c73a3-116">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="c73a3-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c73a3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c73a3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c73a3-118">See also</span></span>

- [<span data-ttu-id="c73a3-119">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c73a3-119">Fusion Interfaces</span></span>](fusion-interfaces.md)
