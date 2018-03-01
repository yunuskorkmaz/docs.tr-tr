---
title: ICorDebugCode::GetCode Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f906fddf8073a00d2a3741613aae537b8604af67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode Metodu
Belirtilen işlev için ayrıştırılmış biçimlendirilmiş tüm kodu alır. Bu yöntem .NET Framework sürüm 2.0 kullanım dışıdır. Kullanım [Icordebugcode2::getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `startOffset`  
 [in] İşlev başlangıç uzaklığı.  
  
 `endOffset`  
 [in] İşlevin sonuna uzaklığı.  
  
 `cBufferAlloc`  
 [in] Boyutunu `buffer` dizi kodu, döndürülecek içine.  
  
 `buffer`  
 [out] Dizi içine kodu döndürülür.  
  
 `pcBufferSize`  
 [out] Döndürülen bayt sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlevin kodunu birden çok parçalara bölünür varsa, bunlar, yerel uzaklığı artan sırada birleşir. Yönerge sınırları denetlenmez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 1.1, 1.0  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetCodeChunks Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 
