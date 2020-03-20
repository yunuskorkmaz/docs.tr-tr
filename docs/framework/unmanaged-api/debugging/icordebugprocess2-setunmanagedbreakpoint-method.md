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
ms.openlocfilehash: fb8b8f3e29c141e91587a4d0cdc81cdabccdbc9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178643"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint Yöntemi
Belirtilen yerel görüntü ofsetinde yönetilmeyen bir kesme noktası ayarlar.  
  
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
 [içinde] Yerel `CORDB_ADDRESS` görüntü ofset belirten bir nesne.  
  
 `bufsize`  
 [içinde] Dizinin boyutu, baytlar halinde. `buffer`  
  
 `buffer`  
 [çıkış] Kesme noktası yla değiştirilen opcode içeren bir dizi.  
  
 `bufLen`  
 [çıkış] Dizide döndürülen bayt sayısına `buffer` işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yerel görüntü ofset ortak dil çalışma süresi (CLR) içinde ise, kesme noktası yoksayılır. Bu, CLR'nin hata ayıklayıcı tarafından kesme noktası ayarlandığında bant dışı bir kesme noktası göndermekten kaçınmasını sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
