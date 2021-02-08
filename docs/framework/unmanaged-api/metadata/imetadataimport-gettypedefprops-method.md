---
description: ': IMetaDataImport:: GetTypeDefProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: da5c6117f636098ed0cfeddc541979d235729d63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799284"
---
# <a name="imetadataimportgettypedefprops-method"></a>IMetaDataImport::GetTypeDefProps Yöntemi

<xref:System.Type>Belirtilen typedef belirteci tarafından temsil edilen için meta veri bilgilerini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
