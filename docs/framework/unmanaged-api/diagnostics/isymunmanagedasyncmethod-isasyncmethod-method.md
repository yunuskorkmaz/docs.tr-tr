---
description: 'Şu konuda daha fazla bilgi edinin: ırivmanagedasyncmethod:: IsAsyncMethod yöntemi'
title: ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 4b151f5367bac5fd92cc8237492cad6dacfb8e88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790262"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a>ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi

Metodun zaman uyumsuz bilgilere sahip olup olmadığını denetler.  
  
 Bu yöntem döndürürse `FALSE` , bu arabirimdeki diğer yöntemleri çağırmak geçersizdir. Hepsi `E_UNEXPECTED` Bu durumda döndürülür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a>Dönüş Değeri  

 `HRESULT` döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedAsyncMethod Arabirimi](isymunmanagedasyncmethod-interface.md)
