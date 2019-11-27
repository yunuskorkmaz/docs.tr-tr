---
title: IMetaDataImport::GetCustomAttributeProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
ms.openlocfilehash: 9a80336db4a5a8d7cfdebb7eb8d25bcb8f96e87c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437640"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a>IMetaDataImport::GetCustomAttributeProps Metodu
Meta veri belirteci verilen özel özniteliğin değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cv`  
 'ndaki Alınacak özel özniteliği temsil eden bir meta veri belirteci.  
  
 `ptkObj`  
 [Out, isteğe bağlı] Özel özniteliğin değiştirdiği nesneyi temsil eden bir meta veri belirteci. Bu değer, `mdCustomAttribute`hariç herhangi bir tür meta veri belirteci olabilir.  
  
 `ptkType`  
 [Out, isteğe bağlı] Döndürülen özel özniteliğin <xref:System.Type> temsil eden bir `mdMethodDef` veya `mdMemberRef` meta veri belirteci.  
  
 `ppBlob`  
 [Out, isteğe bağlı] Özel özniteliğin değeri olan bir veri dizisine yönelik bir işaretçi.  
  
 `pcbSize`  
 [Out, isteğe bağlı] *`ppBlob`döndürülen verilerin bayt cinsinden boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 Özel bir öznitelik, veri dizisi olarak, meta veri altyapısı tarafından anlaşılabilecek biçimde depolanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
