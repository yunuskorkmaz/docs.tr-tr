---
description: 'Daha fazla bilgi edinin: WriteableMetadataUpdateMode numaralandırması'
title: WriteableMetadataUpdateMode Numaralandırması
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
ms.openlocfilehash: b8136963e315c429643bd0ebf4bdb509d5173bec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800519"
---
# <a name="writeablemetadataupdatemode-enumeration"></a>WriteableMetadataUpdateMode Numaralandırması

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Meta verilerde bellek içi güncelleştirmelerin hata ayıklayıcıya görünür olup olmadığını belirten değerler sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye adı|Description|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|Meta verilerde bellek içi güncelleştirmeler üzerinde değişiklik yaparken .NET Framework önceki sürümleriyle uyumluluğu koruyun. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
|`AlwaysShowUpdates`|Hata ayıklayıcıda görünür metaveri için bellek içi güncelleştirmeleri yapın.|  
  
## <a name="remarks"></a>Açıklamalar  

 Numaralandırma üyesi, `WriteableMetadataUpdateMode` hedef işlemdeki meta verilerde bellek içi güncelleştirmelerin hata ayıklayıcıda görünür olup olmadığını denetlemek Için [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) yöntemine geçirilebilir.  
  
 `LegacyCompatPolicy`Seçeneği, 4.5.2 öncesinde .NET Framework sürümleriyle aynı davranışı zorlar. Bu genellikle güncelleştirmelerden meta verilerin görünür olmadığı anlamına gelir. Ancak, bir dizi hata ayıklama yöntemine yapılan çağrılar, güncelleştirmeleri görünür hale getirmek için hata ayıklayıcıyı örtülü olarak çağırır. Örneğin, hata ayıklayıcı [ICorDebugILFrame:: GetLocalVariable](icordebugilframe-getlocalvariable-method.md) öğesini geçirirse, yöntemin özgün meta verilerinde bulunmayan bir değişkenin dizinini, modülün tüm meta verileri işlemin geçerli durumuyla eşleşen bir anlık görüntüye güncelleştirilir. Diğer bir deyişle, `LegacyCompatPolicy` seçeneğiyle hata ayıklayıcı, yönetilmeyen hata ayıklama API 'sinin diğer bölümlerini nasıl kullandığına bağlı olarak, kullanılabilir meta veri güncelleştirmelerinden hiçbiri, bazılarını veya tümünü görebilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
- [SetWriteableMetadataUpdateMode Yöntemi](icordebugprocess7-setwriteablemetadataupdatemode-method.md)
