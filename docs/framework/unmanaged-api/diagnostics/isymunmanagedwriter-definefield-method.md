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
ms.openlocfilehash: 5d5b3c60845fce39ce7f904c6871e7feb16e8970
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429820"
---
# <a name="isymunmanagedwriterdefinefield-method"></a>ISymUnmanagedWriter::DefineField Yöntemi
Yöntemi içinde değil tek bir değişken tanımlar. Bu, kullanılan belirli sınıfları alanları, bit alanları ve benzeri yöntemidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
  
#### <a name="parameters"></a>Parametreler  
 `parent`  
 [in] Meta veri türü veya yöntemi belirteci.  
  
 `name`  
 [in] Alan adı.  
  
 `attributes`  
 [in] Alan öznitelikleri.  
  
 `cSig`  
 [in] A `ULONG32` karakterlerinden alan imzası içermesi gerekir arabellek büyüklüğü diğer bir deyişle.  
  
 `signature`  
 [in] Alan imzaları dizisi.  
  
 `addrKind`  
 [in] Adres türü.  
  
 `addr1`  
 [in] İlk adres alanı belirtimi için.  
  
 `addr2`  
 [in] İkinci adres alanı belirtimi için.  
  
 `addr3`  
 [in] Alan belirtimi üçüncü adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
