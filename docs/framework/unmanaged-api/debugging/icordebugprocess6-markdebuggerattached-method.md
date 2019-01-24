---
title: ICorDebugProcess6::MarkDebuggerAttached Yöntemi
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ecc3ca203167e4201dd1fa4af66b94c45d47509
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567210"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>ICorDebugProcess6::MarkDebuggerAttached Yöntemi
Debugee iç durumunu değiştiren böylece <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntem .NET Framework sınıf kitaplığındaki döndürür `true`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `fIsAttached`  
 `true` varsa <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntemi belirten bir hata ayıklayıcının bağlı olduğu; `false` Aksi takdirde.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem aşağıdaki tabloda listelenen değerler döndürebilir.  
  
|Dönüş değeri|Açıklama|  
|------------------|-----------------|  
|`S_OK`|Hata ayıklanan başarıyla güncelleştirildi.|  
|`CORDBG_E_MODULE_NOT_LOADED`|İçeren derleme <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntemi yüklü değil veya eksik meta verileri gibi bazı diğer hata, kabul engelliyor.<br /><br /> Bu, genel ve zararsız hatasıdır. Ek derlemeler yüklediğinizde yeniden yöntemini çağırmalıdır.|  
|Diğer başarısız `HRESULT` değerleri.|Büyük olasılıkla diğer değerler, hatalı davranan hata ayıklayıcı veya derleyici bileşenleri gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorDebugProcess6 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
