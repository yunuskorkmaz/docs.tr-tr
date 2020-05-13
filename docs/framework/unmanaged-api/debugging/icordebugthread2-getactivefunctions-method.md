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
ms.openlocfilehash: e064a7db131a671adc4d0b6df522f3456e3a31d5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377160"
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions Metodu
Bu iş parçacığı çerçevelerinin her birinde etkin işlev hakkında bilgi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cFunctions`  
 'ndaki `pFunctions`Dizinin boyutu.  
  
 `pcFunctions`  
 dışı Dizide döndürülen nesne sayısına yönelik bir işaretçi `pFunctions` . Döndürülen nesne sayısı, yığındaki yönetilen çerçeve sayısına eşit olacaktır.  
  
 `pFunctions`  
 [in, out] Her biri bu iş parçacığı çerçevelerinden etkin işlevlerle ilgili bilgiler içeren COR_ACTIVE_FUNCTION nesnelerden oluşan bir dizi.  
  
 İlk öğe yaprak çerçeve için kullanılacaktır ve bu nedenle yığının köküne geri dönün.  
  
## <a name="remarks"></a>Açıklamalar  
 `pFunctions`Girişte null ise, `GetActiveFunctions` yalnızca yığında olan işlev sayısını döndürür. Yani, `pFunctions` girişte null ise, `GetActiveFunctions` yalnızca içinde bir değer döndürür `pcFunctions` .  
  
 `GetActiveFunctions`Yöntemi, bir yığın izlemesinde çerçevelerden aynı bilgileri elde etmek için en iyi duruma getirme amaçlıdır ve yalnızca tam yığın izlemesinde bir ICorDebugILFrame nesnesine sahip olacak çerçeveleri içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
