---
description: 'Şu konuda daha fazla bilgi edinin: IDefinitionIdentity arabirimi'
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
ms.openlocfilehash: 3471879cc822b655b786dd9d8234950cb4b99c1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760660"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="76ddb-103">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76ddb-103">IDefinitionIdentity Interface</span></span>

<span data-ttu-id="76ddb-104">Geçerli kapsamdaki uygulamayı tanımlayan kodun benzersiz imzasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="76ddb-104">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="76ddb-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="76ddb-105">Methods</span></span>  
  
|<span data-ttu-id="76ddb-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="76ddb-106">Method</span></span>|<span data-ttu-id="76ddb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76ddb-107">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="76ddb-108">`IDefinitionIdentity` `IDefinitionIdentity` Belirtilen öznitelik değişiklikleri dışında, bu nesneyle özdeş olan yeni bir nesne için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="76ddb-108">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="76ddb-109">Bir [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) nesnesine, bununla ilişkili öznitelikleri içeren bir arabirim işaretçisi alır `IDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="76ddb-109">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="76ddb-110">Belirtilen ad alanında belirtilen ada sahip özniteliğin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="76ddb-110">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="76ddb-111">Belirtilen ad alanında belirtilen ada sahip özniteliği belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="76ddb-111">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="76ddb-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76ddb-112">Requirements</span></span>  

 <span data-ttu-id="76ddb-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76ddb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76ddb-114">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="76ddb-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="76ddb-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76ddb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ddb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76ddb-116">See also</span></span>

- [<span data-ttu-id="76ddb-117">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="76ddb-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
