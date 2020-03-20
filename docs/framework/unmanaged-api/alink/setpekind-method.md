---
title: SetPEKind Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: 5a8442b1f0869e1592a05dfeeb0f5e6d583f3ea8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179384"
---
# <a name="setpekind-method"></a>SetPEKind Yöntemi
Makineye özgü veya makineye özgü taşınabilir çalıştırılabilir türünü belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Derlemenin kimliği.  
  
 `FileToken`  
 PE türünün ayarlanabilmek için dosya belirteci. Bağlanmamış bir `AssemblyID` ağ modül belirtmezise NULL olabilir.  
  
 `dwPEKind`  
 [CorPEKind Numaralandırma](../metadata/corpekind-enumeration.md)da belirtildiği gibi PE türü.  
  
 `dwMachine`  
 Hedef makine mimarisi, NT üstbilgisinde belirtildiği gibi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 Alink.h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetPEKind Metodu](../metadata/imetadataimport2-getpekind-method.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [IALink Arabirimi](ialink-interface.md)
- [ALink API](index.md)
