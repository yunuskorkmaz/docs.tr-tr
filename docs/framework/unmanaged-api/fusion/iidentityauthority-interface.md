---
description: 'Daha fazla bilgi edinin: IIdentityAuthority Arabirimi'
title: IIdentityAuthority Arabirimi
ms.date: 03/30/2017
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
ms.openlocfilehash: 3064a3d95ebe9a098a7cac0766f18654c6fab8b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800144"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="f8824-103">IIdentityAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f8824-103">IIdentityAuthority Interface</span></span>

<span data-ttu-id="f8824-104">Kod nesneleri için kimlik anahtarlarını yönetir.</span><span class="sxs-lookup"><span data-stu-id="f8824-104">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="f8824-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f8824-105">Methods</span></span>

|<span data-ttu-id="f8824-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f8824-106">Method</span></span>|<span data-ttu-id="f8824-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8824-107">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="f8824-108">Belirtilen iki [IDefinitionIdentity](idefinitionidentity-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f8824-108">Gets a value that indicates whether the two specified [IDefinitionIdentity](idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="f8824-109">Belirtilen iki [IReferenceIdentity](ireferenceidentity-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f8824-109">Gets a value that indicates whether the two specified [IReferenceIdentity](ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="f8824-110">Belirtilen iki dize tanımı kimlik temsilinin eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f8824-110">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="f8824-111">Belirtilen iki dize başvurusu kimlik temsilinin eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f8824-111">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="f8824-112">`IDefinitionIdentity`Geçerli kapsamdaki kod nesnesini temsil eden yeni bir örneğe yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f8824-112">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="f8824-113">`IReferenceIdentity`Geçerli kapsamdaki kod nesnesini temsil eden yeni bir örneğe yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f8824-113">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="f8824-114">Belirtilen biçimli bir dize sürümünü alır `IDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="f8824-114">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="f8824-115">Belirtilen geniş karakter arabelleğini belirtilen bir dize sürümüyle doldurur `IDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="f8824-115">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="f8824-116">Belirtilen `IDefinitionIdentity` ve `IReferenceIdentity` örneklerin aynı kod nesnesine başvurmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f8824-116">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="f8824-117">Belirtilen dizelerin aynı kod nesnesine başvurmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f8824-117">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="f8824-118">Belirtilen yeni oluşturulan dize anahtarı için bir işaretçi alır `IDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="f8824-118">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="f8824-119">Belirtilen yeni oluşturulan dize anahtarı için bir işaretçi alır `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="f8824-119">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="f8824-120">Belirtilen için bir karma değeri alır `IDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="f8824-120">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="f8824-121">Belirtilen için bir karma değeri alır `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="f8824-121">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="f8824-122">Belirtilen biçimli bir dize sürümünü alır `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="f8824-122">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="f8824-123">Belirtilen geniş karakter arabelleğini belirtilen bir dize sürümüyle doldurur `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="f8824-123">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="f8824-124">`IDefinitionIdentity`Belirtilen biçimli dizeden oluşturulan örneğe yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="f8824-124">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="f8824-125">`IReferenceIdentity`Belirtilen biçimli dizeden oluşturulan örneğe yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="f8824-125">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="f8824-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8824-126">Requirements</span></span>

<span data-ttu-id="f8824-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8824-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f8824-128">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="f8824-128">**Header:** Isolation.h</span></span>

<span data-ttu-id="f8824-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8824-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f8824-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8824-130">See also</span></span>

- [<span data-ttu-id="f8824-131">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f8824-131">Fusion Interfaces</span></span>](fusion-interfaces.md)
