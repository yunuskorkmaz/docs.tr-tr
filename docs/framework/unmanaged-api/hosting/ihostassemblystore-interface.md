---
title: IHostAssemblyStore Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore
helpviewer_keywords: IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 284afbe73bea28a0aafe8d5e9e030c43be94aea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore Arabirimi
Derlemeler ve modüller ortak dil çalışma zamanı (CLR) bağımsız olarak yüklemek bir konak izin yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ProvideAssembly yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|Tarafından başvurulmuyor bir derlemesine başvuru alır [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) çağrısından döndürülen [Ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).|  
|[ProvideModule yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|Bir derlemeyi ya da bağlantılı (katıştırılmış değil) kaynak dosyası içinde bir modüle giderir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostAssemblyStore`derleme kimliğine verimli bir şekilde bağlı derlemeler yüklemek bir konak için bir yol sağlar. Konak döndürerek derlemelerini yükleyen `IStream` baytları doğrudan noktası örnekleri.  
  
 CLR bir ana bilgisayar uyguladı olup olmadığını belirler `IHostAssemblyStore` çağırarak `IHostAssemblyManager::GetNonHostAssemblyStores` başlatma bağlıdır. Bu konak, örneğin, kullanıcı derlemeleri bağlama denetlemek için ancak çalışma zamanı için .NET Framework derlemeleri bağlamak için kullanır sağlar.  
  
> [!NOTE]
>  Uygulaması sağlama içinde `IHostAssemblyStore`, ana bilgisayarı tarafından başvurulan değil tüm derlemelerde çözmek yapma belirtir `ICLRAssemblyReferenceList` döndürülen `IHostAssemblyManager::GetNonHostStoreAssemblies`.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0 tarafından sağlanan gibi bir derleme yerel görüntü yüklemek ana bilgisayar için bir yol sağlamaz [yerel Görüntü Oluşturucu (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) yardımcı programı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iclrassemblyreferencelist arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [Ihostassemblymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [Barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
