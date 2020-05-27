---
title: ICeeGen::GetSectionBlock Metodu
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
ms.openlocfilehash: ed534890fc90d3b8543a1166c85903f10163f0a8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008343"
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock Metodu
Kod tabanının bir bölüm bloğunu alır.  
  
 Bu yöntem kullanılmıyor ve kullanılmamalıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a>Parametreler  
 `section`  
 'ndaki Kod tabanı bloğunun alınacağı bölüm.  
  
 `len`  
 'ndaki Alınacak bloğun uzunluğu.  
  
 `align`  
 'ndaki Bloğunun ilk baytını hizalamak için, bölümünün başlangıcına göre bayt. Bu, bloğunun bölüm içindeki konumudur.  
  
 `ppBytes`  
 dışı Alınan bloğun adresini alan konuma yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetSectionBlock`Yalnızca diğer yöntemler tarafından işlenmemiş özel bölüm gereksinimleriniz varsa çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICeeGen Arabirimi](iceegen-interface.md)
