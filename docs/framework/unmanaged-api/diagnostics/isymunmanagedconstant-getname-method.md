---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedconstant:: GetName Yöntemi'
title: ISymUnmanagedConstant::GetName Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
ms.openlocfilehash: 57531711ed60c9e35e749a3cb1f1ba5d5c48ca66
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689826"
---
# <a name="isymunmanagedconstantgetname-method"></a>ISymUnmanagedConstant::GetName Yöntemi

Sabitin adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cchName`  
 'ndaki `szName` Parametrenin işaret ettiği arabelleğin uzunluğu.  
  
 `pcchName`  
 dışı `ULONG32` Null sonlandırma dahil olmak üzere, adı içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.  
  
 `szName`  
 dışı Adı depolayan arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedConstant Arabirimi](isymunmanagedconstant-interface.md)
- [GetSignature Metodu](isymunmanagedconstant-getsignature-method.md)
- [GetValue Yöntemi](isymunmanagedconstant-getvalue-method.md)
