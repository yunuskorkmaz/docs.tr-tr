---
title: LoadStringRC İşlevi
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 56ae7b7cf3b577bfe41ebd0bdd98e0da68047b44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176246"
---
# <a name="loadstringrc-function"></a>LoadStringRC İşlevi
Geçerli iş parçacığının varsayılan kültürünü kullanarak bir HRESULT değerini hata iletisine çevirir.  
  
 Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `iResourceID`  
 [içinde] Bir HRESULT.  
  
 `szBuffer`  
 [çıkış] Başarılı bir şekilde tamamlandıktan sonra hata iletisi içeren bir arabellek.  
  
 `iMax`  
 [içinde] Hata iletisi arabelleği boyutu.  
  
 `bQuiet`  
 [içinde] Göz ardı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerlere ek olarak WinError.h'de tanımlandığı şekilde standart Bileşen Nesne Modeli (COM) hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_ınvalıdarg|`szBuffer`null veya `iMax` sıfır (0) olduğunu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntem başarıyla tamamlanmamışsa, `szBuffer` boş bir dize içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** MSCorEE.dll ve Mscorwks.dll. .NET Framework'ün doğru sürümünü hedeflediğinizden emin olmak için Mscorwks.dll yerine MSCorEE.dll'yi kullanın.  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LoadStringRCEx İşlevi](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
