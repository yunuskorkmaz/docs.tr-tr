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
ms.openlocfilehash: a697d96864f336982c05b5bcc7c48efef2df0f6a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799211"
---
# <a name="strong-naming-unmanaged-api-reference"></a>Tanımlayıcı Ad Oluşturma (Yönetilmeyen API Başvurusu)
Güçlü adlandırma API 'SI, bir istemcinin derlemeler için tanımlayıcı ad imzalamayı yönetmesine olanak sağlar.  
  
 Bir derlemeyi katı bir adla imzalamak, dosyaya derleme bildirimini içeren ortak bir anahtar şifrelemesi ekler. Tanımlayıcı ad imzalama, ad benzersizliği doğrulamaya yardımcı olur, ad yanıltmasını önler ve bir başvuru çözüldüğünde çağıranlar benzersiz bir kimlik sağlar. Ancak, tanımlayıcı bir adla ilişkili güven düzeyi yoktur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
> [!NOTE]
> Bu işlevlerin tümü .NET Framework 4 ' den itibaren kullanımdan kaldırılmıştır. Önerilen alternatifler için [ICLRStrongName](../hosting/iclrstrongname-interface.md) arabirimine bakın.  
  
 [GetHashFromAssemblyFile İşlevi](gethashfromassemblyfile-function.md)  
 Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [GetHashFromAssemblyFileW İşlevi](gethashfromassemblyfilew-function.md)  
 Belirtilen karma algoritmasını kullanarak, Unicode dizesi olarak belirtilen derleme dosyasının karmasını alır. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [GetHashFromBlob İşlevi](gethashfromblob-function.md)  
 Belirtilen karma algoritmasını kullanarak, belirtilen bellek adresindeki derlemenin karmasını alır. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [GetHashFromFile İşlevi](gethashfromfile-function.md)  
 Belirtilen dosyanın içeriği üzerinde bir karma oluşturur.  .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [GetHashFromFileW İşlevi](gethashfromfilew-function.md)  
 Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [GetHashFromHandle İşlevi](gethashfromhandle-function.md)  
 Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısına sahip dosyanın içeriği üzerinde bir karma oluşturur.  .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameCompareAssemblies İşlevi](strongnamecompareassemblies-function.md)  
 İki derlemenin yalnızca kendi tanımlayıcı ad imzalarına göre farklı olup olmadığını belirler. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameErrorInfo İşlevi](strongnameerrorinfo-function.md)  
 Tanımlayıcı ad işlevlerinden biri tarafından oluşturulan son hata kodunu alır.  
  
 [StrongNameFreeBuffer İşlevi](strongnamefreebuffer-function.md)  
 [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)veya [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)gibi bir tanımlayıcı ad işlevine daha önceki bir çağrı ile ayrılmış belleği serbest bırakır.   .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameGetBlob İşlevi](strongnamegetblob-function.md)  
 Belirtilen adresteki yürütülebilir dosyanın ikili gösterimiyle belirtilen arabelleği doldurur. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameGetBlobFromImage İşlevi](strongnamegetblobfromimage-function.md)  
 Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameGetPublicKey İşlevi](strongnamegetpublickey-function.md)  
 Özel/ortak anahtar çiftinden ortak anahtarı alır. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameHashSize İşlevi](strongnamehashsize-function.md)  
 Belirtilen karma algoritmasını kullanarak bir karma için gereken arabellek boyutunu alır.  .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameKeyDelete İşlevi](strongnamekeydelete-function.md)  
 Belirtilen anahtar kapsayıcısını siler. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameKeyGen İşlevi](strongnamekeygen-function.md)  
 Tanımlayıcı ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.  .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameKeyGenEx İşlevi](strongnamekeygenex-function.md)  
 Tanımlayıcı ad kullanımı için belirtilen anahtar boyutuyla yeni bir ortak/özel anahtar çifti oluşturur. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameKeyInstall İşlevi](strongnamekeyinstall-function.md)  
 Bir kapsayıcıya ortak/özel anahtar çifti aktarır.  .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameSignatureGeneration İşlevi](strongnamesignaturegeneration-function.md)  
 Belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.   .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameSignatureGenerationEx İşlevi](strongnamesignaturegenerationex-function.md)  
 Belirtilen bayrakları temel alarak, belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.    .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameSignatureSize İşlevi](strongnamesignaturesize-function.md)  
 Tanımlayıcı ad imzasının boyutunu döndürür. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameSignatureVerification İşlevi](strongnamesignatureverification-function.md)  
 Belirtilen bayrağa göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameSignatureVerificationEx İşlevi](strongnamesignatureverificationex-function.md)  
 Belirtilen yoldaki Derleme bildiriminin tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.  .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameSignatureVerificationFromImage İşlevi](strongnamesignatureverificationfromimage-function.md)  
 Zaten bellekle eşlenmiş bir derlemenin ilişkili ortak anahtar için geçerli olduğunu doğrular. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameTokenFromAssembly İşlevi](strongnametokenfromassembly-function.md)  
 Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur.  .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameTokenFromAssemblyEx İşlevi](strongnametokenfromassemblyex-function.md)  
 Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur ve ortak anahtarı döndürür. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [StrongNameTokenFromPublicKey İşlevi](strongnametokenfrompublickey-function.md)  
 Ortak anahtarı temsil eden bir belirteç alır. .NET Framework 4 ile başlayarak kullanım dışıdır.  
  
 [PublicKeyBlob Yapısı](publickeyblob-structure.md)  
 İkili biçimdeki ortak/özel anahtar çiftinin ortak anahtarını temsil eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
- [Yönetilmeyen API Başvurusu](../index.md)
