---
title: ICLRStrongName Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRStrongName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName
helpviewer_keywords:
- ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 2fac66fd-6b3b-4dbd-8baf-86038bd85526
topic_type:
- apiref
ms.openlocfilehash: 04260429dd69f5ba1d6a94b6628979341d12b9e8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762090"
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName Arabirimi
Derlemeleri tanımlayıcı adlarla imzalamak için temel genel statik işlevler sağlar. Tüm `ICLRStrongName` Yöntemler standart com HRESULTs döndürür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetHashFromAssemblyFile Yöntemi](iclrstrongname-gethashfromassemblyfile-method.md)|Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.|  
|[GetHashFromAssemblyFileW Yöntemi](iclrstrongname-gethashfromassemblyfilew-method.md)|Belirtilen karma algoritmasını kullanarak, Unicode dizesi olarak belirtilen derleme dosyasının karmasını alır.|  
|[GetHashFromBlob Yöntemi](iclrstrongname-gethashfromblob-method.md)|Belirtilen karma algoritmasını kullanarak, belirtilen bellek adresindeki derlemenin karmasını alır.|  
|[GetHashFromFile Yöntemi](iclrstrongname-gethashfromfile-method.md)|Belirtilen dosyanın içeriği üzerinde bir karma oluşturur.|  
|[GetHashFromFileW Yöntemi](iclrstrongname-gethashfromfilew-method.md)|Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur.|  
|[GetHashFromHandle Yöntemi](iclrstrongname-gethashfromhandle-method.md)|Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısına sahip dosyanın içeriği üzerinde bir karma oluşturur.|  
|[StrongNameCompareAssemblies Yöntemi](iclrstrongname-strongnamecompareassemblies-method.md)|İki derlemenin yalnızca kendi tanımlayıcı ad imzalarına göre farklı olup olmadığını belirler.|  
|[StrongNameFreeBuffer Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|[StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)veya [StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md)gibi bir tanımlayıcı ad yöntemine önceki bir çağrı ile ayrılmış belleği serbest bırakır.|  
|[StrongNameGetBlob Yöntemi](iclrstrongname-strongnamegetblob-method.md)|Belirtilen adresteki yürütülebilir dosyanın ikili gösterimiyle belirtilen arabelleği doldurur.|  
|[StrongNameGetBlobFromImage Yöntemi](iclrstrongname-strongnamegetblobfromimage-method.md)|Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır.|  
|[StrongNameGetPublicKey Yöntemi](iclrstrongname-strongnamegetpublickey-method.md)|Özel/ortak anahtar çiftinden ortak anahtarı alır.|  
|[StrongNameHashSize Yöntemi](iclrstrongname-strongnamehashsize-method.md)|Belirtilen karma algoritmasını kullanarak bir karma için gereken arabellek boyutunu alır.|  
|[StrongNameKeyDelete Yöntemi](iclrstrongname-strongnamekeydelete-method.md)|Belirtilen anahtar kapsayıcısını siler.|  
|[StrongNameKeyGen Yöntemi](iclrstrongname-strongnamekeygen-method.md)|Tanımlayıcı ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.|  
|[StrongNameKeyGenEx Yöntemi](iclrstrongname-strongnamekeygenex-method.md)|Tanımlayıcı ad kullanımı için belirtilen anahtar boyutuyla yeni bir ortak/özel anahtar çifti oluşturur.|  
|[StrongNameKeyInstall Yöntemi](iclrstrongname-strongnamekeyinstall-method.md)|Bir kapsayıcıya ortak/özel anahtar çifti aktarır.|  
|[StrongNameSignatureGeneration Yöntemi](iclrstrongname-strongnamesignaturegeneration-method.md)|Belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.|  
|[StrongNameSignatureGenerationEx Yöntemi](iclrstrongname-strongnamesignaturegenerationex-method.md)|Belirtilen bayrakları temel alarak, belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.|  
|[StrongNameSignatureSize Yöntemi](iclrstrongname-strongnamesignaturesize-method.md)|Tanımlayıcı ad imzasının boyutunu döndürür.|  
|[StrongNameSignatureVerification Yöntemi](iclrstrongname-strongnamesignatureverification-method.md)|Belirtilen bayrağa göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.|  
|[StrongNameSignatureVerificationEx Yöntemi](iclrstrongname-strongnamesignatureverificationex-method.md)|Belirtilen yoldaki Derleme bildiriminin tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.|  
|[StrongNameSignatureVerificationFromImage Yöntemi](iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Zaten bellekle eşlenmiş bir derlemenin ilişkili ortak anahtar için geçerli olduğunu doğrular.|  
|[StrongNameTokenFromAssembly Yöntemi](iclrstrongname-strongnametokenfromassembly-method.md)|Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur.|  
|[StrongNameTokenFromAssemblyEx Yöntemi](iclrstrongname-strongnametokenfromassemblyex-method.md)|Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur ve ortak anahtarı döndürür.|  
|[StrongNameTokenFromPublicKey Yöntemi](iclrstrongname-strongnametokenfrompublickey-method.md)|Ortak anahtarı temsil eden bir belirteç alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICLRStrongName`Ve parametrelerini kullanarak [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) metodunu çağırarak bir örneğini alabilirsiniz `CLSID_CLRStrongName` `IID_ICLRStrongName` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Barındırma](index.md)
