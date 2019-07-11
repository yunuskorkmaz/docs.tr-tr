---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2debe193b96b065987f6d7ebc6ffc1abac95778
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778218"
---
# <a name="isymunmanagedwriterabort-method"></a>ISymUnmanagedWriter::Abort Yöntemi
Sembolleri sembol deposuna taahhüt vermek zorunda kalmadan sembol yazıcı kapatır. Bu çağrıdan sonra sembol yazıcısı güncelleştirmeleri daha fazla geçersiz hale gelir. Simgeleri işleyin ve sembol yazıcı kapatmak için kullanmak [Isymunmanagedwriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
