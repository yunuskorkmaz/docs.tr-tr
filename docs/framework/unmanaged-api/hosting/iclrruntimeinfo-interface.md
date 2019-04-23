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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 213fa9fda6b154d4548b4163cc7b5890bfcfb49c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186998"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo Arabirimi
Bir belirli ortak dil çalışma zamanı Modülü (CLR), sürüm, dizin ve yükleme durumu dahil olmak üzere bilgi döndüren yöntemler sağlar. Bu arabirim çalışma zamanı başlatma olmadan özel çalışma zamanı işlevselliği de sağlar. Çalışma zamanı göreli içerir [LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) yöntemi, çalışma zamanı modülü özgü [GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) yöntemi ve çalışma zamanı tarafından sağlanan arabirimleri aracılığıyla [Getınterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)yöntemi.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)|Bu çalışma zamanı tüm eski CLR sürüm 2 etkinleştirme İlkesi kararları için bağlar.|  
|[GetDefaultStartupFlags Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getdefaultstartupflags-method.md)|CLR başlangıç bayrakları ve ana bilgisayar yapılandırma dosyası alır.|  
|[GetInterface Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|Geçerli işleme CLR yükler ve çalışma zamanı arabirim işaretçileri gibi döndürür [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) ve [Imetadatadispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md). Bu yöntem tüm yerini `CorBindTo*` işlevleri.|  
|[GetProcAddress Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|Bu arabirim ile ilişkili CLR öğesinden dışarı aktarılan belirtilen işlevin adresini alır. Bu yöntem yerine geçer [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) yöntemi.|  
|[GetRuntimeDirectory Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|Bu arabirim ile ilişkili CLR yükleme dizinini alır. Bu yöntem yerine geçer [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) yöntemi.|  
|[GetVersionString Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|Ortak dil çalışma zamanı (CLR) sürüm bilgileri ile ilişkili alır bir verilen [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi. Bu yöntem yerine geçer [Getrequestedruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) ve [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) yöntemleri.|  
|[IsLoadable Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloadable-method.md)|Bu arabirimi ile ilişkili çalışma zamanı dikkate alarak, geçerli işlem içine yüklenmiş olup olmadığını gösteren zaten işlem içine yüklenmiş diğer çalışma zamanları.|  
|[IsLoaded Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|CLR ile ilişkili olup olmadığını gösteren [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi, işlem içine yüklenir.|  
|[IsStarted Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|CLR, ile ilişkili olup olmadığını gösteren [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi başlatıldı.|  
|[LoadErrorString Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|HRESULT değerini belirtilen kültür için bir uygun hata iletisine çevirir. Bu yöntem yerine geçer [LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md) ve [LoadStringRCEx](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md) yöntemleri.|  
|[LoadLibrary Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|Bir kitaplığı tarafından temsil edilen CLR framework dizininin yükleyen bir [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi. Bu yöntem yerine geçer [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) yöntemi.|  
|[SetDefaultStartupFlags Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)|CLR başlangıç bayrakları ve ana bilgisayar yapılandırma dosyasını ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
