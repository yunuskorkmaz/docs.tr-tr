---
title: IMetaDataDispenserEx::GetOption Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
ms.openlocfilehash: ab74b02df959fe6e6457273e67ba3b82ae6a015c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435997"
---
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption Yöntemi
Geçerli meta veri kapsamı için belirtilen seçeneğin değerini alır. Seçeneği, geçerli meta veri kapsamına yapılan çağrıların işlenme biçimini denetler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `optionId`  
 'ndaki Alınacak seçeneği belirten bir GUID işaretçisi. Desteklenen GUID 'lerin listesi için açıklamalar bölümüne bakın.  
  
 `pValue`  
 dışı Döndürülen seçeneğin değeri. Bu değerin türü, belirtilen seçeneğin türünün bir değişkeni olacaktır.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki liste, bu yöntem için desteklenen GUID 'Leri gösterir. Açıklamalar için, bkz. [ımetadatadağıtıserex:: SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) yöntemi. `optionId` bu listede yoksa, bu yöntem, yanlış bir parametre belirten HRESULT `E_INVALIDARG`döndürür.  
  
- MetaDataCheckDuplicatesFor  
  
- MetaDataRefToDefCheck  
  
- Metadadtanocertificate Ationfortokentaşıması  
  
- MetaDataSetENC  
  
- Metadataerrorifemıtoutoforder  
  
- Metadatageneratetcebağdaştırıcıları  
  
- Metaveriveri ınkeroptions  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataDispenserEx Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
