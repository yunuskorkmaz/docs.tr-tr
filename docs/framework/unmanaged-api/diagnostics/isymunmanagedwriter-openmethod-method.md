---
title: "ISymUnmanagedWriter::OpenMethod Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6cfb41748861150b28493c835e80135abe90826
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriteropenmethod-method"></a>ISymUnmanagedWriter::OpenMethod Yöntemi
Hangi sembolün bilgi yayılan bir yöntem açar. Belirtilen yöntem geçerli yöntem sıralama noktaları, parametreleri ve sözcük kapsamları tanımlamak çağrıları için olur. Tüm yöntemi geçici örtük bir sözcük kapsamı yok. Daha önce kapatıldı bir yöntem açmayı bu yöntem için önceden tanımlanmış semboller siler. Aynı anda yalnızca bir açık yöntemi olabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `method`  
 [in] Yöntemin açılması meta veri simgesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [CloseMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)  
 [OpenMethod2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
