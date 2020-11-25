---
title: ISymUnmanagedVariable::GetStartOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
ms.openlocfilehash: 68d20c33c5ccd554554cae57ee55f6f51d5d980c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733314"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a>ISymUnmanagedVariable::GetStartOffset Yöntemi

Bu değişkenin üst öğesi içindeki başlangıç sapmasını alır. Bu bir kapsamdaki yerel değişkense, başlangıç boşluğu kapsam için tanımlanan uzaklıklara girer.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pRetVal`  
 dışı Başlangıç sapmasını alan bir işaretçisine bir işaretçisi `ULONG32` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedVariable Arabirimi](isymunmanagedvariable-interface.md)
- [GetEndOffset Yöntemi](isymunmanagedvariable-getendoffset-method.md)
