---
title: IMetaDataImport::GetTypeDefProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeDefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1025ffde2bd066c81c4c562c0dd86e829fc2aef3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
