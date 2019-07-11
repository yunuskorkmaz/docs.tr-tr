---
title: EmitAssemblyCustomAttribute Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7dfcc2db3f1f0d8646f903fedb1eb06b39928d00
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742126"
---
# <a name="emitassemblycustomattribute-method"></a>EmitAssemblyCustomAttribute Yöntemi
Özel derleme düzeyinde öznitelikler ayarlanacak çağırın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Derleme kimliği.  
  
 `FileToken`  
 Öznitelik defiles dosyası. NULL olabilir `AssemblyID` ilişkisiz bir netmodule göstermez.  
  
 `tkType`  
 Özel özniteliğin türü.  
  
 `pCustomValue`  
 Özel değer verileri.  
  
 `cbCustomValue`  
 Özel değer verisi uzunluğu.  
  
 `bSecurity`  
 Derleme imzalama için özel özniteliği ilişkiliyse TRUE.  
  
 `bAllowMulti`  
 Birden çok öznitelik yayılan gerekiyorsa TRUE.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
