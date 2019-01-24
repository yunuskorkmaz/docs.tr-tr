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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b49b63049d33c41757db1abae82ed2a4e266b42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572220"
---
# <a name="writeablemetadataupdatemode-enumeration"></a>WriteableMetadataUpdateMode Numaralandırması
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Meta veriler için bellek içi güncelleştirmeler için bir hata ayıklayıcı görünür olup olmadığını belirten değerleri sağlar.  
  
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
|`LegacyCompatPolicy`|.NET Framework'ün önceki sürümleriyle uyumluluk için meta veriler bellek içi güncelleştirmeleri görünür yaparken koruyun. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
|`AlwaysShowUpdates`|Bellek içi güncelleştirmeleri meta verileri için hata ayıklayıcı tarafından görülebilmesi için.|  
  
## <a name="remarks"></a>Açıklamalar  
 Üye `WriteableMetadataUpdateMode` numaralandırma geçilebilir [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) yöntemi bellek içi hedef işlemde meta veri güncelleştirmeleri olup olmadığını denetlemek için hata ayıklayıcıya görünür.  
  
 `LegacyCompatPolicy` Seçeneği, .NET Framework 4.5.2 önce sürümlerindekilerle aynı davranışı uygular. Genellikle bu meta veri güncelleştirmelerin yani görünür değil. Ancak, bir dizi hata ayıklama yöntem çağrısına, örtük olarak güncelleştirmeleri görünür yapmak için hata ayıklayıcı coerce. Örneğin, hata ayıklayıcı geçerse [Icordebugılframe::getlocalvariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) dizini bir değişkenin modülü, geçerli durumunu eşleşen bir anlık görüntü almak için yöntemin özgün meta verilerinde, tüm meta veri bulunamadı işlem. Diğer bir deyişle, ile `LegacyCompatPolicy` seçeneği, hata ayıklayıcı none, bazı veya tüm diğer bölümleri yönetilmeyen hata ayıklama API kullanma bağlı olarak kullanılabilir meta veri güncelleştirmeleri görebilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [SetWriteableMetadataUpdateMode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
