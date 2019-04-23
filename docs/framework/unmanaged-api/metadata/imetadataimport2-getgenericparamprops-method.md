---
title: IMetaDataImport2::GetGenericParamProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 55a765fe3942cbf71a8460187e829dc7f3ca877e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082342"
---
# <a name="imetadataimport2getgenericparamprops-method"></a>IMetaDataImport2::GetGenericParamProps Yöntemi
Belirtilen belirteç tarafından temsil edilen genel parametre ile ilişkili meta verileri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `gp`  
 [in] Genel parametre meta verileri döndürülecek temsil eden belirteç.  
  
 `pulParamSeq`  
 [out] Sıralı konumunu `Type` üst Oluşturucusu veya yöntem parametresi.  
  
 `pdwParamFlags`  
 [out] Değerini [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) açıklayan sabit listesi `Type` genel parametresi için.  
  
 `ptOwner`  
 [out] Parametre sahibi temsil eden bir tür tanımı veya MethodDef belirteci.  
  
 `reserved`  
 [out] Sonra genişletilebilmek için ayrılmış.  
  
 `wzName`  
 [out] Genel parametre adı.  
  
 `cchName`  
 [in] Boyutu `wzName` arabellek.  
  
 `pchName`  
 [out] Geniş karakterler, adı döndürülen boyutu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
