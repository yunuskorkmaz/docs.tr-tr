---
title: ICorDebugProcess6 Arabirimi
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: 73ef1a64deaf5420246fc1ab3e9f88ba5bf049a5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792229"
---
# <a name="icordebugprocess6-interface"></a>ICorDebugProcess6 Arabirimi
Yerel özel durum ayıklama olayları ve sanal modül bölünmesi içinde kodlanmış yönetilen hata ayıklama olaylarının kodunu çözme gibi özellikleri etkinleştirmek için ICorDebugProcess arabirimini mantıksal olarak genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DecodeEvent Yöntemi](icordebugprocess6-decodeevent-method.md)|Özel olarak hazırlanmış yerel özel durum hata ayıklama olaylarının yükünde kapsüllenmiş yönetilen hata ayıklama olaylarının kodunu çözer.|  
|[EnableVirtualModuleSplitting Yöntemi](icordebugprocess6-enablevirtualmodulesplitting-method.md)|Sanal modül bölmeyi etkinleştirilir veya devre dışı bırakır.|  
|[GetCode Yöntemi](icordebugprocess6-getcode-method.md)|Belirli bir kod adresindeki yönetilen kodla ilgili bilgileri alır.|  
|[GetExportStepInfo Yöntemi](icordebugprocess6-getexportstepinfo-method.md)|Yönetilen kodda adım adım yardım için çalışma zamanına aktarılmış işlevler hakkında bilgi sağlar.|  
|[MarkDebuggerAttached Yöntemi](icordebugprocess6-markdebuggerattached-method.md)|.NET Framework sınıf kitaplığındaki <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yönteminin `true`döndürmesi için hata ayıklayıcı 'nın iç durumunu değiştirir.|  
|[ProcessStateChanged Yöntemi](icordebugprocess6-processstatechanged-method.md)|İşlemin çalıştığını [ICorDebug](icordebug-interface.md) öğesine bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Arabirim yalnızca .NET Native kullanılabilir. Bir arabirim işaretçisini almak için `QueryInterface` çağırma girişimi, .NET Native dışındaki ICorDebug senaryoları için `E_NOINTERFACE` döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
