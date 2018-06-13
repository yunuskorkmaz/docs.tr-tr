---
title: ICorDebugILFrame4::EnumerateLocalVariablesEx Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49d2a0955f9ef0c54a8953971ce3671ce16d3b85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418935"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a>ICorDebugILFrame4::EnumerateLocalVariablesEx Yöntemi
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Çerçevede yerel değişken için bir numaralandırıcı alır ve isteğe bağlı olarak profiler ReJIT araçları eklenen değişkenleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `flags`  
 [in] Bir [Ilcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) profiler ReJIT araçları eklenen değişkenleri çerçevede dahil edilip edilmediğini belirten numaralandırma üyesi.  
  
 `ppValueEnum`  
 [out] Bu çerçeve yerel değişkenleri için Numaralandırıcı bir "ICorDebugValueEnum" nesne adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem benzer [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) olan isteğe bağlı olarak profiler ReJIT araçları eklenen değişkenleri erişen dışında yöntemi. Ayarı `flags` için `ILCODE_ORIGINAL_IL` arama için eşdeğer bir gruba [Icordebugılframe::enumeratelocalvariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md). Ayarı `flags` için `ILCODE_REJIT_IL` profiler ReJIT araçları eklenen yerel değişkenler erişmek hata ayıklayıcı sağlar. Ara dile (IL) değil izlenmiş numaralandırması boştur ve yöntemi döndürür `S_OK`.  
  
 Bunlardan bazıları etkin olmayabilir beri Numaralandırıcı çalışan yönteminde tüm yerel değişkenleri içermeyebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugILFrame4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Nasıl yapılır Kılavuzu](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
