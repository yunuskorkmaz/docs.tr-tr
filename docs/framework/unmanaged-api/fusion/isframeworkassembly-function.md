---
description: 'Daha fazla bilgi edinin: IsFrameworkAssembly Işlevi'
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
ms.openlocfilehash: 8f264df7b1ae5c494298b11ebd94cc93aed5543a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800025"
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
 'ndaki Boyutu `pwzFrameworkAssemblyIdentity` .  
  
## <a name="remarks"></a>Açıklamalar  

 Parametresi, bir `pwzAssemblyReference` derlemenin adını içeren bir karakter dizesinin bir işaretçisidir.  
  
 Bu derleme .NET Framework bir parçasıysa, `pbIsFrameworkAssembly` parametresi bir Boolean değeri içerir `true` .  
  
 Adlandırılmış derleme .NET Framework bir parçası değilse veya `pwzAssemblyReference` parametre bir derlemeyi `pbIsFrameworkAssembly` Isimlendirilemez, Boolean değeri içerir `false` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
