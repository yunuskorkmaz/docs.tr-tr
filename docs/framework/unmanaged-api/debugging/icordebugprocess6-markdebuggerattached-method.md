---
title: ICorDebugProcess6::MarkDebuggerAttached Yöntemi
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: b2ecd6da11bffb156826fa0c31b5f32abb54ff4a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792217"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>ICorDebugProcess6::MarkDebuggerAttached Yöntemi
.NET Framework sınıf kitaplığındaki <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yönteminin `true`döndürmesi için hata ayıklayıcı 'nın iç durumunu değiştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fIsAttached`  
 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntemi bir hata ayıklayıcının ekli olduğunu belirtmesi gerekiyorsa `true`; Aksi takdirde `false`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi aşağıdaki tabloda listelenen değerleri döndürebilir.  
  
|Dönüş değeri|Açıklama|  
|------------------|-----------------|  
|`S_OK`|Hata ayıklanan başarıyla güncelleştirildi.|  
|`CORDBG_E_MODULE_NOT_LOADED`|<xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntemi içeren derleme yüklü değil veya eksik meta veriler gibi başka bir hata, tanınmasını engellemektedir.<br /><br /> Bu hata yaygın ve zararsız. Ek derlemeler yüklenirken yöntemi tekrar çağırmalısınız.|  
|Başarısız olan diğer `HRESULT` değerleri.|Diğer değerler muhtemelen hatalı hata ayıklayıcı veya derleyici bileşenlerini gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess6 Arabirimi](icordebugprocess6-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
