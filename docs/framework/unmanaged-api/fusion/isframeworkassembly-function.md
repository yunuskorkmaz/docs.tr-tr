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
ms.openlocfilehash: c3fd130759ab11b54b597d5c099c33dab93070ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly İşlevi
Belirtilen derleme yönetilen olup olmadığını belirten bir değer alır.  
  
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
 [out] Derleme yönetilen olup olmadığını gösteren bir Boole değeri.  
  
 `pwzFrameworkAssemblyIdentity`  
 [in] Derleme benzersiz kimliğini içeren bir uncanonicalized dize.  
  
 `pccSize`  
 [in] Boyutunu `pwzFrameworkAssemblyIdentity`.  
  
## <a name="remarks"></a>Açıklamalar  
 `pwzAssemblyReference` Bir işaretçi bir derleme adını içeren bir karakter dizesi parametresidir.  
  
 Bu derleme parçasıysa .NET Framework'ün `pbIsFrameworkAssembly` parametre bir Boole değeri içerecek `true`.  
  
 Adlandırılmış derlemesi .NET Framework'ün bir parçası değilse veya `pwzAssemblyReference` parametre bir derleme adı değil `pbIsFrameworkAssembly` bir Boole değeri içerecektir `false`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
