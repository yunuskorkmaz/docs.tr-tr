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
ms.openlocfilehash: 9b9a301714ea60b4e3220eb75721e56e39bd9659
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139936"
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
 'ndaki `pFunctions` dizisinin boyutu.  
  
 `pcFunctions`  
 dışı `pFunctions` dizisinde döndürülen nesne sayısına yönelik bir işaretçi. Döndürülen nesne sayısı, yığındaki yönetilen çerçeve sayısına eşit olacaktır.  
  
 `pFunctions`  
 [in, out] Her biri bu iş parçacığı çerçevelerinin etkin işlevleri hakkında bilgi içeren bir COR_ACTIVE_FUNCTION nesneleri dizisi.  
  
 İlk öğe yaprak çerçeve için kullanılacaktır ve bu nedenle yığının köküne geri dönün.  
  
## <a name="remarks"></a>Açıklamalar  
 `pFunctions` girişte null ise, `GetActiveFunctions` yalnızca yığında olan işlevlerin sayısını döndürür. Diğer bir deyişle, `pFunctions` girişte null ise, `GetActiveFunctions` yalnızca `pcFunctions`bir değer döndürür.  
  
 `GetActiveFunctions` yöntemi, bir yığın izlemesinde çerçevelerden aynı bilgileri elde etmek için en iyi duruma getirme amaçlıdır ve yalnızca tam yığın izlemesinde bir ICorDebugILFrame nesnesine sahip olacak çerçeveleri içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
