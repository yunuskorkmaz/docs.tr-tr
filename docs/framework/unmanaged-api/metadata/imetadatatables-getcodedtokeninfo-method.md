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
ms.openlocfilehash: 8ab16ad5b2b2838125e07511ef47be737f40671c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501215"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a>IMetaDataTables::GetCodedTokenInfo Metodu
Belirtilen satır diziniyle ilişkili bir belirteç dizisine yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Döndürülecek kodlanmış belirtecin türü.  
  
 `pcTokens`  
 dışı Uzunluğuna yönelik bir işaretçi `ppTokens` .  
  
 `ppTokens`  
 dışı Döndürülen belirteçlerin listesini içeren bir dizi işaretçisine yönelik işaretçi.  
  
 `ppName`  
 dışı İçindeki belirtecin adı için bir işaretçiye yönelik işaretçi `ixCdTkn` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](imetadatatables2-interface.md)
