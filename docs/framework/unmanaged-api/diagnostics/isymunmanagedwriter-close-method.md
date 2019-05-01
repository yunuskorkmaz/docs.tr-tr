---
title: ISymUnmanagedWriter::Close Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4d3497d3167715d3e8a04f10a6687260949e4a36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934062"
---
# <a name="isymunmanagedwriterclose-method"></a>ISymUnmanagedWriter::Close Yöntemi
Sembolleri sembol deposuna uyguladıktan sonra sembol yazıcı kapatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu çağrıdan sonra sembol yazıcısı güncelleştirmeleri daha fazla geçersiz hale gelir. Sembol yazıcı simgeleri kaydetmeden kapatmak için kullanmak [Isymunmanagedwriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) yöntemi yerine.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
