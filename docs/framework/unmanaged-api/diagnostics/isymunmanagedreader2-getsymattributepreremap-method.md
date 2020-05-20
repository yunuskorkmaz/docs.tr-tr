---
title: ISymUnmanagedReader2::GetSymAttributePreRemap Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
ms.openlocfilehash: e6248aba1c41b2815f2806942d419da869ed94b4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614922"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>ISymUnmanagedReader2::GetSymAttributePreRemap Metodu
Özel bir özniteliği adına göre alır. Meta veri özel özniteliklerinin aksine, bu öznitelikler sembol deposunda tutulur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `parent`  
 'ndaki Üst öğenin meta veri belirteci.  
  
 `name`  
 'ndaki Adını içeren bir işaretçisi `WCHAR` .  
  
 `cBuffer`  
 'ndaki `ULONG32`Dizi boyutunu belirten bir `buffer` .  
  
 `pcBuffer`  
 dışı `ULONG32`Öznitelik baytlarını içermesi için gereken arabellek boyutunu alan bir işaretçisi.  
  
 `buffer`  
 dışı Öznitelik baytlarını alan arabelleğin işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedReader2 Yöntemi](isymunmanagedreader2-interface.md)
