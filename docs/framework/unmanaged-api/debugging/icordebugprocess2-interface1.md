---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5519714ff2b4ee67d0e59001bf5b454cdc25d648
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961075"
---
# <a name="icordebugprocess2-interface"></a>ICorDebugProcess2 Arabirimi
Yönetilen kodu çalıştıran bir işlemi temsil eden ICorDebugProcess arabiriminin mantıksal uzantısı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|Daha önceki bir çağrısıyla `ICorDebugProcess2::SetUnmanagedBreakpoint`ayarlanan belirtilen uzaklığında bir kesme noktasını kaldırır.|  
|[GetDesiredNGENCompilerFlags Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|Görüntüyü bunun `ICorDebugProcess2`başvurduğu işleme yüklemek için ortak dil çalışma zamanı (CLR) için ayarlanması gereken bayrakları alır.|  
|[GetReferenceValueFromGCHandle Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|Bir atık toplama tanıtıcısına sahip olan, belirtilen yönetilen nesneye bir başvuru işaretçisi alır.|  
|[GetThreadForTaskID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|Belirtilen tanımlayıcıya sahip görevin yürütüldüğü iş parçacığını alır.|  
|[GetVersion Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|Hata ayıklamakta olan işlemin üzerinde çalıştığı CLR sürümünü alır.|  
|[SetDesiredNGENCompilerFlags Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|Just-In-Time (JıT) derleyicisi için gereken bayrakları, hata ayıklanan işleme bir görüntü yükleyecek şekilde ayarlar.|  
|[SetUnmanagedBreakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|Belirtilen yerel görüntü uzaklığında yönetilmeyen bir kesme noktası ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
