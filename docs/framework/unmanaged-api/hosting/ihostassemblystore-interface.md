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
ms.openlocfilehash: 87fe0b10f0a1eefa8154c40d39b54285990c410c
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805040"
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore Arabirimi
Bir konağın ortak dil çalışma zamanından (CLR) bağımsız olarak derlemeleri ve modülleri yüklemesine izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ProvideAssembly Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|[IHostAssemblyManager:: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)çağrısından döndürülen [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) tarafından başvurulmayan bir derlemeye başvuru alır.|  
|[ProvideModule Yöntemi](ihostassemblystore-providemodule-method.md)|Derleme içindeki bir modülü veya bağlı (gömülü değil) kaynak dosyasını çözer.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostAssemblyStore`bir konağın derleme kimliği temelinde derlemeleri etkin bir şekilde yüklemesi için bir yol sağlar. Ana bilgisayar, `IStream` doğrudan baytlara işaret eden örnekleri döndürerek derlemeleri yükler.  
  
 CLR, `IHostAssemblyStore` başlatma sonrasında çağırarak bir konağın uygulanıp uygulanmadığı belirler `IHostAssemblyManager::GetNonHostAssemblyStores` . Bu, örneğin, ana bilgisayarın kullanıcı Derlemeleriyle bağlamayı denetlemesini, ancak .NET Framework derlemelerine bağlamak için çalışma zamanına güvenmelerini sağlar.  
  
> [!NOTE]
> Uygulamasının bir uygulamasını sağlamak `IHostAssemblyStore` için konak, öğesinden döndürülen tarafından başvurulmayan tüm derlemeleri çözümleme amacını belirtir `ICLRAssemblyReferenceList` `IHostAssemblyManager::GetNonHostStoreAssemblies` .  
  
> [!NOTE]
> .NET Framework sürüm 2,0, ana bilgisayarın [Yerel Görüntü Oluşturucu (Ngen. exe)](../../tools/ngen-exe-native-image-generator.md) yardımcı programı tarafından sağlandığı şekilde bir derlemenin yerel görüntüsünü yüklemesi için bir yol sağlamaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyReferenceList Arabirimi](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager Arabirimi](ihostassemblymanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
