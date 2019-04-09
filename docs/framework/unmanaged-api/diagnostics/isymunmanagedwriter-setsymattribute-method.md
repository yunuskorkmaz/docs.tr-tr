---
title: ISymUnmanagedWriter::SetSymAttribute Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8ffcc3a079e7e9a9d69622dc6666bb0e7641d4e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155473"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a>ISymUnmanagedWriter::SetSymAttribute Yöntemi
Adını alan özel bir öznitelik tanımlar. Bu öznitelikler, sembol deposundaki özel meta veri öznitelikleri aksine tutulur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `parent`  
 [in] Öznitelik tanımlanmakta olan meta veri belirteci.  
  
 `name`  
 [in] Bir işaretçi bir `WCHAR` , öznitelik adı içerir.  
  
 `cData`  
 [in] A `ULONG32` boyutunu gösteren `data` dizisi.  
  
 `data`  
 [in] Öznitelik değeri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
