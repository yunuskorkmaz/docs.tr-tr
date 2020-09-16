---
title: ILCodeKind Numaralandırması
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
ms.openlocfilehash: b9d27c3e3cd42039aeefcb517ecc81eadeb5c183
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557430"
---
# <a name="ilcodekind-enumeration"></a>ILCodeKind Numaralandırması
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere veya koda erişip erişemeyeceğini belirten değerler sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye adı|Description|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|Hata ayıklayıcının, ReJIT araçlarından bilgilere erişimi yok.|  
|`ILCODE_REJIT_IL`|Hata ayıklayıcının, ReJIT araçlarından bilgilere erişimi vardır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ILCodeKind`Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen değişkenlere [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) erişip erişemeyeceğini ve hata ayıklayıcının [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) belgelenmiş Il 'ye erişip erişemeyeceğini anlamak için [GetCodeEx](icordebugilframe4-getcodeex-method.md) yöntemine bir numaralandırma üyesi iletilebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
- [ICorDebugILFrame4 Arabirimi](icordebugilframe4-interface.md)
- [ReJIT: nasıl yapılır Kılavuzu](/archive/blogs/davbr/rejit-a-how-to-guide)
