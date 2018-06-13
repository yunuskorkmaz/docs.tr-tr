---
title: ISymUnmanagedDocument::GetSourceRange Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 00baed93bd9ab48c92de83dac76931c3149afc2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424644"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>ISymUnmanagedDocument::GetSourceRange Metodu
Katıştırılmış kaynak belirtilen aralığını verilen arabelleğe döndürür. Arabellek kaynak tutabilecek kadar büyük olmalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `startLine`  
 [in] Geçerli belgede başlangıç satırı.  
  
 `startColumn`  
 [in] Geçerli belgede başlangıç sütunu.  
  
 `endLine`  
 [in] Geçerli belgede son satır.  
  
 `endColumn`  
 [in] Geçerli belgede son sütun.  
  
 `cSourceBytes`  
 [in] Kaynak bayt cinsinden boyutu.  
  
 `pcSourceBytes`  
 [out] Bir işaretçi bir değişkene kaynak boyutu alır.  
  
 `source`  
 [out] Boyutu ve belirtilen aralık kaynak belgenin bayt cinsinden uzunluğu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedDocument Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
