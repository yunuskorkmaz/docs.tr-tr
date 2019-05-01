---
title: ICorDebugProcess6 Arabirimi
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 518c6ec99e4062bf8432809d3472baa395017da3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948632"
---
# <a name="icordebugprocess6-interface"></a>ICorDebugProcess6 Arabirimi
Icordebugprocess arabirimi yerel özel durum hata ayıklama olaylarını ve sanal modül bölme kodlanmış yönetilen hata ayıklama olaylarını kod çözme gibi özellikleri etkinleştirmek için mantıksal olarak genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DecodeEvent Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|Özel olarak hazırlanmış yerel özel durum hata ayıklama olaylarını yükteki kapsüllenmiş yönetilen hata ayıklama olaylarını kodunu çözer.|  
|[EnableVirtualModuleSplitting Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|Etkinleştirir veya sanal modül bölme devre dışı bırakır.|  
|[GetCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|Belirli kod adresinde yönetilen kodu hakkında bilgi alır.|  
|[GetExportStepInfo Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|Yönetilen kodu adımlayın yardımcı olmak için çalışma zamanı dışa aktarılan işlevleri hakkında bilgi sağlar.|  
|[MarkDebuggerAttached Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|Debugee iç durumunu değiştiren böylece <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntem .NET Framework sınıf kitaplığındaki döndürür `true`.|  
|[ProcessStateChanged Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|Bildirir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , işlem çalışıyor.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Arabirimi yalnızca .NET Native ile kullanılabilir. Arama girişimi `QueryInterface` bir arabirim işaretçisini almak için döndürür `E_NOINTERFACE` .NET Native dışında Icordebug senaryolar için.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
