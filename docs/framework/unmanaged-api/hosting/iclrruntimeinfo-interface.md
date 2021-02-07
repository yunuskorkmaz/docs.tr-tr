---
description: ': ICLRRuntimeInfo arabirimi hakkında daha fazla bilgi'
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
ms.openlocfilehash: d599c743e5a42801321ea487fdd9e52bfcfaf081
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753867"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo Arabirimi

Sürüm, dizin ve yükleme durumu dahil olmak üzere belirli bir ortak dil çalışma zamanı (CLR) hakkında bilgi döndüren yöntemler sağlar. Bu arabirim, çalışma zamanını başlatmadan çalışma zamanına özgü işlevselliği de sağlar. Çalışma zamanı-göreli [LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) yöntemi, çalışma zamanı modülüne özel [GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) yöntemi ve [GetInterface](iclrruntimeinfo-getinterface-method.md) yöntemi aracılığıyla çalışma zamanı tarafından sağlanmış arabirimler içerir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime Yöntemi](iclrruntimeinfo-bindaslegacyv2runtime-method.md)|Tüm eski CLR sürüm 2 etkinleştirme ilkesi kararları için bu çalışma zamanını bağlar.|  
|[GetDefaultStartupFlags Yöntemi](iclrruntimeinfo-getdefaultstartupflags-method.md)|CLR başlangıç bayraklarını ve ana bilgisayar yapılandırma dosyasını alır.|  
|[GetInterface Yöntemi](iclrruntimeinfo-getinterface-method.md)|CLR 'yi geçerli işleme yükler ve [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md) ve [ımetadatadağıtıcı](../metadata/imetadatadispenser-interface.md)gibi çalışma zamanı arabirimi işaretçilerini döndürür. Bu yöntem tüm işlevlerin yerini alır `CorBindTo*` .|  
|[GetProcAddress Yöntemi](iclrruntimeinfo-getprocaddress-method.md)|Bu arabirimle ilişkili CLR 'den aktarılmış belirtilen işlevin adresini alır. Bu yöntem [GetRealProcAddress](getrealprocaddress-function.md) yönteminin yerini alır.|  
|[GetRuntimeDirectory Yöntemi](iclrruntimeinfo-getruntimedirectory-method.md)|Bu arabirimle ilişkili CLR 'nin yükleme dizinini alır. Bu yöntem [GetCORSystemDirectory](getcorsystemdirectory-function.md) yönteminin yerini alır.|  
|[GetVersionString Yöntemi](iclrruntimeinfo-getversionstring-method.md)|Belirli bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimiyle ilişkili ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır. Bu yöntem, [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md) ve [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) yöntemlerinin yerini alır.|  
|[IsLoadable Yöntemi](iclrruntimeinfo-isloadable-method.md)|Bu arabirimle ilişkili çalışma zamanının geçerli işleme yüklenip yüklenmediğini, işleme daha önce yüklenmiş olabilecek diğer çalışma zamanlarını hesaba ayırarak gösterir.|  
|[IsLoaded Yöntemi](iclrruntimeinfo-isloaded-method.md)|[ICLRRuntimeInfo](iclrruntimeinfo-interface.md) ARABIRIMIYLE ilişkilendirilen clr 'nin bir işleme yüklenip yüklenmediğini belirtir.|  
|[IsStarted Yöntemi](iclrruntimeinfo-isstarted-method.md)|[ICLRRuntimeInfo](iclrruntimeinfo-interface.md) ARABIRIMIYLE ilişkili clr 'nin başlatılmış olup olmadığını gösterir.|  
|[LoadErrorString Yöntemi](iclrruntimeinfo-loaderrorstring-method.md)|Belirtilen kültür için bir HRESULT değerini uygun bir hata iletisine çevirir. Bu yöntem, [LoadStringRC](loadstringrc-function.md) ve [LoadStringRCEx](loadstringrcex-function.md) yöntemlerinin yerini alır.|  
|[LoadLibrary Yöntemi](iclrruntimeinfo-loadlibrary-method.md)|Bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimiyle temsıl edilen clr 'nin çerçeve dizininden bir kitaplık yükler. Bu yöntem [LoadLibraryShim](loadlibraryshim-function.md) yönteminin yerini alır.|  
|[SetDefaultStartupFlags Yöntemi](iclrruntimeinfo-setdefaultstartupflags-method.md)|CLR başlangıç bayraklarını ve ana bilgisayar yapılandırma dosyasını ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Hosting](index.md)
