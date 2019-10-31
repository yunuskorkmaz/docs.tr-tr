---
title: IsFrameworkAssembly İşlevi
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
ms.openlocfilehash: e30b6f2d2254d2d107c4c82a2c5664850ce6ec23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123063"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly İşlevi
Belirtilen derlemenin yönetilip yönetilmediğini gösteren bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzAssemblyReference`  
 'ndaki Denetlenecek derlemenin adı.  
  
 `pbIsFrameworkAssembly`  
 dışı Derlemenin yönetilip yönetilmediğini gösteren bir Boole değeri.  
  
 `pwzFrameworkAssemblyIdentity`  
 'ndaki Derlemenin benzersiz kimliğini içeren bir Uncanonicalized dizesi.  
  
 `pccSize`  
 'ndaki `pwzFrameworkAssemblyIdentity`boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 `pwzAssemblyReference` parametresi, bir derlemenin adını içeren bir karakter dizesinin bir işaretçisidir.  
  
 Bu derleme .NET Framework bir parçasıysa, `pbIsFrameworkAssembly` parametresi bir `true`Boolean değeri içerir.  
  
 Adlandırılmış derleme .NET Framework bir parçası değilse veya `pwzAssemblyReference` parametresi bir derlemeyi isimlendirilemez `pbIsFrameworkAssembly` Boolean değeri `false`içerecektir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
