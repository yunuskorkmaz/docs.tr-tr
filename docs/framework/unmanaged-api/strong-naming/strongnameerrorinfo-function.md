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
ms.openlocfilehash: 90abfcd573795ae529714e21b13f90d6e15c7dad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732274"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo İşlevi

Tanımlayıcı ad işlevlerinden biri tarafından oluşturulan son hata kodunu alır.  
  
 Bu işlev kullanım dışı bırakıldı.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT StrongNameErrorInfo ();
```  
  
## <a name="return-value"></a>Dönüş Değeri  

 Tanımlayıcı ad işlevlerinden biri tarafından ayarlanan son COM hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  

 Tanımlayıcı ad yöntemlerinin çoğu, başarılı bir tamamlamayı basit veya bir şekilde döndürür `true` `false` . `StrongNameErrorInfo`Tanımlayıcı ad işlevleri tarafından oluşturulan son hatayı belirten BIR HRESULT almak için işlevini kullanın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
