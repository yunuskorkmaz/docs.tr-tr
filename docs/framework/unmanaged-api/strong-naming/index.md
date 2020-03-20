---
title: Tanımlayıcı Ad Oluşturma (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7d18513450111d58b5d26fd834addd465cfc4267
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140636"
---
# <a name="strong-naming-unmanaged-api-reference"></a>Tanımlayıcı Ad Oluşturma (Yönetilmeyen API Başvurusu)
Güçlü adlandırma API'si, istemcinin derlemeler için güçlü ad imzalamayı yönetmesini sağlar.  
  
 Bir derlemeyi katı bir adla imzalamak, dosyaya derleme bildirimini içeren ortak bir anahtar şifrelemesi ekler. Güçlü ad imzalama, ad benzersizliğini doğrulamaya yardımcı olur, ad sızdırmasını önler ve bir başvuru çözüldüğünde arayanlara benzersiz bir kimlik sağlar. Ancak, hiçbir güven düzeyi güçlü bir adla ilişkilendirilmez.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
> [!NOTE]
> Bu işlevlerin tümü .NET Framework 4'ten başlayarak amortismana hazırlanmıştır. Önerilen alternatifler için [ICLRStrongName](../hosting/iclrstrongname-interface.md) arabirimine bakın.  
  
 [GetHashFromAssemblyFile İşlevi](gethashfromassemblyfile-function.md)  
 Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [GetHashFromAssemblyFileW İşlevi](gethashfromassemblyfilew-function.md)  
 Belirtilen karma algoritmasını kullanarak Unicode dizesi olarak belirtilen derleme dosyasının karmasını alır. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [GetHashFromBlob İşlevi](gethashfromblob-function.md)  
 Belirtilen karma algoritmasını kullanarak, belirtilen bellek adresinde montaj bir karma alır. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [GetHashFromFile İşlevi](gethashfromfile-function.md)  
 Belirtilen dosyanın içeriği üzerinde karma oluşturur.  .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [GetHashFromFileW İşlevi](gethashfromfilew-function.md)  
 Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde karma oluşturur. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [GetHashFromHandle İşlevi](gethashfromhandle-function.md)  
 Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısıyla dosyanın içeriği üzerinde karma oluşturur.  .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameCompareAssemblies İşlevi](strongnamecompareassemblies-function.md)  
 İki derlemenin yalnızca güçlü ad imzalarına göre farklılık görüp göremeyeceğini belirler. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameErrorInfo İşlevi](strongnameerrorinfo-function.md)  
 Güçlü ad işlevlerinden biri tarafından yükseltilen son hata kodunu alır.  
  
 [StrongNameFreeBuffer İşlevi](strongnamefreebuffer-function.md)  
 [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)veya [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)gibi güçlü bir ad işlevine önceki bir çağrıyla ayrılan belleği serbest sağlar.   .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameGetBlob İşlevi](strongnamegetblob-function.md)  
 Belirtilen arabelleği, belirtilen adreste yürütülebilir dosyanın ikili gösterimiyle doldurur. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameGetBlobFromImage İşlevi](strongnamegetblobfromimage-function.md)  
 Belirtilen bellek adresindemontaj görüntüsünün ikili bir temsilini alır. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameGetPublicKey İşlevi](strongnamegetpublickey-function.md)  
 Ortak anahtarı özel/ortak anahtar çiftinden alır. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameHashSize İşlevi](strongnamehashsize-function.md)  
 Belirtilen karma algoritmasını kullanarak karma için gereken arabellek boyutunu alır.  .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameKeyDelete İşlevi](strongnamekeydelete-function.md)  
 Belirtilen anahtar kapsayıcısını siler. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameKeyGen İşlevi](strongnamekeygen-function.md)  
 Güçlü ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.  .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameKeyGenEx İşlevi](strongnamekeygenex-function.md)  
 Güçlü ad kullanımı için belirtilen anahtar boyutuna sahip yeni bir ortak/özel anahtar çifti oluşturur. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameKeyInstall İşlevi](strongnamekeyinstall-function.md)  
 Bir kapsayıcıya ortak/özel anahtar çifti içe aktun.  .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameSignatureGeneration İşlevi](strongnamesignaturegeneration-function.md)  
 Belirtilen derleme için güçlü bir ad imzası oluşturur.   .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameSignatureGenerationEx İşlevi](strongnamesignaturegenerationex-function.md)  
 Belirtilen bayrakları temel alan belirtilen derleme için güçlü bir ad imzası oluşturur.    .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameSignatureSize İşlevi](strongnamesignaturesize-function.md)  
 Güçlü ad imzasının boyutunu döndürür. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameSignatureVerification İşlevi](strongnamesignatureverification-function.md)  
 Verilen yolda derleme bildirimi belirtilen bayraklara göre doğrulanmış güçlü bir ad imzası içerip içermediğini belirten bir değer alır. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameSignatureVerificationEx İşlevi](strongnamesignatureverificationex-function.md)  
 Verilen yoltaki derleme bildiriminin güçlü bir ad imzası içerip içermediğini belirten bir değer alır.  .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameSignatureVerificationFromImage İşlevi](strongnamesignatureverificationfromimage-function.md)  
 Belleğe eşlenmiş bir derlemenin ilişkili ortak anahtar için geçerli olduğunu doğrular. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameTokenFromAssembly İşlevi](strongnametokenfromassembly-function.md)  
 Belirtilen derleme dosyasından güçlü bir ad belirteci oluşturur.  .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameTokenFromAssemblyEx İşlevi](strongnametokenfromassemblyex-function.md)  
 Belirtilen derleme dosyasından güçlü bir ad belirteci oluşturur ve ortak anahtarı döndürür. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [StrongNameTokenFromPublicKey İşlevi](strongnametokenfrompublickey-function.md)  
 Ortak anahtarı temsil eden bir belirteç alır. .NET Framework 4 ile başlayan amortismana uğradı.  
  
 [PublicKeyBlob Yapısı](publickeyblob-structure.md)  
 Ortak/özel anahtar çiftinin ortak anahtarını ikili biçimde temsil eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
- [Yönetilmeyen API Başvurusu](../index.md)
