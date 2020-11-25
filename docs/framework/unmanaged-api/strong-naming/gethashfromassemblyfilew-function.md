---
title: GetHashFromAssemblyFileW İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
ms.openlocfilehash: b895c77850c0457fd2a152c1128c016093599f76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730987"
---
# <a name="gethashfromassemblyfilew-function"></a>GetHashFromAssemblyFileW İşlevi

Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır. Derleme dosyasının yolu Unicode dize olarak belirtilmelidir.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `wszFilePath`  
 'ndaki Karma hale getirilen dosyanın yolu. Bu parametre bir Unicode dize olmalıdır.  
  
 `piHashAlg`  
 [in, out] Karma algoritmayı belirten bir sabit. Varsayılan karma algoritması için sıfır kullanın.  
  
 `pbHash`  
 dışı Döndürülen karma arabelleği.  
  
 `cchHash`  
 'ndaki İstenen en büyük boyut `pbHash` .  
  
 `pchHash`  
 dışı Bayt cinsinden döndürülen boyut `pbHash` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetHashFromAssemblyFileW Yöntemi](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [GetHashFromAssemblyFile Yöntemi](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
