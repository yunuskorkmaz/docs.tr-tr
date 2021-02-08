---
description: 'Daha fazla bilgi edinin: IEnumDefinitionIdentity Interface'
title: IEnumDefinitionIdentity Arabirimi
ms.date: 03/30/2017
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
ms.openlocfilehash: 1055031c064115410334bbe4b20b48deee7ec4c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800168"
---
# <a name="ienumdefinitionidentity-interface"></a>IEnumDefinitionIdentity Arabirimi

Bir nesne koleksiyonu için numaralandırıcı görevi görür `IDefinitionIdentity` .  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|`IEnumDefinitionIdentity`Bu, ile aynı üyeleri içeren yeni bir nesne için bir arabirim işaretçisi alır `IEnumDefinitionIdentity` .|  
|`IEnumDefinitionIdentity::Next`|`IDefinitionIdentity`Geçerli konumdan başlayarak belirtilen sayıda nesneyi alır.|  
|`IEnumDefinitionIdentity::Reset`|Yönerge işaretçisini bunun başlangıcına taşıdır `IEnumDefinitionIdentity` .|  
|`IEnumDefinitionIdentity::Skip`|Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
- [IDefinitionIdentity Arabirimi](idefinitionidentity-interface.md)
