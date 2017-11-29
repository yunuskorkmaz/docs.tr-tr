---
title: IMetaDataImport::GetMethodProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMethodProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d02369f1e401f49548f4fdb0fc177dc7403654d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
