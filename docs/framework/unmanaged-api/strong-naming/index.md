---
title: "Tanımlayıcı Ad Oluşturma (Yönetilmeyen API Başvurusu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 86d741a16a0293892d0d6d90f1763d744ed3675d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="strong-naming-unmanaged-api-reference"></a>Tanımlayıcı Ad Oluşturma (Yönetilmeyen API Başvurusu)
Tanımlayıcı adlı derlemeler için imzalama yönetmek bir istemci güçlü adlandırma API sağlar.  
  
 Bir derlemeyi katı bir adla imzalamak, dosyaya derleme bildirimini içeren ortak bir anahtar şifrelemesi ekler. Tanımlayıcı ad imzası yardımcı adı benzersizlik doğrulayın adı yanıltma engeller ve başvuru çözümlendiğinde arayanlar benzersiz bir kimliği sağlar. Ancak, hiçbir güven düzeyini tanımlayıcı bir ad ile ilişkilidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Güçlü adlandırma genel statik işlevleri](http://msdn.microsoft.com/en-us/efa715df-e8cc-48f2-9ec4-26586f0dc8d0)  
 Güçlü adlandırma API'sini kullanan yönetilmeyen genel statik işlevleri açıklanmaktadır.  
  
> [!NOTE]
>  Tüm bu işlevlerin başlayarak kullanım dışı bırakıldı [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Önerilen alternatifler için bkz: [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) arabirimi.  
  
 [GetHashFromAssemblyFile işlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 Belirtilen karma algoritması kullanılarak belirtilen derleme dosyası karmasını alır. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromAssemblyFileW işlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 Belirtilen karma algoritması kullanılarak bir UNICODE dizesi belirtilen derleme dosyası karmasını alır. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromBlob işlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 Derleme karmasını belirtilen karma algoritması kullanılarak belirtilen bellek adresinde alır. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromFile işlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 Belirtilen dosyanın içeriğini bir karma oluşturur.  İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromFileW işlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 Bir UNICODE dizesi tarafından belirtilen dosyanın içeriğini üzerinden bir karma oluşturur. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromHandle işlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 Belirtilen karma algoritması kullanılarak belirtilen dosya tanıtıcısıyla dosyasının içeriği üzerinden bir karma oluşturur.  İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameCompareAssemblies işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 İki derleme yalnızca güçlü ad imzaları tarafından farklı olup olmadığını belirler. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnameerrorınfo işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 Güçlü ad işlevleri biri tarafından gerçekleştirilen son hata kodunu alır.  
  
 [StrongNameFreeBuffer işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 Önceki bir güçlü ad işlevi çağrısı ile ayrıldı bellek boşaltır [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), veya [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).   İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetBlob işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 Belirtilen arabellek yürütülebilir dosyanın belirtilen adresteki ikili gösterimidir doldurur. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamegetblobfromımage işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 Belirtilen bellek adresinde derleme görüntü ikili bir gösterimini alır. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetPublicKey işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 Ortak anahtarı bir özel/ortak anahtar çifti alır. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameHashSize işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 Belirtilen karma algoritması kullanan bir karma için gerekli arabellek boyutunu alır.  İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyDelete işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 Belirtilen anahtar kapsayıcısı siler. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyGen işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 Güçlü ad kullanmak için yeni bir ortak/özel anahtar çifti oluşturur.  İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyGenEx işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 Güçlü ad kullanım için belirtilen anahtar boyutu ile yeni bir ortak/özel anahtar çifti oluşturur. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamekeyınstall işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 Bir ortak/özel anahtar çifti bir kapsayıcıya alır.  İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureGeneration işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 Tanımlayıcı ad imzası için belirtilen derlemeyi oluşturur.   İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureGenerationEx işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 Belirtilen bayrakları dayalı belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.    İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureSize işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 Tanımlayıcı ad imzası boyutu döndürür. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerification işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 Derleme bildirimi sağlanan yolunda belirtilen bayrakları göre doğrulanır bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerificationEx işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 Sağlanan yol, derleme bildirimi sağlam ad imzası içeren olup olmadığını belirten bir değer alır.  İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Strongnamesignatureverificationfromımage işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 Bellek zaten eşlendi bütünleştirilmiş ilişkili ortak anahtarı için geçerli olduğunu doğrular. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromAssembly işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 Güçlü ad belirteci belirtilen derleme dosyası oluşturur.  İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromAssemblyEx işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 Belirtilen derleme dosyasından bir güçlü ad belirteci oluşturur ve ortak anahtar döndürür. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromPublicKey işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 Bir ortak anahtar temsil eden bir belirteci alır. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Güçlü adlandırma yapısı](http://msdn.microsoft.com/en-us/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)  
 Tanımlayıcı adlı derlemeler için imzalama yönetmek için güçlü adlandırma API'sini kullanan yönetilmeyen yapısını açıklar...  
  
 [PublicKeyBlob yapısı](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 Bir ortak/özel anahtar çifti ikili biçimindeki ortak anahtarı temsil eder.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iclrstrongname arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [Yönetilmeyen API Başvurusu](../../../../docs/framework/unmanaged-api/index.md)
