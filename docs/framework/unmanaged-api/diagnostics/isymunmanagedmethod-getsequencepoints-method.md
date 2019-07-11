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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d8cfde8f0eb14919c12d261c3f9f7209365829c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759455"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints Yöntemi
Bu yöntem içinde tüm dizi noktalarını alır.  
  
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
 [in] A `ULONG32` boyutunu alır `offsets`, `documents`, `lines`, `columns`, `endLines`, ve `endColumns` dizileri.  
  
 `pcPoints`  
 [out] Bir işaretçi bir `ULONG32` dizi noktalarını içerecek şekilde gerekli arabellek uzunluğunu alır.  
  
 `offsets`  
 [in] Bir dizi saklanacağı Microsoft Ara dili (MSIL) sıralama noktaları yöntemi başından itibaren kaydırır.  
  
 `documents`  
 [in] Dizi noktaları bulunan belgeleri depolamak için bir dizi.  
  
 `lines`  
 [in] Satırları sıralama noktaları yer olan belgeleri depolamak için bir dizi.  
  
 `columns`  
 [in] Sütunları sıralama noktaları yer olan belgeleri depolamak için bir dizi.  
  
 `endLines`  
 [in] Belgelerde dizisi son işaret ettiği satırları dizisi.  
  
 `endColumns`  
 [in] Sütun sırası son işaret ettiği belgelerdeki dizisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
