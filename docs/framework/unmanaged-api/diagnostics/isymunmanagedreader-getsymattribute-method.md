---
title: ISymUnmanagedReader::GetSymAttribute Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 763e698c7149de0fee61770e601032a4160b839f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378580"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a>ISymUnmanagedReader::GetSymAttribute Yöntemi
Özel bir öznitelik adı üzerinde temel alır. Meta veri özel öznitelikleri, bu özel öznitelikler sembol deposu içerisinde tutulur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `parent`  
 [in] Öznitelik istendiği nesnesi için meta veri belirteci.  
  
 `name`  
 [in] Bir işaretçi değişkenine almak için bir özniteliği gösterir.  
  
 `cBuffer`  
 [in] Boyutu `buffer` dizisi.  
  
 `pcBuffer`  
 [out] Bir işaretçi değişkenine özniteliği veri uzunluğunu alır.  
  
 `buffer`  
 [out] Bir işaretçi değişkenine öznitelik verilerini alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ISymUnmanagedReader Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
