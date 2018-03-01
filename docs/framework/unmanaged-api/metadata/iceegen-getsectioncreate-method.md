---
title: ICeeGen::GetSectionCreate Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a069f65d3059bfa427ea20623ff9a2ac4049fd39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetsectioncreate-method"></a>ICeeGen::GetSectionCreate Metodu
Oluşturur ve belirtilen ad ve bayrak değerleri kullanarak bir kod bölümü alır.  
  
 Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `name`  
 [in] Oluşturulacak bölümün adını belirten bir dize için bir işaretçi.  
  
 `flags`  
 [in] Seçeneklerini belirtin bayraklar.  
  
 `section`  
 [out] Yeni oluşturulan kod bölümünde bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrı `GetSectionCreate` yalnızca diğer yöntemler tarafından işlenmemiş özel bölümü gereksinimleri varsa.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICeeGen Arabirimi](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
