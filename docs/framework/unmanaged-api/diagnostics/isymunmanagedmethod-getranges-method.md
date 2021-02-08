---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedmethod:: GetRanges yöntemi'
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
ms.openlocfilehash: e6a1da285c0574ef5910e8e727c3bcc5cb9e5d35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790106"
---
# <a name="isymunmanagedmethodgetranges-method"></a>ISymUnmanagedMethod::GetRanges Yöntemi

Belgedeki bir konum verildiğinde, konumun bu yöntem içinde kapsamakta olduğu Microsoft ara dili (MSIL) aralıklarına karşılık gelen başlangıç ve bitiş konumu çiftleri dizisini döndürür. Dizi tamsayılar dizisidir ve [Start, End, Start, End] biçiminde olur. Aralık çifti sayısı, dizinin uzunluğu 2 ' ye bölünür.  
  
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
 'ndaki Kaydırın istendiği belge.  
  
 `line`  
 'ndaki Aralıklara karşılık gelen belge satırı.  
  
 `column`  
 'ndaki Aralıklara karşılık gelen belge sütunu.  
  
 `cRanges`  
 'ndaki `ranges` Dizinin boyutu.  
  
 `pcRanges`  
 dışı `ULONG32` Aralıkları içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.  
  
 `ranges`  
 dışı Aralıkları alan arabelleğin işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedMethod Arabirimi](isymunmanagedmethod-interface.md)
