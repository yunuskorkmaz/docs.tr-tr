---
description: ': Imetadatayayma:: SetParamProps yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataEmit::SetParamProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
ms.openlocfilehash: 35e839b05b3671c6c09f315ac636971c386e766e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772033"
---
# <a name="imetadataemitsetparamprops-method"></a>IMetaDataEmit::SetParamProps Yöntemi

Imetadatayayma için önceki bir çağrı tarafından tanımlanan bir yöntem parametresinin özelliklerini ayarlar veya değiştirir [::D efineParam](imetadataemit-defineparam-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetParamProps (
    [in]  mdParamDef  pd,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pd`  
 'ndaki Hedef parametrenin belirteci.  
  
 `szName`  
 'ndaki Parametrenin Unicode olarak adı.  
  
 `dwParamFlags`  
 'ndaki Parametresinin bayrakları.  
  
 `dwCPlusTypeFlag`  
 'ndaki Sabit değer için ELEMENT_TYPE_ *.  
  
 `pValue`  
 'ndaki Parametrenin sabit değeri.  
  
 `cchValue`  
 'ndaki (Unicode) karakter boyutu `pValue` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
