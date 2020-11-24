---
title: CallFunctionShim İşlevi
ms.date: 03/30/2017
api_name:
- CallFunctionShim
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CallFunctionShim
helpviewer_keywords:
- CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type:
- apiref
ms.openlocfilehash: f72c987294d7768eacf112c622ab15494fb75e34
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685792"
---
# <a name="callfunctionshim-function"></a>CallFunctionShim İşlevi

Belirtilen kitaplıkta belirtilen ad ve parametrelere sahip işleve bir çağrı yapar.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `szDllName`  
 'ndaki İşlevi içeren kitaplığın adı.  
  
 `szFunctionName`  
 'ndaki İşlevin adı.  
  
 `lpvArgument1`  
 'ndaki İşleve geçirilecek ilk bağımsız değişken.  
  
 `lpvArgument2`  
 'ndaki İşleve geçirilecek ikinci bağımsız değişken.  
  
 `szVersion`  
 'ndaki İşlevin bulunduğu kitaplığın sürümü.  
  
 `pvReserved`  
 'ndaki Gelecekte kullanılmak üzere ayrılmıştır. Bu parametreye sıfır geçirin.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
