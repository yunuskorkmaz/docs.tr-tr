---
title: Tanımlayıcı adlandırmayı iyileştirme
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
ms.openlocfilehash: 1d582513b10de88e4e5b9b9ef8c338599d6980f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141164"
---
# <a name="enhanced-strong-naming"></a>Tanımlayıcı adlandırmayı iyileştirme
Güçlü ad imzası, .NET Framework'de derlemeleri tanımlamak için bir kimlik mekanizmasıdır. Genellikle bir kaynaktan (imzalayan) alıcıya (doğrulayıcı) geçirilen verilerin bütünlüğünü doğrulamak için kullanılan ortak anahtarlı bir dijital imzadır. Bu imza, derleme için benzersiz bir kimlik olarak kullanılır ve derlemeye yapılan başvuruların belirsiz olmamasını sağlar. Derleme yapı işleminin bir parçası olarak imzalanır ve yüklendiğinde doğrulanır.  
  
 Güçlü ad imzaları, kötü niyetli tarafların bir derlemeyi kurcalamasını ve ardından orijinal imzalayanın anahtarıyla derlemeyi yeniden imzalamasını önlemeye yardımcı olur. Ancak, güçlü ad anahtarları yayımcı hakkında güvenilir bir bilgi içermez veya sertifika hiyerarşisi içermez. Güçlü bir ad imzası, montajı imzalayan kişinin güvenilirliğini garanti etmez veya bu kişinin anahtarın yasal sahibi olup olmadığını göstermez; yalnızca anahtarın sahibinin montajı imzaladığını gösterir. Bu nedenle, üçüncü taraf koduna güvenmek için güvenlik doğrulayıcısı olarak güçlü bir ad imzası kullanmanızı önermiyoruz. Microsoft Authenticode, kodun kimliğini doğrulamanın önerilen yoludur.  
  
## <a name="limitations-of-conventional-strong-names"></a>Geleneksel güçlü isimlerin sınırlamaları  
 .NET Framework 4.5'ten önceki sürümlerde kullanılan güçlü adlandırma teknolojisiaşağıdaki eksikliklere sahiptir:  
  
- Anahtarlar sürekli saldırı altındadır ve geliştirilmiş teknikler ve donanım, ortak bir anahtardan özel bir anahtarı çıkarmasını kolaylaştırır. Saldırılara karşı korumak için daha büyük tuşlar gereklidir. .NET Framework 4.5'ten önce .NET Framework sürümleri herhangi bir boyut tuşuyla (varsayılan boyut 1024 bittir) imzalama olanağı sağlar, ancak yeni bir anahtarla bir derlemeimzalama, derlemenin eski kimliğine başvuran tüm ikilileri kırar. Bu nedenle, uyumluluğu korumak istiyorsanız, bir imzalama anahtarıboyutunu yükseltmek son derece zordur.  
  
- Güçlü ad imzalama yalnızca SHA-1 algoritmasını destekler. SHA-1 son zamanlarda güvenli karma uygulamalar için yetersiz olduğu tespit edilmiştir. Bu nedenle, daha güçlü bir algoritma (SHA-256 veya daha büyük) gereklidir. SHA-1'in FIPS uyumlu duruşunu kaybetmesi mümkündür, bu da yalnızca FIPS uyumlu yazılım ve algoritmaları kullanmayı seçenler için sorun teşkil eder.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Gelişmiş güçlü isimlerin avantajları  
 Gelişmiş güçlü adların başlıca avantajları, önceden varolan güçlü adlarla uyumluluk ve bir kimliğin diğerine eşdeğer olduğunu iddia edebilme yeteneğidir:  
  
- Önceden varolan imzalı derlemelere sahip geliştiriciler, eski kimliklere başvuran derlemelerle uyumluluğu korurken kimliklerini SHA-2 algoritmalarına geçirebilirsiniz.  
  
- Yeni derlemeler oluşturan ve önceden varolan güçlü ad imzalarıyla ilgilenmeyen geliştiriciler, daha güvenli SHA-2 algoritmalarını kullanabilir ve derlemeleri her zaman olduğu gibi imzalayabilir.  
  
## <a name="use-enhanced-strong-names"></a>Gelişmiş güçlü adlar kullanma  
 Güçlü ad anahtarları imza anahtarı ve kimlik anahtarından oluşur. Derleme imza anahtarı ile imzalanır ve kimlik anahtarı ile tanımlanır. .NET Framework 4.5'ten önce bu iki anahtar aynıydı. .NET Framework 4.5 ile başlayarak, kimlik anahtarı önceki .NET Framework sürümlerinde olduğu gibi kalır, ancak imza anahtarı daha güçlü bir karma algoritması ile geliştirilmiştir. Buna ek olarak, imza anahtarı bir karşı imza oluşturmak için kimlik anahtarı ile imzalanır.  
  
 Öznitelik, <xref:System.Reflection.AssemblySignatureKeyAttribute> derleme meta verilerinin derleme kimliği için önceden varolan ortak anahtarı kullanmasına olanak tanır ve bu da eski derleme başvurularının çalışmaya devam etmesine olanak tanır.  Öznitelik, <xref:System.Reflection.AssemblySignatureKeyAttribute> yeni imza anahtarının sahibinin aynı zamanda eski kimlik anahtarının sahibi olduğundan emin olmak için karşı imzayı kullanır.  
  
### <a name="sign-with-sha-2-without-key-migration"></a>Anahtar geçişi olmadan SHA-2 ile imzalayın  
 Güçlü bir ad imzası geçirmeden bir derlemeyi imzalamak için komut isteminden aşağıdaki komutları çalıştırın:  
  
1. Yeni kimlik anahtarını oluşturun (gerekirse).  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. Kimlik ortak anahtarını ayıklayın ve bu anahtarla imzalarken SHA-2 algoritmasının kullanılması gerektiğini belirtin.  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. Kimlik ortak anahtar dosyasıyla montajı geciktirme işareti.  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. Tam kimlik anahtar çifti ile montajı yeniden imzalayın.  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a>ANAHTAR geçişi ile SHA-2 ile imzalayın  
 Geçirilen güçlü ad imzası olan bir derlemeyi imzalamak için komut isteminden aşağıdaki komutları çalıştırın.  
  
1. Kimlik ve imza anahtar çifti (gerekirse) oluşturun.  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. İmza ortak anahtarını ayıklayın ve bu anahtarla imzalanırken SHA-2 algoritmasının kullanılması gerektiğini belirtin.  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. Karşı imza oluşturan karma algoritmasını belirleyen kimlik ortak anahtarını ayıklayın.  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. Bir <xref:System.Reflection.AssemblySignatureKeyAttribute> öznitelik için parametreleri oluşturun ve özniteliği derlemeye takın.  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    Bu, aşağıdakine benzer çıktı üretir.

    ```output
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

    Bu çıktı daha sonra bir AssemblySignatureKeyAttribute dönüştürülebilir.

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. Kimlik ortak anahtarıyla montajı geciktirme işareti.  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. Tam imza anahtar çifti ile montaj imzalayın.  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
