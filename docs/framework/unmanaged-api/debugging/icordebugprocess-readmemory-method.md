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
ms.openlocfilehash: dca2a4e5ee869346108137a8ba01ab8855756725
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792554"
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
  
 Yönetilen kesme noktaları, `buffer` parametresinde döndürülen verilerden kaldırılır. [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md)tarafından ayarlanan yerel kesme noktaları için hiçbir değişiklik yapılmayacak.  
  
 İşlem belleğini önbelleğe alma işlemi yapılmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
