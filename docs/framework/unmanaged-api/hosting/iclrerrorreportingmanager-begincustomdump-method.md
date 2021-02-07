---
description: ': ICLRErrorReportingManager:: BeginCustomDump Yöntemi hakkında daha fazla bilgi edinin'
title: ICLRErrorReportingManager::BeginCustomDump Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
ms.openlocfilehash: 3f8498068d50ffc6ea00cf4f08f969c92f010d6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689488"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a>ICLRErrorReportingManager::BeginCustomDump Yöntemi

Hata raporlama için özel yığın dökümlerinin yapılandırmasını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwFlavor`  
 'ndaki Özel yığın dökümünden sonra oluşturulacak yığın dökümü türünü gösteren bir [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) değeri.  
  
 `dwNumItems`  
 'ndaki `items` Dizinin uzunluğu. `dwFlavor`DUMP_FLAVOR_Mini değilse, sıfır olmalıdır `dwNumItems` .  
  
 `items`  
 'ndaki Mini döküme eklenecek öğeleri belirten bir [Customdumpitem](customdumpitem-structure.md) örnekleri dizisi. `dwFlavor`DUMP_FLAVOR_Mini değilse, null olmalıdır `items` .  
  
 `dwReserved`  
 'ndaki Gelecekte kullanılmak üzere ayrılmıştır.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 `BeginCustomDump`Yöntemi özel yığın dökümü yapılandırmasını ayarlar. [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) yöntemi özel yığın dökümü yapılandırmasını temizler ve ilişkili tüm durumları serbest bırakır. Özel yığın dökümü tamamlandıktan sonra çağrılmalıdır.  
  
> [!IMPORTANT]
> Çağırma hatası, `EndCustomDump` belleğin sızmasını sağlar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CustomDumpItem Yapısı](customdumpitem-structure.md)
- [ECustomDumpFlavor Numaralandırması](ecustomdumpflavor-enumeration.md)
- [ICLRErrorReportingManager Arabirimi](iclrerrorreportingmanager-interface.md)
