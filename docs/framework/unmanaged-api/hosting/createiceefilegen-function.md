---
description: 'Şu konuda daha fazla bilgi edinin: CreateICeeFileGen Işlevi'
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
ms.openlocfilehash: 10aefaad4dd1173e4ef55f727371bab508e2d40c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716939"
---
# <a name="createiceefilegen-function"></a>CreateICeeFileGen İşlevi

Bir [ICeeFileGen](iceefilegen-class.md) nesnesi oluşturur.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
