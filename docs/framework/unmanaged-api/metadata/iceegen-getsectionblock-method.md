---
title: ICeeGen::GetSectionBlock Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionBlock
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4732eef9a47f9ea1e919bd9d855afbec18974454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock Metodu
Kod temeliniz bölüm bloğunu alır.  
  
 Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a>Parametreler  
 `section`  
 [in] Kod temeliniz bloğunu alınacağı bölümü.  
  
 `len`  
 [in] Alınacak Blok uzunluğu.  
  
 `align`  
 [in] Hangi blok ilk baytını hizalamak bölüm başına göreli bayt. Blok bölüm içindeki konumudur.  
  
 `ppBytes`  
 [out] Bir işaretçi bir konuma alınan blok adresi alır.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrı `GetSectionBlock` yalnızca diğer yöntemler tarafından işlenmemiş özel bölümü gereksinimleri varsa.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iceegen arabirimi](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
