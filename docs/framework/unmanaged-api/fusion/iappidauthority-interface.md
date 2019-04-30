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
ms.openlocfilehash: 724ee01e91f1e9f4e34d2262610152a977ed4f53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697582"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority Arabirimi
Oluşturma ve uygulama kimlikleri ve başvurular için anahtarları karşılaştırma yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|İki belirtilen olup olmadığını gösteren bir değer alır [Idefinitionappıd](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) örnekleri eşit. İlgili sürüm bilgilerini yok saymak için IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.|  
|`IAppIdAuthority::AreReferencesEqual`|İki belirtilen olup olmadığını gösteren bir değer alır [Ireferenceappıd](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) örnekleri eşit. İlgili sürüm bilgilerini yok saymak için IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|İki belirtilen dize tanımları eşit olup olmadığını gösteren bir değer alır. İlgili sürüm bilgilerini yok saymak için IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.|  
|`IAppIdAuthority::AreTextualReferencesEqual`|İki belirtilen dize başvuru eşit olup olmadığını gösteren bir değer alır. İlgili sürüm bilgilerini yok saymak için IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION bayrak değerini geçirebilirsiniz.|  
|`IAppIdAuthority::CreateDefinition`|Yeni oluşturulan bir arabirim işaretçisi alır `IDefinitionAppId` derleme geçerli kapsamda temsil eden örneği.|  
|`IAppIdAuthority::CreateReference`|Yeni oluşturulan bir arabirim işaretçisi alır `IReferenceAppId` , derleme geçerli kapsamda temsil eder.|  
|`IAppIdAuthority::DefinitionToText`|Belirtilen bir dize sürümünü alır `IDefinitionAppId`, belirtilen bayrak değerleri kullanarak.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Belirten bir değer alır olup belirtilen `IDefinitionAppId` ve `IReferenceAppId` aynı derlemenin temsil eder.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Başvuru dizesi ve belirtilen tanım dize aynı derlemenin gösterip göstermediğini gösteren bir değer alır.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Belirtilen temsil eden bir dize anahtarı alır `IDefinitionAppId` örneği.|  
|`IAppIdAuthority::GenerateReferenceKey`|Belirtilen temsil eden bir dize anahtarı alır `IReferenceAppId` örneği.|  
|`IAppIdAuthority::HashDefinition`|Bir karma anahtar için belirtilen alır `IDefinitionAppId` örneği.|  
|`IAppIdAuthority::HashReference`|Bir karma anahtar için belirtilen alır `IReferenceAppId` örneği.|  
|`IAppIdAuthority::ReferenceToText`|Belirtilen bir dize sürümünü alır `IReferenceAppId`, belirtilen bayrak değerleri kullanarak.|  
|`IAppIdAuthority::TextToDefinition`|Bir arabirim işaretçisi alır bir `IDefinitionAppId` örneğini belirtilen dizeyi anahtarı tarafından başvurulan bütünleştirilmiş kodu temsil eder.|  
|`IAppIdAuthority::TextToReference`|Bir arabirim işaretçisi alır bir `IReferenceAppId` örneğini belirtilen dizeyi anahtarı tarafından başvurulan bütünleştirilmiş kodu temsil eder.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Isolation.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
