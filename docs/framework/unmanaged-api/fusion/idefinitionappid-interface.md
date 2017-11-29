---
title: IDefinitionAppId Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionAppId
helpviewer_keywords: IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 382c82ff773d0ab1c046fc131fa87a4f74d19ea6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="d2024-102">IDefinitionAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2024-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="d2024-103">Uygulama geçerli kapsamda tanımlar kodu için benzersiz bir tanımlayıcıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d2024-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2024-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d2024-104">Methods</span></span>  
  
|<span data-ttu-id="d2024-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d2024-105">Method</span></span>|<span data-ttu-id="d2024-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2024-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="d2024-107">Bu kodda temsil eden biçimlendirilmiş bir dize alır `IDefinitionAppId` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d2024-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="d2024-108">Bu kod ayarlar `IDefinitionAppId` belirtilen nesneye biçimlendirilmiş bir dize değeri.</span><span class="sxs-lookup"><span data-stu-id="d2024-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="d2024-109">Bir arabirim işaretçisi alır bir [Ienumdefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) geçerli uygulama yolu derlemelerde içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="d2024-109">Gets an interface pointer to an [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="d2024-110">Uygulama yolu, belirtilen tarafından başvurulan değer için geçerli kapsamdaki derleme için ayarlar [Idefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d2024-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="d2024-111">Bu abonelik için bir işaretçi belirteç tanımlayıcı bir dize gösterimini alır `IDefinitionAppId` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d2024-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="d2024-112">Bir abonelik için belirteç tanımlayıcı için ayarlar `IDefinitionAppId` nesne için belirtilen dize değeri.</span><span class="sxs-lookup"><span data-stu-id="d2024-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2024-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2024-113">Requirements</span></span>  
 <span data-ttu-id="d2024-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2024-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2024-115">**Başlık:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="d2024-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="d2024-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2024-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2024-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d2024-117">See Also</span></span>  
 [<span data-ttu-id="d2024-118">Fusion arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d2024-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
