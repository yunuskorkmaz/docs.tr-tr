---
title: ISymUnmanagedWriter::SetMethodSourceRange Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
ms.openlocfilehash: 85e65f6a3ec13c2acc31b8f87dbe4b4476ffc2a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427870"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a>ISymUnmanagedWriter::SetMethodSourceRange Yöntemi
Kaynak dosya içindeki bir yöntemin doğru başlangıcını ve sonunu belirtir. Yöntemin içinde var olan sıra noktalarından bağımsız olarak bir yöntemin kapsamını belirtmek için bu yöntemi kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a>Parametreler  
 `startDoc`  
 'ndaki Başlangıç konumunu içeren belgeye yönelik bir işaretçi.  
  
 `startLine`  
 'ndaki Başlangıç satır numarası.  
  
 `startColumn`  
 'ndaki Başlangıç sütunu.  
  
 `endDoc`  
 'ndaki Bitiş konumunu içeren belgeye yönelik bir işaretçi.  
  
 `endLine`  
 'ndaki Son satır numarası.  
  
 `endColumn`  
 'ndaki Bitiş sütun numarası.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
