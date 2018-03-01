---
title: IMetaDataImport::GetFieldProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7785ea6beaa882e72d200ef559ba75538224091d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps Metodu
Belirtilen fieldDef simgesi tarafından başvurulan alanıyla ilişkili meta verileri belirtecini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `mb`  
 [in] İlişkili meta verileri almak için alanını temsil eden bir fieldDef simgesi belirteci.  
  
 `pClass`  
 [out] Alanın ait sınıf türünü temsil eden bir TypeDef belirteci için bir işaretçi.  
  
 `szField`  
 [out] Alanın adı.  
  
 `cchField`  
 [in] Geniş karakterler için arabellek boyutu *szField*.  
  
 `pchField`  
 [out] Döndürülen arabellek gerçek boyutu.  
  
 `pdwAttr`  
 [out] Alanın meta verileriyle ilişkili bayraklar.  
  
 `ppvSigBlob`  
 [in] Alan açıklar ikili meta veri değeri için bir işaretçi.  
  
 `pcbSigBlob`  
 [out] Bayt cinsinden boyutu `ppvSigBlob`.  
  
 `pdwCPlusTypeFlag`  
 [out] Alan değeri türünü belirten bir bayrak.  
  
 `ppValue`  
 [out] Alan için sabit bir değer.  
  
 `pcchValue`  
 [out] Karakter boyutu `ppValue`, veya dize varsa sıfır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
