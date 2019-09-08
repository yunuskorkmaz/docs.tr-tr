---
title: StrongNameTokenFromAssemblyEx İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c000aad12000a9c76fb6dd805a9b002c021be6ef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798836"
---
# <a name="strongnametokenfromassemblyex-function"></a>StrongNameTokenFromAssemblyEx İşlevi
Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur ve belirtecin temsil ettiği ortak anahtarı döndürür.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszFilePath`  
 'ndaki Bütünleştirilmiş kod için Taşınabilir çalıştırılabilir (PE) dosyanın yolu.  
  
 `ppbStrongNameToken`  
 dışı Döndürülen tanımlayıcı ad belirteci.  
  
 `pcbStrongNameToken`  
 dışı Tanımlayıcı ad belirtecinin bayt cinsinden boyutu.  
  
 `ppbPublicKeyBlob`  
 dışı Döndürülen ortak anahtar.  
  
 `pcbPublicKeyBlob`  
 dışı Ortak anahtarın bayt cinsinden boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`başarıyla tamamlandığında; Aksi takdirde `false`,.  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımlayıcı ad belirteci, ortak anahtarın kısaltılmış biçimidir. Belirteç, derlemeyi imzalamak için kullanılan ortak anahtardan oluşturulan 64 bitlik bir karmadır. Belirteç, derlemenin tanımlayıcı adının bir parçasıdır ve derleme meta verilerinden okunabilir.  
  
 Anahtar alındıktan ve belirteç oluşturulduktan sonra, ayrılan belleği serbest bırakmak için [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini çağırmanız gerekir.  
  
 İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo işlevini çağırın.](strongnameerrorinfo-function.md) `StrongNameTokenFromAssemblyEx`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** StrongName. h  
  
 **Kitaplığı** Mscoree. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameTokenFromAssemblyEx Yöntemi](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [StrongNameTokenFromAssembly Yöntemi](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
