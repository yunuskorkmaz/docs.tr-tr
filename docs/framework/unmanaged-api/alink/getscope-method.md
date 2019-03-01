---
title: GetScope Metodu
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c5798fc488cf4453b6abcf00a7169b1ec0b529ec
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965377"
---
# <a name="getscope-method"></a>GetScope Metodu
Bir içeri aktarma kapsamı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Derleme için alınacak benzersiz kimliği.  
  
 `FileToken`  
 Alınacak benzersiz kimliği dosyanın.  
  
 `dwScope`  
 İçeri aktarmak için sıfır tabanlı kapsam.  
  
 `ppImportScope`  
 Alan [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) kapsam için arabirim.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
