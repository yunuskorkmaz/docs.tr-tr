---
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
ms.openlocfilehash: 5c3f2f7a9c0804b71c9c8a52bb032aca7c03825e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790299"
---
# <a name="writeablemetadataupdatemode-enumeration"></a>WriteableMetadataUpdateMode Numaralandırması
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Meta verilerde bellek içi güncelleştirmelerin hata ayıklayıcıya görünür olup olmadığını belirten değerler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye adı|Açıklama|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|Meta verilerde bellek içi güncelleştirmeler üzerinde değişiklik yaparken .NET Framework önceki sürümleriyle uyumluluğu koruyun. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
|`AlwaysShowUpdates`|Hata ayıklayıcıda görünür metaveri için bellek içi güncelleştirmeleri yapın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hedef işlemdeki meta verilere yönelik bellek güncelleştirmelerinin hata ayıklayıcıya görünür olup olmadığını denetlemek için `WriteableMetadataUpdateMode` numaralandırmanın bir üyesi [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) yöntemine geçirilebilir.  
  
 `LegacyCompatPolicy` seçeneği, 4.5.2 önce .NET Framework sürümleriyle aynı davranışı zorlar. Bu genellikle güncelleştirmelerden meta verilerin görünür olmadığı anlamına gelir. Ancak, bir dizi hata ayıklama yöntemine yapılan çağrılar, güncelleştirmeleri görünür hale getirmek için hata ayıklayıcıyı örtülü olarak çağırır. Örneğin, hata ayıklayıcı [ICorDebugILFrame:: GetLocalVariable](icordebugilframe-getlocalvariable-method.md) öğesini geçirirse, yöntemin özgün meta verilerinde bulunmayan bir değişkenin dizinini, modülün tüm meta verileri işlemin geçerli durumuyla eşleşen bir anlık görüntüye güncelleştirilir. Diğer bir deyişle, `LegacyCompatPolicy` seçeneği ile, hata ayıklayıcı yönetilmeyen hata ayıklama API 'sinin diğer bölümlerini nasıl kullandığına bağlı olarak, kullanılabilir meta veri güncelleştirmelerinden hiçbiri, bazılarını veya tümünü görebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](debugging-enumerations.md)
- [SetWriteableMetadataUpdateMode Yöntemi](icordebugprocess7-setwriteablemetadataupdatemode-method.md)
