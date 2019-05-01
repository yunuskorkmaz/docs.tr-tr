---
title: ICorDebugProcess2::SetUnmanagedBreakpoint Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b374720bd7bdad48222da006b809702de6462a62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948854"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint Yöntemi
Belirtilen yerel görüntü uzaklığında yönetilmeyen bir kesme noktası ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `address`  
 [in] A `CORDB_ADDRESS` nesnesini yerel görüntü uzaklığını belirtir.  
  
 `bufsize`  
 [in] Bayt cinsinden boyutu, `buffer` dizisi.  
  
 `buffer`  
 [out] Kesme noktası tarafından değiştirilen bir işlem kodu içeren bir dizi.  
  
 `bufLen`  
 [out] Döndürülen bayt sayısı için bir işaretçi `buffer` dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yerel görüntü uzaklığı ortak dil çalışma zamanı içinde (CLR) ise, kesme noktasına göz ardı edilir. Kesme noktası hata ayıklayıcı tarafından olarak ayarlandığında bir bant dışı kesme noktası göndermeyi önlemek CLR böylece.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
