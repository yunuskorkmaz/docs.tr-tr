---
title: ISymUnmanagedENCUpdate::GetLocalVariables Metodu
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
ms.openlocfilehash: 82e657e91e586d7fe409646ea4fb8946c026e84c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424345"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a>ISymUnmanagedENCUpdate::GetLocalVariables Metodu
Yerel değişkenler alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `mdMethodToken`  
 [in] Yönteminin meta veri simgesi.  
  
 `cLocals`  
 [in] A `ULONG` boyutunu gösterir `rgLocals` parametresi.  
  
 `rgLocals`  
 [out] Döndürülen dizi <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable` örnekleri.  
  
 `pceltFetched`  
 [out] Bir işaretçi bir `ULONG` boyutunu alır `rgLocals` arabellek Yereller içermesi gerekir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedENCUpdate Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
