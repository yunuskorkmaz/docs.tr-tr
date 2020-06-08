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
ms.openlocfilehash: cac5aaa7ed13b6a48b36ad550da8b73d0deb2ee7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491049"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps Metodu
Belirtilen belirteç tarafından temsil edilen özelliğin meta verilerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Meta verilerini döndürecek özelliği temsil eden bir belirteç.  
  
 `pClass`  
 dışı Özelliği uygulayan türü temsil eden TypeDef belirtecinin işaretçisi.  
  
 `szProperty`  
 dışı Özellik adını tutan bir arabellek.  
  
 `cchProperty`  
 'ndaki Öğesinin geniş karakterdeki boyutu `szProperty` .  
  
 `pchProperty`  
 dışı İçinde döndürülen geniş karakter sayısı `szProperty` .  
  
 `pdwPropFlags`  
 dışı Özelliğe uygulanan öznitelik bayraklarının bir işaretçisi. Bu değer [CorPropertyAttr](corpropertyattr-enumeration.md) numaralandırmasından bir bit dır.  
  
 `ppvSig`  
 dışı Özelliğin meta veri imzasına yönelik bir işaretçi.  
  
 `pbSig`  
 dışı İçinde döndürülen bayt sayısı `ppvSig` .  
  
 `pdwCPlusTypeFlag`  
 dışı Özelliğin varsayılan değeri olan sabitin türünü belirten bayrak. Bu değer CorElementType numaralandırmasından.  
  
 `ppDefaultValue`  
 dışı Bu özellik için varsayılan değeri depolayan bayta yönelik bir işaretçi.  
  
 `pcchDefaultValue`  
 dışı ' Nin geniş karakterdeki boyutu `ppDefaultValue` , `pdwCPlusTypeFlag` ELEMENT_TYPE_STRING; Aksi takdirde, bu değer ilgili değildir. Bu durumda, uzunluğu `ppDefaultValue` tarafından belirtilen türden çıkarsanamıyor `pdwCPlusTypeFlag` .  
  
 `pmdSetter`  
 dışı Özelliği için set erişimcisi metodunu temsil eden MethodDef belirtecinin işaretçisi.  
  
 `pmdGetter`  
 dışı Özelliği için get erişimcisi metodunu temsil eden MethodDef belirtecinin işaretçisi.  
  
 `rmdOtherMethod`  
 dışı Özelliği ile ilişkili diğer yöntemleri temsil eden bir MethodDef belirteçleri dizisi.  
  
 `cMax`  
 'ndaki Dizinin en büyük boyutu `rmdOtherMethod` . Tüm yöntemleri tutacak büyüklükte bir dizi sağlamazsanız, bunlar uyarı vermeden atlanır.  
  
 `pcOtherMethod`  
 dışı İçinde döndürülen MethodDef belirteçleri sayısı `rmdOtherMethod` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
