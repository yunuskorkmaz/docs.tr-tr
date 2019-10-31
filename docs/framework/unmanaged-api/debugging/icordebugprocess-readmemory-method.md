---
title: ICorDebugProcess::ReadMemory Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
ms.openlocfilehash: ef9e339c74b2d2785d758ed9c4adfc1901073253
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139367"
---
# <a name="icordebugprocessreadmemory-method"></a>ICorDebugProcess::ReadMemory Yöntemi
Bu işlem için belirtilen bellek alanını okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a>Parametreler  
 `address`  
 'ndaki Okunacak belleğin temel adresini belirten bir `CORDB_ADDRESS` değeri.  
  
 `size`  
 'ndaki Bellekten okunacak bayt sayısı.  
  
 `buffer`  
 dışı Belleğin içeriğini alan bir arabellek.  
  
 `read`  
 dışı Belirtilen arabelleğe aktarılan bayt sayısına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `ReadMemory` Yöntemi öncelikle, hata ayıklanan yönetilmeyen bölümü tarafından kullanılmakta olan bellek bölgelerini incelemek için birlikte çalışma hata ayıklaması tarafından kullanılmak üzere tasarlanmıştır. Bu yöntem, Microsoft ara dili (MSIL) kodu ve yerel JıT derlenmiş kod okumak için de kullanılabilir.  
  
 Yönetilen kesme noktaları, `buffer` parametresinde döndürülen verilerden kaldırılır. [ICorDebugProcess2:: SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)tarafından ayarlanan yerel kesme noktaları için hiçbir değişiklik yapılmayacak.  
  
 İşlem belleğini önbelleğe alma işlemi yapılmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
