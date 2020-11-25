---
title: ICorDebugProcess5::EnableNGENPolicy Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
ms.openlocfilehash: e3dfd3cae83c7891d246ff3a81427c161cc0e2d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731395"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy Yöntemi

Bir uygulamanın yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri nasıl yüklediğini belirleyen bir değer ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ePolicy`  
 'ndaki Bir uygulamanın yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri nasıl yüklediğini belirleyen bir [Cordebugger Gngenpolicy](cordebugngenpolicy-enumeration.md) sabiti.  
  
## <a name="remarks"></a>Açıklamalar  

 İlke başarıyla ayarlandıysa, yöntemi döndürür `S_OK` . , `ePolicy` [Corspergngenpolicy](cordebugngenpolicy-enumeration.md)tarafından tanımlanan numaralandırılmış değerler aralığının dışındaysa, yöntemi döner `E_INVALIDARG` ve yöntem çağrısının etkisi olmaz. Yerel Görüntü Oluşturucu (Ngen.exe) ilkesi güncelleştirilemeyebilir, yöntemi döndürür `E_FAIL` .  
  
 `ICorDebugProcess5::EnableNGenPolicy`Yöntemi, işlemin kullanım ömrü boyunca herhangi bir zamanda çağrılabilir. İlke, ilke ayarlandıktan sonra yüklenen tüm modüller için geçerli olur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess5 Arabirimi](icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
