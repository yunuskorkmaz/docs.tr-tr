---
title: ISymUnmanagedVariable::GetAddressField3 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
ms.openlocfilehash: 13746c4ac6322a401e547c1c7acc99c0eda9accf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723343"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a>ISymUnmanagedVariable::GetAddressField3 Yöntemi

Bu değişken için üçüncü adres alanını alır. Bunun anlamı, adresin türüne bağlıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pRetVal`  
 dışı `ULONG32` Üçüncü adres alanını alan bir işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedVariable Arabirimi](isymunmanagedvariable-interface.md)
- [GetAddressField1 Yöntemi](isymunmanagedvariable-getaddressfield1-method.md)
- [GetAddressField2 Yöntemi](isymunmanagedvariable-getaddressfield2-method.md)
- [GetAddressKind Yöntemi](isymunmanagedvariable-getaddresskind-method.md)
