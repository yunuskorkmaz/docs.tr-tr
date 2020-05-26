---
title: IHostSecurityManager::OpenThreadToken Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
ms.openlocfilehash: 85c7308f794929d753b50f58f69168f67a31cb85
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803883"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken Yöntemi
Şu anda yürütülmekte olan iş parçacığıyla ilişkili olan isteğe bağlı erişim belirtecini açar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwDesiredAccess`  
 'ndaki İş parçacığı belirtecine istenen erişim türlerini belirten bir erişim değerleri maskesi. Bu değerler Win32 `OpenThreadToken` işlevinde tanımlanmıştır. İstenen erişim türleri, izin verilecek veya reddedilecek erişim türlerini belirleyen belirtecin kısıtlı erişim denetim listesine (DACL) göre mutabık kılınmakta.  
  
 `bOpenAsSelf`  
 [in] `true` erişim denetiminin, çağıran iş parçacığı için işlemin güvenlik bağlamı kullanılarak yapılması gerektiğini belirtmek için; `false`erişim denetiminin, çağıran iş parçacığının güvenlik bağlamı kullanılarak gerçekleştirilmesi gerektiğini belirtmek için. İş parçacığı bir istemciyi taklit alıyorsa, güvenlik bağlamı bir istemci işlemi olabilir.  
  
 `phThreadToken`  
 dışı Yeni açılan erişim belirtecine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostSecurityManager::OpenThreadToken`aynı ada sahip karşılık gelen Win32 işlevine benzer şekilde davranır, ancak Win32 işlevi çağıranın rastgele bir iş parçacığına bir tutamacı geçmesine izin verdiğinden, `IHostSecurityManager::OpenThreadToken` yalnızca çağıran iş parçacığıyla ilişkili belirteci açar.  
  
 `HANDLE`Tür, com uyumlu değildir, diğer bir deyişle, boyutu işletim sistemine özeldir ve özel sıralama gerektirir. Bu nedenle, bu belirteç yalnızca işlem içinde, CLR ile ana bilgisayar arasında kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostSecurityContext Arabirimi](ihostsecuritycontext-interface.md)
- [IHostSecurityManager Arabirimi](ihostsecuritymanager-interface.md)
