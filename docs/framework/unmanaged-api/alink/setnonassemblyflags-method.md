---
title: SetNonAssemblyFlags Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
ms.openlocfilehash: 2dcb363a2a84b3c2e0438e45663b96d9a0f83f61
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445546"
---
# <a name="setnonassemblyflags-method"></a>SetNonAssemblyFlags Yöntemi
Sets flags that are not assembly-specific.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  
 `afFlags`  
 ALink flags.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>Gereksinimler  
 Requires alink.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
