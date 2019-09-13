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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fea08331fffb85c91721d60764bae8bfe8b30e27
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928809"
---
# <a name="ilcodekind-enumeration"></a>ILCodeKind Numaralandırması
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere veya koda erişip erişemeyeceğini belirten değerler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye adı|Açıklama|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|Hata ayıklayıcının, ReJIT araçlarından bilgilere erişimi yok.|  
|`ILCODE_REJIT_IL`|Hata ayıklayıcının, ReJIT araçlarından bilgilere erişimi vardır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcının profil oluşturucu `ILCodeKind` ReJIT araçları ' na eklenen değişkenlere erişip [erişemeyeceğini ve](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) bunun [](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) için [bir numaralandırma üyesi olup olmadığını ](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)Hata ayıklayıcının IŞARETLENMIŞ Il 'ye erişip erişemeyeceğini belirleme GetCodeEx yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [ICorDebugILFrame4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [ReJIT: Nasıl yapılır Kılavuzu](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
