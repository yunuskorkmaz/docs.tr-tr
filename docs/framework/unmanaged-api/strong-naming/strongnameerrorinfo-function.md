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
ms.openlocfilehash: d5eedc34b75d3a0c02969c06454b0f7ec942ed17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176948"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo İşlevi
Güçlü ad işlevlerinden biri tarafından yükseltilen son hata kodunu alır.  
  
 Bu işlev amortismana kaldırıldı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT StrongNameErrorInfo ();
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Güçlü ad işlevlerinden biri tarafından ayarlanan son COM hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  
 Güçlü ad yöntemlerinin çoğu `true` basit `false` veya başarılı bir tamamlama göstergesi döndürün. Güçlü `StrongNameErrorInfo` ad işlevleri tarafından oluşturulan son hatayı belirten bir HRESULT almak için işlevi kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** StrongName.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
