---
title: ISymENCUnmanagedMethod::GetDocumentsForMethod Metodu
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethod
helpviewer_keywords:
- GetDocumentsForMethod method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethod method [.NET Framework debugging]
ms.assetid: bd6ccde5-d578-48d8-abed-b474fbd48d13
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cd294037774721839b0c4f1f09bdc2a6e3b87841
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562680"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a>ISymENCUnmanagedMethod::GetDocumentsForMethod Metodu
Bu yöntem satır var, belgeleri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cDocs`  
 [in] Arabellek uzunluğu tarafından işaret edilen `pcDocs`.  
  
 `pcDocs`  
 [out] Bir işaretçi bir `ULONG32` karakter belgeleri içermesini gerekli arabellek boyutunu alır.  
  
 `documents`  
 [in] Belgeleri içeren arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ISymENCUnmanagedMethod Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
