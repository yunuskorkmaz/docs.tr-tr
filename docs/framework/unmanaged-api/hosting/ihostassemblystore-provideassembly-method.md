---
title: IHostAssemblyStore::ProvideAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e32d48931177a42dd14092b4052370764a217abe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly Yöntemi
Tarafından başvurulmuyor bir derlemesine başvuru alır [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) sağlayıcıdan döndürülen [Ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md). Ortak dil çalışma zamanı (CLR) çağırır `ProvideAssembly` listede görünmeyen her derleme için.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pBindInfo`  
 [in] Bir işaretçi bir [Assemblybindınfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) ana bilgisayar varlığı veya yokluğuna göre herhangi bir sürüm oluşturma ilkesi de dahil olmak üzere, belirli bir bağlama özellikleri belirlemek için kullanır örneği ve bağlamak için hangi derleme.  
  
 `pAssemblyId`  
 [out] Bunun için istenen derlemesi için benzersiz bir tanımlayıcı için bir işaretçi `IStream`.  
  
 `pHostContext`  
 [out] Bir platform gerek kalmadan istenen derleme kanıtı belirlemek için kullanılan konak özgü veriler için bir işaretçi çağrısı çağırır. `pHostContext` karşılık gelen <xref:System.Reflection.Assembly.HostContext%2A> yönetilen özelliği <xref:System.Reflection.Assembly> sınıfı.  
  
 `ppStmAssemblyImage`  
 [out] Adresine bir işaretçi bir `IStream` yüklenmesi veya derlemenin bulunamamış olması, boş için taşınabilir yürütülebilir (PE) görüntüsünü içerir.  
  
 `ppStmPDB`  
 [out] Adresine bir işaretçi bir `IStream` , içeriyorsa program hata ayıklama (PDB) bilgileri ya da null .pdb dosyası bulunamadı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|COR_E_FILENOTFOUND (0X80070002)|İstenen derlemesi bulunamadı.|  
|E_NOT_SUFFICIENT_BUFFER|Belirtilen arabellek boyutu `pAssemblyId` döndürmek için konak istediği tanımlayıcı tutmak için yeterince büyük değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 İçin kimlik değeri döndürülen `pAssemblyId` ana bilgisayar tarafından belirtilir. Tanımlayıcıları bir işlem yaşam süresi içinde benzersiz olmalıdır. CLR akış için benzersiz bir tanımlayıcı olarak bu değeri kullanır. Her değer için değerleri karşı denetler `pAssemblyId` diğer çağrı tarafından döndürülen `ProvideAssembly`. Ana bilgisayar aynı döndürürse `pAssemblyId` için başka bir değer `IStream`, CLR, akış içeriğini zaten eşlenmiş olup olmadığını denetler. Bu durumda, var olan kopyasını yeni bir eşleme yerine görüntü çalışma zamanı yükler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
