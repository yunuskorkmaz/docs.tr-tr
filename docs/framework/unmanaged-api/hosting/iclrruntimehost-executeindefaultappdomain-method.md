---
description: ': ICLRRuntimeHost:: ExecuteInDefaultAppDomain yöntemi hakkında daha fazla bilgi edinin'
title: ICLRRuntimeHost::ExecuteInDefaultAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
ms.openlocfilehash: 0fae9be69cf67da252dcdb423432ec922c0b00ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785145"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a>ICLRRuntimeHost::ExecuteInDefaultAppDomain Yöntemi

Belirtilen yönetilen derlemede belirtilen türde belirtilen metodu çağırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pwzAssemblyPath`  
 'ndaki <xref:System.Reflection.Assembly> Yöntemi çağrılacak öğesini tanımlayan öğesine yolu <xref:System.Type> .  
  
 `pwzTypeName`  
 'ndaki <xref:System.Type> Çağrılacak yöntemi tanımlayan öğesinin adı.  
  
 `pwzMethodName`  
 'ndaki Çağrılacak yöntemin adı.  
  
 `pwzArgument`  
 'ndaki Yönteme geçirilecek dize parametresi.  
  
 `pReturnValue`  
 dışı Çağrılan yöntem tarafından döndürülen tamsayı değeri.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ExecuteInDefaultAppDomain` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürürse, CRL artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 Çağrılan yöntem aşağıdaki imzaya sahip olmalıdır:  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 , `pwzMethodName` çağrılan yöntemin adını temsil eder ve `pwzArgument` Bu yönteme parametre olarak geçirilen dize değerini temsil eder. HRESULT değeri S_OK olarak ayarlandıysa, `pReturnValue` çağrılan yöntem tarafından döndürülen tamsayı değerine ayarlanır. Aksi takdirde, `pReturnValue` ayarlı değildir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeHost Arabirimi](iclrruntimehost-interface.md)
