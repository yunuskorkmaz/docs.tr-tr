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
ms.openlocfilehash: bc5bbba2fa4a95955e52a2e083a2097178b5d96a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437511"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps Metodu
Belirtilen meta veri belirtecinin başvurduğu <xref:System.Type> üyesinin adı, ikili imzası ve göreli sanal adresi de dahil olmak üzere, belirtilen üye tanımı için meta verilerde depolanan bilgileri alır. Bu basit bir yardımcı yöntemdir: *MB* bir MethodDef Ise **GetMethodProps** çağrılır; *MB* bir fieldDef Ise, **GetFieldProps** çağırılır. Ayrıntılar için diğer yöntemlere bakın. 
  
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
 'ndaki İlişkili meta verileri almak için üyeye başvuran belirteç.  
  
 `pClass`  
 dışı Üyenin sınıfını temsil eden meta veri belirtecinin işaretçisi.  
  
 `szMember`  
 dışı Üyenin adı.  
  
 `cchMember`  
 'ndaki `szMember` arabelleğinin geniş karakterdeki boyutu.  
  
 `pchMember`  
 dışı Döndürülen adın geniş karakterdeki boyutu.  
  
 `pdwAttr`  
 dışı Üyeye uygulanan bayrak değerleri.  
  
 `ppvSigBlob`  
 dışı Üyenin ikili meta veri imzasına yönelik bir işaretçi.  
  
 `pcbSigBlob`  
 dışı `ppvSigBlob`bayt cinsinden boyutu.  
  
 `pulCodeRVA`  
 dışı Üyenin göreli sanal adresine yönelik bir işaretçi.  
  
 `pdwImplFlags`  
 dışı Üyeyle ilişkili herhangi bir yöntem uygulama bayrağı.  
  
 `pdwCPlusTypeFlag`  
 dışı Bir <xref:System.ValueType>işaretleyen bayrak. `ELEMENT_TYPE_*` değerlerinden biridir.
  
 `ppValue`  
 dışı Bu üye tarafından döndürülen sabit dize değeri.  
  
 `pcchValue`  
 dışı `ppValue`karakter cinsinden boyut veya `ppValue` bir dize yoksa sıfır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
