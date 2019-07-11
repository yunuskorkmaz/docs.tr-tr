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
ms.openlocfilehash: 989d046bba1ba3170649e9d908a850bd1177fdd2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773837"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly İşlevi
Belirtilen derleme yönetilip yönetilmediğini belirten bir değer alır.  
  
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
