---
title: ISymUnmanagedENCUpdate::GetLocalVariables Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16e91a0c748e5b148e79dc73cf213b03c68c5021
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939730"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a>ISymUnmanagedENCUpdate::GetLocalVariables Yöntemi
Yerel değişkenlerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mdMethodToken`  
 [in] Yöntemin meta veri belirteci.  
  
 `cLocals`  
 [in] A `ULONG` boyutunu gösteren `rgLocals` parametresi.  
  
 `rgLocals`  
 [out] Döndürülen dizi [Isymunmanagedvariable](isymunmanagedvariable-interface.md) örnekleri.  
  
 `pceltFetched`  
 [out] Bir işaretçi bir `ULONG` boyutunu alır `rgLocals` arabellek yerel öğeler içermesi gerekir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedENCUpdate Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
