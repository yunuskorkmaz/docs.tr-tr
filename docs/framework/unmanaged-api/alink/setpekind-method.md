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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5fe770ffc5a9c187e9069e8a66553976f9a53b2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709890"
---
# <a name="setpekind-method"></a>SetPEKind Yöntemi
Taşınabilir yürütülebilir türü, makineye özgü veya makine geçişte sorun yaşamaz belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
#### <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Derleme kimliği.  
  
 `FileToken`  
 Dosyanın PE türü ayarlanacak olduğu belirteci. NULL olabilir `AssemblyID` ilişkisiz bir netmodule göstermez.  
  
 `dwPEKind`  
 Türü tarafından belirtildiği şekilde PE [CorPEKind numaralandırması](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).  
  
 `dwMachine`  
 NT başlığında belirtildiği gibi hedef makine mimarisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [GetPEKind Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)
- [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
