---
title: IMetaDataTables::GetCodedTokenInfo Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetCodedTokenInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetCodedTokenInfo
helpviewer_keywords:
- GetCodedTokenInfo method [.NET Framework metadata]
- IMetaDataTables::GetCodedTokenInfo method [.NET Framework metadata]
ms.assetid: 31214d3a-715e-49af-92b3-0fd11e4f218a
topic_type:
- apiref
ms.openlocfilehash: 64c70fe0b657047ae35dccb763fa57120403deef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177148"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a>IMetaDataTables::GetCodedTokenInfo Metodu
Belirtilen satır dizini ile ilişkili belirteçleri bir dizi için bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ixCdTkn`  
 [içinde] İade etmek için kodlanmış bir belirteç türü.  
  
 `pcTokens`  
 [çıkış] Uzunluğuna işareteden `ppTokens`bir işaretçi.  
  
 `ppTokens`  
 [çıkış] Döndürülen belirteçlerin listesini içeren bir dizi için işaretçi.  
  
 `ppName`  
 [çıkış] 'deki `ixCdTkn`belirteç adına işaretçi için bir işaretçi  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
