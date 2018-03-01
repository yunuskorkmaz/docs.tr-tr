---
title: ISymUnmanagedReader2::GetSymAttributePreRemap Metodu
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4a9e2304e746578fbe0e7a5c4d1b0ef1f1c8a1b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>ISymUnmanagedReader2::GetSymAttributePreRemap Metodu
Adını dayalı özel bir öznitelik alır. Meta veri özel öznitelikler farklı olarak bu öznitelikler simgesi deposunda tutulur.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `parent`  
 [in] Üst meta veri simgesi.  
  
 `name`  
 [in] Bir işaretçi bir `WCHAR` adı içeriyor.  
  
 `cBuffer`  
 [in] A `ULONG32` boyutunu gösterir `buffer` dizi.  
  
 `pcBuffer`  
 [out] Bir işaretçi bir `ULONG32` özniteliği bayt içermesi gerekir arabellek boyutunu alır.  
  
 `buffer`  
 [out] Öznitelik bayt alır arabellek için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedReader2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
