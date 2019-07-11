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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d305aa59c1b9e9e1225b30f12e36fc689d584db1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778890"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA Metodu
Göreli sanal adres (RVA) ve yöntem veya belirtilen belirteci tarafından temsil edilen alan uygulama bayraklarını alır.  
  
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
 [in] İçin RVA döndürmek için kod nesneyi temsil eden bir MethodDef veya fieldDef simgesi meta veri belirteci. Bir fieldDef simgesi belirteci ise alan genel bir değişken olmalıdır.  
  
 `pulCodeRVA`  
 [out] Göreli sanal adres belirteci tarafından temsil edilen kod nesnenin bir işaretçi.  
  
 `pdwImplFlags`  
 [out] Uygulama bayrakları yöntemi için bir işaretçi. Gelen bir bit maskesi değerdir [Cormethodımpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) sabit listesi. Değerini `pdwImplFlags` geçerli yalnızca `tk` MethodDef belirtecidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
