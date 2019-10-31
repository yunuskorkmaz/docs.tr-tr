---
title: ICLRRuntimeInfo Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo
helpviewer_keywords:
- ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 287e5ede-b3a7-4ef8-a756-4fca3f285a82
topic_type:
- apiref
ms.openlocfilehash: f6608b03df80fa37ebf5049b53bce46da3e155e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120369"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo Arabirimi
Sürüm, dizin ve yükleme durumu dahil olmak üzere belirli bir ortak dil çalışma zamanı (CLR) hakkında bilgi döndüren yöntemler sağlar. Bu arabirim, çalışma zamanını başlatmadan çalışma zamanına özgü işlevselliği de sağlar. Çalışma zamanı-göreli [LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) yöntemi, çalışma zamanı modülüne özel [GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) yöntemi ve [GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) yöntemi aracılığıyla çalışma zamanı tarafından sağlanmış arabirimler içerir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)|Tüm eski CLR sürüm 2 etkinleştirme ilkesi kararları için bu çalışma zamanını bağlar.|  
|[GetDefaultStartupFlags Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getdefaultstartupflags-method.md)|CLR başlangıç bayraklarını ve ana bilgisayar yapılandırma dosyasını alır.|  
|[GetInterface Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|CLR 'yi geçerli işleme yükler ve [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) ve [ımetadatadağıtıcı](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)gibi çalışma zamanı arabirimi işaretçilerini döndürür. Bu yöntem tüm `CorBindTo*` işlevlerinin yerini alır.|  
|[GetProcAddress Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|Bu arabirimle ilişkili CLR 'den aktarılmış belirtilen işlevin adresini alır. Bu yöntem [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) yönteminin yerini alır.|  
|[GetRuntimeDirectory Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|Bu arabirimle ilişkili CLR 'nin yükleme dizinini alır. Bu yöntem [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) yönteminin yerini alır.|  
|[GetVersionString Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|Belirli bir [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimiyle ilişkili ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır. Bu yöntem, [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) ve [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) yöntemlerinin yerini alır.|  
|[IsLoadable Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloadable-method.md)|Bu arabirimle ilişkili çalışma zamanının geçerli işleme yüklenip yüklenmediğini, işleme daha önce yüklenmiş olabilecek diğer çalışma zamanlarını hesaba ayırarak gösterir.|  
|[IsLoaded Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ARABIRIMIYLE ilişkilendirilen clr 'nin bir işleme yüklenip yüklenmediğini belirtir.|  
|[IsStarted Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ARABIRIMIYLE ilişkili clr 'nin başlatılmış olup olmadığını gösterir.|  
|[LoadErrorString Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|Belirtilen kültür için bir HRESULT değerini uygun bir hata iletisine çevirir. Bu yöntem, [LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md) ve [LoadStringRCEx](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md) yöntemlerinin yerini alır.|  
|[LoadLibrary Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|Bir [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimiyle temsıl edilen clr 'nin çerçeve dizininden bir kitaplık yükler. Bu yöntem [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) yönteminin yerini alır.|  
|[SetDefaultStartupFlags Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)|CLR başlangıç bayraklarını ve ana bilgisayar yapılandırma dosyasını ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
