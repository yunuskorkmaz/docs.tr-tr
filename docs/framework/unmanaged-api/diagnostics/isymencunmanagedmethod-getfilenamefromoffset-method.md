---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 494f39855132bc4a9551b78f746517862d285034
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074735"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a>ISymENCUnmanagedMethod::GetFileNameFromOffset Yöntemi
Bir uzaklık ile ilişkili satırı dosya adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwOffset`  
 [in] A `ULONG32` içeren uzaklığı.  
  
 `cchName`  
 [in] A `ULONG32` boyutunu gösteren `szName` arabellek.  
  
 `pcchName`  
 [out] Bir işaretçi bir `ULONG32` karakter dosya adlarını içermesini gerekli arabellek boyutunu alır.  
  
 `szName`  
 [out] Dosya adlarını içeren arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymENCUnmanagedMethod Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
