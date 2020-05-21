---
title: ICLRRuntimeInfo::IsLoaded Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: 3275a69683a312340f35841815685066def10b23
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762532"
---
# <a name="iclrruntimeinfoisloaded-method"></a>ICLRRuntimeInfo::IsLoaded Yöntemi
[ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimiyle ilişkili ortak dil çalışma ZAMANıNıN (CLR) bir işleme yüklenip yüklenmediğini gösterir. Çalışma zamanı, aynı zamanda başlatılmadan de yüklenebilir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hndProcess`  
 'ndaki İşlem için bir tanıtıcı.  
  
 `pbLoaded`  
 [out] `true` CLR işleme yüklenirse, Aksi takdirde, `false` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pbLoaded`null.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, aşağıdaki işlevler ve arabirimler ile geriye dönük olarak uyumludur:  
  
- [ICorRuntimeHost](icorruntimehost-interface.md) arabirimi (.NET Framework sürüm 1 barındırma API 'si).  
  
- [ICLRRuntimeHost](iclrruntimehost-interface.md) arabirimi (.NET Framework 2,0 barındırma API 'si).  
  
- Kullanım dışı bırakılan `CorBindTo*` işlevler (bkz. .NET Framework 2,0 barındırma API 'Sindeki [kullanım dışı clr barındırma işlevleri](deprecated-clr-hosting-functions.md) ).  
  
 Bir ana bilgisayar, `CorBindTo*` clr 'nin belirli bir sürümünü oluşturmak Için [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) işlevi gibi kullanım dışı işlevlerden birini çağırabilir. Konak daha sonra [ICLRMetaHost:: GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) metodunu çağırabilir ve bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi elde etmek için aynı sürüm numarasını belirtebilir.  
  
 Daha sonra ana bilgisayar `IsLoaded` döndürülen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimindeki yöntemi çağırırsa `pbLoaded` `true` ; Aksi takdirde, döndürür `false` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeInfo Arabirimi](iclrruntimeinfo-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Barındırma](index.md)
