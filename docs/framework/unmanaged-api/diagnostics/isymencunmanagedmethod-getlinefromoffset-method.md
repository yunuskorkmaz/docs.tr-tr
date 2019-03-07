---
title: ISymENCUnmanagedMethod::GetLineFromOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90d993bc6b947d309ce1a0fb10ad231a429be567
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471920"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset Yöntemi
Bir uzaklık ile ilişkili satır bilgilerini alır. Varsa uzaklık parametresi (`dwOffset`) bir dizi noktası değil. Bu yöntem, önceki uzaklığı ile ilişkili satır bilgileri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwOffset`  
 [in] A `ULONG32` içeren uzaklığı.  
  
 `pline`  
 [out] Bir işaretçi bir `ULONG32` , satır alır.  
  
 `pcolumn`  
 [out] Bir işaretçi bir `ULONG32` , sütunu alır.  
  
 `pendLine`  
 [out] Bir işaretçi bir `ULONG32` , satır sonunu alır.  
  
 `pendColumn`  
 [out] Bir işaretçi bir `ULONG32` , end sütunu alır.  
  
 `pdwStartOffset`  
 [out] Bir işaretçi bir `ULONG32` , ilişkili dizi noktası alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ISymENCUnmanagedMethod Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
