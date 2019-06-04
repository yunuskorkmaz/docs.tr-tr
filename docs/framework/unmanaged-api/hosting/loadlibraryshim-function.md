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
ms.openlocfilehash: 87ca5470fe5994d34d12a339c2d92a5f3917063d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490229"
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim İşlevi
Belirtilen .NET Framework yeniden dağıtılabilir pakette bulunan bir DLL sürümünü yükler.  
  
 Bu işlev .NET Framework 4'te kullanım dışıdır. Kullanım [Iclrruntimeınfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szDllName`  
 [in] .NET Framework Kitaplığı'ndan yüklenecek DLL adını temsil eden sıfır ile sonlandırılmış dize.  
  
 `szVersion`  
 [in] Yüklenecek DLL sürümünü temsil eden sıfır ile sonlandırılmış dize. Varsa `szVersion` null, 4 sürümünden küçük belirtilen DLL'yi en son sürümünü yükleme için seçilen sürüm olduğu. Diğer bir deyişle, tüm sürümler sürüm 4'değerinden büyük veya eşit sayılır `szVersion` null ise, sürüm 4 değerinden hiçbir sürüm yüklüyse, DLL yüklenecek başarısız olur. Bu, .NET Framework 4'ün yüklenmesi önceden mevcut olan uygulamaları veya bileşenleri etkilememesini sağlamak içindir. Girdisine bakın [In-Proc SxS ve geçiş Hızlı Başlangıç](https://go.microsoft.com/fwlink/?LinkId=200329) CLR Ekibi blogunda.  
  
 `pvReserved`  
 Daha sonraki kullanımlar için ayrılmıştır.  
  
 `phModDll`  
 [out] Modül tanıtıcısını işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Wınerror içinde tanımlanan döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|CLR_E_SHIM_RUNTIMELOAD|Yükleme `szDllName` ortak dil çalışma zamanı (CLR) ve CLR'nin gereken sürümü yüklenemiyor yüklenmesini gerektirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, .NET Framework yeniden dağıtılabilir paketine dahil edilen DLL'lerini yüklemek için kullanılır. Kullanıcı tarafından oluşturulan DLL'leri yüklenmez.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0 ile başlayarak, Fusion.dll yüklenirken yüklenecek CLR neden olur. Fusion.dll işlevler çalışma zamanı tarafından sağlanan uygulamaları sarmalayıcıları sunulmuştur olmasıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
