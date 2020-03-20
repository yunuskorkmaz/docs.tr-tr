---
title: ICorDebugProcess6::GetCode Metodu
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: 94882c67752705f9f13b858ae3b386a19dc103a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178550"
---
# <a name="icordebugprocess6getcode-method"></a>ICorDebugProcess6::GetCode Metodu
Belirli bir kod adresindeyönetilen kod hakkında bilgi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a>Parametreler  
 `codeAddress`  
 [içinde] Yönetilen kod kesiminin başlangıç adresini belirten [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) değeri.  
  
 `ppCode`  
 [çıkış] Yönetilen kodun bir kesimini temsil eden "ICorDebugCode" nesnesinin adresine işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess6 Arabirimi](icordebugprocess6-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
