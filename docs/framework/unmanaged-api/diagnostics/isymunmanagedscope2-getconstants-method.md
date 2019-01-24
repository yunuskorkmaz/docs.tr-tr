---
title: ISymUnmanagedScope2::GetConstants Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24fd642b8eaba19a8bfb32d2dc61a87595cb3c61
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643734"
---
# <a name="isymunmanagedscope2getconstants-method"></a>ISymUnmanagedScope2::GetConstants Metodu
Bu kapsam içinde tanımlanan yerel sabitleri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*   
             constants[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cConstants`  
 [in] Arabellek uzunluğu, `pcConstants` parametre işaret eder.  
  
 `pcConstants`  
 [out] Bir işaretçi bir `ULONG32` karakter sabitleri içerecek şekilde gerekli arabellek boyutunu alır.  
  
 `constants`  
 [out] Sabitler depolayan arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ISymUnmanagedScope2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
