---
title: IMetaDataImport::GetMemberRefProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ac0d77b1d8d35a7753d3a501f147bd5ac53750c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583736"
---
# <a name="imetadataimportgetmemberrefprops-method"></a>IMetaDataImport::GetMemberRefProps Metodu
Belirtilen belirteç tarafından başvurulan üye ile ilişkili meta verileri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,   
   [out] mdToken           *ptk,   
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pbSig   
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `mr`  
 [in] İlişkili meta verileri için döndürülecek MemberRef belirteç.  
  
 `ptk`  
 [out] Üye ya da üyeye ya da üye temsil eden bir MethodDef bildirir modül sınıfı temsil eden bir ModuleRef belirteci bildiren sınıfın temsil ettiği bir TypeDef veya TypeRef veya TypeSpec'te belirteci.  
  
 `szMember`  
 [out] Üyenin adını bir dize arabelleği.  
  
 `cchMember`  
 [in] Geniş karakter cinsinden istenen boyuta `szMember`.  
  
 `pchMember`  
 [out] Geniş karakter cinsinden döndürülen boyutu `szMember`.  
  
 `ppvSibBlob`  
 [out] İkili meta veri imzası üyesi için bir işaretçi.  
  
 `pbSig`  
 [out] Bayt cinsinden boyutu `ppvSigBlob`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
