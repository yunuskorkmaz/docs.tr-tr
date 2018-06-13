---
title: IAppIdAuthority Arabirimi
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 819afec2c448e5f396ab54e2dde00c01da310b12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433756"
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="b700a-102">IAppIdAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b700a-102">IAppIdAuthority Interface</span></span>
<span data-ttu-id="b700a-103">Oluşturma ve uygulama kimlikleri ve başvurular tuşları karşılaştırmak yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b700a-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b700a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b700a-104">Methods</span></span>  
  
|<span data-ttu-id="b700a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b700a-105">Method</span></span>|<span data-ttu-id="b700a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b700a-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="b700a-107">İki belirtilen olup olmadığını belirten bir değer alır [Idefinitionappıd](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) örnekleri eşit.</span><span class="sxs-lookup"><span data-stu-id="b700a-107">Gets a value that indicates whether the two specified [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="b700a-108">Bayrak değeri, ilgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b700a-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="b700a-109">İki belirtilen olup olmadığını belirten bir değer alır [Ireferenceappıd](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) örnekleri eşit.</span><span class="sxs-lookup"><span data-stu-id="b700a-109">Gets a value that indicates whether the two specified [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="b700a-110">Bayrak değeri, ilgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b700a-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="b700a-111">İki belirtilen dize tanımları eşit olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b700a-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="b700a-112">Bayrak değeri, ilgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b700a-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="b700a-113">İki belirtilen dize başvuru eşit olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b700a-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="b700a-114">Bayrak değeri, ilgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b700a-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="b700a-115">Arabirim işaretçisi yeni oluşturulan alır `IDefinitionAppId` geçerli kapsamdaki derleme temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="b700a-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="b700a-116">Arabirim işaretçisi yeni oluşturulan alır `IReferenceAppId` , geçerli kapsamdaki derleme temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b700a-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="b700a-117">Dize sürümünü belirtilen alır `IDefinitionAppId`, belirtilen bayrak değerleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b700a-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="b700a-118">Gösteren bir değer alır olup belirtilen `IDefinitionAppId` ve `IReferenceAppId` aynı bütünleştirilmiş kodda temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b700a-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="b700a-119">Başvuru dizesi ve belirtilen tanımı dize aynı bütünleştirilmiş kodda gösterip göstermediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b700a-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="b700a-120">Belirtilen temsil eden bir dize anahtarı alır `IDefinitionAppId` örneği.</span><span class="sxs-lookup"><span data-stu-id="b700a-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="b700a-121">Belirtilen temsil eden bir dize anahtarı alır `IReferenceAppId` örneği.</span><span class="sxs-lookup"><span data-stu-id="b700a-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="b700a-122">Karma anahtar için belirtilen alır `IDefinitionAppId` örneği.</span><span class="sxs-lookup"><span data-stu-id="b700a-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="b700a-123">Karma anahtar için belirtilen alır `IReferenceAppId` örneği.</span><span class="sxs-lookup"><span data-stu-id="b700a-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="b700a-124">Dize sürümünü belirtilen alır `IReferenceAppId`, belirtilen bayrak değerleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b700a-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="b700a-125">Bir arabirim işaretçisi alır bir `IDefinitionAppId` belirtilen dizeyi anahtarı tarafından başvurulan derlemeyi temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="b700a-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="b700a-126">Bir arabirim işaretçisi alır bir `IReferenceAppId` belirtilen dizeyi anahtarı tarafından başvurulan derlemeyi temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="b700a-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b700a-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b700a-127">Requirements</span></span>  
 <span data-ttu-id="b700a-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b700a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b700a-129">**Başlık:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="b700a-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b700a-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b700a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b700a-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b700a-131">See Also</span></span>  
 [<span data-ttu-id="b700a-132">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b700a-132">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
