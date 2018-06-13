---
title: ICorDebugCode2::GetCodeChunks Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdfcd45b15ddc1491b12de0fa42901b6d3f7fe9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413159"
---
# <a name="icordebugcode2getcodechunks-method"></a>ICorDebugCode2::GetCodeChunks Metodu
Bu kod nesnesi oluşan kod parçalarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cbufSize`  
 [in] Boyutunu `chunks` dizi.  
  
 `pcnumChunks`  
 [out] Döndürülen öbeği sayısı `chunks` dizi.  
  
 `chunks`  
 [out] Her biri tek bir öbek kodunun temsil eden bir dizi "Codechunkınfo" yapıları. Varsa değerini `cbufSize` 0'dır, bu parametre null olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kod öbekleri hiçbir zaman çakışır ve, bunlar birleştirilmiş tarafından sipariş izleyeceği [Icordebugcode::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md). .NET Framework sürüm 2.0 Microsoft Ara dili (MSIL) kod nesnesinde bir tek bir kod öbek oluşturan.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
