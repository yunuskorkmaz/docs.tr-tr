---
title: CertFreeAuthenticodeTimestamperInfo İşlevi
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c37a9af6a1532d03fa04ca151605cef7ab5244e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401774"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a>CertFreeAuthenticodeTimestamperInfo İşlevi
İçin ayrılan kaynakları serbest bırakır [axl_authentıcode_tımestamper_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) yapısı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pTimestamperInfo`  
 [içinde out] Yayımlanacak zaman stamper bilgileri. Bkz: [axl_authentıcode_tımestamper_ınfo](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) yapısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK` işlev başarılı olursa. Aksi takdirde bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
