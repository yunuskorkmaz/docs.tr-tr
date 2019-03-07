---
title: IMetaDataImport::GetFieldProps Metodu
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1064300d8bb3a9b03e1dfad1c30596c35ee1c941
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485206"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps Metodu
Belirteç belirtilen fieldDef simgesi tarafından başvurulan alanı ile ilişkili meta verileri alır.  
  
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
  
## <a name="parameters"></a>Parametreler  
 `mb`  
 [in] İlgili meta verilerini almak için alan temsil eden bir fieldDef simgesi belirteci.  
  
 `pClass`  
 [out] Alanın ait sınıf türünü temsil eden bir tür tanımı belirteci için bir işaretçi.  
  
 `szField`  
 [out] Alanın adı.  
  
 `cchField`  
 [in] Geniş karakterler için arabellek boyutu *szField*.  
  
 `pchField`  
 [out] Döndürülen arabellek gerçek boyutu.  
  
 `pdwAttr`  
 [out] Alanın meta verileriyle ilişkili bayraklar.  
  
 `ppvSigBlob`  
 [in] Alan açıklayan ikili meta veri değeri için bir işaretçi.  
  
 `pcbSigBlob`  
 [out] Bayt cinsinden boyutu `ppvSigBlob`.  
  
 `pdwCPlusTypeFlag`  
 [out] Alanın değeri türünü belirten bir bayrak.  
  
 `ppValue`  
 [out] Alan için sabit bir değer.  
  
 `pcchValue`  
 [out] Karakter boyutu `ppValue`, veya dize varsa sıfır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
