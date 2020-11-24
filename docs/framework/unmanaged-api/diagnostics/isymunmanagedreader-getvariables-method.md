---
title: ISymUnmanagedReader::GetVariables Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
ms.openlocfilehash: c4341a5ffe557694473ae505590b57d39a27a721
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675899"
---
# <a name="isymunmanagedreadergetvariables-method"></a>ISymUnmanagedReader::GetVariables Yöntemi

Üst ve adı verilen yerel olmayan bir değişken döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `parent`  
 'ndaki Değişkenin üst öğesi.  
  
 `cVars`  
 'ndaki `pVars` Dizinin boyutu.  
  
 `pcVars`  
 dışı Değişkenine döndürülen değişken sayısını alan bir işaretçi `pVars` .  
  
 `pVars`  
 dışı Değişkenleri alan değişkene yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedReader Arabirimi](isymunmanagedreader-interface.md)
