---
description: 'Şu konuda daha fazla bilgi edinin: ISymENCUnmanagedMethod:: GetDocumentsForMethod yöntemi'
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
ms.openlocfilehash: 01c7280abe437266618d96c6e195e61a4f830131
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721547"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a>ISymENCUnmanagedMethod::GetDocumentsForMethod Yöntemi

Bu yöntemin içindeki satırları içeren belgeleri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cDocs`  
 'ndaki Tarafından işaret edilen arabelleğin uzunluğu `pcDocs` .  
  
 `pcDocs`  
 dışı `ULONG32` Belgeyi içermesi için gereken arabelleğin boyutunu, karakter cinsinden alan bir işaretçisi.  
  
 `documents`  
 'ndaki Belgeleri içeren arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymENCUnmanagedMethod Arabirimi](isymencunmanagedmethod-interface.md)
