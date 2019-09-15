---
title: Gelişmiş tanımlayıcı adlandırma
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f9a5c848a8a46b72fb39865ffa861424107438
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973252"
---
# <a name="enhanced-strong-naming"></a>Gelişmiş tanımlayıcı adlandırma
Tanımlayıcı ad imzası, derlemeleri tanımlamak için .NET Framework bir kimlik mekanizmasıdır. Genellikle bir oluşturana (imzalayan) bir alıcıya (Doğrulayıcı) geçirilen verilerin bütünlüğünü doğrulamak için kullanılan ortak anahtar dijital imzadır. Bu imza, bir derleme için benzersiz bir kimlik olarak kullanılır ve derlemeye yapılan başvuruların belirsiz olmamasını sağlar. Derleme, derleme sürecinin bir parçası olarak imzalanır ve sonra yüklendiğinde doğrulanır.  
  
 Tanımlayıcı ad imzaları kötü amaçlı tarafların bir bütünleştirilmiş koda müdahale etmelerini önlemeye yardımcı olur ve derlemeyi özgün imzalayan anahtarıyla yeniden imzalamasını önler. Ancak, tanımlayıcı ad anahtarları yayımcı hakkında güvenilir bilgiler içermez ve bir sertifika hiyerarşisi içermez. Tanımlayıcı ad imzası, derlemeyi imzalayan kişinin güvenilirliğini garanti etmez veya bu kişinin, anahtarın meşru sahibi olup olmadığını belirtir; yalnızca anahtarın sahibinin derlemeyi imzaladığı anlamına gelir. Bu nedenle, üçüncü taraf koda güvenmek için bir güvenlik doğrulayıcısı olarak tanımlayıcı ad imzası kullanılması önerilmez. Microsoft Authenticode, kodun kimliğini doğrulamak için önerilen yoldur.  
  
## <a name="limitations-of-conventional-strong-names"></a>Geleneksel tanımlayıcı adların sınırlamaları  
 .NET Framework 4,5 ' den önceki sürümlerde kullanılan tanımlayıcı adlandırma teknolojisinin aşağıdaki eksiklikleri vardır:  
  
- Anahtarlar sürekli saldırı aşamasındadır ve geliştirilmiş teknikler ve donanımlar, ortak anahtardan özel bir anahtar çıkarmayı kolaylaştırır. Saldırılara karşı koruma sağlamak için daha büyük anahtarlar gereklidir. .NET Framework 4,5 ' den önceki sürümlerde .NET Framework, herhangi bir boyut anahtarıyla (varsayılan boyut 1024 bit) oturum açabilme olanağı sağlar, ancak yeni bir anahtarla bir derlemeyi imzalamak, derlemenin eski kimliğine başvuran tüm ikili dosyaları keser. Bu nedenle, uyumluluk sağlamak istiyorsanız İmzalama anahtarının boyutunu yükseltmek son derece zordur.  
  
- Tanımlayıcı ad imzalama yalnızca SHA-1 algoritmasını destekler. SHA-1 ' in yakın zamanda güvenli karma uygulamalar için yetersiz olduğu belirlenmiştir. Bu nedenle, daha güçlü bir algoritma (SHA-256 veya üzeri) gereklidir. SHA-1 ' i, FIPS ile uyumlu olan ve yalnızca FIPS uyumlu yazılım ve algoritmaları kullanmayı seçen sorunlar sunacak şekilde kaybedecektir.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Gelişmiş tanımlayıcı adların avantajları  
 Gelişmiş tanımlayıcı adların başlıca avantajları, önceden var olan kesin adlarla ve bir kimliğin diğerine eşdeğer bir şekilde talep etme özelliği ile uyumludur:  
  
- Önceden varolan imzalı derlemeler içeren geliştiriciler, eski kimliklere başvuran Derlemelerle uyumluluğu sürdürirken kimliklerini SHA-2 algoritmalarına geçirebilir.  
  
- Yeni derlemeler oluşturan ve önceden var olan güçlü ad imzalarıyla ilgilenme yapan geliştiriciler, daha güvenli SHA-2 algoritmalarını kullanabilir ve derlemeleri her zaman sahip oldukları şekilde imzalayabilirler.  
  
## <a name="use-enhanced-strong-names"></a>Gelişmiş tanımlayıcı adlar kullanın  
 Tanımlayıcı ad anahtarları bir imza anahtarından ve bir kimlik anahtarından oluşur. Derleme imza anahtarıyla imzalanır ve kimlik anahtarı tarafından tanımlanır. .NET Framework 4,5 ' den önce bu iki anahtar birbirinin aynısıdır. .NET Framework 4,5 ' den başlayarak, kimlik anahtarı önceki .NET Framework sürümlerle aynı kalır, ancak imza anahtarı daha güçlü bir karma algoritmayla geliştirilmiştir. Ayrıca, imza anahtarı kimlik anahtarıyla imzalanır ve bir sayaç imzası oluşturulur.  
  
 <xref:System.Reflection.AssemblySignatureKeyAttribute> Özniteliği, derleme meta verilerinin derleme kimliği için önceden mevcut ortak anahtarı kullanmasını sağlar, bu da eski derleme başvurularının çalışmaya devam etmesine olanak tanır.  <xref:System.Reflection.AssemblySignatureKeyAttribute> Özniteliği, yeni imza anahtarı sahibinin de eski kimlik anahtarının sahibi olduğundan emin olmak için sayaç imzasını kullanır.  
  
### <a name="sign-with-sha-2-without-key-migration"></a>Anahtar Geçişi olmadan SHA-2 ile imzala  
 Bir derlemeyi tanımlayıcı ad imzasına geçirmeden imzalamak için komut isteminden aşağıdaki komutları çalıştırın:  
  
1. Yeni kimlik anahtarını (gerekliyse) oluşturun.  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2. Kimlik ortak anahtarını ayıklayın ve bu anahtarla imzalarken bir SHA-2 algoritmasının kullanılması gerektiğini belirtin.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. Derlemeyi kimlik ortak anahtar dosyası ile gecikmeli imzalayın.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. Derlemeyi tam kimlik anahtar çifti ile yeniden imzalayın.  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a>Anahtar geçişi ile SHA-2 ile oturum açma  
 Bir derlemeyi geçirilmiş bir tanımlayıcı ad imzasıyla imzalamak için komut isteminden aşağıdaki komutları çalıştırın.  
  
1. Bir kimlik ve imza anahtarı çifti oluşturun (gerekirse).  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. İmza ortak anahtarını ayıklayın ve bu anahtarla imzalarken bir SHA-2 algoritmasının kullanılması gerektiğini belirtin.  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. Bir sayaç imzası üreten karma algoritmayı belirleyen kimlik ortak anahtarını ayıklayın.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. Bir <xref:System.Reflection.AssemblySignatureKeyAttribute> öznitelik için parametreler oluşturun ve özniteliği derlemeye ekleyin.  
  
    ```  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    Bu, aşağıdakine benzer bir çıktı üretir.

    ```
    Information for key migration attribute.
    (System.Reflection.AssemblySignatureKeyAttribute):
    publicKey=
    002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519
    d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936
    e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b4
    3893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a3
    4d153cdd

    counterSignature=
    e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91eb
    e1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8
    ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3
    ae5fec2c682e57b7442738
    ```

    Bu çıkış daha sonra AssemblySignatureKeyAttribute içine dönüştürülebilir.

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. Derlemeyi kimlik ortak anahtarı ile gecikmeli imzalayın.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. Derlemeyi imza anahtar çiftiyle tamamen imzalayın.  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
