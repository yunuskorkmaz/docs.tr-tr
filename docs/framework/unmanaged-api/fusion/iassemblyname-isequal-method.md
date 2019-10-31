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
ms.openlocfilehash: 23bc251053dd27a7c5accb48ab4759ecdb79fe09
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134301"
---
# <a name="iassemblynameisequal-method"></a>IAssemblyName::IsEqual Yöntemi
Belirtilen bir [IAssemblyName](iassemblyname-interface.md) nesnesinin, belirtilen karşılaştırma bayraklarını temel alarak bu `IAssemblyName`eşit olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pName`  
 'ndaki Bu `IAssemblyName`Karşılaştırılacak `IAssemblyName` nesnesi.  
  
 `dwCmpFlags`  
 'ndaki Karşılaştırmayı etkileyen [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) değerlerinin bit düzeyinde birleşimi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **Net Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyName Arabirimi](iassemblyname-interface.md)
- [Fusion Sabit Listeleri](fusion-enumerations.md)
