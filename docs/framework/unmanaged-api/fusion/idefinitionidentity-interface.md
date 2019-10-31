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
ms.openlocfilehash: 59578e1d3a66809c86f7daad1b208df2ae09568d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108036"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity Arabirimi
Geçerli kapsamdaki uygulamayı tanımlayan kodun benzersiz imzasını temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Belirtilen öznitelik değişiklikleri dışında, bu `IDefinitionIdentity`özdeş olan yeni bir `IDefinitionIdentity` nesnesine bir arabirim işaretçisi alır.|  
|`IDefinitionIdentity::EnumAttributes`|Bu `IDefinitionIdentity`ilişkili öznitelikleri içeren bir [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) nesnesine yönelik bir arabirim işaretçisi alır.|  
|`IDefinitionIdentity::GetAttribute`|Belirtilen ad alanında belirtilen ada sahip özniteliğin değerini alır.|  
|`IDefinitionIdentity::SetAttribute`|Belirtilen ad alanında belirtilen ada sahip özniteliği belirtilen değere ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
