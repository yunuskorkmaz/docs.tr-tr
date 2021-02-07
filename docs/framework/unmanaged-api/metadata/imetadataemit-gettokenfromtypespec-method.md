---
description: ': Imetadatayayma:: GetTokenFromTypeSpec metodu hakkında daha fazla bilgi edinin'
title: IMetaDataEmit::GetTokenFromTypeSpec Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
ms.openlocfilehash: 09f7133af9b9d912b03cdc1c93744ee260c69169
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728242"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a>IMetaDataEmit::GetTokenFromTypeSpec Metodu

Belirtilen meta veri imzasına sahip tür için bir meta veri belirteci alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pvSig`  
 'ndaki Tanımlanmakta olan imza.  
  
 `cbSig`  
 'ndaki İçindeki bayt sayısı `pvSig` .  
  
 `ptypespec`  
 dışı `mdTypeSpec` Atanan belirteç.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
