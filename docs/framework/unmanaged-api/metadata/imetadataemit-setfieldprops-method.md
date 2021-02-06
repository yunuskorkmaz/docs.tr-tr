---
description: ': Imetadatayayma:: SetFieldProps yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataEmit::SetFieldProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: ee9964077e556a1d0666a836ca0c3bab92540252
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658015"
---
# <a name="imetadataemitsetfieldprops-method"></a>IMetaDataEmit::SetFieldProps Yöntemi

Belirtilen alan belirteci tarafından başvurulan alan için varsayılan değeri ayarlar veya güncelleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `fd`  
 'ndaki Hedef alan için belirteç.  
  
 `dwFieldFlags`  
 'ndaki Alan öznitelikleri. Bu bir değer bit değeridir `CorFieldAttr` .  
  
 `dwCPlusTypeFlag`  
 'ndaki `ELEMENT_TYPE_` *\** Sabit değer için. Bu bir `CorElementType` değerdir. Bir sabit tanımlanmamışsa, bu değeri olarak ayarlayın `ELEMENT_TYPE_END` .  
  
 `pValue`  
 'ndaki Alanın sabit değeri.  
  
 `cchValue`  
 'ndaki ' Nin Unicode karakterdeki boyutu `pValue` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
