---
title: ISymUnmanagedMethod::GetRanges Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef5a98d510eee8942a2cad0525b6902e3e4eaa52
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769381"
---
# <a name="isymunmanagedmethodgetranges-method"></a>ISymUnmanagedMethod::GetRanges Yöntemi
Belgede bir konuma konumu bu yöntem içinde kapsayan Microsoft Ara dilini (MSIL) aralıklarına karşılık gelen başlangıç ve bitiş uzaklığında Çiftler dizisini döndürür. Dizi tamsayı dizisi ve [Başlangıç, bitiş, başlangıç, bitiş] biçimi vardır. 2 tarafından ayrılmış dizi uzunluğu aralığın çiftleri sayısıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `document`  
 [in] Uzaklık istendiği belge.  
  
 `line`  
 [in] Aralıkları için karşılık gelen belge satır.  
  
 `column`  
 [in] Aralıkları için karşılık gelen belge sütun.  
  
 `cRanges`  
 [in] Boyutu `ranges` dizisi.  
  
 `pcRanges`  
 [out] Bir işaretçi bir `ULONG32` içeriyor aralıkları için gerekli arabellek boyutunu alır.  
  
 `ranges`  
 [out] Aralık alan arabellek için işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
