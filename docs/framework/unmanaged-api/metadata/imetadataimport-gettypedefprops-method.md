---
title: IMetaDataImport::GetTypeDefProps Metodu
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa69eda974187748d7046c792fa16b7729e3deff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446888"
---
# <a name="imetadataimportgettypedefprops-method"></a>IMetaDataImport::GetTypeDefProps Metodu
Meta veri bilgilerini döndürür <xref:System.Type> belirtilen TypeDef belirteç tarafından temsil edilen.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `td`  
 [in] Meta veriler için dönüş türü temsil eder TypeDef simgesi.  
  
 `szTypeDef`  
 [out] Tür adını içeren bir arabellek.  
  
 `cchTypeDef`  
 [in] Geniş karakter cinsinden boyutu `szTypeDef`.  
  
 `pchTypeDef`  
 [out] Döndürülen geniş karakter sayısını `szTypeDef`.  
  
 `pdwTypeDefFlags`  
 [out] Tür tanımı değiştirme bayrakları gösteren bir işaretçi. Bu değer gelen bir bit maskesi olan [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) numaralandırması.  
  
 `ptkExtends`  
 [out] İstenen türün temel türünü temsil eden bir TypeDef veya TypeRef meta veri simgesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
