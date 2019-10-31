---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 0ea4c21e9e6a49d7bbbad5e1853598c440cd6410
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129207"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a>ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi
Metodun zaman uyumsuz bilgilere sahip olup olmadığını denetler.  
  
 Bu yöntem `FALSE` döndürürse, bu arabirimdeki diğer yöntemleri çağırmak geçersizdir. Bu durumda `E_UNEXPECTED` hepsi döndürülür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a>Dönüş Değeri  
 `HRESULT`döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedAsyncMethod Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
