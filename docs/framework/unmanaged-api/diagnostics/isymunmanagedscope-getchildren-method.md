---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedscope:: GetChildren Yöntemi'
title: ISymUnmanagedScope::GetChildren Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
ms.openlocfilehash: 55d72c98d34fcb30a479611895228fbc1b9f7f55
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763507"
---
# <a name="isymunmanagedscopegetchildren-method"></a>ISymUnmanagedScope::GetChildren Metodu

Bu kapsamın alt öğelerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cChildren`  
 'ndaki `ULONG32` Dizi boyutunu belirten bir `children` .  
  
 `pcChildren`  
 dışı `ULONG32` Alt öğeleri içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.  
  
 `children`  
 dışı Döndürülen alt öğe dizisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedScope Arabirimi](isymunmanagedscope-interface.md)
- [GetParent Yöntemi](isymunmanagedscope-getparent-method.md)
