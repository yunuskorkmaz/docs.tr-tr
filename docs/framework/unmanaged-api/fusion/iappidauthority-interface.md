---
description: 'Daha fazla bilgi edinin: ıappidaduthority arabirimi'
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
ms.openlocfilehash: 238885c7f080571b414511c24f9772dbc19b4683
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761011"
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="4731f-103">IAppIdAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4731f-103">IAppIdAuthority Interface</span></span>

<span data-ttu-id="4731f-104">Uygulama kimlikleri ve başvuruları için anahtarlar oluşturan ve karşılaştıran yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4731f-104">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4731f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4731f-105">Methods</span></span>  
  
|<span data-ttu-id="4731f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4731f-106">Method</span></span>|<span data-ttu-id="4731f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4731f-107">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="4731f-108">Belirtilen iki [IDefinitionAppId](idefinitionappid-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="4731f-108">Gets a value that indicates whether the two specified [IDefinitionAppId](idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="4731f-109">İlgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4731f-109">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="4731f-110">Belirtilen iki [IReferenceAppId](ireferenceappid-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="4731f-110">Gets a value that indicates whether the two specified [IReferenceAppId](ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="4731f-111">İlgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4731f-111">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="4731f-112">Belirtilen iki dize tanımının eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="4731f-112">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="4731f-113">İlgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4731f-113">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="4731f-114">Belirtilen iki dize başvurusunun eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="4731f-114">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="4731f-115">İlgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4731f-115">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="4731f-116">Geçerli kapsamdaki derlemeyi temsil eden yeni oluşturulan örneğe yönelik bir arabirim işaretçisi alır `IDefinitionAppId` .</span><span class="sxs-lookup"><span data-stu-id="4731f-116">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="4731f-117">Yeni oluşturulan `IReferenceAppId` , geçerli kapsamdaki derlemeyi temsil eden bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="4731f-117">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="4731f-118">Belirtilen bayrak değerlerini kullanarak belirtilen bir dize sürümünü alır `IDefinitionAppId` .</span><span class="sxs-lookup"><span data-stu-id="4731f-118">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="4731f-119">Belirtilen `IDefinitionAppId` ve aynı derlemenin temsil edilip edilmeyeceğini belirten bir değer alır `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="4731f-119">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="4731f-120">Belirtilen tanım dizesi ve başvuru dizesinin aynı derlemeyi temsil ettiğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="4731f-120">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="4731f-121">Belirtilen örneği temsil eden bir dize anahtarı alır `IDefinitionAppId` .</span><span class="sxs-lookup"><span data-stu-id="4731f-121">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="4731f-122">Belirtilen örneği temsil eden bir dize anahtarı alır `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="4731f-122">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="4731f-123">Belirtilen örnek için bir karma anahtar alır `IDefinitionAppId` .</span><span class="sxs-lookup"><span data-stu-id="4731f-123">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="4731f-124">Belirtilen örnek için bir karma anahtar alır `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="4731f-124">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="4731f-125">Belirtilen bayrak değerlerini kullanarak belirtilen bir dize sürümünü alır `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="4731f-125">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="4731f-126">`IDefinitionAppId`Belirtilen dize anahtarı tarafından başvurulan derlemeyi temsil eden bir örneğe yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="4731f-126">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="4731f-127">`IReferenceAppId`Belirtilen dize anahtarı tarafından başvurulan derlemeyi temsil eden bir örneğe yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="4731f-127">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4731f-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4731f-128">Requirements</span></span>  

 <span data-ttu-id="4731f-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4731f-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4731f-130">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="4731f-130">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="4731f-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4731f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4731f-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4731f-132">See also</span></span>

- [<span data-ttu-id="4731f-133">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4731f-133">Fusion Interfaces</span></span>](fusion-interfaces.md)
