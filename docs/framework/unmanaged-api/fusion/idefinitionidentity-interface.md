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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84c595bfdcca84ee43a53e2ea913cc978ae0953e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796528"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity Arabirimi
Geçerli kapsamdaki uygulamayı tanımlayan kodun benzersiz imzasını temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Belirtilen öznitelik değişiklikleri dışında, bu `IDefinitionIdentity` `IDefinitionIdentity`nesneyle özdeş olan yeni bir nesne için bir arabirim işaretçisi alır.|  
|`IDefinitionIdentity::EnumAttributes`|Bir [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) nesnesine, bununla ilişkili `IDefinitionIdentity`öznitelikleri içeren bir arabirim işaretçisi alır.|  
|`IDefinitionIdentity::GetAttribute`|Belirtilen ad alanında belirtilen ada sahip özniteliğin değerini alır.|  
|`IDefinitionIdentity::SetAttribute`|Belirtilen ad alanında belirtilen ada sahip özniteliği belirtilen değere ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
