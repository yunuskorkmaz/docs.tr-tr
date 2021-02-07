---
description: 'Şu konuda daha fazla bilgi edinin: ICeeGen:: GetSectionBlock yöntemi'
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
ms.openlocfilehash: d1a9fdeb35507f9dd6528b581be877049d2a1478
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721157"
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock Metodu

Kod tabanının bir bölüm bloğunu alır.  
  
 Bu yöntem kullanılmıyor ve kullanılmamalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICeeGen Arabirimi](iceegen-interface.md)
