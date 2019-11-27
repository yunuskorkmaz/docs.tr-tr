---
title: GetResolutionScope Metodu
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
ms.openlocfilehash: f2b78b35db6306c82e389955c4824875bcf25334
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447229"
---
# <a name="getresolutionscope-method"></a>GetResolutionScope Metodu
Verilen bir türün kapsamını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Derlemenin KIMLIĞI.  
  
 `FileToken`  
 Bir başvuru gerektiren dosya.  
  
 `TargetFile`  
 Türü tanımlanmış, genellikle [ImportFile yöntemiyle](importfile-method.md)alınan dosyanın belirteci.  
  
 `pScope`  
 Derlemeyi veya modül başvurusunu alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
