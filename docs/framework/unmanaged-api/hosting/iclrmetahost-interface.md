---
title: ICLRMetaHost Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
ms.openlocfilehash: bb7c3659930f308328cba121c06a88cb6a95eb26
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504166"
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost Arabirimi
Ortak dil çalışma zamanının (CLR) sürüm numarasına göre belirli bir sürümünü döndüren, tüm yüklü CLRs 'leri listeleme, belirli bir işlemde yüklü olan tüm çalışma zamanlarını listeleme, bir derlemeyi derlemek için kullanılan CLR sürümünü bulma, temiz çalışma zamanı ile bir işlemden çıkma ve eski API bağlamasını sorgulama gibi yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes Yöntemi](iclrmetahost-enumerateinstalledruntimes-method.md)|Bir bilgisayarda yüklü her CLR sürümü için geçerli bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi işaretçisi içeren bir sabit listesi döndürür.|  
|[EnumerateLoadedRuntimes Yöntemi](iclrmetahost-enumerateloadedruntimes-method.md)|Belirli bir işlemde yüklenen her CLR için geçerli bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi işaretçisi içeren bir sabit listesi döndürür. Bu yöntem [GetVersionFromProcess](getversionfromprocess-function.md)'in yerini alır.|  
|[ExitProcess Yöntemi](iclrmetahost-exitprocess-method.md)|Tüm yüklenen çalışma zamanlarını sorunsuz bir şekilde kapatmaya çalışır ve sonra işlemi sonlandırır. [CorExitProcess](corexitprocess-function.md) işlevinin yerini alır.|  
|[GetRuntime Yöntemi](iclrmetahost-getruntime-method.md)|Belirli bir CLR sürümüne karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimini alır. Bu yöntem [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) bayrağıyla kullanılan [CorBindToRuntimeEx](corbindtoruntimeex-function.md) işlevinin yerini alır.|  
|[GetVersionFromFile Yöntemi](iclrmetahost-getversionfromfile-method.md)|Derlemenin özgün .NET Framework derleme sürümünü (meta verilerde depolanır), onun dosya yolu olarak alır. Bu yöntem, [GetFileVersion](getfileversion-function.md)'ın yerini alır.|  
|[QueryLegacyV2RuntimeBinding Yöntemi](iclrmetahost-querylegacyv2runtimebinding-method.md)|Eski etkinleştirme ilkesinin bağlı olduğu bir çalışma zamanını temsil eden bir arabirim döndürür. Örneğin, `useLegacyV2RuntimeActivationPolicy` Eski etkinleştirme API 'lerinin doğrudan kullanımı ile veya [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) yöntemini çağırarak, [ \<startup> öğe](../../configure-apps/file-schema/startup/startup-element.md) yapılandırma dosyası girişinde özniteliği kullanarak.|  
|[RequestRuntimeLoadedNotification Yöntemi](iclrmetahost-requestruntimeloadednotification-method.md)|CLR sürümü ilk yüklendiğinde belirtilen işlev işaretçisine geri çağırma garantisi verir, ancak henüz başlatılmamıştır. Bu yöntem [LockClrVersion](lockclrversion-function.md) yerine geçiyor|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirimin bir örneğini almanın tek yolu, aşağıdaki gibi [CLRCreateInstance](clrcreateinstance-function.md) işlevini çağırarak olur:  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Hosting](index.md)
