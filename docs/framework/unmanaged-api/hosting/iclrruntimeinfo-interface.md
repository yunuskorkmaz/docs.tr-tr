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
ms.openlocfilehash: cc8225b6612c7bf07d220b20d515f64a346b9691
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo Arabirimi
Sürüm, dizin ve yük durumu da dahil olmak üzere bir belirli ortak dil çalışma zamanı Modülü (CLR) hakkında bilgi döndürmek yöntemleri sağlar. Bu arabirim çalışma zamanı başlatmadan çalışma zamanı özgü işlevselliği de sağlar. Çalışma zamanı göreli içeren [LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) yöntemi, çalışma zamanı modülü özgü [GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) yöntemi ve çalışma zamanı tarafından sağlanan arabirimleri aracılığıyla [Getınterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)yöntemi.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)|Tüm eski CLR sürüm 2 etkinleştirme ilke kararları için bu çalışma zamanı bağlar.|  
|[GetDefaultStartupFlags Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getdefaultstartupflags-method.md)|CLR başlangıç bayrakları ve ana bilgisayar yapılandırma dosyası alır.|  
|[GetInterface Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|CLR geçerli sürecine yükler ve çalışma zamanı arabirim işaretçileri gibi döndürür [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) ve [Imetadatadispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md). Bu yöntem tüm yerini `CorBindTo*` işlevleri.|  
|[GetProcAddress Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|Bu arabirim ile ilişkili CLR dışarı aktarılan belirtilen bir işlevin adresini alır. Bu yöntem yerini [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) yöntemi.|  
|[GetRuntimeDirectory Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|Bu arabirim ile ilişkili CLR yükleme dizinini alır. Bu yöntem yerini [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) yöntemi.|  
|[GetVersionString Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|Ortak dil çalışma zamanı (CLR) sürüm bilgileri ile ilişkili alır bir verilen [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi. Bu yöntem yerini [Getrequestedruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) ve [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) yöntemleri.|  
|[IsLoadable Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloadable-method.md)|Geçerli işlemine dikkate alarak bu arabirimle ilişkili çalışma zamanının yüklü olup olmadığını gösterir işlemine zaten yüklenmiş diğer çalışma zamanları.|  
|[IsLoaded Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|CLR ile ilişkili olup olmadığını gösteren [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi süreç içine yüklenir.|  
|[IsStarted Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|CLR, ile ilişkili olup olmadığını belirten [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi başlatıldı.|  
|[LoadErrorString Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|Uygun bir hata iletisi belirtilen kültür için bir HRESULT değeri çevirir. Bu yöntem yerini [LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md) ve [LoadStringRCEx](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md) yöntemleri.|  
|[LoadLibrary Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|Bir kitaplık tarafından temsil edilen CLR framework dizininden yükleyen bir [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi. Bu yöntem yerini [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) yöntemi.|  
|[SetDefaultStartupFlags Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)|CLR başlangıç bayrakları ve ana bilgisayar yapılandırma dosyasını ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
