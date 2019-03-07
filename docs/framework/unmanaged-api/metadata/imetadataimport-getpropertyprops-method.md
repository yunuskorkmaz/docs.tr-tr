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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e1b065ecb9a715601e617e288c1dfc0de8dd323d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466576"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps Metodu
Belirtilen belirteç tarafından temsil edilen bir özellik için meta verileri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 [in] Özellik için meta verileri döndürmek için temsil eden bir belirteci.  
  
 `pClass`  
 [out] Özelliği uygulayan türü temsil eden TypeDef belirteci için bir işaretçi.  
  
 `szProperty`  
 [out] Özellik adını tutan bir arabellek.  
  
 `cchProperty`  
 [in] Geniş karakter cinsinden boyutu `szProperty`.  
  
 `pchProperty`  
 [out] Döndürülen geniş karakter sayısını `szProperty`.  
  
 `pdwPropFlags`  
 [out] Özelliğine uygulanan herhangi bir öznitelik bayrakları için bir işaretçi. Gelen bir bit maskesi değerdir [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) sabit listesi.  
  
 `ppvSig`  
 [out] Özelliğin meta veri imzası bir işaretçi.  
  
 `pbSig`  
 [out] Döndürülen bayt sayısı `ppvSig`.  
  
 `pdwCPlusTypeFlag`  
 [out] Özelliğin varsayılan değeri sabiti türünü belirten bir bayrak. CorElementType numaralandırması değerdir.  
  
 `ppDefaultValue`  
 [out] Bu özellik için varsayılan değeri depolamak bayt için bir işaretçi.  
  
 `pcchDefaultValue`  
 [out] Geniş karakter cinsinden boyutu `ppDefaultValue`, `pdwCPlusTypeFlag` olduğu ELEMENT_TYPE_STRING; Aksi takdirde, bu değeri uygun değil. Bu durumda, uzunluğunu `ppDefaultValue` tarafından belirtilen türden çıkarılan `pdwCPlusTypeFlag`.  
  
 `pmdSetter`  
 [out] Özelliği için set erişimcisi yöntemi temsil eden MethodDef belirteci için bir işaretçi.  
  
 `pmdGetter`  
 [out] Özellik get erişimci yöntemi temsil eden MethodDef belirteci için bir işaretçi.  
  
 `rmdOtherMethod`  
 [out] Özellikle ilişkili diğer yöntemleri temsil eden MethodDef belirteçleri dizisi.  
  
 `cMax`  
 [in] En büyük boyutunu `rmdOtherMethod` dizisi. Tüm yöntemleri tutabilecek kadar büyük bir dizi belirtmezseniz, bunlar uyarı vermeden atlanır.  
  
 `pcOtherMethod`  
 [out] Döndürülen MethodDef belirteçleri sayısı `rmdOtherMethod`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
