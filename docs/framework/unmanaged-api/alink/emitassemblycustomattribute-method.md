---
description: 'Şu konuda daha fazla bilgi edinin: Emıtassemblycustomattribute yöntemi'
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
ms.openlocfilehash: c91eb563c14b442a22db8f328287c10e5cc9a63c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638333"
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
 Özniteliği olan dosyayı kaldırır. `AssemblyID`İlişkisiz bir netmodule BELIRTMEZSE null olabilir.  
  
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
