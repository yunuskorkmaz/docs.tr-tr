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
ms.openlocfilehash: a905840c471a268c6b106c5e25baca9c36f485d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731068"
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
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Tanımlayıcı adlandırma genel statik işlevleri](https://msdn.microsoft.com/library/efa715df-e8cc-48f2-9ec4-26586f0dc8d0)
