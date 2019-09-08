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
ms.openlocfilehash: 77d54f6c8f67dda5132518d1fbd579a91ce82071
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777447"
---
# <a name="emitassemblycustomattribute-method"></a>EmitAssemblyCustomAttribute Yöntemi
Derleme düzeyi özel özniteliklerini ayarlama çağrısı.  
  
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
 Derlemenin KIMLIĞI.  
  
 `FileToken`  
 Özniteliği olan dosyayı kaldırır. İlişkisiz bir netmodule belirtmezse `AssemblyID` null olabilir.  
  
 `tkType`  
 Özel özniteliğin türü.  
  
 `pCustomValue`  
 Özel değer verileri.  
  
 `cbCustomValue`  
 Özel değer verisinin uzunluğu.  
  
 `bSecurity`  
 Özel öznitelik, derleme imzalama ile ilgiliyse TRUE.  
  
 `bAllowMulti`  
 Birden çok öznitelik yayınlandıysanız TRUE.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink. h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
