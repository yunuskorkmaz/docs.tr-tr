---
title: ISymUnmanagedScope2::GetConstants Yöntemi
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
ms.openlocfilehash: 45268929b6e9ad6ac6423aa0fa2b7b5022bc9179
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176623"
---
# <a name="isymunmanagedscope2getconstants-method"></a>ISymUnmanagedScope2::GetConstants Yöntemi
Bu kapsamda tanımlanan yerel sabitleri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cConstants`  
 [içinde] `pcConstants` Parametrenin işaret ettiği arabelleğe in uzunluğu.  
  
 `pcConstants`  
 [çıkış] Sabitleri içermek için gereken arabelleğe in boyutlarını karakterlerde alan bir `ULONG32` işaretçi.  
  
 `constants`  
 [çıkış] Sabitleri depolayan arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 yöntem başarılı olursa S_OK; aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedScope2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
