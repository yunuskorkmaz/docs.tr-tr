---
title: AXL_AUTHENTICODE_SIGNER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 024837870aade6b0beb76fe758a571b15fd14d59
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107672"
---
# <a name="axlauthenticodesignerinfo-structure"></a>AXL_AUTHENTICODE_SIGNER_INFO Yapısı
Authenticode imzalayan bilgileri tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`cbSize`|Bu yapının boyutu.|  
|`dwError`|Hata kodu.|  
|`algHash`|Karma algoritması.|  
|`pwszHash`|Karma değeri.|  
|`pwszDescription`|Açıklaması.|  
|`pwszDescriptionUrl`|Açıklama URL'si.|  
|`pChainContext`|İmzalayan zincirini bağlamı. Bkz: [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) yapısı.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
