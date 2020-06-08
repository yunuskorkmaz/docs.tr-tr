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
ms.openlocfilehash: 320cfae93f8aae94f9315e8e20ed6cf7f9cced7c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491322"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a>IMetaDataImport::GetCustomAttributeProps Metodu
Meta veri belirteci verilen özel özniteliğin değerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 [Out, isteğe bağlı] Özel özniteliğin değiştirdiği nesneyi temsil eden bir meta veri belirteci. Bu değer, hariç herhangi bir tür meta veri belirteci olabilir `mdCustomAttribute` .  
  
 `ptkType`  
 [Out, isteğe bağlı] `mdMethodDef` `mdMemberRef` Döndürülen özel özniteliği temsil eden bir veya meta veri belirteci <xref:System.Type> .  
  
 `ppBlob`  
 [Out, isteğe bağlı] Özel özniteliğin değeri olan bir veri dizisine yönelik bir işaretçi.  
  
 `pcbSize`  
 [Out, isteğe bağlı] * ' De döndürülen verilerin bayt cinsinden boyutu `ppBlob` .  
  
## <a name="remarks"></a>Açıklamalar  
 Özel bir öznitelik, veri dizisi olarak, meta veri altyapısı tarafından anlaşılabilecek biçimde depolanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
