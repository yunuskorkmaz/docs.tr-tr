---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedwriter:: SetMethodSourceRange Yöntemi'
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
ms.openlocfilehash: 2e2f0f664d8be30a8c3628100fafb3740d34f54f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762077"
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

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
