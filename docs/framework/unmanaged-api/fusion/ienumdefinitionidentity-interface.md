---
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
ms.openlocfilehash: f3872a2b03d3b22d695af1c104e9ae8ba8856990
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729011"
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
