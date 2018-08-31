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
ms.openlocfilehash: 9ad328d484ba01e22557d7d23d1cfa21813de9c8
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332753"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo İşlevi
Tanımlayıcı ad işlevlerden biri tarafından tetiklendi son hata kodu alır.  
  
 Bu işlev kullanım dışı bırakıldı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT StrongNameErrorInfo ();   
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Tanımlayıcı ad işlevlerden biri tarafından ayarlanmış son COM hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımlayıcı ad yöntemlerin çoğu, basit bir iade `true` veya `false` başarılı olarak tamamlanmasına göstergesi. Kullanım `StrongNameErrorInfo` tanımlayıcı ad işlevleri tarafından oluşturulan son hata belirten HRESULT almak için işlevi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** StrongName.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanımlayıcı adlandırma genel statik işlevleri](https://msdn.microsoft.com/library/efa715df-e8cc-48f2-9ec4-26586f0dc8d0)
