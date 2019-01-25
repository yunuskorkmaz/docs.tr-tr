---
title: Init Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 315ddf89d9c0653f357490dc31986dc302024622
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662653"
---
# <a name="init-method"></a>Init Yöntemi
Uygulama nesneleri hazırlar [Ialink arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) kullanmak için.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pDispenser`  
 [Imetadatadispenserex arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) meta verileri dağıtıcısı için işaretçi.  
  
 `pErrorHandler`  
 [Imetadataerror arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) işleme arabirimini hatayla isteğe bağlı işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
