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
ms.openlocfilehash: 263dc0f9d686440aaa23e359c26db1b4d3d09b1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609106"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="bfc70-102">IIdentityAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bfc70-102">IIdentityAuthority Interface</span></span>

<span data-ttu-id="bfc70-103">Kod nesneleri için kimlik anahtarları yönetir.</span><span class="sxs-lookup"><span data-stu-id="bfc70-103">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="bfc70-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bfc70-104">Methods</span></span>

|<span data-ttu-id="bfc70-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bfc70-105">Method</span></span>|<span data-ttu-id="bfc70-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfc70-106">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="bfc70-107">İki belirtilen olup olmadığını gösteren bir değer alır [Idefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) örnekleri eşit.</span><span class="sxs-lookup"><span data-stu-id="bfc70-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="bfc70-108">İki belirtilen olup olmadığını gösteren bir değer alır [Ireferenceıdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) örnekleri eşit.</span><span class="sxs-lookup"><span data-stu-id="bfc70-108">Gets a value that indicates whether the two specified [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="bfc70-109">İki belirtilen dize tanımı kimliği gösterimleri eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="bfc70-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="bfc70-110">İki belirtilen dize başvuru kimliği gösterimleri eşit olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="bfc70-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="bfc70-111">Yeni bir işaretçi alır `IDefinitionIdentity` geçerli kapsamda kod nesnesini temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="bfc70-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="bfc70-112">Yeni bir işaretçi alır `IReferenceIdentity` geçerli kapsamda kod nesnesini temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="bfc70-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="bfc70-113">Belirtilen bir biçimlendirilmiş dize sürümünü alır `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bfc70-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="bfc70-114">Belirtilen dize sürümüyle belirtilen geniş karakter arabelleği doldurur `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bfc70-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="bfc70-115">Belirten bir değer alır olup belirtilen `IDefinitionIdentity` ve `IReferenceIdentity` örnekleri aynı kodu nesnesine başvurun.</span><span class="sxs-lookup"><span data-stu-id="bfc70-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="bfc70-116">Belirtilen dizelerin kod aynı nesneye başvurup başvurmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="bfc70-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="bfc70-117">Belirtilen bir yeni oluşturulan bir dize anahtarı için bir işaretçi alır `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bfc70-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="bfc70-118">Belirtilen bir yeni oluşturulan bir dize anahtarı için bir işaretçi alır `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bfc70-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="bfc70-119">Bir karma değer belirtilen alır `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bfc70-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="bfc70-120">Bir karma değer belirtilen alır `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bfc70-120">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="bfc70-121">Belirtilen bir biçimlendirilmiş dize sürümünü alır `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bfc70-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="bfc70-122">Belirtilen dize sürümüyle belirtilen geniş karakter arabelleği doldurur `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bfc70-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="bfc70-123">Bir arabirim işaretçisi alır bir `IDefinitionIdentity` belirtilen oluşturulan örnek biçimlendirilmiş dize.</span><span class="sxs-lookup"><span data-stu-id="bfc70-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="bfc70-124">Bir arabirim işaretçisi alır bir `IReferenceIdentity` belirtilen oluşturulan örnek biçimlendirilmiş dize.</span><span class="sxs-lookup"><span data-stu-id="bfc70-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="bfc70-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bfc70-125">Requirements</span></span>

<span data-ttu-id="bfc70-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfc70-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="bfc70-127">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="bfc70-127">**Header:** Isolation.h</span></span>

<span data-ttu-id="bfc70-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfc70-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bfc70-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfc70-129">See also</span></span>

- [<span data-ttu-id="bfc70-130">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bfc70-130">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
