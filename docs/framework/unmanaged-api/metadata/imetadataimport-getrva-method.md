---
title: IMetaDataImport::GetRVA Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: 190bcacc84646cfd9294cf2b6b53b0474f38758f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177209"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA Metodu
Belirtilen belirteç tarafından temsil edilen yöntem veya alanın göreli sanal adresi (RVA) ve uygulama bayraklarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tk`  
 [içinde] RVA'yı döndürecek kod nesnesini temsil eden bir MethodDef veya FieldDef meta veri belirteci. Belirteç bir FieldDef ise, alan küresel bir değişken olmalıdır.  
  
 `pulCodeRVA`  
 [çıkış] Belirteç tarafından temsil edilen kod nesnesinin göreli sanal adresine işaretçi.  
  
 `pdwImplFlags`  
 [çıkış] Yöntem için uygulama bayrakları için bir işaretçi. Bu değer [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) numaralandırma bir bitmask olduğunu. Değeri `pdwImplFlags` yalnızca Bir MethodDef belirteci ise `tk` geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
