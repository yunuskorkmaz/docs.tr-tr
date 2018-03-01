---
title: IMetaDataImport::GetPropertyProps Metodu
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d838f43b500ac3dd0c3b44d9d84dd9fc039c6e16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
  
#### <a name="parameters"></a>Parametreler  
 `prop`  
 [in] Özellik için meta verileri döndürmek için temsil eden bir belirteci.  
  
 `pClass`  
 [out] Özellik uygulayan türünü temsil eden TypeDef belirteci için bir işaretçi.  
  
 `szProperty`  
 [out] Özellik adı tutacak bir arabellek.  
  
 `cchProperty`  
 [in] Geniş karakter cinsinden boyutu `szProperty`.  
  
 `pchProperty`  
 [out] Döndürülen geniş karakter sayısını `szProperty`.  
  
 `pdwPropFlags`  
 [out] Özelliğine uygulanan herhangi bir öznitelik bayrağı için bir işaretçi. Bu değer gelen bir bit maskesi olan [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) numaralandırması.  
  
 `ppvSig`  
 [out] Meta veri imza özelliği için bir işaretçi.  
  
 `pbSig`  
 [out] Döndürülen bayt sayısı `ppvSig`.  
  
 `pdwCPlusTypeFlag`  
 [out] Özelliğin varsayılan değeri sabiti türünü belirleyen bir bayrak. CorElementType numaralandırması değerdir.  
  
 `ppDefaultValue`  
 [out] Bu özellik için varsayılan değer depolamak bayt gösteren bir işaretçi.  
  
 `pcchDefaultValue`  
 [out] Geniş karakter cinsinden boyutu `ppDefaultValue`, `pdwCPlusTypeFlag` olan ELEMENT_TYPE_STRING; Aksi takdirde, bu değer ilgili değildir. Bu durumda, uzunluğu `ppDefaultValue` tarafından belirtilen türden olayla `pdwCPlusTypeFlag`.  
  
 `pmdSetter`  
 [out] Özelliği için set erişimcisi yöntemi temsil eden MethodDef belirteci için bir işaretçi.  
  
 `pmdGetter`  
 [out] Özellik get erişimcisi yöntemi temsil eden MethodDef belirteci için bir işaretçi.  
  
 `rmdOtherMethod`  
 [out] Özellik ile ilişkilendirilmiş diğer yöntemleri gösteren MethodDef belirteçleri dizisi.  
  
 `cMax`  
 [in] En büyük boyutunu `rmdOtherMethod` dizi. Tüm yöntemleri tutabilecek kadar büyük bir dizi belirtmezseniz, bunlar uyarmadan atlanır.  
  
 `pcOtherMethod`  
 [out] Döndürülen MethodDef belirteçleri sayısı `rmdOtherMethod`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
