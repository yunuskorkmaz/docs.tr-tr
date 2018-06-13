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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f56376d4400f4e24aefe2d1e5d4ad504b1d281cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446010"
---
# <a name="iceegenallocatemethodbuffer-method"></a>ICeeGen::AllocateMethodBuffer Yöntemi
Bir yöntem için belirtilen boyutta bir arabellek oluşturur ve göreli sanal adres yönteminin alır.  
  
 Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cchBuffer`  
 [in] Oluşturmak için arabellek uzunluğu.  
  
 `lpBuffer`  
 [out] Döndürülen arabellek.  
  
 `RVA`  
 [out] Yönteminin göreli sanal adres.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICeeGen Arabirimi](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
