---
title: ICLRStrongName Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName
helpviewer_keywords: ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 2fac66fd-6b3b-4dbd-8baf-86038bd85526
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8e8a3c9ff4ec3d6b124f95edd31e277db3eb872
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName Arabirimi
Derlemeleri tanımlayıcı adlar ile imzalama için temel genel statik işlevleri sağlar. Tüm `ICLRStrongName` yöntemleri standart COM HRESULTs döndürür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetHashFromAssemblyFile yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)|Belirtilen karma algoritması kullanılarak belirtilen derleme dosyası karmasını alır.|  
|[GetHashFromAssemblyFileW yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)|Belirtilen karma algoritması kullanılarak bir UNICODE dizesi belirtilen derleme dosyası karmasını alır.|  
|[GetHashFromBlob yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)|Derleme karmasını belirtilen karma algoritması kullanılarak belirtilen bellek adresinde alır.|  
|[GetHashFromFile yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)|Belirtilen dosyanın içeriğini bir karma oluşturur.|  
|[GetHashFromFileW yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)|Bir UNICODE dizesi tarafından belirtilen dosyanın içeriğini üzerinden bir karma oluşturur.|  
|[GetHashFromHandle yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)|Belirtilen karma algoritması kullanılarak belirtilen dosya tanıtıcısıyla dosyasının içeriği üzerinden bir karma oluşturur.|  
|[StrongNameCompareAssemblies yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)|İki derleme yalnızca güçlü ad imzaları tarafından farklı olup olmadığını belirler.|  
|[StrongNameFreeBuffer yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|Güçlü ad yöntemi önceki çağrısıyla ayrıldı bellek boşaltır [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), veya [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).|  
|[StrongNameGetBlob yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)|Belirtilen arabellek yürütülebilir dosyanın belirtilen adresteki ikili gösterimidir doldurur.|  
|[Strongnamegetblobfromımage yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)|Belirtilen bellek adresinde derleme görüntü ikili bir gösterimini alır.|  
|[StrongNameGetPublicKey yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)|Ortak anahtarı bir özel/ortak anahtar çifti alır.|  
|[StrongNameHashSize yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)|Belirtilen karma algoritması kullanan bir karma için gerekli arabellek boyutunu alır.|  
|[StrongNameKeyDelete yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)|Belirtilen anahtar kapsayıcısı siler.|  
|[StrongNameKeyGen yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)|Güçlü ad kullanmak için yeni bir ortak/özel anahtar çifti oluşturur.|  
|[StrongNameKeyGenEx yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)|Güçlü ad kullanım için belirtilen anahtar boyutu ile yeni bir ortak/özel anahtar çifti oluşturur.|  
|[Strongnamekeyınstall yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)|Bir ortak/özel anahtar çifti bir kapsayıcıya alır.|  
|[StrongNameSignatureGeneration yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)|Tanımlayıcı ad imzası için belirtilen derlemeyi oluşturur.|  
|[StrongNameSignatureGenerationEx yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)|Belirtilen bayrakları dayalı belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.|  
|[StrongNameSignatureSize yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)|Tanımlayıcı ad imzası boyutu döndürür.|  
|[StrongNameSignatureVerification yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)|Derleme bildirimi sağlanan yolunda belirtilen bayrakları göre doğrulanır bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.|  
|[StrongNameSignatureVerificationEx yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)|Sağlanan yol, derleme bildirimi sağlam ad imzası içeren olup olmadığını belirten bir değer alır.|  
|[Strongnamesignatureverificationfromımage yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Bellek zaten eşlendi bütünleştirilmiş ilişkili ortak anahtarı için geçerli olduğunu doğrular.|  
|[StrongNameTokenFromAssembly yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)|Güçlü ad belirteci belirtilen derleme dosyası oluşturur.|  
|[StrongNameTokenFromAssemblyEx yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)|Belirtilen derleme dosyasından bir güçlü ad belirteci oluşturur ve ortak anahtar döndürür.|  
|[StrongNameTokenFromPublicKey yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)|Bir ortak anahtar temsil eden bir belirteci alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir örneği elde edebilirsiniz `ICLRStrongName` çağırarak [Iclrruntimeınfo::getınterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) yöntemini kullanarak `CLSID_CLRStrongName` ve `IID_ICLRStrongName` parametre olarak.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
