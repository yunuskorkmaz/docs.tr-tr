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
# <a name="iidentityauthority-interface"></a>IIdentityAuthority Arabirimi

Kod nesneleri için kimlik anahtarlarını yönetir.

## <a name="methods"></a>Yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|Belirtilen iki [IDefinitionIdentity](idefinitionidentity-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır.|
|`IIdentityAuthority::AreReferencesEqual`|Belirtilen iki [IReferenceIdentity](ireferenceidentity-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır.|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|Belirtilen iki dize tanımı kimlik temsilinin eşit olup olmadığını gösteren bir değer alır.|
|`IIdentityAuthority::AreTextualReferencesEqual`|Belirtilen iki dize başvurusu kimlik temsilinin eşit olup olmadığını gösteren bir değer alır.|
|`IIdentityAuthority::CreateDefinition`|`IDefinitionIdentity`Geçerli kapsamdaki kod nesnesini temsil eden yeni bir örneğe yönelik bir işaretçi alır.|
|`IIdentityAuthority::CreateReference`|`IReferenceIdentity`Geçerli kapsamdaki kod nesnesini temsil eden yeni bir örneğe yönelik bir işaretçi alır.|
|`IIdentityAuthority::DefinitionToText`|Belirtilen biçimli bir dize sürümünü alır `IDefinitionIdentity` .|
|`IIdentityAuthority::DefinitionToTextBuffer`|Belirtilen geniş karakter arabelleğini belirtilen bir dize sürümüyle doldurur `IDefinitionIdentity` .|
|`IIdentityAuthority::DoesDefinitionMatchReference`|Belirtilen `IDefinitionIdentity` ve `IReferenceIdentity` örneklerin aynı kod nesnesine başvurmadığını gösteren bir değer alır.|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Belirtilen dizelerin aynı kod nesnesine başvurmadığını gösteren bir değer alır.|
|`IIdentityAuthority::GenerateDefinitionKey`|Belirtilen yeni oluşturulan dize anahtarı için bir işaretçi alır `IDefinitionIdentity` .|
|`IIdentityAuthority::GenerateReferenceKey`|Belirtilen yeni oluşturulan dize anahtarı için bir işaretçi alır `IReferenceIdentity` .|
|`IIdentityAuthority::HashDefinition`|Belirtilen için bir karma değeri alır `IDefinitionIdentity` .|
|`IIdentityAuthority::HashReference`|Belirtilen için bir karma değeri alır `IReferenceIdentity` .|
|`IIdentityAuthority::ReferenceToText`|Belirtilen biçimli bir dize sürümünü alır `IReferenceIdentity` .|
|`IIdentityAuthority::ReferenceToTextBuffer`|Belirtilen geniş karakter arabelleğini belirtilen bir dize sürümüyle doldurur `IReferenceIdentity` .|
|`IIdentityAuthority::TextToDefinition`|`IDefinitionIdentity`Belirtilen biçimli dizeden oluşturulan örneğe yönelik bir arabirim işaretçisi alır.|
|`IIdentityAuthority::TextToReference`|`IReferenceIdentity`Belirtilen biçimli dizeden oluşturulan örneğe yönelik bir arabirim işaretçisi alır.|

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** Yalıtım. h

**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
