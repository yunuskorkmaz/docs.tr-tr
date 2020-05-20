---
title: ISymUnmanagedWriter::DefineField Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
ms.openlocfilehash: aba551a1973a41a909869316cda07e8d655e9882
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614844"
---
# <a name="isymunmanagedwriterdefinefield-method"></a>ISymUnmanagedWriter::DefineField Yöntemi
Bir yöntem içinde olmayan tek bir değişkeni tanımlar. Bu yöntem, sınıflardaki belirli alanlar, bit alanları vb. için kullanılır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>Parametreler  
 `parent`  
 'ndaki Meta veri türü veya yöntem belirteci.  
  
 `name`  
 'ndaki Alan adı.  
  
 `attributes`  
 'ndaki Alan öznitelikleri.  
  
 `cSig`  
 'ndaki `ULONG32`Bu, alan imzasını içermesi için gereken arabelleğin karakter cinsinden boyutudur.  
  
 `signature`  
 'ndaki Alan imzalarının dizisi.  
  
 `addrKind`  
 'ndaki Adres türü.  
  
 `addr1`  
 'ndaki Alan belirtiminin ilk adresi.  
  
 `addr2`  
 'ndaki Alan belirtiminin ikinci adresi.  
  
 `addr3`  
 'ndaki Alan belirtiminin üçüncü adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
