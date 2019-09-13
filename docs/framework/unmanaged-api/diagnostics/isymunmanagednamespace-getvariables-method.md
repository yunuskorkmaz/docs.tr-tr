---
title: ISymUnmanagedNamespace::GetVariables Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 813f57377c1885b09190ada3c73f4391a3f2d931
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895054"
---
# <a name="isymunmanagednamespacegetvariables-method"></a>ISymUnmanagedNamespace::GetVariables Metodu
Bu ad alanı içinde genel kapsamda tanımlanan tüm değişkenleri döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cVars`  
 'ndaki Dizi`pVars` boyutunu belirten bir `ULONG32` .  
  
 `pcVars`  
 dışı Ad alanlarını içermesi için `ULONG32` gereken arabellek boyutunu alan bir işaretçisi.  
  
 `pVars`  
 dışı Ad alanlarını içeren bir arabelleğin işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAıL veya diğer bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedNamespace Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
