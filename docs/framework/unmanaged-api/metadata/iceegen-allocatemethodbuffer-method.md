---
title: ICeeGen::AllocateMethodBuffer Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
ms.openlocfilehash: 8dc7f439cac56c2d55916ff8631ec3095c67680d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008891"
---
# <a name="iceegenallocatemethodbuffer-method"></a>ICeeGen::AllocateMethodBuffer Yöntemi
Bir yöntem için belirtilen boyutun bir arabelleğini oluşturur ve yöntemin göreli sanal adresini alır.  
  
 Bu yöntem kullanılmıyor ve kullanılmamalıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cchBuffer`  
 'ndaki Oluşturulacak arabelleğin uzunluğu.  
  
 `lpBuffer`  
 dışı Döndürülen arabellek.  
  
 `RVA`  
 dışı Metodun göreli sanal adresi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICeeGen Arabirimi](iceegen-interface.md)
