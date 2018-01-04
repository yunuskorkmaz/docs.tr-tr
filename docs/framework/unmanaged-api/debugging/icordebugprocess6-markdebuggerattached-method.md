---
title: "ICorDebugProcess6::MarkDebuggerAttached Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d3d47f3b5ce6912d5a58f79117b6cd2e05d3ecd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>ICorDebugProcess6::MarkDebuggerAttached Yöntemi
Debugee iç durumu değişir böylece <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> .NET Framework Sınıf Kitaplığı'nda yöntemi döndürür `true`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `fIsAttached`  
 `true`varsa <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntemi belirten bir hata ayıklayıcısı bağlı olduğu; `false` Aksi takdirde.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi aşağıdaki tabloda listelenen değerleri döndürebilir.  
  
|Dönüş değeri|Açıklama|  
|------------------|-----------------|  
|`S_OK`|Ayıklayıcı başarıyla güncelleştirildi.|  
|`CORDBG_E_MODULE_NOT_LOADED`|İçeren derlemenin <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntemi yüklü değil veya eksik meta verileri gibi diğer bazı hata kabul görünür duruma engelliyor.<br /><br /> Bu, ortak ve zararsız hatasıdır. Ek derlemeler yüklediğinizde yöntemi yeniden çağırmanız gerekir.|  
|Diğer başarısız `HRESULT` değerleri.|Diğer değerleri büyük olasılıkla hatalı davranan hata ayıklayıcı veya derleyici bileşenleri gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugProcess6 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
