---
title: ICLRDebuggingLibraryProvider::ProvideLibrary Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
ms.openlocfilehash: 7bbb49dc6ee9b1d29dd61ccdcfdacb62740133ed
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860271"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>ICLRDebuggingLibraryProvider::ProvideLibrary Yöntemi

Ortak dil çalışma zamanı (CLR) sürümüne özel hata ayıklama kitaplıklarının isteğe bağlı olarak bulunmasını ve yüklenmesini sağlayan bir kitaplık sağlayıcısı geri çağırma arabirimi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a>Parametreler

`pwszFilename` \
'ndaki İstenen modülün adı.

`dwTimestamp` \
'ndaki PE dosyalarının COFF dosya üstbilgisinde depolanan tarih saat damgası.

`pLibraryProvider` \
'ndaki PE `SizeOfImage` dosyalarının COFF isteğe bağlı dosya üstbilgisinde depolanan alan.

`hModule` \
dışı İstenen modülün tanıtıcısı.

## <a name="return-value"></a>Dönüş Değeri

Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.

|HRESULT|Açıklama|
|-------------|-----------------|
|S_OK|Yöntem başarıyla tamamlandı.|

## <a name="exceptions"></a>Özel durumlar

## <a name="remarks"></a>Açıklamalar

`ProvideLibrary`hata ayıklayıcının mscordbi. dll ve Mscordacwks. dll gibi belirli CLR dosyalarını ayıklamak için gereken modüller sağlamasına izin verir. [Ilrdebugging:: CanUnloadNow](iclrdebugging-canunloadnow-method.md) yöntemine yapılan bir çağrı, serbest bırakılabileceğini, bu noktada tutamaçları serbest bırakmak için çağıranın sorumluluğunda olduğunu belirten modül tanıtıcılarının geçerli kalması gerekir.

Hata ayıklayıcı, hata ayıklama modülünü bulmak veya temin etmek için kullanılabilir tüm araçları kullanabilir.

> [!IMPORTANT]
> Bu özellik, API çağıranın yürütülebilir ve olası kötü amaçlı kod içeren modüller sağlamasına olanak sağlar. Güvenlik önlemi olarak çağıran, kendisini yürütmek zorunda olmadığı kodu `ProvideLibrary` dağıtmak için kullanmaz.
>
> Mscordbi. dll veya Mscordacwks. dll gibi önceden yayımlanmış bir kitaplıkta önemli bir güvenlik sorunu bulunursa, dolgunun dosyaların bozuk sürümlerini tanıması için düzeltme eki uygulanabilir. Dolgu daha sonra dosyaların düzeltme eki eklenen sürümleri için istekler verebilir ve herhangi bir isteğe yanıt olarak sağlanmışsa hatalı sürümleri reddedebilir. Bu, yalnızca Kullanıcı dolgunun yeni bir sürümüne düzeltme eki uygulanmış olması durumunda gerçekleşebilir. Düzeltme eki yüklenmemiş sürümler, savunmasız kalacaktır.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
