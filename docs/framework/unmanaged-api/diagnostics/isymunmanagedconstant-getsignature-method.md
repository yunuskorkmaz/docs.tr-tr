---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedconstant:: GetSignature Yöntemi'
title: ISymUnmanagedConstant::GetSignature Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
ms.openlocfilehash: d28051c9d0e2675e980926fe63ffa7c4d13ef13a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689800"
---
# <a name="isymunmanagedconstantgetsignature-method"></a>ISymUnmanagedConstant::GetSignature Yöntemi

Sabitin imzasını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cSig`  
 'ndaki `pcSig` Parametrenin işaret ettiği arabelleğin uzunluğu.  
  
 `pcSig`  
 dışı `ULONG32` İmzayı içermesi için gereken arabelleğin boyutunu, karakter cinsinden alan bir işaretçisi.  
  
 `sig`  
 dışı İmzayı depolayan arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedConstant Arabirimi](isymunmanagedconstant-interface.md)
- [GetName Yöntemi](isymunmanagedconstant-getname-method.md)
- [GetValue Yöntemi](isymunmanagedconstant-getvalue-method.md)
