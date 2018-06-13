---
title: ICorDebugHeapValue2::CreateHandle Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c69d1f83a4591df4d2dcb7fb9724fa582ea28387
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413585"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle Yöntemi
Belirtilen tür bu Icordebugheapvalue2 nesnesi tarafından temsil edilen yığın değer için bir tanıtıcı oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `type`  
 [in] Oluşturulacak tanıtıcı türü belirtir CorDebugHandleType numaralandırması değeri.  
  
 `ppHandle`  
 [out] Bir işaretçi adresine Icordebughandlevalue nesnenin Bu yığın değer için yeni tanıtıcısını temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Tanıtıcı yığın değeriyle ilişkili uygulama etki alanında oluşturulur ve uygulama etki alanı bellekten alırsa geçersiz hale gelecek.  
  
 Bu işlev aynı yığın değeri için birden fazla çağrı birden çok işleyici oluşturur. Hata ayıklayıcı tanıtıcıları atık toplayıcı performansı etkilediğinden, aynı anda etkin olan tanıtıcıları (yaklaşık 256) görece küçük bir dizi kendisine sınırlamanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
