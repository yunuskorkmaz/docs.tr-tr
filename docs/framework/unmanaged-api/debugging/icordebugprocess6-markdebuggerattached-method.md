---
title: ICorDebugProcess6::MarkDebuggerAttached Yöntemi
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c818b196f3252138f2a9c601b04f1d7a6727bc6b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912737"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>ICorDebugProcess6::MarkDebuggerAttached Yöntemi
.NET Framework sınıf kitaplığındaki <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntemin döndürdüğü `true`şekilde, hata ayıklayıcı 'nın iç durumunu değiştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fIsAttached`  
 `true`<xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntemin bir hata ayıklayıcının ekli olduğunu belirtmesi gerekiyorsa; `false` Aksi takdirde.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi aşağıdaki tabloda listelenen değerleri döndürebilir.  
  
|Dönüş değeri|Açıklama|  
|------------------|-----------------|  
|`S_OK`|Hata ayıklanan başarıyla güncelleştirildi.|  
|`CORDBG_E_MODULE_NOT_LOADED`|<xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> Yöntemi içeren derleme yüklü değil veya eksik meta veriler gibi başka bir hata da tanınmasını engellemektedir.<br /><br /> Bu hata yaygın ve zararsız. Ek derlemeler yüklenirken yöntemi tekrar çağırmalısınız.|  
|Diğer başarısız `HRESULT` değerler.|Diğer değerler muhtemelen hatalı hata ayıklayıcı veya derleyici bileşenlerini gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess6 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
