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
ms.openlocfilehash: 343abf450a49ad222c403c28e46c6e3aac33e1b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966161"
---
# <a name="strong-naming-unmanaged-api-reference"></a>Tanımlayıcı Ad Oluşturma (Yönetilmeyen API Başvurusu)
Güçlü adlandırma API 'SI, bir istemcinin derlemeler için tanımlayıcı ad imzalamayı yönetmesine olanak sağlar.  
  
 Bir derlemeyi katı bir adla imzalamak, dosyaya derleme bildirimini içeren ortak bir anahtar şifrelemesi ekler. Tanımlayıcı ad imzalama, ad benzersizliği doğrulamaya yardımcı olur, ad yanıltmasını önler ve bir başvuru çözüldüğünde çağıranlar benzersiz bir kimlik sağlar. Ancak, tanımlayıcı bir adla ilişkili güven düzeyi yoktur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
> [!NOTE]
> Bu işlevlerin tümü .NET Framework 4 ' den itibaren kullanımdan kaldırılmıştır. Önerilen alternatifler için [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) arabirimine bakın.  
  
 [GetHashFromAssemblyFile İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [GetHashFromAssemblyFileW İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 Belirtilen karma algoritmasını kullanarak, Unicode dizesi olarak belirtilen derleme dosyasının karmasını alır. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [GetHashFromBlob İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 Belirtilen karma algoritmasını kullanarak, belirtilen bellek adresindeki derlemenin karmasını alır. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [GetHashFromFile İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 Belirtilen dosyanın içeriği üzerinde bir karma oluşturur.  .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [GetHashFromFileW İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [GetHashFromHandle İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısına sahip dosyanın içeriği üzerinde bir karma oluşturur.  .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameCompareAssemblies İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 İki derlemenin yalnızca kendi tanımlayıcı ad imzalarına göre farklı olup olmadığını belirler. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameErrorInfo İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 Tanımlayıcı ad işlevlerinden biri tarafından oluşturulan son hata kodunu alır.  
  
 [StrongNameFreeBuffer İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)veya [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)gibi bir tanımlayıcı ad işlevine daha önceki bir çağrı ile ayrılmış belleği serbest bırakır.   .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameGetBlob İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 Belirtilen adresteki yürütülebilir dosyanın ikili gösterimiyle belirtilen arabelleği doldurur. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameGetBlobFromImage İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameGetPublicKey İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 Özel/ortak anahtar çiftinden ortak anahtarı alır. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameHashSize İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 Belirtilen karma algoritmasını kullanarak bir karma için gereken arabellek boyutunu alır.  .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameKeyDelete İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 Belirtilen anahtar kapsayıcısını siler. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameKeyGen İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 Tanımlayıcı ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.  .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameKeyGenEx İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 Tanımlayıcı ad kullanımı için belirtilen anahtar boyutuyla yeni bir ortak/özel anahtar çifti oluşturur. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameKeyInstall İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 Bir kapsayıcıya ortak/özel anahtar çifti aktarır.  .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameSignatureGeneration İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 Belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.   .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameSignatureGenerationEx İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 Belirtilen bayrakları temel alarak, belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.    .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameSignatureSize İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 Tanımlayıcı ad imzasının boyutunu döndürür. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameSignatureVerification İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 Belirtilen bayrağa göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameSignatureVerificationEx İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 Belirtilen yoldaki Derleme bildiriminin tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.  .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameSignatureVerificationFromImage İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 Zaten bellekle eşlenmiş bir derlemenin ilişkili ortak anahtar için geçerli olduğunu doğrular. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameTokenFromAssembly İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur.  .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameTokenFromAssemblyEx İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur ve ortak anahtarı döndürür. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameTokenFromPublicKey İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 Ortak anahtarı temsil eden bir belirteç alır. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [PublicKeyBlob Yapısı](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 İkili biçimdeki ortak/özel anahtar çiftinin ortak anahtarını temsil eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [Yönetilmeyen API Başvurusu](../../../../docs/framework/unmanaged-api/index.md)
