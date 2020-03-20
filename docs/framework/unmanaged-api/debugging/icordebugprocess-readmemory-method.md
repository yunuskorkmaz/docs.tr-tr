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
ms.openlocfilehash: 383e3f8990a1f355c94ff5e9f9daa69bdbdd97bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178657"
---
# <a name="icordebugprocessreadmemory-method"></a>ICorDebugProcess::ReadMemory Yöntemi
Bu işlem için belirli bir bellek alanını okur.  
  
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
 [içinde] Okunacak belleğin temel adresini belirten bir `CORDB_ADDRESS` değer.  
  
 `size`  
 [içinde] Bellekten okunacak bayt sayısı.  
  
 `buffer`  
 [çıkış] Belleğin içeriğini alan bir arabellek.  
  
 `read`  
 [çıkış] Belirtilen arabelleğe aktarılan bayt sayısına işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntem `ReadMemory` öncelikle hata ayıklama nın yönetilmeyen bölümü tarafından kullanılan bellek bölgelerini incelemek için interop hata ayıklama tarafından kullanılmak üzere tasarlanmıştır. Bu yöntem, Microsoft ara dili (MSIL) kodunu ve yerel JIT tarafından derlenen kodu okumak için de kullanılabilir.  
  
 Yönetilen kesme noktaları `buffer` parametrede döndürülen verilerden kaldırılır. ICorDebugProcess2 tarafından ayarlanan yerel kesme noktaları için ayarlama [yapılmaz::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 İşlem belleği önbelleğe alma işlemi yapılmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
