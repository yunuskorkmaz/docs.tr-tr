---
title: ISymUnmanagedMethod::GetSequencePoints Metodu
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9a35f35d7aea34c0ef08c30415fde75fe71e645
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426056"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints Metodu
Bu yöntem içindeki tüm sıralama noktaları alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
  
#### <a name="parameters"></a>Parametreler  
 `cPoints`  
 [in] A `ULONG32` boyutunu alır `offsets`, `documents`, `lines`, `columns`, `endLines`, ve `endColumns` dizileri.  
  
 `pcPoints`  
 [out] Bir işaretçi bir `ULONG32` sıralama noktaları içermesi gerekir arabelleği uzunluğunu alır.  
  
 `offsets`  
 [in] Sıralama noktaları yöntemi başından itibaren dili (MSIL) kaydırır, Microsoft Ara depolamak bir dizi.  
  
 `documents`  
 [in] Sıralama noktaları bulunan belgeleri depolamak üzere bir dizi.  
  
 `lines`  
 [in] Satırları sıralama noktaları bulunduğu olan belgeleri depolamak üzere bir dizi.  
  
 `columns`  
 [in] Sütunları sıralama noktaları bulunduğu olan belgeleri depolamak üzere bir dizi.  
  
 `endLines`  
 [in] En son sırası işaret belgelerde satırları dizisi.  
  
 `endColumns`  
 [in] En son sırası işaret belgelerde sütun dizisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
