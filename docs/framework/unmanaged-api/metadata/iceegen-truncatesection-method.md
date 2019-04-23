---
title: ICeeGen::TruncateSection Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.TruncateSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1036d6080bf17eea288724c7980ce53dfa2121f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116327"
---
# <a name="iceegentruncatesection-method"></a>ICeeGen::TruncateSection Yöntemi
Belirtilen kod bölümünde belirtilen uzunluğa göre keser.  
  
 Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `section`  
 [in] Truncate bölümü.  
  
 `len`  
 [in] Bölüm kesmek, bayt cinsinden uzunluğu.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrı `TruncateSection` yalnızca diğer yöntemler tarafından işlenmemiş özel bölümü gereksinimleriniz varsa.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICeeGen Arabirimi](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
