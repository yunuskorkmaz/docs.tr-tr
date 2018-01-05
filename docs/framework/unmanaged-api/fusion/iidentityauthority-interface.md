---
title: IIdentityAuthority Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IIdentityAuthority
api_location: fusion.dll
api_type: COM
f1_keywords: IIdentityAuthority
helpviewer_keywords: IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 322b15252271472b5bee1dfc6a843079cebbe0b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority Arabirimi
Kod nesneleri kimlik tuşları yönetir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|İki belirtilen olup olmadığını belirten bir değer alır [Idefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) örnekleri eşit.|  
|`IIdentityAuthority::AreReferencesEqual`|İki belirtilen olup olmadığını belirten bir değer alır [Ireferenceıdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) örnekleri eşit.|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|İki belirtilen dize tanımı kimliği sunumu eşit olup olmadığını belirten bir değer alır.|  
|`IIdentityAuthority::AreTextualReferencesEqual`|İki belirtilen dize başvuru kimliği sunumu eşit olup olmadığını belirten bir değer alır.|  
|`IIdentityAuthority::CreateDefinition`|Bir işaretçi yeni bir alır `IDefinitionIdentity` geçerli kapsamdaki kod nesnesini temsil eden örneği.|  
|`IIdentityAuthority::CreateReference`|Bir işaretçi yeni bir alır `IReferenceIdentity` geçerli kapsamdaki kod nesnesini temsil eden örneği.|  
|`IIdentityAuthority::DefinitionToText`|Biçimlendirilmiş dize sürümünü belirtilen alır `IDefinitionIdentity`.|  
|`IIdentityAuthority::DefinitionToTextBuffer`|Belirtilen dize sürümüyle belirtilen geniş karakter arabellek doldurur `IDefinitionIdentity`.|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|Gösteren bir değer alır olup belirtilen `IDefinitionIdentity` ve `IReferenceIdentity` örnekleri aynı kodu nesnesine bakın.|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Belirtilen dizeleri aynı kodu nesnesine başvuru olup olmadığını belirten bir değer alır.|  
|`IIdentityAuthority::GenerateDefinitionKey`|Yeni oluşturulan dize anahtarı için belirtilen bir işaretçi alır `IDefinitionIdentity`.|  
|`IIdentityAuthority::GenerateReferenceKey`|Yeni oluşturulan dize anahtarı için belirtilen bir işaretçi alır `IReferenceIdentity`.|  
|`IIdentityAuthority::HashDefinition`|Bir karma değer için belirtilen alır `IDefinitionIdentity`.|  
|`IIdentityAuthority::HashReference`|Bir karma değer için belirtilen alır `IreferenceIdentity`.|  
|`IIdentityAuthority::ReferenceToText`|Biçimlendirilmiş dize sürümünü belirtilen alır `IReferenceIdentity`.|  
|`IIdentityAuthority::ReferenceToTextBuffer`|Belirtilen dize sürümüyle belirtilen geniş karakter arabellek doldurur `IReferenceIdentity`.|  
|`IIdentityAuthority::TextToDefinition`|Bir arabirim işaretçisi alır bir `IDefinitionIdentity` örneği belirtilen oluşturulan biçimlendirilmiş dize.|  
|`IIdentityAuthority::TextToReference`|Bir arabirim işaretçisi alır bir `IReferenceIdentity` örneği belirtilen oluşturulan biçimlendirilmiş dize.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Isolation.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
