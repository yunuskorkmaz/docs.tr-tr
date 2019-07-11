---
title: EnumCustomAttributes Yöntemi
ms.date: 03/30/2017
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09ccf731f0494b6eda49f6a15d04970a723c473b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742061"
---
# <a name="enumcustomattributes-method"></a>EnumCustomAttributes Yöntemi
Derleme düzeyi özel öznitelikleri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  
 `hEnum`  
 Numaralandırıcı tanıtıcısı.  
  
 `tkType`  
 Numaralandırılacak özniteliklerin türü. Kullanım `mdTokenNill` tüm öznitelikler için.  
  
 `rCustomValues`  
 Özel öznitelikler belirteçlerini alır.  
  
 `cMax`  
 Boyutunu belirtir `rCustomValues` dizisi.  
  
 `pcCustomValues`  
 İsteğe bağlı olarak belirteç değerlerin sayısını alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
