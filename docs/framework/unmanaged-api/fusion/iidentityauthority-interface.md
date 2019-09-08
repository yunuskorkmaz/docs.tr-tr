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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7421e0d0e1a1f0e1a5fbe0d0eb7d5a0ab2a48b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796428"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="a0b10-102">IIdentityAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a0b10-102">IIdentityAuthority Interface</span></span>

<span data-ttu-id="a0b10-103">Kod nesneleri için kimlik anahtarlarını yönetir.</span><span class="sxs-lookup"><span data-stu-id="a0b10-103">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="a0b10-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a0b10-104">Methods</span></span>

|<span data-ttu-id="a0b10-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a0b10-105">Method</span></span>|<span data-ttu-id="a0b10-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0b10-106">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="a0b10-107">Belirtilen iki [IDefinitionIdentity](idefinitionidentity-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="a0b10-108">Belirtilen iki [IReferenceIdentity](ireferenceidentity-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-108">Gets a value that indicates whether the two specified [IReferenceIdentity](ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="a0b10-109">Belirtilen iki dize tanımı kimlik temsilinin eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="a0b10-110">Belirtilen iki dize başvurusu kimlik temsilinin eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="a0b10-111">Geçerli kapsamdaki kod nesnesini temsil eden `IDefinitionIdentity` yeni bir örneğe yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="a0b10-112">Geçerli kapsamdaki kod nesnesini temsil eden `IReferenceIdentity` yeni bir örneğe yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="a0b10-113">Belirtilen `IDefinitionIdentity`biçimli bir dize sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="a0b10-114">Belirtilen geniş karakter arabelleğini belirtilen `IDefinitionIdentity`bir dize sürümüyle doldurur.</span><span class="sxs-lookup"><span data-stu-id="a0b10-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="a0b10-115">Belirtilen `IDefinitionIdentity` ve`IReferenceIdentity` örneklerin aynı kod nesnesine başvurmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="a0b10-116">Belirtilen dizelerin aynı kod nesnesine başvurmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="a0b10-117">Belirtilen `IDefinitionIdentity`yeni oluşturulan dize anahtarı için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="a0b10-118">Belirtilen `IReferenceIdentity`yeni oluşturulan dize anahtarı için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="a0b10-119">Belirtilen `IDefinitionIdentity`için bir karma değeri alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="a0b10-120">Belirtilen `IReferenceIdentity`için bir karma değeri alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-120">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="a0b10-121">Belirtilen `IReferenceIdentity`biçimli bir dize sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="a0b10-122">Belirtilen geniş karakter arabelleğini belirtilen `IReferenceIdentity`bir dize sürümüyle doldurur.</span><span class="sxs-lookup"><span data-stu-id="a0b10-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="a0b10-123">Belirtilen biçimli dizeden oluşturulan `IDefinitionIdentity` örneğe yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="a0b10-124">Belirtilen biçimli dizeden oluşturulan `IReferenceIdentity` örneğe yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="a0b10-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="a0b10-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0b10-125">Requirements</span></span>

<span data-ttu-id="a0b10-126">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0b10-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a0b10-127">**Üst bilgi** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="a0b10-127">**Header:** Isolation.h</span></span>

<span data-ttu-id="a0b10-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0b10-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a0b10-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0b10-129">See also</span></span>

- [<span data-ttu-id="a0b10-130">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a0b10-130">Fusion Interfaces</span></span>](fusion-interfaces.md)
