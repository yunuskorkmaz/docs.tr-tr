---
title: CertFreeAuthenticodeSignerInfo İşlevi
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 357a2ca0ffc733adb14a21624cbe28fb754c8240
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776734"
---
# <a name="certfreeauthenticodesignerinfo-function"></a>CertFreeAuthenticodeSignerInfo İşlevi
[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) yapısı için ayrılan kaynakları boşaltır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pSignerInfo`  
 [in, out] Yayımlanacak imzalayan bilgileri. Bkz. [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) yapısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`işlev başarılı olursa. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
