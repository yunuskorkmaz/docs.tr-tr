---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
ms.openlocfilehash: 036397928703aea6199a59ae9c1e66153c30ec7b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132499"
---
# <a name="axl_authenticode_timestamper_info-structure"></a>AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı
Authenticode zaman Stamper bilgilerini tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`cbSize`|Bu yapının boyutu.|  
|`dwError`|Hata kodu.|  
|`algHash`|Karma algoritması.|  
|`ftTimestamp`|Zaman damgasının saati.|  
|`pChainContext`|Zaman stamplayıcı zinciri bağlamı.  Bkz. [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) yapısı.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
