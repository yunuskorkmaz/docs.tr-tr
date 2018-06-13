---
title: ISymUnmanagedWriter::CloseScope Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a11f689f1fa93e1122ffcc78187c4287db7ea534
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427030"
---
# <a name="isymunmanagedwriterclosescope-method"></a>ISymUnmanagedWriter::CloseScope Yöntemi
Geçerli sözcük kapsamı kapatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `endOffset`  
 [in] Sözcük kapsamda bayt son yönergenin sonunda nokta yöntemi başlangıç uzaklığı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir kapsam kapatıldıktan sonra daha fazla değişken içinde tanımlanabilir.  
  
 [Isymunmanagedwriter::openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) ile kullanılan donuk kapsam tanımlayıcıyı döndürür [Isymunmanagedwriter::setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) daha sonra bir kapsamını tanımlamak için başlangıç ve bitiş uzaklığı. Uzaklık bu durumda, geçirilen `ISymUnmanagedWriter::OpenScope` ve `ISymUnmanagedWriter::CloseScope` göz ardı edilir. Kapsam tanımlayıcıları yalnızca geçerli yöntemi geçerli değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
