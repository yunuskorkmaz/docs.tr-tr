---
title: IAssemblyEnum::GetNextAssembly Metodu
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
ms.openlocfilehash: ade404557d65fa073b6a0e66fe8234b41223ecde
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134432"
---
# <a name="iassemblyenumgetnextassembly-method"></a>IAssemblyEnum::GetNextAssembly Metodu
Bu [IAssemblyEnum](iassemblyenum-interface.md) nesnesinde bulunan sonraki [IAssemblyName](iassemblyname-interface.md) öğesine bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pvReserved`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır. `pvReserved`, null bir başvuru olmalıdır.  
  
 `ppName`  
 dışı Döndürülen `IAssemblyName` işaretçisi.  
  
 `dwFlags`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır. `dwFlags` 0 (sıfır) olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyName Arabirimi](iassemblyname-interface.md)
- [IAssemblyEnum Arabirimi](iassemblyenum-interface.md)
