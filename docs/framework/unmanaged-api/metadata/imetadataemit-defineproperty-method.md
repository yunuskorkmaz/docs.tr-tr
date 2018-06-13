---
title: IMetaDataEmit::DefineProperty Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c250a577f2ccdbbfefb35225b880c0e4317db36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448113"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty Yöntemi
Belirtilen türde bir özellik tanımı belirtilen oluşturur `get` ve `set` yöntemi erişimciler ve bu özellik tanımı için bir belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineProperty (   
    [in]  mdTypeDef          td,   
    [in]  LPCWSTR            szProperty,   
    [in]  DWORD              dwPropFlags,   
    [in]  PCCOR_SIGNATURE    pvSig,   
    [in]  ULONG              cbSig,   
    [in]  DWORD              dwCPlusTypeFlag,   
    [in]  void const         *pValue,   
    [in]  ULONG              cchValue,   
    [in]  mdMethodDef        mdSetter,   
    [in]  mdMethodDef        mdGetter,   
    [in]  mdMethodDef        rmdOtherMethods[],   
    [out] mdProperty         *pmdProp   
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `td`  
 [in] Sınıf veya özellik tanımlanıyorsa arabirim için belirteci.  
  
 `szProperty`  
 [in] Özelliğin adı.  
  
 `dwPropFlags`  
 [in] Özellik bayraklar.  
  
 `pvSig`  
 [in] Özellik imzası.  
  
 `cbSig`  
 [in] Bayt sayısı `pvSig`.  
  
 `dwCPlusTypeFlag`  
 [in] Özelliğin varsayılan değeri türü.  
  
 `pValue`  
 [in] Özelliğin varsayılan değeri.  
  
 `cchValue`  
 [in] \(Unicode) sayısını karakterleri `pValue`.  
  
 `mdSetter`  
 [in] Özellik değeri ayarlar yöntemi.  
  
 `mdGetter`  
 [in] Özellik değeri alır yöntemi.  
  
 `rmdOtherMethods[]`  
 [in] Özellik ile ilişkilendirilmiş diğer yöntemleri dizisi. Dizi ile sonlandırmak bir `mdTokenNil`.  
  
 `pmdProp`  
 [out] `mdProperty` Atanan simgesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
