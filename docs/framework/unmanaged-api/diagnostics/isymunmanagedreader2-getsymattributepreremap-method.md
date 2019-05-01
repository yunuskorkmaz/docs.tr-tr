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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 543a8015e944333942b619060059273577902a74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986342"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>ISymUnmanagedReader2::GetSymAttributePreRemap Metodu
Özel bir öznitelik adı üzerinde temel alır. Meta veri özel öznitelikleri farklı olarak bu öznitelikler sembol deposundaki tutulur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 [in] Ana meta veri belirteci.  
  
 `name`  
 [in] Bir işaretçi bir `WCHAR` , adı içeriyor.  
  
 `cBuffer`  
 [in] A `ULONG32` boyutunu gösteren `buffer` dizisi.  
  
 `pcBuffer`  
 [out] Bir işaretçi bir `ULONG32` içeren öznitelik bayt için gerekli arabellek boyutunu alır.  
  
 `buffer`  
 [out] Öznitelik bayt alan arabellek için işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedReader2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
