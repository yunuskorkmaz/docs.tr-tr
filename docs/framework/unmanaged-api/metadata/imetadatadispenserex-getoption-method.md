---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatadağıtıserex:: GetOption yöntemi'
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
ms.openlocfilehash: cf52a251c3c0e0485558a150b727d58eeae81995
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753555"
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

 Aşağıdaki liste, bu yöntem için desteklenen GUID 'Leri gösterir. Açıklamalar için, bkz. [ımetadatadağıtıserex:: SetOption](imetadatadispenserex-setoption-method.md) yöntemi. `optionId`Bu listede yoksa, bu yöntem, `E_INVALIDARG` yanlış bir parametre belirten hresult döndürür.  
  
- MetaDataCheckDuplicatesFor  
  
- MetaDataRefToDefCheck  
  
- Metadadtanocertificate Ationfortokentaşıması  
  
- MetaDataSetENC  
  
- Metadataerrorifemıtoutoforder  
  
- Metadatageneratetcebağdaştırıcıları  
  
- Metaveriveri ınkeroptions  
  
## <a name="requirements"></a>Gereksinimler  

 **Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataDispenserEx Arabirimi](imetadatadispenserex-interface.md)
- [IMetaDataDispenser Arabirimi](imetadatadispenser-interface.md)
