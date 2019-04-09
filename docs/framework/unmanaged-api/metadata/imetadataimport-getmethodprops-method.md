---
title: IMetaDataImport::GetMethodProps Yöntemi
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
ms.openlocfilehash: c61931f5f6a4bbbf66446d68b0d1b2d1df958a66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137929"
---
# <a name="imetadataimportgetmethodprops-method"></a>IMetaDataImport::GetMethodProps Yöntemi
Belirtilen MethodDef tarafından başvurulan yöntemi ile ilişkili meta veri belirteci alır.  
  
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
  
## <a name="parameters"></a>Parametreler  
 `mb`  
 [in] Meta verileri döndürmek için yöntemin temsil eden MethodDef belirteci.  
  
 `pClass`  
 [out] Yöntemi uygulayan türü temsil eden bir tür tanımı belirteci için bir işaretçi.  
  
 `szMethod`  
 [out] Yöntemin adı olan bir arabellek için bir işaretçi.  
  
 `cchMethod`  
 [in] İstenen boyutu `szMethod`.  
  
 `pchMethod`  
 [out] Geniş karakter cinsinden boyutu işaretçi `szMethod`, ya da söz konusu olduğunda kesilmesi, yöntem adı geniş karakter gerçek sayısı.  
  
 `pdwAttr`  
 [out] Yöntemiyle ilişkili bayrakları için bir işaretçi.  
  
 `ppvSigBlob`  
 [out] İkili meta veri imzası yöntem bir işaretçi.  
  
 `pcbSigBlob`  
 [out] Bayt cinsinden boyutu işaretçi `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Göreli sanal adres yönteminin bir işaretçi.  
  
 `pdwImplFlags`  
 [out] Herhangi bir uygulama bayrağı yöntemi için bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
