---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanageddocument:: GetSourceRange yöntemi'
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
ms.openlocfilehash: 98718298d7bf2f44d418a40f17ad19cdee0b6771
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790171"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>ISymUnmanagedDocument::GetSourceRange Yöntemi

Eklenmiş kaynağın belirtilen aralığını verilen arabelleğe döndürür. Arabellek, kaynağı tutabilecek kadar büyük olmalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki Geçerli belgedeki başlangıç satırı.  
  
 `startColumn`  
 'ndaki Geçerli belgedeki başlangıç sütunu.  
  
 `endLine`  
 'ndaki Geçerli belgedeki son satır.  
  
 `endColumn`  
 'ndaki Geçerli belgedeki son sütun.  
  
 `cSourceBytes`  
 'ndaki Kaynağın bayt cinsinden boyutu.  
  
 `pcSourceBytes`  
 dışı Kaynak boyutunu alan değişken için bir işaretçi.  
  
 `source`  
 dışı Kaynak belge için bayt cinsinden belirtilen aralığın boyutu ve uzunluğu.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedDocument Arabirimi](isymunmanageddocument-interface.md)
