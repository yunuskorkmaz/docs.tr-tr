---
title: IHostAssemblyStore Arabirimi
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3714f31d0ab58584a8671055cf4c607f04a832c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611065"
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore Arabirimi
Derlemeler ve modüller ortak dil çalışma zamanı (CLR) bağımsız olarak yüklemek konak izin vermek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ProvideAssembly Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|Tarafından başvurulmuyor bir derlemeye bir başvuru alır [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) çağrısından döndürülen [Ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).|  
|[ProvideModule Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|Bir derleme veya bağlı (embedded değil) kaynak dosyası içinde bir modüle çözümleniyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostAssemblyStore` verimli bir şekilde derleme kimliğine dayalı derlemeler yüklemek için bir konak için bir yol sağlar. Döndürerek ana bilgisayar bütünleştirilmiş kodları yükler `IStream` doğrudan baytları gösteren örnekler.  
  
 CLR bir konağa uygulanan olup olmadığını belirler. `IHostAssemblyStore` çağırarak `IHostAssemblyManager::GetNonHostAssemblyStores` başlatma temel alır. Bu konak, örneğin, kullanıcı bütünleştirilmiş kodları bağlamayı denetlemek için ancak .NET Framework derlemeleri bağlamak için çalışma zamanı üzerinde yararlanmayı sağlar.  
  
> [!NOTE]
>  Sağlama uygulaması içinde `IHostAssemblyStore`, konak tarafından başvurulmuyor tüm derlemelerin çözümlenecek konuşmanın niyetini belirtir `ICLRAssemblyReferenceList` döndürüldüğü `IHostAssemblyManager::GetNonHostStoreAssemblies`.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0 tarafından sağlanan bir derlemenin yerel görüntü yüklemek ana bilgisayar için bir yol sunmaz [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) yardımcı programı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
