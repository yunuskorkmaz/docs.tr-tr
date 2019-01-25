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
ms.openlocfilehash: 3e231c4fa51e6e66cba6227233cf73dd1cd4ebbe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733928"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly İşlevi
Belirtilen derleme yönetilip yönetilmediğini belirten bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pwzAssemblyReference`  
 [in] Denetlenecek derlemenin adı.  
  
 `pbIsFrameworkAssembly`  
 [out] Derleme yönetilip yönetilmediğini belirten bir Boole değeri.  
  
 `pwzFrameworkAssemblyIdentity`  
 [in] Derlemenin benzersiz kimliği içeren uncanonicalized bir dize.  
  
 `pccSize`  
 [in] Boyutu `pwzFrameworkAssemblyIdentity`.  
  
## <a name="remarks"></a>Açıklamalar  
 `pwzAssemblyReference` Parametresi, bir derlemenin adını içeren bir karakter dizesine bir işaretçi.  
  
 Bu derleme parçasıysa .NET Framework'ün `pbIsFrameworkAssembly` parametresi bir Boolean değerini içerecek `true`.  
  
 Adlandırılmış derlemeyi .NET Framework'ün bir parçası değilse veya `pwzAssemblyReference` parametre, bir derleme adı değil `pbIsFrameworkAssembly` Boolean değerini içerecek `false`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Fusion Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
