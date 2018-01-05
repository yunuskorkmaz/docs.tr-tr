---
title: ICorDebugFunction2::GetVersionNumber Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.GetVersionNumber
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16902d1a50f691ae555fdbc964bb9a1c6bf563c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber Metodu
Bu işlev Düzenle ve devam et sürümünü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pnVersion`  
 [out] Bu Icordebugfunction2 nesnesi tarafından temsil edilen işlevi sürüm sayısı bir tamsayı gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Çalışma zamanı, her modül için bir hata ayıklama oturumu sırasında yapılmadığı düzenlemeleri sayısını izler. Bir işlevin sürüm numarası biridir işlevi sunulan düzenleme sayıdan fazla. İşlevin özgün sürüm 1 sürümüdür. Sayı, her seferinde bir modülü için artırılır [Icordebugmodule2::applychanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) üzerinde bu modül çağrılır. Bu nedenle, bir işlevin gövdesi birinci ve üçüncü çağrısında değiştirilmişse `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` sürüm 1, 2 veya 4 Bu işlevin, ancak sürüm 3 döndürebilir. (İşlev hiçbir sürüm 3 olması.)  
  
 Sürüm numarası, her modül için ayrı olarak izlenir. Modül 1 ve hiçbiri modülü 2 dört düzenlemeleri gerçekleştirirseniz, bu nedenle, sonraki düzenlemeniz modülü 1 sürüm numarası 6 olarak düzenlenen uygulamasında tüm işlevleri Modül 1 atar. Aynı rötuşları Modül 2 düzenlerseniz, Modül 2 işlevlerde 2 sürüm sayısını alır.  
  
 Sürüm numarasını elde tarafından `GetVersionNumber` yöntemi tarafından edindiğiniz daha düşük [ICorDebugFunction::getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).  
  
 [Icordebugcode::getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) yöntemi olarak aynı işlemi gerçekleştirir `ICorDebugFunction2::GetVersionNumber`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
