---
title: ICLRMetaHost::EnumerateLoadedRuntimes Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: 7b09bb9c3abcb23997bfd412c3ea939404e583c1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504179"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a>ICLRMetaHost::EnumerateLoadedRuntimes Yöntemi
Belirli bir işlemde yüklenen ortak dil çalışma zamanının (CLR) her sürümü için geçerli bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi işaretçisi içeren bir sabit listesi döndürür. Bu yöntem [GetVersionFromProcess](getversionfromprocess-function.md) işlevinin yerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hndProcess`  
 'ndaki Yüklenen çalışma zamanları için İnceleme işleminin tanıtıcısı.  
  
 `ppEnumerator`  
 dışı <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>İşlem tarafından yüklenen her clr 'ye karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimlerinin numaralandırması.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`ppEnumerator`null.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, [CorBindToRuntime](corbindtoruntime-function.md)gibi kullanım dışı işlevlerle yüklenseler bile, tüm yüklenen çalışma zamanlarını listeler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetaHost Arabirimi](iclrmetahost-interface.md)
- [Hosting](index.md)
