---
title: ICorDebugFunction2::GetVersionNumber Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
ms.openlocfilehash: 5826297d8151cf05e1ec08acbf5c9cd381d2452b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137801"
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber Yöntemi
Bu işlevin Düzenle ve devam et sürümünü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pnVersion`  
 dışı Bu ICorDebugFunction2 nesnesi tarafından temsil edilen işlevin sürüm numarası olan tamsayıya yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Çalışma zamanı, hata ayıklama oturumu sırasında her bir modüle gerçekleşen düzenleme sayısını izler. Bir işlevin sürüm numarası, işlevi sunan düzenleme sayısından bir daha fazla. İşlevin özgün sürümü sürüm 1 ' dir. Bu modülde her [ICorDebugModule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) çağrıldığında sayı bir modül için artırılır. Bu nedenle, bir işlevin gövdesi `ICorDebugModule2::ApplyChanges`ilk ve üçüncü çağrısında değiştirildiyse, `GetVersionNumber` söz konusu işlev için sürüm 1, 2 veya 4 döndürebilir, sürüm 3 ' ü içermez. (Bu işlevin sürüm 3 ' ü yoktur.)  
  
 Sürüm numarası her modül için ayrı olarak izlenir. Bu nedenle, modül 1 üzerinde dört düzenleme gerçekleştirirseniz ve modül 2 ' de hiç bir işlem yaptıysanız, modül 1 ' deki bir sonraki düzenleme, modül 1 ' deki tüm düzenlenmiş işlevlere 6 sürüm numarası atar. Aynı düzenleme, modül 2 ' ye dokunursa modül 2 ' deki işlevler sürüm numarası 2 alır.  
  
 `GetVersionNumber` yöntemi tarafından edinilen sürüm numarası [ICorDebugFunction:: GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)tarafından elde edilenden daha düşük olabilir.  
  
 [ICorDebugCode:: GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) yöntemi, `ICorDebugFunction2::GetVersionNumber`ile aynı işlemi gerçekleştirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
