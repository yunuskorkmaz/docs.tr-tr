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
ms.openlocfilehash: a494b1aaa762549528e92ab93d18929ef73eb8da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176090"
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock Metodu
Kod tabanının bir bölüm bloğunu alır.  
  
 Bu yöntem eskidir ve kullanılmamalıdır.  
  
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
 [içinde] Kod tabanının bir bloğunu almak için hangi bölüm.  
  
 `len`  
 [içinde] Alınacak bloğun uzunluğu.  
  
 `align`  
 [içinde] Bloğun ilk baytını hizalamak için bölümün başına göre bayt. Bu, bloğun bölüm içindeki konumudur.  
  
 `ppBytes`  
 [çıkış] Alınan bloğun adresini alan bir konuma işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca `GetSectionBlock` diğer yöntemlerle işlenmemiş özel bölüm gereksinimleriniz varsa arayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICeeGen Arabirimi](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
