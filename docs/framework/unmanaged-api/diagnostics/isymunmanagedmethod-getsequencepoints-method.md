---
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
ms.openlocfilehash: 75d477af7395a9b7d3328b2a5787f810733f3749
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448880"
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
 'ndaki `offsets`, `documents`, `lines`, `columns`, `endLines`ve `endColumns` dizilerinin boyutunu alan bir `ULONG32`.  
  
 `pcPoints`  
 dışı Sıra noktalarını içermesi için gereken arabelleğin uzunluğunu alan `ULONG32` işaretçisi.  
  
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

- [ISymUnmanagedMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
