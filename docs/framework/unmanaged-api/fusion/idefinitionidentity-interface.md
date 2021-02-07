---
description: 'Şu konuda daha fazla bilgi edinin: IDefinitionIdentity arabirimi'
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
ms.openlocfilehash: 3471879cc822b655b786dd9d8234950cb4b99c1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760660"
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
