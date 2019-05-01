---
title: Tanımlayıcı Ad Oluşturma (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32e74a76b6b1bedee4efc5715d0710c8efce2455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049381"
---
# <a name="strong-naming-unmanaged-api-reference"></a>Tanımlayıcı Ad Oluşturma (Yönetilmeyen API Başvurusu)
Tanımlayıcı ad derlemeleri imzalama yönetmek bir istemci tanımlayıcı adlandırma API sağlar.  
  
 Bir derlemeyi katı bir adla imzalamak, dosyaya derleme bildirimini içeren ortak bir anahtar şifrelemesi ekler. Tanımlayıcı ad imzalama ad benzersizliğini doğrulamaya yardımcı olan ad sahtekarlığını engeller ve bir referans çözüldüğünde çağıranlar benzersiz bir kimliği sağlar. Ancak, hiçbir güven düzeyi güçlü bir adla ilişkilidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
> [!NOTE]
>  Bu işlevlerin tümü başlayarak kullanımdan kaldırılan [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Önerilen alternatifleri için bkz: [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) arabirimi.  
  
 [GetHashFromAssemblyFile İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 Belirtilen karma algoritması kullanılarak, belirtilen derleme dosyasının bir karmasını alır. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromAssemblyFileW İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 Belirtilen karma algoritması kullanılarak bir Unicode dize olarak belirtilen derleme dosyasının bir karmasını alır. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromBlob İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 Derleme karması belirtilen karma algoritması kullanılarak belirtilen bellek adresinde alır. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromFile İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 Belirtilen dosyanın içeriğini bir karma oluşturur.  İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromFileW İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 Unicode dizesi tarafından belirtilen dosyanın içeriğini üzerinden bir karma oluşturur. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromHandle İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 Belirtilen dosya tanıtıcısıyla belirtilen karma algoritması kullanarak bir dosyanın içeriğini üzerinden bir karma oluşturur.  İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameCompareAssemblies İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 İki derlemenin yalnızca tanımlayıcı ad imzaları tarafından farklı olup olmadığını belirler. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameErrorInfo İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 Tanımlayıcı ad işlevlerden biri tarafından tetiklendi son hata kodu alır.  
  
 [StrongNameFreeBuffer İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 Önceki bir tanımlayıcı ad işlev çağrısı ile ayrıldı bellek serbest bırakma [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), veya [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).   İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetBlob İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 Belirtilen arabellek, yürütülebilir dosyanın belirtilen adreste ikili gösterimini ile doldurur. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetBlobFromImage İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 Belirtilen bellek adresinde derleme yansıma ikili gösterimini alır. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetPublicKey İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 Private/public anahtar çiftinden ortak anahtarı alır. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameHashSize İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 Belirtilen karma algoritması kullanarak bir karma için gerekli arabellek boyutunu alır.  İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyDelete İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 Belirtilen anahtar kapsayıcısında siler. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyGen İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 Tanımlayıcı ad kullanmak için yeni bir ortak/özel anahtar çifti oluşturur.  İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyGenEx İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 Tanımlayıcı ad kullanmak için belirtilen anahtar boyutu ile yeni bir ortak/özel anahtar çifti oluşturur. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyInstall İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 Bir ortak/özel anahtar çifti bir kapsayıcının içine aktarır.  İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureGeneration İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 Tanımlayıcı ad imzası için belirtilen derlemeyi oluşturur.   İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureGenerationEx İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 Belirtilen bayraklar üzerinde göre belirtilen derleme için tanımlayıcı ad imzası oluşturur.    İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureSize İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 Tanımlayıcı ad imzası boyutunu döndürür. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerification İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 Sağlanan yol, derleme bildirimi belirtilen bayraklar göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerificationEx İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 Sağlanan yol, derleme bildirimi tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.  İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerificationFromImage İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 Bellek zaten eşleştirilmiş bir derleme için ilişkili ortak anahtar geçerli olduğunu doğrular. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromAssembly İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 Belirtilen derleme dosyasından bir güçlü ad simgesi oluşturur.  İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromAssemblyEx İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 Belirtilen derleme dosyasından tanımlayıcı ad belirteci oluşturur ve ortak anahtarını döndürür. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromPublicKey İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 Bir ortak anahtar temsil eden bir belirteç alır. İle başlayarak kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [PublicKeyBlob Yapısı](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 Bir ortak/özel anahtar çifti ikili biçimindeki ortak anahtarı temsil eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [Yönetilmeyen API Başvurusu](../../../../docs/framework/unmanaged-api/index.md)
