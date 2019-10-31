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
# <a name="iidentityauthority-interface"></a>IIdentityAuthority Arabirimi

Kod nesneleri için kimlik anahtarlarını yönetir.

## <a name="methods"></a>Yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|Belirtilen iki [IDefinitionIdentity](idefinitionidentity-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır.|
|`IIdentityAuthority::AreReferencesEqual`|Belirtilen iki [IReferenceIdentity](ireferenceidentity-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır.|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|Belirtilen iki dize tanımı kimlik temsilinin eşit olup olmadığını gösteren bir değer alır.|
|`IIdentityAuthority::AreTextualReferencesEqual`|Belirtilen iki dize başvurusu kimlik temsilinin eşit olup olmadığını gösteren bir değer alır.|
|`IIdentityAuthority::CreateDefinition`|Geçerli kapsamdaki kod nesnesini temsil eden yeni bir `IDefinitionIdentity` örneğine yönelik bir işaretçi alır.|
|`IIdentityAuthority::CreateReference`|Geçerli kapsamdaki kod nesnesini temsil eden yeni bir `IReferenceIdentity` örneğine yönelik bir işaretçi alır.|
|`IIdentityAuthority::DefinitionToText`|Belirtilen `IDefinitionIdentity`biçimlendirilen dize sürümünü alır.|
|`IIdentityAuthority::DefinitionToTextBuffer`|Belirtilen geniş karakter arabelleğini belirtilen `IDefinitionIdentity`bir dize sürümüyle doldurur.|
|`IIdentityAuthority::DoesDefinitionMatchReference`|Belirtilen `IDefinitionIdentity` ve `IReferenceIdentity` örneklerinin aynı kod nesnesine başvuruda bulunup bulunmadığını gösteren bir değer alır.|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Belirtilen dizelerin aynı kod nesnesine başvurmadığını gösteren bir değer alır.|
|`IIdentityAuthority::GenerateDefinitionKey`|Belirtilen `IDefinitionIdentity`yeni oluşturulan dize anahtarına yönelik bir işaretçi alır.|
|`IIdentityAuthority::GenerateReferenceKey`|Belirtilen `IReferenceIdentity`yeni oluşturulan dize anahtarına yönelik bir işaretçi alır.|
|`IIdentityAuthority::HashDefinition`|Belirtilen `IDefinitionIdentity`için bir karma değer alır.|
|`IIdentityAuthority::HashReference`|Belirtilen `IReferenceIdentity`için bir karma değer alır.|
|`IIdentityAuthority::ReferenceToText`|Belirtilen `IReferenceIdentity`biçimlendirilen dize sürümünü alır.|
|`IIdentityAuthority::ReferenceToTextBuffer`|Belirtilen geniş karakter arabelleğini belirtilen `IReferenceIdentity`bir dize sürümüyle doldurur.|
|`IIdentityAuthority::TextToDefinition`|Belirtilen biçimli dizeden oluşturulan `IDefinitionIdentity` örneğine yönelik bir arabirim işaretçisi alır.|
|`IIdentityAuthority::TextToReference`|Belirtilen biçimli dizeden oluşturulan `IReferenceIdentity` örneğine yönelik bir arabirim işaretçisi alır.|

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** Yalıtım. h

**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
