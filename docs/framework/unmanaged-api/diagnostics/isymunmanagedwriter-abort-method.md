---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: Abort yöntemi'
title: ISymUnmanagedWriter::Abort Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
ms.openlocfilehash: 312694bf2b667ea78bf5ddc993d0e2b71c85a8ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762688"
---
# <a name="isymunmanagedwriterabort-method"></a>ISymUnmanagedWriter::Abort Yöntemi

Sembol deposuna sembolleri kaydetmeden sembol yazıcısını kapatır. Bu çağrıdan sonra sembol yazıcısı, daha fazla güncelleştirme için geçersiz hale gelir. Sembolleri yürütmek ve sembol yazıcısını kapatmak için, bunun yerine [ıvmunmanagedwriter:: Close](isymunmanagedwriter-close-method.md) metodunu kullanın.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
