---
title: ISymUnmanagedWriter::UsingNamespace Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a5ff52a95fd6ebaec05439cbc702d5513d0cc78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427775"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a>ISymUnmanagedWriter::UsingNamespace Yöntemi
Verilen tam ad alanı adı şu anda açık sözcük kapsamında kullanılmakta olduğunu belirtir. Ad alanı, açık olan kapsamlardan devralır tüm kapsamlarında kullanılır. Geçerli kapsamdaki kapatma ad alanı kullanımını de durdurulur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `fullName`  
 [in] Ad alanının tam adı için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
