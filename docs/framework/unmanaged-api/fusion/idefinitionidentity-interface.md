---
title: IDefinitionIdentity Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionIdentity
helpviewer_keywords: IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a63436f107a2604fd5620854339447a4af254e52
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity Arabirimi
Uygulama geçerli kapsamda tanımlar kodunun benzersiz imza temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Arabirim işaretçisi yeni bir alır `IDefinitionIdentity` için aynı nesne `IDefinitionIdentity`, belirtilen öznitelik değişikliklerini dışında.|  
|`IDefinitionIdentity::EnumAttributes`|Bir arabirim işaretçisi alır bir [Ienumıdentıty_attrıbute](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) bu ile ilişkili öznitelikleri içeren nesne `IDefinitionIdentity`.|  
|`IDefinitionIdentity::GetAttribute`|Belirtilen ada sahip özniteliğin değerini belirtilen ad alanında alır.|  
|`IDefinitionIdentity::SetAttribute`|Belirtilen değer için belirtilen ad alanında belirtilen ada sahip öznitelik ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Isolation.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
