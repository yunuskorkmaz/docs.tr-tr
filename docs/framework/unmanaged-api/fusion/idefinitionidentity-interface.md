---
title: IDefinitionIdentity Arabirimi
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
ms.openlocfilehash: 4f08fbbf9c8be16dff092327713e731c5aa14661
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732885"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity Arabirimi

Geçerli kapsamdaki uygulamayı tanımlayan kodun benzersiz imzasını temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|`IDefinitionIdentity` `IDefinitionIdentity` Belirtilen öznitelik değişiklikleri dışında, bu nesneyle özdeş olan yeni bir nesne için bir arabirim işaretçisi alır.|  
|`IDefinitionIdentity::EnumAttributes`|Bir [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) nesnesine, bununla ilişkili öznitelikleri içeren bir arabirim işaretçisi alır `IDefinitionIdentity` .|  
|`IDefinitionIdentity::GetAttribute`|Belirtilen ad alanında belirtilen ada sahip özniteliğin değerini alır.|  
|`IDefinitionIdentity::SetAttribute`|Belirtilen ad alanında belirtilen ada sahip özniteliği belirtilen değere ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
