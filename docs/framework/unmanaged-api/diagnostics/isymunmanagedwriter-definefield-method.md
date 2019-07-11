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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37794d40b4b379c5d3a05935cf1f2b7b3da11baa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777371"
---
# <a name="isymunmanagedwriterdefinefield-method"></a>ISymUnmanagedWriter::DefineField Yöntemi
Bir yöntem içinde değil tek bir değişkeni tanımlar. Bu, kullanılan belirli alanları sınıflarda, bit alanları ve benzeri yöntemidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 [in] Meta veri türünde veya yönteminde ' belirteci.  
  
 `name`  
 [in] Alan adı.  
  
 `attributes`  
 [in] Alan öznitelikleri.  
  
 `cSig`  
 [in] A `ULONG32` alan imzası içermesi gereken arabelleğin karakter cinsinden boyutu diğer bir deyişle.  
  
 `signature`  
 [in] Alan imzaları dizisi.  
  
 `addrKind`  
 [in] Adres türü.  
  
 `addr1`  
 [in] İlk adres alanı belirtimi için.  
  
 `addr2`  
 [in] İkinci bir adres alanı belirtimi için.  
  
 `addr3`  
 [in] Üçüncü adres alanı belirtimi için.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
