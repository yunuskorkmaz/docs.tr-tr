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
ms.openlocfilehash: dd83fc6a7f553b54cc2acd5e9a93d8d58747d75a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141709"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo İşlevi
Tanımlayıcı ad işlevlerinden biri tarafından oluşturulan son hata kodunu alır.  
  
 Bu işlev kullanım dışı bırakıldı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT StrongNameErrorInfo ();   
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Tanımlayıcı ad işlevlerinden biri tarafından ayarlanan son COM hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımlayıcı ad yöntemlerinin çoğu, başarılı tamamlama işleminin basit bir `true` veya `false` göstergesi döndürür. Güçlü ad işlevleri tarafından oluşturulan son hatayı belirten bir HRESULT almak için `StrongNameErrorInfo` işlevini kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
