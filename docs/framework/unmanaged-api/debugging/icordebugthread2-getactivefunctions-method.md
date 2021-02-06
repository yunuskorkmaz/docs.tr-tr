---
description: 'Daha fazla bilgi edinin: ICorDebugThread2:: GetActiveFunctions yöntemi'
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
ms.openlocfilehash: 841e8ff17f15cfb14e1c1bf65c651a5177db2eaa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658769"
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
 'ndaki `pFunctions` Dizinin boyutu.  
  
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
