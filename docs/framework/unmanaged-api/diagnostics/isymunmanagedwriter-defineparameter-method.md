---
title: ISymUnmanagedWriter::DefineParameter Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b552ef39c7f73aaa5cfeae4a313e329b267abf98
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643396"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a>ISymUnmanagedWriter::DefineParameter Yöntemi
Tek bir parametre, geçerli yöntemi tanımlar. Parametre türü yöntemin imzasını içinde parametrenin konumu (sıra) alınmıştır.  
  
 Parametreler için belirli bir yöntemin meta verilerindeki tanımlanmışsa, bu yöntemi kullanarak bunları yeniden tanımlamanız gerekmez. Sembol okuyucu parametreleri için normal meta veriler, sembol deposuna iade etmeden önce işaretlemeniz gerekir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `name`  
 [in] Parametre adı.  
  
 `attributes`  
 [in] Parametre öznitelikleri.  
  
 `sequence`  
 [in] Parametre imzası.  
  
 `addrKind`  
 [in] Adres türü.  
  
 `addr1`  
 [in] Parametre belirtimine ilk adresi.  
  
 `addr2`  
 [in] Parametre belirtimine ikinci adresi.  
  
 `addr3`  
 [in] Parametre belirtimine üçüncü adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
