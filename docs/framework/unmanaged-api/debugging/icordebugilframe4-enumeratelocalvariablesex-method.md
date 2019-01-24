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
ms.openlocfilehash: f770182ef8489d503ed092bb4c6cf43ae5b9ce10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663355"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a>ICorDebugILFrame4::EnumerateLocalVariablesEx Yöntemi
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Bir numaralandırıcı yerel değişken için çerçeveyi alır ve isteğe bağlı olarak ReJIT izleme profil oluşturucu, eklenen değişkenler içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `flags`  
 [in] Bir [Ilcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) çerçevede ReJIT izleme profil oluşturucu, eklenen değişkenleri dahil edilip edilmeyeceğini belirten sabit listesi üyesi.  
  
 `ppValueEnum`  
 [out] Numaralandırıcı bu çerçevesinde yerel değişkenler için bir "ICorDebugValueEnum" Nesne adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem benzer [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) dışında olan isteğe bağlı olarak ReJIT izleme profil oluşturucu, eklenen değişkenlere erişimi yöntemi. Ayarı `flags` için `ILCODE_ORIGINAL_IL` çağırmakla eşdeğerdir [Icordebugılframe::enumeratelocalvariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md). Ayarı `flags` için `ILCODE_REJIT_IL` ReJIT izleme profil oluşturucu, eklenen yerel değişkenlere erişmek hata ayıklayıcı sağlar. Ara dil (IL) izlenmiyor numaralandırma boştur ve yöntemi döndürür `S_OK`.  
  
 Bunlardan bazıları etkin olmayabilir olduğundan Numaralandırıcı çalışan yönteminde, tüm yerel değişkenlerin içermeyebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorDebugILFrame4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT: Nasıl yapılır Kılavuzu](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
