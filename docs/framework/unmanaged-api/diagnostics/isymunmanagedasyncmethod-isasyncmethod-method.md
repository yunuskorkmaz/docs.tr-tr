---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f5bf8252986ffa90ea5380d5342595cb91e5419
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424947"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a>ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi
Metodu zaman uyumsuz bilgi olup olmadığını denetler.  
  
 Bu yöntem döndürürse `FALSE` sonra da bu arabirimi diğer yöntemleri çağırmak için geçersiz. Tüm iade edecek `E_UNEXPECTED` bu durumda.  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `HRESULT`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedAsyncMethod Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
