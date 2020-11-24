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
ms.openlocfilehash: be8a11cbf70e2c6f19ace67648b124515c1fb3c3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680046"
---
# <a name="setpekind-method"></a>SetPEKind Yöntemi

Taşınabilir yürütülebilir türü, makineye özgü veya makine belirsiz olarak belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 Derlemenin KIMLIĞI.  
  
 `FileToken`  
 PE türü ayarlanacak dosyanın belirteci. `AssemblyID`İlişkisiz bir netmodule BELIRTMEZSE null olabilir.  
  
 `dwPEKind`  
 [CorPEKind numaralandırması](../metadata/corpekind-enumeration.md)tarafından BELIRTILDIĞI gibi PE türü.  
  
 `dwMachine`  
 NT üstbilgisinde gösterildiği gibi hedef makine mimarisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetPEKind Yöntemi](../metadata/imetadataimport2-getpekind-method.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [IALink Arabirimi](ialink-interface.md)
- [ALink API](index.md)
