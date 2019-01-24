---
title: Güçlü Adlandırmayı İyileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a0b63e27a3eceb80d42d43eea321b0dc757ad69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688876"
---
# <a name="enhanced-strong-naming"></a>Güçlü Adlandırmayı İyileştirme
Tanımlayıcı ad imzası derlemeleri tanımlamak için bir kimlik .NET Framework mekanizmasıdır. Buna genellikle bir oluşturucu (imzalayan) alıcıya (doğrulama) geçirilen verilerin bütünlüğünü doğrulamak için kullanılan ortak anahtar dijital imzası var. Bu imza, bir derleme için benzersiz bir kimlik kullanılır ve derlemeye yapılan başvuruların belirsiz olmamasını sağlar. Derleme oluşturma işleminin bir parçası imzalanır ve sonra yüklendiğinde doğrulanır.  
  
 Tanımlayıcı ad imzaları, kötü amaçlı taraflar bir derlemeye müdahale etmesine ve derlemeyi özgün İmzalayanın anahtarıyla yeniden imzalama engelleyin. Ancak kesin ad anahtarları yayıncı hakkında herhangi bir güvenilir bilgi içermeyen ya da bunlar bir sertifika hiyerarşisi içermez. Tanımlayıcı ad imzası derlemeyi imzalayan kişinin güvenilirliğini garanti vermez veya söz konusu kişinin anahtarın yasal sahibi olup olmadığını göstermez; yalnızca anahtar sahibinin derlemeyi imzaladığını gösterir. Bu nedenle, tanımlayıcı ad imzası, güvenen üçüncü taraf kodu için güvenlik Doğrulayıcısı olarak kullanılması önerilmez. Microsoft Authenticode, kod kimlik doğrulaması için önerilen yoldur.  
  
## <a name="limitations-of-conventional-strong-names"></a>Geleneksel tanımlayıcı adlar kısıtlamaları  
 Önceki sürümlerde kullanılan tanımlayıcı adlandırma teknolojisinin [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aşağıdaki eksiklikleri vardır:  
  
-   Anahtarlar sürekli saldırı altında olan ve gelişmiş teknikler ve donanım bir özel anahtarı bir ortak anahtar Infer kolaylaştırır. Saldırılara karşı korunmak için büyük anahtarlar gereklidir. .NET framework sürümlerini önce [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] herhangi boyutta anahtarla (varsayılan boyut 1024 bit olan) olanağı sağlar, ancak yeni anahtarla bir derlemeyi imzalamak, derlemenin daha eski kimliği başvuran tüm ikili dosyaları keser. Bu nedenle, uyumluluğu korumak istiyorsanız, bir imzalama anahtarı boyutunu yükseltmek son derece zordur.  
  
-   Tanımlayıcı ad imzası yalnızca SHA-1 algoritmasını destekler. SHA-1, güvenli karma uygulamalar için yetersiz olduğu yakın zamanda bulundu. Bu nedenle, daha güçlü bir algoritma (SHA-256 veya daha büyük) gereklidir. SHA-1 yalnızca FIPS uyumlu yazılım ve algoritmaları kullanmayı tercih edenler için sorunlara neden olabilir, FIPS uyumlu ayakta kaybedersiniz mümkündür.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Gelişmiş tanımlayıcı adların avantajları  
 Önceden varolan tanımlayıcı adlarla uyumluluk ve tek bir kimlik diğerine eşdeğer olduğunu iddia edebilme yeteneğidir geliştirilmiş tanımlayıcı adların başlıca avantajları şunlardır:  
  
-   Önceden mevcut olan imzalı derlemelere sahip geliştiriciler eski kimliklere başvuran derlemeler ile uyumluluğu korurken kendi kimliklerini SHA-2 algoritmalarına geçirebilirsiniz.  
  
-   Yeni derlemeler oluşturan ve tanımlayıcı ad imzaları önceden mevcut olan ilgisi olmayan geliştiriciler daha güvenli SHA-2 algoritmalarını kullanabilir ve her zaman olduğu gibi derlemelerini imzalayabilirler.  
  
## <a name="using-enhanced-strong-names"></a>Geliştirilmiş katı adları kullanma  
 Tanımlayıcı ad anahtarı bir imza anahtarı ve bir kimlik anahtarından oluşur. Derleme imza anahtarıyla imzalanır ve kimlik anahtarı tarafından tanımlanır. Öncesinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], bu iki tuş aynıydı. İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]kimlik anahtarı önceki .NET Framework sürümlerinde olduğu gibi aynı kalır, ancak imza anahtarı daha güçlü bir karma algoritması ile geliştirilmiştir. Ayrıca, imza anahtarı kimlik anahtarı ile bir karşı imza oluşturmak için imzalanır.  
  
 <xref:System.Reflection.AssemblySignatureKeyAttribute> Özniteliği derleme meta verileri, eski derleme başvurularının çalışmaya devam etmeyi sağlayan derleme kimliği için önceden varolan genel anahtarı kullanmayı sağlar.  <xref:System.Reflection.AssemblySignatureKeyAttribute> Özniteliği, yeni imza anahtarı sahibinin eski kimlik anahtarının sahibi olduğundan emin olmak için olması için karşı imzayı kullanır.  
  
### <a name="signing-with-sha-2-without-key-migration"></a>SHA-2, anahtar geçişi olmadan imzalama  
 Bir derlemeyi bir güçlü ad geçirmeden imzalamak için bir komut istemi penceresinden aşağıdaki komutları çalıştırın:  
  
1.  Yeni bir kimlik anahtarı (gerekiyorsa) üretin.  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  Kimlik genel anahtarını ayıklayın ve bu anahtar ile imzalarken bir SHA-2 algoritmasının kullanılacağını belirtin.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  Derlemeyi kimlik genel anahtar dosyasıyla Gecikmeli imzalayın.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  Derlemeyi tam kimlik anahtar çifti ile yeniden imzalayın.  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a>SHA-2 ile anahtar geçişi ile imzalama  
 Bir derlemeyi geçirilen kesin ad imzalı imzalamak için bir komut istemi penceresinden aşağıdaki komutları çalıştırın.  
  
1.  Bir kimlik ve imza anahtar çifti (gerekiyorsa) üretin.  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  İmza genel anahtarını ayıklayın ve bu anahtar ile imzalarken bir SHA-2 algoritmasının kullanılacağını belirtin.  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  Bir karşı imza üreten karma algoritmayı belirleyen kimlik genel anahtarını ayıklayın.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  İçin parametreler üretin bir <xref:System.Reflection.AssemblySignatureKeyAttribute> özniteliği ve özniteliği derlemeye ekleyin.  
  
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

    Bu çıkış ardından dönüştürülmüş bir AssemblySignatureKeyAttribute.

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5.  Derlemeyi kimlik genel anahtarıyla Gecikmeli imzalayın.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  Derlemeyi imza kimlik anahtar çifti ile tam olarak imzalayın.  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
