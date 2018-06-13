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
ms.openlocfilehash: f7ed7787f0302826cab67664780177f05e551199
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421112"
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions Metodu
Etkin işlevi hakkında bilgi her bu iş parçacığının çerçeveleri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cFunctions`  
 [in] Boyutunu `pFunctions` dizi.  
  
 `pcFunctions`  
 [out] Döndürülen nesne sayısı için bir işaretçi `pFunctions` dizi. Döndürülen nesne sayısı yığında yönetilen çerçeveler sayısına eşit olur.  
  
 `pFunctions`  
 [içinde out] Her biri bu iş parçacığının çerçeveleri etkin işlevleri hakkında bilgi içeren bir dizi cor_actıve_functıon nesneleri.  
  
 İlk öğe yaprak çerçeve ve yığın kökünde vb. geri için kullanılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `pFunctions` giriş, null `GetActiveFunctions` yalnızca olduğundan yığınındaki işlevler sayısını döndürür. Diğer bir deyişle, `pFunctions` giriş, null `GetActiveFunctions` bir değer döndürür yalnızca `pcFunctions`.  
  
 `GetActiveFunctions` Yöntemi bir iyileştirme yığın izlemesi çerçevelere gelen aynı bilgi alma yöneliktir ve yalnızca Icordebugılframe nesne için tam yığın izlemesinde beklendiğinden çerçevelerini içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
