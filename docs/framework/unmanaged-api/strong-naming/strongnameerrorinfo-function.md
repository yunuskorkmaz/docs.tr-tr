---
title: StrongNameErrorInfo İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameErrorInfo
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameErrorInfo
helpviewer_keywords:
- StrongNameErrorInfo function [.NET Framework strong naming]
ms.assetid: e91bf8c3-7c26-4732-938e-2e5b04abfc99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f495500b087b9e24936acd414f1aff463d7f64
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781069"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo İşlevi
Tanımlayıcı ad işlevlerden biri tarafından tetiklendi son hata kodu alır.  
  
 Bu işlev kullanım dışı bırakıldı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT StrongNameErrorInfo ();   
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Tanımlayıcı ad işlevlerden biri tarafından ayarlanmış son COM hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımlayıcı ad yöntemlerin çoğu, basit bir iade `true` veya `false` başarılı olarak tamamlanmasına göstergesi. Kullanım `StrongNameErrorInfo` tanımlayıcı ad işlevleri tarafından oluşturulan son hata belirten HRESULT almak için işlevi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
