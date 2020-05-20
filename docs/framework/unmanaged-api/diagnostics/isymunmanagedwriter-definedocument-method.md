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
ms.openlocfilehash: fdcfb0c4f9c21eb516f4196d0c8f682669468219
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615234"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a>ISymUnmanagedWriter::DefineDocument Yöntemi
Bir kaynak belge tanımlar. GUID 'Ler, bilinen diller, satıcılar ve belge türleri için sağlanır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a>Parametreler  
 `url`  
 'ndaki `WCHAR`Belgeyi tanımlayan Tekdüzen Kaynak Konumlandırıcı 'sını (URL) tanımlayan bir işaretçisi.  
  
 `language`  
 'ndaki Belge dilini tanımlayan bir GUID işaretçisi.  
  
 `languageVendor`  
 'ndaki Belge dili için satıcının kimliğini tanımlayan bir GUID işaretçisi.  
  
 `documentType`  
 'ndaki Belge türünü tanımlayan GUID için bir işaretçi.  
  
 `pRetVal`  
 dışı Döndürülen [ıdimunmanagedwriter](isymunmanagedwriter-interface.md) arabirimine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
