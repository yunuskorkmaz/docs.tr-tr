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
ms.openlocfilehash: 445c833d10631341ef7ad579eaff8ddd96be3428
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684856"
---
# <a name="enumcustomattributes-method"></a>EnumCustomAttributes Yöntemi

Derleme düzeyi özel özniteliklerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 Numaralandırılacak özniteliklerin türü. `mdTokenNill`Tüm öznitelikler için kullanın.  
  
 `rCustomValues`  
 Özel öznitelik belirteçleri alır.  
  
 `cMax`  
 Dizinin boyutunu belirtir `rCustomValues` .  
  
 `pcCustomValues`  
 İsteğe bağlı olarak belirteç değerleri sayısını alır.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
