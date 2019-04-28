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
# <a name="iidentityauthority-interface"></a>IIdentityAuthority Arabirimi

Kod nesneleri için kimlik anahtarları yönetir.

## <a name="methods"></a>Yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|İki belirtilen olup olmadığını gösteren bir değer alır [Idefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) örnekleri eşit.|
|`IIdentityAuthority::AreReferencesEqual`|İki belirtilen olup olmadığını gösteren bir değer alır [Ireferenceıdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) örnekleri eşit.|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|İki belirtilen dize tanımı kimliği gösterimleri eşit olup olmadığını gösteren bir değer alır.|
|`IIdentityAuthority::AreTextualReferencesEqual`|İki belirtilen dize başvuru kimliği gösterimleri eşit olup olmadığını gösteren bir değer alır.|
|`IIdentityAuthority::CreateDefinition`|Yeni bir işaretçi alır `IDefinitionIdentity` geçerli kapsamda kod nesnesini temsil eden örneği.|
|`IIdentityAuthority::CreateReference`|Yeni bir işaretçi alır `IReferenceIdentity` geçerli kapsamda kod nesnesini temsil eden örneği.|
|`IIdentityAuthority::DefinitionToText`|Belirtilen bir biçimlendirilmiş dize sürümünü alır `IDefinitionIdentity`.|
|`IIdentityAuthority::DefinitionToTextBuffer`|Belirtilen dize sürümüyle belirtilen geniş karakter arabelleği doldurur `IDefinitionIdentity`.|
|`IIdentityAuthority::DoesDefinitionMatchReference`|Belirten bir değer alır olup belirtilen `IDefinitionIdentity` ve `IReferenceIdentity` örnekleri aynı kodu nesnesine başvurun.|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Belirtilen dizelerin kod aynı nesneye başvurup başvurmadığını gösteren bir değer alır.|
|`IIdentityAuthority::GenerateDefinitionKey`|Belirtilen bir yeni oluşturulan bir dize anahtarı için bir işaretçi alır `IDefinitionIdentity`.|
|`IIdentityAuthority::GenerateReferenceKey`|Belirtilen bir yeni oluşturulan bir dize anahtarı için bir işaretçi alır `IReferenceIdentity`.|
|`IIdentityAuthority::HashDefinition`|Bir karma değer belirtilen alır `IDefinitionIdentity`.|
|`IIdentityAuthority::HashReference`|Bir karma değer belirtilen alır `IReferenceIdentity`.|
|`IIdentityAuthority::ReferenceToText`|Belirtilen bir biçimlendirilmiş dize sürümünü alır `IReferenceIdentity`.|
|`IIdentityAuthority::ReferenceToTextBuffer`|Belirtilen dize sürümüyle belirtilen geniş karakter arabelleği doldurur `IReferenceIdentity`.|
|`IIdentityAuthority::TextToDefinition`|Bir arabirim işaretçisi alır bir `IDefinitionIdentity` belirtilen oluşturulan örnek biçimlendirilmiş dize.|
|`IIdentityAuthority::TextToReference`|Bir arabirim işaretçisi alır bir `IReferenceIdentity` belirtilen oluşturulan örnek biçimlendirilmiş dize.|

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** Isolation.h

**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
