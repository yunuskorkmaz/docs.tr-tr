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
ms.openlocfilehash: 4b270c36bdbea9c8d81915eba424cae1054ce7d7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008540"
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim İşlevi
Yeniden dağıtılabilir .NET Framework paketinde bulunan bir DLL 'nin belirtilen sürümünü yükler.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır. Bunun yerine [ICLRRuntimeInfo:: LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szDllName`  
 'ndaki .NET Framework kitaplığından yüklenecek DLL 'nin adını temsil eden sıfır ile sonlandırılmış bir dize.  
  
 `szVersion`  
 'ndaki Yüklenecek DLL sürümünü temsil eden sıfır ile sonlandırılmış bir dize. `szVersion`Null ise, yükleme için seçilen sürüm, BELIRTILEN dll 'nin sürüm 4 ' ten küçük olan en son sürümüdür. Yani, sürüm 4 ' ten büyük veya bundan büyük olan tüm sürümler yok sayılır `szVersion` ve sürüm 4 ' ten küçük bir sürüm yüklü değilse, dll yüklenemez. Bu, .NET Framework 4 yüklemesinin önceden var olan uygulamaları veya bileşenleri etkilememesini sağlamaktır. CLR ekibi bloguna [-proc sxs ve geçiş hızlı başlangıç](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) girdisine bakın.  
  
 `pvReserved`  
 Daha sonraki kullanımlar için ayrılmıştır.  
  
 `phModDll`  
 dışı Modülün tanıtıcısına yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|CLR_E_SHIM_RUNTIMELOAD|Yükleme, `szDllName` ortak dil çalışma zamanının (CLR) yüklenmesini gerektirir ve clr 'nin gerekli sürümü yüklenemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, .NET Framework yeniden dağıtılabilir pakette bulunan dll 'Leri yüklemek için kullanılır. Kullanıcı tarafından oluşturulan dll 'Leri yüklemez.  
  
> [!NOTE]
> .NET Framework sürüm 2,0 ' den başlayarak Fusion. dll ' yi yüklemek CLR 'nin yüklenmesine neden olur. Bunun nedeni, Fusion. dll ' deki işlevlerin artık uygulamaları çalışma zamanı tarafından sağlanışları olan sarmalayıcılardır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
