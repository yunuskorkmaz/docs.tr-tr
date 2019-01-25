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
ms.openlocfilehash: 12adffbfeb2ce6271774cf44c1a913d7a1414ba4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718617"
---
# <a name="imetadataimportgettypedefprops-method"></a>IMetaDataImport::GetTypeDefProps Metodu
Meta veri bilgilerini döndürür <xref:System.Type> belirtilen TypeDef belirteci tarafından temsil edilir.  
  
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
 [in] TypeDef belirteç meta verileri için dönüş türü temsil eder.  
  
 `szTypeDef`  
 [out] Tür adı içeren bir arabelleği.  
  
 `cchTypeDef`  
 [in] Geniş karakter cinsinden boyutu `szTypeDef`.  
  
 `pchTypeDef`  
 [out] Döndürülen geniş karakter sayısını `szTypeDef`.  
  
 `pdwTypeDefFlags`  
 [out] Tür tanımını değiştiren bayrakları için bir işaretçi. Gelen bir bit maskesi değerdir [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) sabit listesi.  
  
 `ptkExtends`  
 [out] İstenen türün temel türünü temsil eden bir tür tanımı veya TypeRef meta veri belirteci.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
