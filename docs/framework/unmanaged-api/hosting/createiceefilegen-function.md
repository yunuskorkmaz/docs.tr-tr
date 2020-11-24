---
title: CreateICeeFileGen İşlevi
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: 454cfa2dd1b676f32649050625b1074fbd776d54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673338"
---
# <a name="createiceefilegen-function"></a>CreateICeeFileGen İşlevi

Bir [ICeeFileGen](iceefilegen-class.md) nesnesi oluşturur.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ceeFileGen`  
 dışı Yeni bir nesnenin adresine yönelik bir işaretçi `ICeeFileGen` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, standart COM hata kodlarını döndürür.  
  
## <a name="remarks"></a>Açıklamalar  

 `ICeeFileGen`Nesnesi, ortak dil çalışma zamanı (CLR) taşınabilir yürütülebilir (PE) dosyaları oluşturmak için kullanılır.  
  
 Sona erdiğinde nesneyi yok etmek için [Destroııceefilegen](destroyiceefilegen-function.md) işlevini çağırın `ICeeFileGen` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** ICeeFileGen. h  
  
 **Kitaplık:** MSCorPE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
