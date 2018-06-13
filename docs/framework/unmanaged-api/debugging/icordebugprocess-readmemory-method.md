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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0063e33a6a7861815ebb9d9eb3dabec64dd4b9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419659"
---
# <a name="icordebugprocessreadmemory-method"></a>ICorDebugProcess::ReadMemory Yöntemi
Bu işlem için bellek belirtilen alan okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 [in] A `CORDB_ADDRESS` okumak için bellek taban adresini belirten değer.  
  
 `size`  
 [in] Bellekten okunacak bayt sayısı.  
  
 `buffer`  
 [out] Bellek içeriğini alır arabelleği.  
  
 `read`  
 [out] Bir işaretçi bayt sayısı belirtilen arabelleğe aktarılan.  
  
## <a name="remarks"></a>Açıklamalar  
 `ReadMemory` Yöntemi ayıklayıcı yönetilmeyen bölümü tarafından kullanılan bellek bölümlerinin incelemek için birlikte çalışma hata ayıklama tarafından kullanılmak üzere öncelikle amaçlanmıştır. Bu yöntem, Microsoft Ara dili (MSIL) kodu ve yerel JIT derlenmiş kod okumak için de kullanılabilir.  
  
 Tüm yönetilen kesme noktalarını döndürülür verileri kaldırılacak `buffer` parametresi. Yerel kesme noktaları ayarlayın ayarlama yapılmayan yapılan [Icordebugprocess2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 Önbelleğe alma işlemi bellek gerçekleştirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
