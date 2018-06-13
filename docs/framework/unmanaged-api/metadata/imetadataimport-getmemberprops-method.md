---
title: IMetaDataImport::GetMemberProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d93763da2afbbdb1e738c802ba172e9f16e5f7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448464"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps Metodu
Adını, ikili imza ve göreli sanal adres, meta veri bilgilerini alır <xref:System.Type> belirtilen meta veri simgesi tarafından başvurulan üye.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] ULONG             *pulCodeRVA,   
   [out] DWORD             *pdwImplFlags,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `mb`  
 [in] İlişkili meta verileri almak için üye başvuran belirteci.  
  
 `pClass`  
 [out] Üye sınıfı temsil eder meta veri simgesi için bir işaretçi.  
  
 `szMember`  
 [out] Üyenin adı.  
  
 `cchMember`  
 [in] Geniş karakter cinsinden boyutu `szMember` arabellek.  
  
 `pchMember`  
 [out] Döndürülen adını geniş karakter cinsinden boyutu.  
  
 `pdwAttr`  
 [out] Üyeye uygulanan tüm bayrak değeri.  
  
 `ppvSigBlob`  
 [out] Üyenin ikili meta verileri imza için bir işaretçi.  
  
 `pcbSigBlob`  
 [out] Bayt cinsinden boyutu `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Göreli sanal adres üyesi için bir işaretçi.  
  
 `pdwImplFlags`  
 [out] Üye ile ilişkili tüm yöntemi uygulama bayrakları.  
  
 `pdwCPlusTypeFlag`  
 [out] İşaretler bir bayrak bir <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Bu üye tarafından döndürülen bir sabit dize değeri.  
  
 `pcchValue`  
 [out] Karakter cinsinden boyutu `ppValue`, ya da sıfır `ppValue` bir dize tutmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
