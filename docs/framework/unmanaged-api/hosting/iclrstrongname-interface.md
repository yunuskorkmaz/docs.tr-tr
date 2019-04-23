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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abe967195694dd61b4af18fb4eebbc3caad2ef4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205868"
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName Arabirimi
Derlemeleri tanımlayıcı adlarla imzalamak için temel genel statik işlevleri sağlar. Tüm `ICLRStrongName` yöntemleri standart COM HRESULTs döndürür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetHashFromAssemblyFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)|Belirtilen karma algoritması kullanılarak, belirtilen derleme dosyasının bir karmasını alır.|  
|[GetHashFromAssemblyFileW Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)|Belirtilen karma algoritması kullanılarak bir Unicode dize olarak belirtilen derleme dosyasının bir karmasını alır.|  
|[GetHashFromBlob Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)|Derleme karması belirtilen karma algoritması kullanılarak belirtilen bellek adresinde alır.|  
|[GetHashFromFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)|Belirtilen dosyanın içeriğini bir karma oluşturur.|  
|[GetHashFromFileW Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)|Unicode dizesi tarafından belirtilen dosyanın içeriğini üzerinden bir karma oluşturur.|  
|[GetHashFromHandle Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)|Belirtilen dosya tanıtıcısıyla belirtilen karma algoritması kullanarak bir dosyanın içeriğini üzerinden bir karma oluşturur.|  
|[StrongNameCompareAssemblies Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)|İki derlemenin yalnızca tanımlayıcı ad imzaları tarafından farklı olup olmadığını belirler.|  
|[StrongNameFreeBuffer Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|Önceki bir tanımlayıcı ad yöntemi çağrısı ile ayrıldı bellek serbest bırakma [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), veya [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).|  
|[StrongNameGetBlob Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)|Belirtilen arabellek, yürütülebilir dosyanın belirtilen adreste ikili gösterimini ile doldurur.|  
|[StrongNameGetBlobFromImage Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)|Belirtilen bellek adresinde derleme yansıma ikili gösterimini alır.|  
|[StrongNameGetPublicKey Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)|Private/public anahtar çiftinden ortak anahtarı alır.|  
|[StrongNameHashSize Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)|Belirtilen karma algoritması kullanarak bir karma için gerekli arabellek boyutunu alır.|  
|[StrongNameKeyDelete Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)|Belirtilen anahtar kapsayıcısında siler.|  
|[StrongNameKeyGen Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)|Tanımlayıcı ad kullanmak için yeni bir ortak/özel anahtar çifti oluşturur.|  
|[StrongNameKeyGenEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)|Tanımlayıcı ad kullanmak için belirtilen anahtar boyutu ile yeni bir ortak/özel anahtar çifti oluşturur.|  
|[StrongNameKeyInstall Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)|Bir ortak/özel anahtar çifti bir kapsayıcının içine aktarır.|  
|[StrongNameSignatureGeneration Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)|Tanımlayıcı ad imzası için belirtilen derlemeyi oluşturur.|  
|[StrongNameSignatureGenerationEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)|Belirtilen bayraklar üzerinde göre belirtilen derleme için tanımlayıcı ad imzası oluşturur.|  
|[StrongNameSignatureSize Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)|Tanımlayıcı ad imzası boyutunu döndürür.|  
|[StrongNameSignatureVerification Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)|Sağlanan yol, derleme bildirimi belirtilen bayraklar göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.|  
|[StrongNameSignatureVerificationEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)|Sağlanan yol, derleme bildirimi tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.|  
|[StrongNameSignatureVerificationFromImage Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Bellek zaten eşleştirilmiş bir derleme için ilişkili ortak anahtar geçerli olduğunu doğrular.|  
|[StrongNameTokenFromAssembly Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)|Belirtilen derleme dosyasından bir güçlü ad simgesi oluşturur.|  
|[StrongNameTokenFromAssemblyEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)|Belirtilen derleme dosyasından tanımlayıcı ad belirteci oluşturur ve ortak anahtarını döndürür.|  
|[StrongNameTokenFromPublicKey Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)|Bir ortak anahtar temsil eden bir belirteç alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Örneği alabilirsiniz `ICLRStrongName` çağırarak [Iclrruntimeınfo::getınterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) yöntemi kullanarak `CLSID_CLRStrongName` ve `IID_ICLRStrongName` parametre olarak.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
