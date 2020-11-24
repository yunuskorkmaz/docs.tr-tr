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
ms.openlocfilehash: dc6bb5a137a50ec07f89f292e5d9beac4349c3c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674183"
---
# <a name="certfreeauthenticodesignerinfo-function"></a>CertFreeAuthenticodeSignerInfo İşlevi

[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) yapısı için ayrılan kaynakları boşaltır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pSignerInfo`  
 [in, out] Yayımlanacak imzalayan bilgileri. [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) yapısına bakın.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` işlev başarılı olursa. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
