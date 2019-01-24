---
title: ISymUnmanagedWriter::DefineDocument Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d1c214918b4a41ac989a3804c9146c4a54c5909f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738215"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a>ISymUnmanagedWriter::DefineDocument Yöntemi
Kaynak belge tanımlar. GUID'ler, bilinen diller, satıcılar ve belge türü için sağlanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `url`  
 [in] Bir işaretçi bir `WCHAR` belgenin tanımlar Tekdüzen Kaynak Konum Belirleyicisi (URL) tanımlar.  
  
 `language`  
 [in] Belge dili tanımlayan bir GUID için bir işaretçi.  
  
 `languageVendor`  
 [in] Belge dili satıcısının kimliğini tanımlayan bir GUID için bir işaretçi.  
  
 `documentType`  
 [in] Belge türünü tanımlayan bir GUID için bir işaretçi.  
  
 `pRetVal`  
 [out] Döndürülen işaretçi [Isymunmanagedwriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) arabirimi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
