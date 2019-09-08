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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 269e3702c21532f377735ba6087abb1603dde4f7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796322"
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
 'ndaki Boyutu `pwzFrameworkAssemblyIdentity`.  
  
## <a name="remarks"></a>Açıklamalar  
 `pwzAssemblyReference` Parametresi, bir derlemenin adını içeren bir karakter dizesinin bir işaretçisidir.  
  
 Bu derleme .NET Framework bir parçasıysa, `pbIsFrameworkAssembly` parametresi bir Boolean `true`değeri içerir.  
  
 Adlandırılmış derleme .NET Framework bir parçası değilse veya `pwzAssemblyReference` parametre bir derlemeyi isimlendirilemez, `pbIsFrameworkAssembly` Boolean değeri `false`içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
