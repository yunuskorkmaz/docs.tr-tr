---
title: IMetaDataImport::GetPropertyProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: 5fc71bf240b89afadbf8f2ba10906322921bdda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175336"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps Metodu
Belirtilen belirteç tarafından temsil edilen özelliğin meta verilerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,
   [out] LPCWSTR           szProperty,
   [in]  ULONG             cchProperty,
   [out] ULONG             *pchProperty,
   [out] DWORD             *pdwPropFlags,
   [out] PCCOR_SIGNATURE   *ppvSig,
   [out] ULONG             *pbSig,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,
   [out] mdMethodDef       *pmdGetter,
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,
   [out] ULONG             *pcOtherMethod
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `prop`  
 [içinde] Meta verileri döndürecek özelliği temsil eden bir belirteç.  
  
 `pClass`  
 [çıkış] Özelliği uygulayan türü temsil eden TypeDef belirteci için bir işaretçi.  
  
 `szProperty`  
 [çıkış] Özellik adını tutmak için bir arabellek.  
  
 `cchProperty`  
 [içinde] Geniş karakterler boyutu `szProperty`.  
  
 `pchProperty`  
 [çıkış] Döndürülen geniş karakter `szProperty`sayısı.  
  
 `pdwPropFlags`  
 [çıkış] Özelliğe uygulanan herhangi bir öznitelik bayrakları için bir işaretçi. Bu değer [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) numaralandırmabir bitmask olduğunu.  
  
 `ppvSig`  
 [çıkış] Özelliğin meta veri imzasına işaretçi.  
  
 `pbSig`  
 [çıkış] Döndürülen bayt `ppvSig`sayısı.  
  
 `pdwCPlusTypeFlag`  
 [çıkış] Özelliğin varsayılan değeri olan sabit türünü belirten bir bayrak. Bu değer CorElementType numaralandırmasından dır.  
  
 `ppDefaultValue`  
 [çıkış] Bu özellik için varsayılan değeri depolayan baytlar için bir işaretçi.  
  
 `pcchDefaultValue`  
 [çıkış] Geniş karakterlerdeki boyut `ppDefaultValue`, `pdwCPlusTypeFlag` ELEMENT_TYPE_STRING ise; aksi takdirde, bu değer ilgili değildir. Bu durumda, uzunluk `ppDefaultValue` tarafından belirtilen türden `pdwCPlusTypeFlag`çıkarılır.  
  
 `pmdSetter`  
 [çıkış] Özelliğin ayarlanan erişimci yöntemini temsil eden MethodDef belirteci için bir işaretçi.  
  
 `pmdGetter`  
 [çıkış] Özelliğin erişime alma yöntemini temsil eden MethodDef belirteci için bir işaretçi.  
  
 `rmdOtherMethod`  
 [çıkış] Özellik ile ilişkili diğer yöntemleri temsil eden MethodDef belirteçleri bir dizi.  
  
 `cMax`  
 [içinde] `rmdOtherMethod` Dizinin en büyük boyutu. Tüm yöntemleri tutabilecek kadar büyük bir dizi sağlamazsanız, bunlar uyarı yapılmadan atlanır.  
  
 `pcOtherMethod`  
 [çıkış] MethodDef belirteçlerinin sayısı `rmdOtherMethod`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
