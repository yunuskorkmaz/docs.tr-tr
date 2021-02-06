---
description: 'Daha fazla bilgi edinin: StrongNameTokenFromAssemblyEx Işlevi'
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
ms.openlocfilehash: 4ca08c8cfa90415723fc2632e32aa8f45c334db3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636291"
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

 `true` başarıyla tamamlandığında; Aksi takdirde, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 Tanımlayıcı ad belirteci, ortak anahtarın kısaltılmış biçimidir. Belirteç, derlemeyi imzalamak için kullanılan ortak anahtardan oluşturulan 64 bitlik bir karmadır. Belirteç, derlemenin tanımlayıcı adının bir parçasıdır ve derleme meta verilerinden okunabilir.  
  
 Anahtar alındıktan ve belirteç oluşturulduktan sonra, ayrılan belleği serbest bırakmak için [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini çağırmanız gerekir.  
  
 `StrongNameTokenFromAssemblyEx`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** mscoree.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameTokenFromAssemblyEx Yöntemi](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [StrongNameTokenFromAssembly Yöntemi](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
