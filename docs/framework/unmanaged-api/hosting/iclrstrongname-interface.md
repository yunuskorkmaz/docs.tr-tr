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
ms.openlocfilehash: 4f774915cdbb12b13fa334db37c8e0fa2a7e5829
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135136"
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName Arabirimi
Derlemeleri tanımlayıcı adlarla imzalamak için temel genel statik işlevler sağlar. Tüm `ICLRStrongName` Yöntemler standart COM HRESULTs döndürür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetHashFromAssemblyFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)|Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.|  
|[GetHashFromAssemblyFileW Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)|Belirtilen karma algoritmasını kullanarak, Unicode dizesi olarak belirtilen derleme dosyasının karmasını alır.|  
|[GetHashFromBlob Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)|Belirtilen karma algoritmasını kullanarak, belirtilen bellek adresindeki derlemenin karmasını alır.|  
|[GetHashFromFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)|Belirtilen dosyanın içeriği üzerinde bir karma oluşturur.|  
|[GetHashFromFileW Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)|Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur.|  
|[GetHashFromHandle Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)|Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısına sahip dosyanın içeriği üzerinde bir karma oluşturur.|  
|[StrongNameCompareAssemblies Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)|İki derlemenin yalnızca kendi tanımlayıcı ad imzalarına göre farklı olup olmadığını belirler.|  
|[StrongNameFreeBuffer Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|[StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)veya [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)gibi bir tanımlayıcı ad yöntemine önceki bir çağrı ile ayrılmış belleği serbest bırakır.|  
|[StrongNameGetBlob Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)|Belirtilen adresteki yürütülebilir dosyanın ikili gösterimiyle belirtilen arabelleği doldurur.|  
|[StrongNameGetBlobFromImage Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)|Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır.|  
|[StrongNameGetPublicKey Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)|Özel/ortak anahtar çiftinden ortak anahtarı alır.|  
|[StrongNameHashSize Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)|Belirtilen karma algoritmasını kullanarak bir karma için gereken arabellek boyutunu alır.|  
|[StrongNameKeyDelete Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)|Belirtilen anahtar kapsayıcısını siler.|  
|[StrongNameKeyGen Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)|Tanımlayıcı ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.|  
|[StrongNameKeyGenEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)|Tanımlayıcı ad kullanımı için belirtilen anahtar boyutuyla yeni bir ortak/özel anahtar çifti oluşturur.|  
|[StrongNameKeyInstall Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)|Bir kapsayıcıya ortak/özel anahtar çifti aktarır.|  
|[StrongNameSignatureGeneration Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)|Belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.|  
|[StrongNameSignatureGenerationEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)|Belirtilen bayrakları temel alarak, belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.|  
|[StrongNameSignatureSize Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)|Tanımlayıcı ad imzasının boyutunu döndürür.|  
|[StrongNameSignatureVerification Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)|Belirtilen bayrağa göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.|  
|[StrongNameSignatureVerificationEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)|Belirtilen yoldaki Derleme bildiriminin tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.|  
|[StrongNameSignatureVerificationFromImage Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Zaten bellekle eşlenmiş bir derlemenin ilişkili ortak anahtar için geçerli olduğunu doğrular.|  
|[StrongNameTokenFromAssembly Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)|Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur.|  
|[StrongNameTokenFromAssemblyEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)|Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur ve ortak anahtarı döndürür.|  
|[StrongNameTokenFromPublicKey Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)|Ortak anahtarı temsil eden bir belirteç alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `CLSID_CLRStrongName` kullanarak [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) metodunu çağırarak ve parametre olarak `IID_ICLRStrongName` `ICLRStrongName` bir örneğini alabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
