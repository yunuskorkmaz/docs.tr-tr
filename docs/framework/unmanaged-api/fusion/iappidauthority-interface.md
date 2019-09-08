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
ms.openlocfilehash: 91ab2f71e7fb74f8e0e517b566d46d61c316ebe2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796843"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority Arabirimi
Uygulama kimlikleri ve başvuruları için anahtarlar oluşturan ve karşılaştıran yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|Belirtilen iki [IDefinitionAppId](idefinitionappid-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır. İlgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.|  
|`IAppIdAuthority::AreReferencesEqual`|Belirtilen iki [IReferenceAppId](ireferenceappid-interface.md) örneğinin eşit olup olmadığını gösteren bir değer alır. İlgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|Belirtilen iki dize tanımının eşit olup olmadığını gösteren bir değer alır. İlgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.|  
|`IAppIdAuthority::AreTextualReferencesEqual`|Belirtilen iki dize başvurusunun eşit olup olmadığını gösteren bir değer alır. İlgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.|  
|`IAppIdAuthority::CreateDefinition`|Geçerli kapsamdaki derlemeyi temsil eden yeni oluşturulan `IDefinitionAppId` örneğe yönelik bir arabirim işaretçisi alır.|  
|`IAppIdAuthority::CreateReference`|Yeni oluşturulan `IReferenceAppId` , geçerli kapsamdaki derlemeyi temsil eden bir arabirim işaretçisi alır.|  
|`IAppIdAuthority::DefinitionToText`|Belirtilen bayrak değerlerini kullanarak belirtilen `IDefinitionAppId`bir dize sürümünü alır.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Belirtilen `IDefinitionAppId` ve`IReferenceAppId` aynı derlemenin temsil edilip edilmeyeceğini belirten bir değer alır.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Belirtilen tanım dizesi ve başvuru dizesinin aynı derlemeyi temsil ettiğini gösteren bir değer alır.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Belirtilen `IDefinitionAppId` örneği temsil eden bir dize anahtarı alır.|  
|`IAppIdAuthority::GenerateReferenceKey`|Belirtilen `IReferenceAppId` örneği temsil eden bir dize anahtarı alır.|  
|`IAppIdAuthority::HashDefinition`|Belirtilen `IDefinitionAppId` örnek için bir karma anahtar alır.|  
|`IAppIdAuthority::HashReference`|Belirtilen `IReferenceAppId` örnek için bir karma anahtar alır.|  
|`IAppIdAuthority::ReferenceToText`|Belirtilen bayrak değerlerini kullanarak belirtilen `IReferenceAppId`bir dize sürümünü alır.|  
|`IAppIdAuthority::TextToDefinition`|Belirtilen dize anahtarı tarafından başvurulan derlemeyi `IDefinitionAppId` temsil eden bir örneğe yönelik bir arabirim işaretçisi alır.|  
|`IAppIdAuthority::TextToReference`|Belirtilen dize anahtarı tarafından başvurulan derlemeyi `IReferenceAppId` temsil eden bir örneğe yönelik bir arabirim işaretçisi alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
