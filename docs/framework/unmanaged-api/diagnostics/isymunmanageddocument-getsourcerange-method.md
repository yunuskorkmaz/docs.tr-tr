---
title: ISymUnmanagedDocument::GetSourceRange Yöntemi
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
ms.openlocfilehash: 767508e51660a161a7a6ff0b168a46178d66be99
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474157"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>ISymUnmanagedDocument::GetSourceRange Yöntemi
Katıştırılmış kaynak Belirtilen aralıktaki belirli arabelleğe döndürür. Arabellek kaynağını tutabilecek kadar büyük olmalıdır.  
  
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
  
## <a name="parameters"></a>Parametreler  
 `startLine`  
 [in] Geçerli belgedeki başlangıç satırı.  
  
 `startColumn`  
 [in] Geçerli belgedeki başlangıç sütunu.  
  
 `endLine`  
 [in] Geçerli belgedeki son satır.  
  
 `endColumn`  
 [in] Son sütun geçerli belge.  
  
 `cSourceBytes`  
 [in] Kaynak, bayt cinsinden boyutu.  
  
 `pcSourceBytes`  
 [out] Kaynak boyutu alan bir değişken için bir işaretçi.  
  
 `source`  
 [out] Boyutu ve belirtilen kaynak belgesinde bayt aralığı uzunluğu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ISymUnmanagedDocument Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
