---
title: ISymUnmanagedMethod::GetOffset Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a42dc624d4de9cddebad287f6d90590f96b30272
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939665"
---
# <a name="isymunmanagedmethodgetoffset-method"></a>ISymUnmanagedMethod::GetOffset Metodu
Bir belge içindeki belirli bir konuma karşılık gelen bu yöntem içinde uzaklığını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a>Parametreler  
 `document`  
 [in] Uzaklık istendiği belge işaretçisi.  
  
 `line`  
 [in] Uzaklık istendiği belge satır.  
  
 `column`  
 [in] Uzaklık istendiği belge sütun.  
  
 `pRetVal`  
 [out] Bir işaretçi bir `ULONG32` , uzaklıkları alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
