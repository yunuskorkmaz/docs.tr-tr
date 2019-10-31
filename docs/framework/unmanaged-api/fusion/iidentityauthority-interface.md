---
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
ms.openlocfilehash: 3e2d2335e37ced9139ea44092f10b19566894681
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127089"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="74810-102">IIdentityAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74810-102">IIdentityAuthority Interface</span></span>

<span data-ttu-id="74810-103">Kod nesneleri için kimlik anahtarlarını yönetir.</span><span class="sxs-lookup"><span data-stu-id="74810-103">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="74810-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="74810-104">Methods</span></span>

|<span data-ttu-id="74810-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="74810-105">Method</span></span>|<span data-ttu-id="74810-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74810-106">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="74810-107">Belirtilen iki [IDefinitionIdentity](idefinitionidentity-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="74810-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="74810-108">Belirtilen iki [IReferenceIdentity](ireferenceidentity-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="74810-108">Gets a value that indicates whether the two specified [IReferenceIdentity](ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="74810-109">Belirtilen iki dize tanımı kimlik temsilinin eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="74810-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="74810-110">Belirtilen iki dize başvurusu kimlik temsilinin eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="74810-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="74810-111">Geçerli kapsamdaki kod nesnesini temsil eden yeni bir `IDefinitionIdentity` örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="74810-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="74810-112">Geçerli kapsamdaki kod nesnesini temsil eden yeni bir `IReferenceIdentity` örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="74810-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="74810-113">Belirtilen `IDefinitionIdentity`biçimlendirilen dize sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="74810-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="74810-114">Belirtilen geniş karakter arabelleğini belirtilen `IDefinitionIdentity`bir dize sürümüyle doldurur.</span><span class="sxs-lookup"><span data-stu-id="74810-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="74810-115">Belirtilen `IDefinitionIdentity` ve `IReferenceIdentity` örneklerinin aynı kod nesnesine başvuruda bulunup bulunmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="74810-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="74810-116">Belirtilen dizelerin aynı kod nesnesine başvurmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="74810-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="74810-117">Belirtilen `IDefinitionIdentity`yeni oluşturulan dize anahtarına yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="74810-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="74810-118">Belirtilen `IReferenceIdentity`yeni oluşturulan dize anahtarına yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="74810-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="74810-119">Belirtilen `IDefinitionIdentity`için bir karma değer alır.</span><span class="sxs-lookup"><span data-stu-id="74810-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="74810-120">Belirtilen `IReferenceIdentity`için bir karma değer alır.</span><span class="sxs-lookup"><span data-stu-id="74810-120">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="74810-121">Belirtilen `IReferenceIdentity`biçimlendirilen dize sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="74810-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="74810-122">Belirtilen geniş karakter arabelleğini belirtilen `IReferenceIdentity`bir dize sürümüyle doldurur.</span><span class="sxs-lookup"><span data-stu-id="74810-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="74810-123">Belirtilen biçimli dizeden oluşturulan `IDefinitionIdentity` örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="74810-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="74810-124">Belirtilen biçimli dizeden oluşturulan `IReferenceIdentity` örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="74810-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="74810-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74810-125">Requirements</span></span>

<span data-ttu-id="74810-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74810-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="74810-127">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="74810-127">**Header:** Isolation.h</span></span>

<span data-ttu-id="74810-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74810-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="74810-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74810-129">See also</span></span>

- [<span data-ttu-id="74810-130">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="74810-130">Fusion Interfaces</span></span>](fusion-interfaces.md)
