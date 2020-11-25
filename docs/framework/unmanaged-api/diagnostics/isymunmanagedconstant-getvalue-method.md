---
title: ISymUnmanagedConstant::GetValue Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
ms.openlocfilehash: 7a1c795f4a162699078e91bcaa274253169234e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732846"
---
# <a name="isymunmanagedconstantgetvalue-method"></a>ISymUnmanagedConstant::GetValue Metodu

Sabitin değerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pValue`  
 dışı Değeri alan bir değişkene yönelik işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedConstant Arabirimi](isymunmanagedconstant-interface.md)
- [GetName Yöntemi](isymunmanagedconstant-getname-method.md)
- [GetSignature Metodu](isymunmanagedconstant-getsignature-method.md)
