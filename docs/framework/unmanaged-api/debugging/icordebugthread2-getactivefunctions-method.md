---
title: ICorDebugThread2::GetActiveFunctions Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed13f78d5a1f6d54b12c86613715f4878a521bfa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489936"
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions Metodu
Bu bu iş parçacığının çerçevede etkin işlevi hakkında bilgi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cFunctions`  
 [in] Boyutu `pFunctions` dizisi.  
  
 `pcFunctions`  
 [out] Döndürülen nesne sayısı için bir işaretçi `pFunctions` dizisi. Döndürülen nesne sayısını yığın üzerinde yönetilen çerçeve sayısı eşit olacaktır.  
  
 `pFunctions`  
 [out içinde] Bir dizi cor_actıve_functıon nesnelerin her biri bu iş parçacığının çerçeveler etkin işlevler hakkında bilgiler içerir.  
  
 İlk öğeyi yaprak çerçeve ve yığın kökünün vb. geri için kullanılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `pFunctions` girişte, null `GetActiveFunctions` yalnızca yığında olan işlev sayısını döndürür. Diğer bir deyişle, `pFunctions` girişte, null `GetActiveFunctions` bir değer döndürür. yalnızca `pcFunctions`.  
  
 `GetActiveFunctions` Yöntemi bir iyileştirme bir yığın izlemesi çerçevelerde aynı bilgileri almaya oluşturulmuştur ve yalnızca bir Icordebugılframe nesne için tam bir yığın izlemeyle uygulamanızda zorunda kalacaktır çerçevelerini içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
