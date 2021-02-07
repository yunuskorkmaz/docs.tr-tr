---
description: 'Daha fazla bilgi edinin: ıappidaduthority arabirimi'
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
ms.openlocfilehash: 238885c7f080571b414511c24f9772dbc19b4683
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761011"
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
|`IAppIdAuthority::CreateDefinition`|Geçerli kapsamdaki derlemeyi temsil eden yeni oluşturulan örneğe yönelik bir arabirim işaretçisi alır `IDefinitionAppId` .|  
|`IAppIdAuthority::CreateReference`|Yeni oluşturulan `IReferenceAppId` , geçerli kapsamdaki derlemeyi temsil eden bir arabirim işaretçisi alır.|  
|`IAppIdAuthority::DefinitionToText`|Belirtilen bayrak değerlerini kullanarak belirtilen bir dize sürümünü alır `IDefinitionAppId` .|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Belirtilen `IDefinitionAppId` ve aynı derlemenin temsil edilip edilmeyeceğini belirten bir değer alır `IReferenceAppId` .|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Belirtilen tanım dizesi ve başvuru dizesinin aynı derlemeyi temsil ettiğini gösteren bir değer alır.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Belirtilen örneği temsil eden bir dize anahtarı alır `IDefinitionAppId` .|  
|`IAppIdAuthority::GenerateReferenceKey`|Belirtilen örneği temsil eden bir dize anahtarı alır `IReferenceAppId` .|  
|`IAppIdAuthority::HashDefinition`|Belirtilen örnek için bir karma anahtar alır `IDefinitionAppId` .|  
|`IAppIdAuthority::HashReference`|Belirtilen örnek için bir karma anahtar alır `IReferenceAppId` .|  
|`IAppIdAuthority::ReferenceToText`|Belirtilen bayrak değerlerini kullanarak belirtilen bir dize sürümünü alır `IReferenceAppId` .|  
|`IAppIdAuthority::TextToDefinition`|`IDefinitionAppId`Belirtilen dize anahtarı tarafından başvurulan derlemeyi temsil eden bir örneğe yönelik bir arabirim işaretçisi alır.|  
|`IAppIdAuthority::TextToReference`|`IReferenceAppId`Belirtilen dize anahtarı tarafından başvurulan derlemeyi temsil eden bir örneğe yönelik bir arabirim işaretçisi alır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
