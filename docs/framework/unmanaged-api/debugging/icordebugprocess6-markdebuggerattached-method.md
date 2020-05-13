---
title: ICorDebugProcess6::MarkDebuggerAttached Yöntemi
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: c83d6e892b89e6e50779abf9a71a2cbe9093af2c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212858"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>ICorDebugProcess6::MarkDebuggerAttached Yöntemi
<xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>.NET Framework sınıf kitaplığındaki yöntemin döndürdüğü şekilde, hata ayıklayıcı 'nın iç durumunu değiştirir `true` .  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fIsAttached`  
 `true`<xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>yöntemin bir hata ayıklayıcının bağlı olduğunu belirtmesi gerekiyorsa, `false` Aksi takdirde.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi aşağıdaki tabloda listelenen değerleri döndürebilir.  
  
|Döndürülen değer|Açıklama|  
|------------------|-----------------|  
|`S_OK`|Hata ayıklanan başarıyla güncelleştirildi.|  
|`CORDBG_E_MODULE_NOT_LOADED`|Yöntemi içeren derleme <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yüklü değil veya eksik meta veriler gibi başka bir hata da tanınmasını engellemektedir.<br /><br /> Bu hata yaygın ve zararsız. Ek derlemeler yüklenirken yöntemi tekrar çağırmalısınız.|  
|Diğer başarısız `HRESULT` değerler.|Diğer değerler muhtemelen hatalı hata ayıklayıcı veya derleyici bileşenlerini gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess6 Arabirimi](icordebugprocess6-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
