---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
ms.openlocfilehash: b6852519da6cf4e12669aa2efa24862053adbc03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674248"
---
# <a name="axl_authenticode_timestamper_info-structure"></a>AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı

Authenticode zaman Stamper bilgilerini tanımlar.  
  
## <a name="syntax"></a>Syntax  
  
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
|`pChainContext`|Zaman stamplayıcı zinciri bağlamı.  [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) yapısına bakın.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
