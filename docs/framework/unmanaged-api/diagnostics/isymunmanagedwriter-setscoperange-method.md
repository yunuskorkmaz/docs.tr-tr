---
title: "ISymUnmanagedWriter::SetScopeRange Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9afb0038adc4273033fb9f1db1ebc57f43eae779
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritersetscoperange-method"></a>ISymUnmanagedWriter::SetScopeRange Yöntemi
Belirtilen sözcük kapsamı için uzaklık aralığını tanımlar. Kapsam yeni geçerli kapsam haline gelir ve kapsamları yığına gönderilir. Kapsamları bir hiyerarşi oluşturması gerekir. Eşdüzey çakışma izin verilmiyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `scopeId`  
 [in] Kapsam için kapsam tanımlayıcısı.  
  
 `startOffset`  
 [in] Başlangıçtan itibaren sözcük kapsamdaki ilk yönergenin yönteminin bayt uzaklığı.  
  
 `endOffset`  
 [in] Başlangıçtan itibaren sözcük kapsamdaki son yönergenin yönteminin bayt uzaklığı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  
 [Isymunmanagedwriter::openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) ile kullanılan donuk kapsam tanımlayıcıyı döndürür `ISymUnmanagedWriter::SetScopeRange` bir kapsamını tanımlamak için başlangıç ve bitiş uzaklığı daha sonra. Uzaklık bu durumda, geçirilen `ISymUnmanagedWriter::OpenScope` ve [Isymunmanagedwriter::closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) göz ardı edilir. Kapsam yalnızca geçerli yönteminde geçerli tanımlayıcılardır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
