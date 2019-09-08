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
# <a name="iidentityauthority-interface"></a>IIdentityAuthority Arabirimi

Kod nesneleri için kimlik anahtarlarını yönetir.

## <a name="methods"></a>Yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|Belirtilen iki [IDefinitionIdentity](idefinitionidentity-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır.|
|`IIdentityAuthority::AreReferencesEqual`|Belirtilen iki [IReferenceIdentity](ireferenceidentity-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır.|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|Belirtilen iki dize tanımı kimlik temsilinin eşit olup olmadığını gösteren bir değer alır.|
|`IIdentityAuthority::AreTextualReferencesEqual`|Belirtilen iki dize başvurusu kimlik temsilinin eşit olup olmadığını gösteren bir değer alır.|
|`IIdentityAuthority::CreateDefinition`|Geçerli kapsamdaki kod nesnesini temsil eden `IDefinitionIdentity` yeni bir örneğe yönelik bir işaretçi alır.|
|`IIdentityAuthority::CreateReference`|Geçerli kapsamdaki kod nesnesini temsil eden `IReferenceIdentity` yeni bir örneğe yönelik bir işaretçi alır.|
|`IIdentityAuthority::DefinitionToText`|Belirtilen `IDefinitionIdentity`biçimli bir dize sürümünü alır.|
|`IIdentityAuthority::DefinitionToTextBuffer`|Belirtilen geniş karakter arabelleğini belirtilen `IDefinitionIdentity`bir dize sürümüyle doldurur.|
|`IIdentityAuthority::DoesDefinitionMatchReference`|Belirtilen `IDefinitionIdentity` ve`IReferenceIdentity` örneklerin aynı kod nesnesine başvurmadığını gösteren bir değer alır.|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Belirtilen dizelerin aynı kod nesnesine başvurmadığını gösteren bir değer alır.|
|`IIdentityAuthority::GenerateDefinitionKey`|Belirtilen `IDefinitionIdentity`yeni oluşturulan dize anahtarı için bir işaretçi alır.|
|`IIdentityAuthority::GenerateReferenceKey`|Belirtilen `IReferenceIdentity`yeni oluşturulan dize anahtarı için bir işaretçi alır.|
|`IIdentityAuthority::HashDefinition`|Belirtilen `IDefinitionIdentity`için bir karma değeri alır.|
|`IIdentityAuthority::HashReference`|Belirtilen `IReferenceIdentity`için bir karma değeri alır.|
|`IIdentityAuthority::ReferenceToText`|Belirtilen `IReferenceIdentity`biçimli bir dize sürümünü alır.|
|`IIdentityAuthority::ReferenceToTextBuffer`|Belirtilen geniş karakter arabelleğini belirtilen `IReferenceIdentity`bir dize sürümüyle doldurur.|
|`IIdentityAuthority::TextToDefinition`|Belirtilen biçimli dizeden oluşturulan `IDefinitionIdentity` örneğe yönelik bir arabirim işaretçisi alır.|
|`IIdentityAuthority::TextToReference`|Belirtilen biçimli dizeden oluşturulan `IReferenceIdentity` örneğe yönelik bir arabirim işaretçisi alır.|

## <a name="requirements"></a>Gereksinimler

**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi** Yalıtım. h

**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
