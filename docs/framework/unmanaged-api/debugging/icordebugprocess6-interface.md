---
description: 'Daha fazla bilgi edinin: ICorDebugProcess6 Interface'
title: ICorDebugProcess6 Arabirimi
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: f303670d0667a80507bc623f9af037759fdde463
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691464"
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
|[MarkDebuggerAttached Yöntemi](icordebugprocess6-markdebuggerattached-method.md)|<xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>.NET Framework sınıf kitaplığındaki yöntemin döndürdüğü şekilde, hata ayıklayıcı 'nın iç durumunu değiştirir `true` .|  
|[ProcessStateChanged Yöntemi](icordebugprocess6-processstatechanged-method.md)|İşlemin çalıştığını [ICorDebug](icordebug-interface.md) öğesine bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Arabirim yalnızca .NET Native kullanılabilir. `QueryInterface` `E_NOINTERFACE` .NET Native dışında ICorDebug senaryolarına yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
