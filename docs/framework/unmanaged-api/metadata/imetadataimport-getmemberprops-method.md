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
ms.openlocfilehash: 72e14ea0414ebdeb8f54a4bdef8ce5208fc8ef72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177224"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps Metodu
Belirtilen meta veri belirteci tarafından başvurulan üyenin <xref:System.Type> adı, ikili imza ve göreli sanal adresi de dahil olmak üzere, belirli bir üye tanımı için meta verilerde depolanan bilgileri alır. Bu basit bir yardımcı yöntemdir: *mb* bir MethodDef ise, **getMethodProps** denir; *mb* bir FieldDef ise, o zaman **GetFieldProps** denir. Ayrıntılar için diğer yöntemlere bakın.
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
  
## <a name="parameters"></a>Parametreler  
 `mb`  
 [içinde] İlişkili meta verileri almak için üyeye başvurur belirteç.  
  
 `pClass`  
 [çıkış] Üyenin sınıfını temsil eden meta veri belirteci için bir işaretçi.  
  
 `szMember`  
 [çıkış] Üyenin adı.  
  
 `cchMember`  
 [içinde] `szMember` Arabellek geniş karakterlerboyutu.  
  
 `pchMember`  
 [çıkış] Döndürülen adın geniş karakterlerindeki boyutu.  
  
 `pdwAttr`  
 [çıkış] Üyeye uygulanan tüm bayrak değerleri.  
  
 `ppvSigBlob`  
 [çıkış] Üyenin ikili meta veri imzasına işaretçi.  
  
 `pcbSigBlob`  
 [çıkış] `ppvSigBlob`Baytboyutu.  
  
 `pulCodeRVA`  
 [çıkış] Üyenin göreli sanal adresine işaretçi.  
  
 `pdwImplFlags`  
 [çıkış] Üyeyle ilişkili herhangi bir yöntem uygulama bayrakları.  
  
 `pdwCPlusTypeFlag`  
 [çıkış] Bir bayrak. <xref:System.ValueType> Bu `ELEMENT_TYPE_*` değerlerden biridir.
  
 `ppValue`  
 [çıkış] Bu üye tarafından döndürülen sabit bir dize değeri.  
  
 `pcchValue`  
 [çıkış] Bir dize tutmuyorsa `ppValue` `ppValue` , veya sıfır karakter boyutu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
