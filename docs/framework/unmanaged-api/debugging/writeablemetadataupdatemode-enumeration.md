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
ms.openlocfilehash: 2fbf9a24c350dd4c33bb50b0add8817c8922925f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436013"
---
# <a name="writeablemetadataupdatemode-enumeration"></a>WriteableMetadataUpdateMode Numaralandırması
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Bellek içi güncelleştirmeleri meta verilerinin bir hata ayıklayıcısı görünür olup olmadığını belirten değerleri sağlar.  
  
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
|`LegacyCompatPolicy`|Bellek içi güncelleştirmeleri meta verileri görünür yaparken, .NET Framework'ün önceki sürümleriyle uyumluluğunu korumak. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
|`AlwaysShowUpdates`|Bellek içi güncelleştirmeleri meta verileri için hata ayıklayıcı görünür kılma.|  
  
## <a name="remarks"></a>Açıklamalar  
 Üye `WriteableMetadataUpdateMode` numaralandırması için geçirilebilir [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) bellek içi hedef işleminde meta veri güncelleştirmeleri olup olmadığını denetlemek için yöntemi için hata ayıklayıcı görünür.  
  
 `LegacyCompatPolicy` Seçeneği .NET Framework 4.5.2 önce sürümlerindekilerle aynı davranışı zorlar. Genellikle bu meta veri güncelleştirmelerin yani görünür değil. Ancak, bir dizi hata ayıklama yöntem çağrıları, güncelleştirmelerinin görünür olması için hata ayıklayıcı örtük olarak coerce. Örneğin, hata ayıklayıcı geçerse [Icordebugılframe::getlocalvariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) dizini bir değişkenin modülü geçerli durumunu eşleşen bir anlık görüntüye güncelleştirilmiş yöntemin özgün meta verilerde, tüm meta veri bulunamadı işlem. Diğer bir deyişle, ile `LegacyCompatPolicy` seçeneği, hata ayıklayıcı yok, bazı veya tüm diğer bölümleri yönetilmeyen hata ayıklama API'si kullanma bağlı olarak kullanılabilir meta veri güncelleştirmeleri görebilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [SetWriteableMetadataUpdateMode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
