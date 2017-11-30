---
title: Icordebugprocess2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2
helpviewer_keywords: ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca1a73874f6ca2f839639cbaf731a59721b2aede
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2-interface1"></a>Icordebugprocess2 Interface1
Bir işlem çalışan yönetilen kodu temsil eden Icordebugprocess arabirimi mantıksal bir uzantısıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|Önceki bir çağrı tarafından ayarlanan belirtilen uzaklığında bir kesme noktası kaldırır `ICorDebugProcess2::SetUnmanagedBreakpoint`.|  
|[GetDesiredNGENCompilerFlags yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|Ortak Dil Çalışma Zamanı Modülü (CLR) bu tarafından başvurulan işlemine resmi yüklemek için ayarlanmalıdır bayraklarını alır `ICorDebugProcess2`.|  
|[GetReferenceValueFromGCHandle yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|Bir başvuru işaretçi işlemek çöp toplama sahip belirtilen yönetilen nesneyi alır.|  
|[Getthreadfortaskıd yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|Belirtilen tanımlayıcıya sahip görev dosyanızın çalıştığı iş parçacığı alır.|  
|[GetVersion yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|Ayıklanacak işlem üzerinde çalıştığı CLR sürümünü alır.|  
|[SetDesiredNGENCompilerFlags yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|Ayıklanacak işlemine bir görüntü yüklemek tam zamanında (JIT) derleyici için gerekli olan bayrakları ayarlar.|  
|[SetUnmanagedBreakpoint yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|Yönetilmeyen bir kesme noktası belirtilen yerel görüntü uzaklığı ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
