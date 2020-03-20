---
title: IMetaDataImport::CountEnum Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: b780ca513d8a0b4f88e66594e86e9ff8290f6523
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177357"
---
# <a name="imetadataimportcountenum-method"></a>IMetaDataImport::CountEnum Yöntemi
Belirtilen numaralandırma tarafından alınan numaralandırmadaki öğelerin sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hEnum`  
 [içinde] Tümumeratörün sapı.  
  
 `pulCount`  
 [çıkış] Numaralandırılmış öğelerin sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Tarafından belirtilen `hEnum` tutamaç önceki `Enum`bir *Ad* çağrısından elde edilir (örneğin, [IMetaDataImport::EnumTypeDefs).](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
