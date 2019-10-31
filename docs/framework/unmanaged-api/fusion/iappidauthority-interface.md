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
ms.openlocfilehash: 004e4f70e3385e7a71c356cce38e64d0253dcfa4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127129"
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
|`IAppIdAuthority::CreateDefinition`|Geçerli kapsamdaki derlemeyi temsil eden yeni oluşturulan `IDefinitionAppId` örneğine yönelik bir arabirim işaretçisi alır.|  
|`IAppIdAuthority::CreateReference`|Geçerli kapsamdaki derlemeyi temsil eden yeni oluşturulan `IReferenceAppId` yönelik bir arabirim işaretçisi alır.|  
|`IAppIdAuthority::DefinitionToText`|Belirtilen bayrak değerlerini kullanarak belirtilen `IDefinitionAppId`bir dize sürümünü alır.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Belirtilen `IDefinitionAppId` ve `IReferenceAppId` aynı derlemeyi temsil ettiğini gösteren bir değer alır.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Belirtilen tanım dizesi ve başvuru dizesinin aynı derlemeyi temsil ettiğini gösteren bir değer alır.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Belirtilen `IDefinitionAppId` örneğini temsil eden bir dize anahtarı alır.|  
|`IAppIdAuthority::GenerateReferenceKey`|Belirtilen `IReferenceAppId` örneğini temsil eden bir dize anahtarı alır.|  
|`IAppIdAuthority::HashDefinition`|Belirtilen `IDefinitionAppId` örneği için bir karma anahtar alır.|  
|`IAppIdAuthority::HashReference`|Belirtilen `IReferenceAppId` örneği için bir karma anahtar alır.|  
|`IAppIdAuthority::ReferenceToText`|Belirtilen bayrak değerlerini kullanarak belirtilen `IReferenceAppId`bir dize sürümünü alır.|  
|`IAppIdAuthority::TextToDefinition`|Belirtilen dize anahtarı tarafından başvurulan derlemeyi temsil eden bir `IDefinitionAppId` örneğine yönelik bir arabirim işaretçisi alır.|  
|`IAppIdAuthority::TextToReference`|Belirtilen dize anahtarı tarafından başvurulan derlemeyi temsil eden bir `IReferenceAppId` örneğine yönelik bir arabirim işaretçisi alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
