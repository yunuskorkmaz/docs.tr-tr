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
ms.openlocfilehash: 724ee01e91f1e9f4e34d2262610152a977ed4f53
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206661"
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="b02db-102">IAppIdAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b02db-102">IAppIdAuthority Interface</span></span>
<span data-ttu-id="b02db-103">Oluşturma ve uygulama kimlikleri ve başvurular için anahtarları karşılaştırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b02db-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b02db-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b02db-104">Methods</span></span>  
  
|<span data-ttu-id="b02db-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b02db-105">Method</span></span>|<span data-ttu-id="b02db-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b02db-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="b02db-107">İki belirtilen olup olmadığını gösteren bir değer alır [Idefinitionappıd](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) örnekleri eşit.</span><span class="sxs-lookup"><span data-stu-id="b02db-107">Gets a value that indicates whether the two specified [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="b02db-108">İlgili sürüm bilgilerini yok saymak için IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b02db-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="b02db-109">İki belirtilen olup olmadığını gösteren bir değer alır [Ireferenceappıd](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) örnekleri eşit.</span><span class="sxs-lookup"><span data-stu-id="b02db-109">Gets a value that indicates whether the two specified [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="b02db-110">İlgili sürüm bilgilerini yok saymak için IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b02db-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="b02db-111">İki belirtilen dize tanımları eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b02db-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="b02db-112">İlgili sürüm bilgilerini yok saymak için IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b02db-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="b02db-113">İki belirtilen dize başvuru eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b02db-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="b02db-114">İlgili sürüm bilgilerini yok saymak için IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b02db-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="b02db-115">Yeni oluşturulan bir arabirim işaretçisi alır `IDefinitionAppId` derleme geçerli kapsamda temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="b02db-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="b02db-116">Yeni oluşturulan bir arabirim işaretçisi alır `IReferenceAppId` , derleme geçerli kapsamda temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b02db-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="b02db-117">Belirtilen bir dize sürümünü alır `IDefinitionAppId`, belirtilen bayrak değerleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b02db-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="b02db-118">Belirten bir değer alır olup belirtilen `IDefinitionAppId` ve `IReferenceAppId` aynı derlemenin temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b02db-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="b02db-119">Başvuru dizesi ve belirtilen tanım dize aynı derlemenin gösterip göstermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b02db-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="b02db-120">Belirtilen temsil eden bir dize anahtarı alır `IDefinitionAppId` örneği.</span><span class="sxs-lookup"><span data-stu-id="b02db-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="b02db-121">Belirtilen temsil eden bir dize anahtarı alır `IReferenceAppId` örneği.</span><span class="sxs-lookup"><span data-stu-id="b02db-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="b02db-122">Bir karma anahtar için belirtilen alır `IDefinitionAppId` örneği.</span><span class="sxs-lookup"><span data-stu-id="b02db-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="b02db-123">Bir karma anahtar için belirtilen alır `IReferenceAppId` örneği.</span><span class="sxs-lookup"><span data-stu-id="b02db-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="b02db-124">Belirtilen bir dize sürümünü alır `IReferenceAppId`, belirtilen bayrak değerleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b02db-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="b02db-125">Bir arabirim işaretçisi alır bir `IDefinitionAppId` örneğini belirtilen dizeyi anahtarı tarafından başvurulan bütünleştirilmiş kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b02db-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="b02db-126">Bir arabirim işaretçisi alır bir `IReferenceAppId` örneğini belirtilen dizeyi anahtarı tarafından başvurulan bütünleştirilmiş kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b02db-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b02db-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b02db-127">Requirements</span></span>  
 <span data-ttu-id="b02db-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b02db-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b02db-129">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="b02db-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b02db-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b02db-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b02db-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b02db-131">See also</span></span>

- [<span data-ttu-id="b02db-132">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b02db-132">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
