---
title: IAssemblyName::IsEqual Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 926bdcee3a3c3974c8546f3a6dfe98f0b62c93c8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796561"
---
# <a name="iassemblynameisequal-method"></a>IAssemblyName::IsEqual Yöntemi
Belirtilen bir [IAssemblyName](iassemblyname-interface.md) nesnesinin, belirtilen karşılaştırma bayraklarını temel alarak `IAssemblyName`bu değere eşit olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pName`  
 'ndaki `IAssemblyName` Bu`IAssemblyName`nesnenin karşılaştırılacağı nesne.  
  
 `dwCmpFlags`  
 'ndaki Karşılaştırmayı etkileyen [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) değerlerinin bit düzeyinde birleşimi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Fusion. h  
  
 **Net Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyName Arabirimi](iassemblyname-interface.md)
- [Fusion Sabit Listeleri](fusion-enumerations.md)
