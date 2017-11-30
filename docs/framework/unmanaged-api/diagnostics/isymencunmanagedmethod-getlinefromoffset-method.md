---
title: ISymENCUnmanagedMethod::GetLineFromOffset Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetLineFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f18357b3a58a5409da93d4d2491997e9ca1cc70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset Metodu
Bir uzaklık ile ilişkili satır bilgilerini alır. Varsa uzaklık parametresi (`dwOffset`) bir dizi noktası değil Bu yöntem önceki uzaklık ile ilişkili satır bilgilerini alır.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `dwOffset`  
 [in] A `ULONG32` uzaklık içerir.  
  
 `pline`  
 [out] Bir işaretçi bir `ULONG32` satır alır.  
  
 `pcolumn`  
 [out] Bir işaretçi bir `ULONG32` sütunu alır.  
  
 `pendLine`  
 [out] Bir işaretçi bir `ULONG32` satır sonu alır.  
  
 `pendColumn`  
 [out] Bir işaretçi bir `ULONG32` end sütunu alır.  
  
 `pdwStartOffset`  
 [out] Bir işaretçi bir `ULONG32` ilişkili dizi noktası alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Isymencunmanagedmethod arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
