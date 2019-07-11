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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bbd8476b7778de6d0023f3a8522a44be6626884
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751518"
---
# <a name="ienumdefinitionidentity-interface"></a>IEnumDefinitionIdentity Arabirimi
Bir koleksiyonu için bir numaralandırıcı görevi gören `IDefinitionIdentity` nesneleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
|`IEnumDefinitionIdentity::Clone`|Yeni bir arabirim işaretçisi alır `IEnumDefinitionIdentity` bu aynı üyeleri içeren nesne `IEnumDefinitionIdentity`.|  
|`IEnumDefinitionIdentity::Next`|Belirtilen sayıda alır `IDefinitionIdentity` nesneleri, geçerli konumdan başlayarak.|  
|`IEnumDefinitionIdentity::Reset`|Yönerge işaretçisini bu başlangıcına taşır `IEnumDefinitionIdentity`.|  
|`IEnumDefinitionIdentity::Skip`|Öğe, geçerli konumdan başlayarak belirtilen sayıda yönerge işaretçisini ileriye taşır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Isolation.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IDefinitionIdentity Arabirimi](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
