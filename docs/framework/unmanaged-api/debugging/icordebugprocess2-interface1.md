---
description: 'Daha fazla bilgi edinin: ICorDebugProcess2 Interface'
title: ICorDebugProcess2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
ms.openlocfilehash: 47e94ee8ee4f45e365fa9efe888cb706f8bb1dfd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746600"
---
# <a name="icordebugprocess2-interface"></a>ICorDebugProcess2 Arabirimi

Yönetilen kodu çalıştıran bir işlemi temsil eden ICorDebugProcess arabiriminin mantıksal uzantısı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint Yöntemi](icordebugprocess2-clearunmanagedbreakpoint-method.md)|Daha önceki bir çağrısıyla ayarlanan belirtilen uzaklığında bir kesme noktasını kaldırır `ICorDebugProcess2::SetUnmanagedBreakpoint` .|  
|[GetDesiredNGENCompilerFlags Yöntemi](icordebugprocess2-getdesiredngencompilerflags-method.md)|Görüntüyü bunun başvurduğu işleme yüklemek için ortak dil çalışma zamanı (CLR) için ayarlanması gereken bayrakları alır `ICorDebugProcess2` .|  
|[GetReferenceValueFromGCHandle Yöntemi](icordebugprocess2-getreferencevaluefromgchandle-method.md)|Bir atık toplama tanıtıcısına sahip olan, belirtilen yönetilen nesneye bir başvuru işaretçisi alır.|  
|[GetThreadForTaskID Yöntemi](icordebugprocess2-getthreadfortaskid-method.md)|Belirtilen tanımlayıcıya sahip görevin yürütüldüğü iş parçacığını alır.|  
|[GetVersion Yöntemi](icordebugprocess2-getversion-method.md)|Hata ayıklamakta olan işlemin üzerinde çalıştığı CLR sürümünü alır.|  
|[SetDesiredNGENCompilerFlags Yöntemi](icordebugprocess2-setdesiredngencompilerflags-method.md)|Just-In-Time (JıT) derleyicisi için gereken bayrakları, hata ayıklanan işleme bir görüntü yükleyecek şekilde ayarlar.|  
|[SetUnmanagedBreakpoint Yöntemi](icordebugprocess2-setunmanagedbreakpoint-method.md)|Belirtilen yerel görüntü uzaklığında yönetilmeyen bir kesme noktası ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
