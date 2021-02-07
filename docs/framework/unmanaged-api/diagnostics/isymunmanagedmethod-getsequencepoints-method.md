---
description: 'Şu konuda daha fazla bilgi edinin: ırivınunmanagedmethod:: GetSequencePoints yöntemi'
title: ISymUnmanagedMethod::GetSequencePoints Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
ms.openlocfilehash: acdfcb014648593065bd1ae252ef936898a1e8b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721300"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints Yöntemi

Bu yöntemin içindeki tüm sıra noktalarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cPoints`  
 'ndaki ,,,,, `ULONG32` `offsets` `documents` `lines` `columns` `endLines` Ve `endColumns` dizilerinin boyutunu alan bir.  
  
 `pcPoints`  
 dışı `ULONG32` Dizi noktalarını içermesi için gereken arabelleğin uzunluğunu alan öğesine bir işaretçisi.  
  
 `offsets`  
 'ndaki Dizi noktaları için yöntemin başlangıcından Microsoft ara dili (MSIL) uzaklıklarını depolayan bir dizi.  
  
 `documents`  
 'ndaki Dizi noktalarının bulunduğu belgelerin depolandığı bir dizi.  
  
 `lines`  
 'ndaki Sıra noktalarının bulunduğu belgelerde satırların depolandığı bir dizi.  
  
 `columns`  
 'ndaki Dizi noktalarının bulunduğu belgelerde sütunların depolandığı bir dizi.  
  
 `endLines`  
 'ndaki Sıra noktalarının sonundaki belgelerdeki satır dizisi.  
  
 `endColumns`  
 'ndaki Sıra noktalarının sonundaki belgelerdeki sütunların dizisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedMethod Arabirimi](isymunmanagedmethod-interface.md)
