---
description: 'Daha fazla bilgi edinin: ICorDebugProcess2:: SetUnmanagedBreakpoint yöntemi'
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
ms.openlocfilehash: 7989f0fc9908941513b7d099fde81c79cef82c5b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746548"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint Yöntemi

Belirtilen yerel görüntü uzaklığında yönetilmeyen bir kesme noktası ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki `CORDB_ADDRESS` Yerel görüntü sapmasını belirten bir nesne.  
  
 `bufsize`  
 'ndaki Dizinin bayt cinsinden boyutu `buffer` .  
  
 `buffer`  
 dışı Kesme noktası tarafından değiştirilmiş Opcode içeren bir dizi.  
  
 `bufLen`  
 dışı Dizide döndürülen bayt sayısına yönelik bir işaretçi `buffer` .  
  
## <a name="remarks"></a>Açıklamalar  

 Yerel görüntü boşluğu ortak dil çalışma zamanı (CLR) içindeyse, kesme noktası yok sayılır. Bu, bir kesme noktası hata ayıklayıcı tarafından ayarlandığında, CLR 'nin bant dışı bir kesme noktası gönderdikten engel olmasını sağlar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
