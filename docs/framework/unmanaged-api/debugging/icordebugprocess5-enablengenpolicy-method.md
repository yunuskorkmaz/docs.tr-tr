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
ms.openlocfilehash: 9497bea9b7cc5eb98876c923858dbcbc6adf9d07
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792459"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy Yöntemi
Bir uygulamanın yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri nasıl yüklediğini belirleyen bir değer ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ePolicy`  
 'ndaki Bir uygulamanın yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri nasıl yüklediğini belirleyen bir [Cordebugger Gngenpolicy](cordebugngenpolicy-enumeration.md) sabiti.  
  
## <a name="remarks"></a>Açıklamalar  
 İlke başarıyla ayarlandıysa, yöntem `S_OK`döndürür. `ePolicy`, [cormısgngenpolicy](cordebugngenpolicy-enumeration.md)tarafından tanımlanan numaralandırılmış değerler aralığının dışındaysa, yöntemi `E_INVALIDARG` döndürür ve yöntem çağrısının etkisi yoktur. Yerel Görüntü Oluşturucu (Ngen. exe) ilkesi güncelleştirilemeyebilir, yöntem `E_FAIL`döndürür.  
  
 `ICorDebugProcess5::EnableNGenPolicy` yöntemi, işlemin kullanım ömrü boyunca herhangi bir zamanda çağrılabilir. İlke, ilke ayarlandıktan sonra yüklenen tüm modüller için geçerli olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess5 Arabirimi](icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
