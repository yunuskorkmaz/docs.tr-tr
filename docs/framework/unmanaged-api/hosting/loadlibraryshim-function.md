---
title: LoadLibraryShim İşlevi
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c8936fa3d22cfde4c2536fccf9d46c1990133db1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445318"
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim İşlevi
.NET Framework yeniden dağıtılabilir paketinde bulunan bir DLL belirtilen sürümünü yükler.  
  
 Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Kullanım [Iclrruntimeınfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `szDllName`  
 [in] .NET Framework Kitaplığı'ndan yüklenecek DLL adını temsil eden bir sıfır ile sonlandırılan bir dize.  
  
 `szVersion`  
 [in] Yüklenecek DLL sürümü temsil eden bir sıfır ile sonlandırılan bir dize. Varsa `szVersion` null, yükleme sürüm 4'dan küçük belirtilen DLL Dosyasının en son sürümü için seçtiğiniz sürüm değil. Diğer bir deyişle, tüm sürümleri eşit veya bundan büyük sürüm 4 sayılır `szVersion` null, ve sürüm 4 değerinden küçük bir sürümü yüklüyse, DLL yüklemek başarısız olur. Bu yüklemesini sağlamaktır [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] önceden var olan uygulamaları veya bileşenleri etkilemez. Girişine bakın [işlem dışı SxS ve geçiş Hızlı Başlangıç](http://go.microsoft.com/fwlink/?LinkId=200329) CLR ekip blogu içinde.  
  
 `pvReserved`  
 Daha sonraki kullanımlar için ayrılmıştır.  
  
 `phModDll`  
 [out] Modül işleyicisi için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|CLR_E_SHIM_RUNTIMELOAD|Yükleme `szDllName` ortak dil çalışma zamanı (CLR) ve CLR'nin gereken sürümü yüklenemiyor yüklenmesini gerektirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, .NET Framework yeniden dağıtılabilir paketinin içerdiği DLL'leri yüklemek için kullanılır. Kullanıcı tarafından oluşturulan DLL'leri yüklemez.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0 ile başlayarak, Fusion.dll yüklenirken yüklenecek CLR neden olur. Bunun nedeni, Fusion.dll işlevlerde şimdi uygulamaları çalışma zamanı tarafından sağlanan sarmalayıcıları olmasıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
