---
title: ISymUnmanagedVariable::GetAddressKind Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18e83582a73ba3b2eb2538bcdf60984c46131768
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426961"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a>ISymUnmanagedVariable::GetAddressKind Metodu
Bu değişkenin adres türünü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 [out] Bir işaretçi bir `ULONG32` değerini alır. Olası değerler tanımlanan [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) numaralandırması.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedVariable Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
