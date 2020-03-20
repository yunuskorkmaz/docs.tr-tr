---
title: ISymENCUnmanagedMethod::GetDocumentsForMethod Yöntemi
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
ms.openlocfilehash: 97f0d81c389ffd0bd8a69df2ca39322d726f98bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176636"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a>ISymENCUnmanagedMethod::GetDocumentsForMethod Yöntemi
Bu yöntemin satırları olan belgeleri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cDocs`  
 [içinde] Arabelleğe işaret edilen tampon `pcDocs`uzunluğu.  
  
 `pcDocs`  
 [çıkış] Belgeleri içermek `ULONG32` için gereken arabelleğe in boyutlarını, karakterlerdeki boyutu alan bir işaretçi.  
  
 `documents`  
 [içinde] Belgeleri içeren arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 yöntem başarılı olursa S_OK; aksi takdirde, bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymENCUnmanagedMethod Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
