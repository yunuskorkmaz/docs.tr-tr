---
title: ISymUnmanagedWriter::OpenNamespace Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1585acce8bba0dff327c961f5e32ef6b46794401
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986030"
---
# <a name="isymunmanagedwriteropennamespace-method"></a>ISymUnmanagedWriter::OpenNamespace Yöntemi
Yeni bir ad alanı açılır. Yöntem veya bir ad alanı kaplayan değişkenleri tanımlamadan önce bu yöntemi çağırın. Ad alanları yuvalanabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a>Parametreler  
 `name`  
 [in] Yeni ad alanı adı için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [CloseNamespace Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
