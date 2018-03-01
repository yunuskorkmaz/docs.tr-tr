---
title: IIdentityAuthority Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 322b15252271472b5bee1dfc6a843079cebbe0b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="12f8f-102">IIdentityAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12f8f-102">IIdentityAuthority Interface</span></span>
<span data-ttu-id="12f8f-103">Kod nesneleri kimlik tuşları yönetir.</span><span class="sxs-lookup"><span data-stu-id="12f8f-103">Manages identity keys for code objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12f8f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="12f8f-104">Methods</span></span>  
  
|<span data-ttu-id="12f8f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="12f8f-105">Method</span></span>|<span data-ttu-id="12f8f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12f8f-106">Description</span></span>|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="12f8f-107">İki belirtilen olup olmadığını belirten bir değer alır [Idefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) örnekleri eşit.</span><span class="sxs-lookup"><span data-stu-id="12f8f-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="12f8f-108">İki belirtilen olup olmadığını belirten bir değer alır [Ireferenceıdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) örnekleri eşit.</span><span class="sxs-lookup"><span data-stu-id="12f8f-108">Gets a value that indicates whether the two specified [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="12f8f-109">İki belirtilen dize tanımı kimliği sunumu eşit olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="12f8f-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|  
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="12f8f-110">İki belirtilen dize başvuru kimliği sunumu eşit olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="12f8f-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|  
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="12f8f-111">Bir işaretçi yeni bir alır `IDefinitionIdentity` geçerli kapsamdaki kod nesnesini temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="12f8f-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="12f8f-112">Bir işaretçi yeni bir alır `IReferenceIdentity` geçerli kapsamdaki kod nesnesini temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="12f8f-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="12f8f-113">Biçimlendirilmiş dize sürümünü belirtilen alır `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="12f8f-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="12f8f-114">Belirtilen dize sürümüyle belirtilen geniş karakter arabellek doldurur `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="12f8f-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="12f8f-115">Gösteren bir değer alır olup belirtilen `IDefinitionIdentity` ve `IReferenceIdentity` örnekleri aynı kodu nesnesine bakın.</span><span class="sxs-lookup"><span data-stu-id="12f8f-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="12f8f-116">Belirtilen dizeleri aynı kodu nesnesine başvuru olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="12f8f-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|  
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="12f8f-117">Yeni oluşturulan dize anahtarı için belirtilen bir işaretçi alır `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="12f8f-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="12f8f-118">Yeni oluşturulan dize anahtarı için belirtilen bir işaretçi alır `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="12f8f-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="12f8f-119">Bir karma değer için belirtilen alır `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="12f8f-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::HashReference`|<span data-ttu-id="12f8f-120">Bir karma değer için belirtilen alır `IreferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="12f8f-120">Gets a hash value for the specified `IreferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="12f8f-121">Biçimlendirilmiş dize sürümünü belirtilen alır `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="12f8f-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="12f8f-122">Belirtilen dize sürümüyle belirtilen geniş karakter arabellek doldurur `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="12f8f-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="12f8f-123">Bir arabirim işaretçisi alır bir `IDefinitionIdentity` örneği belirtilen oluşturulan biçimlendirilmiş dize.</span><span class="sxs-lookup"><span data-stu-id="12f8f-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|  
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="12f8f-124">Bir arabirim işaretçisi alır bir `IReferenceIdentity` örneği belirtilen oluşturulan biçimlendirilmiş dize.</span><span class="sxs-lookup"><span data-stu-id="12f8f-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="12f8f-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12f8f-125">Requirements</span></span>  
 <span data-ttu-id="12f8f-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12f8f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12f8f-127">**Başlık:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="12f8f-127">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="12f8f-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12f8f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f8f-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12f8f-129">See Also</span></span>  
 [<span data-ttu-id="12f8f-130">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="12f8f-130">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
