---
title: IMetaDataImport::GetMethodProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4037ca42c5a66f075e949cd2035c1e7db510bb8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetmethodprops-method"></a>IMetaDataImport::GetMethodProps Metodu
Belirtilen MethodDef tarafından başvurulan yöntemi ile ilişkili meta veri belirtecini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `mb`  
 [in] Meta verileri döndürmek için yöntemini temsil eden MethodDef belirteci.  
  
 `pClass`  
 [out] Bir işaretçi yöntemi uygulayan türünü temsil eden TypeDef belirteç.  
  
 `szMethod`  
 [out] Yöntemin ada sahip bir arabellek için bir işaretçi.  
  
 `cchMethod`  
 [in] İstenen boyutu `szMethod`.  
  
 `pchMethod`  
 [out] Geniş karakter cinsinden boyutu gösteren bir işaretçi `szMethod`, veya kesme, yöntem adı geniş karakter gerçek sayısını söz konusu olduğunda.  
  
 `pdwAttr`  
 [out] Yöntemiyle ilişkili herhangi bir bayrağı için bir işaretçi.  
  
 `ppvSigBlob`  
 [out] Yönteminin ikili meta verileri imza için bir işaretçi.  
  
 `pcbSigBlob`  
 [out] Bayt cinsinden boyutu gösteren bir işaretçi `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Göreli sanal adres yönteminin bir işaretçi.  
  
 `pdwImplFlags`  
 [out] Herhangi bir uygulama bayrağı yöntemi için bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
