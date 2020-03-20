---
title: IMetaDataImport::GetMemberRefProps Yöntemi
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
ms.openlocfilehash: a61254ba751e47b0089a3f7528aca337a32e2db3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175375"
---
# <a name="imetadataimportgetmemberrefprops-method"></a>IMetaDataImport::GetMemberRefProps Yöntemi
Belirtilen belirteç tarafından başvurulan üye ile ilişkili meta verileri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
  
## <a name="parameters"></a>Parametreler  
 `mr`  
 [içinde] ÜyeRef belirteç için ilişkili meta verileri döndürmek için.  
  
 `ptk`  
 [çıkış] Üyeyi bildiren sınıfı temsil eden bir TypeDef veya TypeRef veya TypeSpec belirteci veya üyeyi bildiren modül sınıfını temsil eden bir ModuleRef belirteci veya üyeyi temsil eden bir MethodDef belirteç.  
  
 `szMember`  
 [çıkış] Üyenin adı için bir dize arabelleği.  
  
 `cchMember`  
 [içinde] Geniş karakterlerde istenen `szMember`boyut.  
  
 `pchMember`  
 [çıkış] Döndürülen boyut geniş karakterler `szMember`.  
  
 `ppvSibBlob`  
 [çıkış] Üye için ikili meta veri imzasına işaretçi.  
  
 `pbSig`  
 [çıkış] `ppvSigBlob`Baytboyutu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
