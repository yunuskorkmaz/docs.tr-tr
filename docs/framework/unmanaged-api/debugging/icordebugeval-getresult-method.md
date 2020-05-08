---
title: ICorDebugEval::GetResult Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
ms.openlocfilehash: 2d065d956319076d3b92eddafd4a2c25ffbfbac1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976271"
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult Yöntemi
Bu değerlendirmenin sonuçlarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppResult`  
 dışı Değerlendirme normal şekilde tamamlanırsa, bu değerlendirmenin sonuçlarını temsil eden bir ICorDebugValue nesnesinin adresine yönelik işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetResult` Yöntem yalnızca değerlendirme tamamlandıktan sonra geçerlidir.  
  
 Değerlendirme normal şekilde tamamlanırsa, `ppResult` sonuçları belirtir. Bir özel durumla sonlandığında sonuç, oluşturulan özel durumdur. Değerlendirme yeni bir nesne için ise, sonuç yeni nesneye başvurudur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
