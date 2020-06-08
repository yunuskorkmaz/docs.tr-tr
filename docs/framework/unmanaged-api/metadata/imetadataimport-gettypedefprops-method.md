---
title: IMetaDataImport::GetTypeDefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
ms.openlocfilehash: 6346b1e34e508e5c173bfd0119ac7451d7eef40e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490802"
---
# <a name="imetadataimportgettypedefprops-method"></a>IMetaDataImport::GetTypeDefProps Yöntemi
<xref:System.Type>Belirtilen typedef belirteci tarafından temsil edilen için meta veri bilgilerini döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 'ndaki Meta verilerini döndürecek türü temsil eden TypeDef belirteci.  
  
 `szTypeDef`  
 dışı Tür adını içeren bir arabellek.  
  
 `cchTypeDef`  
 'ndaki Öğesinin geniş karakterdeki boyutu `szTypeDef` .  
  
 `pchTypeDef`  
 dışı İçinde döndürülen geniş karakter sayısı `szTypeDef` .  
  
 `pdwTypeDefFlags`  
 dışı Tür tanımını değiştiren bayrakların bir işaretçisi. Bu değer [CorTypeAttr](cortypeattr-enumeration.md) numaralandırmasından bir bit dır.  
  
 `ptkExtends`  
 dışı İstenen türün temel türünü temsil eden bir TypeDef veya TypeRef meta veri belirteci.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
