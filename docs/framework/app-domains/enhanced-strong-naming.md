---
title: Güçlü Adlandırmayı İyileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf4a8df87cd507f2bfb17086e83dc8374a22fe71
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746897"
---
# <a name="enhanced-strong-naming"></a>Güçlü Adlandırmayı İyileştirme
Tanımlayıcı ad imzası derlemeleri tanımlamak için bir kimlik .NET Framework'teki mekanizmasıdır. Bu, genellikle bir gönderene (imzalayan) bir alıcı (Doğrulayıcı) geçirilen verilerin bütünlüğünü doğrulamak için kullanılan bir ortak anahtar dijital imza olur. Bu imza, bir derleme için benzersiz bir kimliği olarak kullanılan ve derleme başvurularını belirsiz olmadığından sağlar. Derleme oluşturma işleminin bir parçası olarak imzalanır ve yüklendiğinde sonra doğrulandı.  
  
 Güçlü ad imzaları ile bir derlemeyi izinsiz ve derleme özgün imzalayan anahtarla yeniden imzalama amaçlı tarafların önlemeye yardımcı olur. Ancak, güçlü ad anahtarları yayımcı ilgili herhangi bir güvenilir bilgi içermeyen veya bir sertifika hiyerarşisi içerirler. Sağlam ad imzası derleme imzalanmamış kişiye'nın güvenilirliği garanti ya da bu kişi yasal bir anahtarın sahibi olduğunu gösterir; yalnızca anahtarın sahibini derleme imzalanmamış gösterir. Bu nedenle, bir tanımlayıcı ad imzası güvenen üçüncü taraf kodu için bir güvenlik Doğrulayıcı kullanarak önerilmez. Microsoft Authenticode kod kimlik doğrulaması için önerilen yoldur.  
  
## <a name="limitations-of-conventional-strong-names"></a>Geleneksel tanımlayıcı adlar sınırlamaları  
 Önceki sürümler kullanılan güçlü adlandırma teknolojisi [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aşağıdaki eksiklikleri vardır:  
  
-   Anahtarları sürekli Saldırıya uğramış olan ve geliştirilmiş teknikleri ve donanım ortak anahtarı bir özel anahtar Infer kolaylaştırmak. Saldırılara karşı koruma sağlamak için daha büyük anahtarları gereklidir. .NET framework sürümleri önce [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] (varsayılan büyüklüğü, 1024 bit) tüm boyutu anahtar ile oturum açma olanağı sağlar, ancak yeni bir anahtar ile bir derlemeyi imzalamak derleme eski kimliğini başvuru tüm ikili dosyaları keser. Bu nedenle, uyumluluğu korumak istiyorsanız, imzalama anahtarı boyutunu yükseltmek son derece zordur.  
  
-   Tanımlayıcı ad imzası yalnızca SHA-1 algoritmasını destekler. SHA-1, güvenli karma uygulamalar için yetersiz olması için en son bulunmadı. Bu nedenle, daha güçlü bir algoritma (SHA-256 veya daha büyük) gereklidir. SHA-1 sorunları yalnızca FIPS uyumlu yazılım ve algoritmaları kullanmayı tercih olanlar için sunmak, FIPS uyumlu durumu kaybedersiniz mümkündür.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Gelişmiş tanımlayıcı adlar avantajları  
 Önceden varolan tanımlayıcı adlar ile uyumluluk ve bir kimlik başka eşdeğer olduğunu talep yeteneği Gelişmiş tanımlayıcı adlar ana avantajları şunlardır:  
  
-   Önceden varolan imzalı derlemeler sahip geliştiriciler, SHA-2 algoritmaları eski kimlikleri başvuru derlemeleri uyumluluğunu korurken kimliklerini geçirebilirsiniz.  
  
-   Yeni derlemeleri oluşturma ve güçlü ad imzaları önceden var olan bir kaygınız geliştiriciler daha güvenli SHA-2 algoritmaları ve her zamanki gibi derlemeler oturum kullanabilirsiniz.  
  
## <a name="using-enhanced-strong-names"></a>Gelişmiş güçlü adlarını kullanma  
 Güçlü ad anahtarları bir imza anahtarı ve bir kimlik anahtarı oluşur. Derleme imza anahtarı ile imzalanmış ve kimlik anahtar tarafından tanımlanır. Öncesinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], bu iki anahtarlar aynı. İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]kimlik anahtarı önceki .NET Framework sürümlerinde olduğu gibi aynı kalır, ancak imza anahtarı daha güçlü bir karma algoritması ile geliştirilmiştir. Ayrıca, imza anahtarı karşı imza oluşturmak için kimlik anahtarla imzalanmıştır.  
  
 <xref:System.Reflection.AssemblySignatureKeyAttribute> Özniteliği önceden var olan ortak anahtar çalışmaya devam etmek eski derleme başvurularını sağlayan derleme kimlik için kullanılacak derleme meta verilerini sağlar.  <xref:System.Reflection.AssemblySignatureKeyAttribute> Özniteliğini yeni imza anahtarı sahibi eski kimlik anahtarı sahibi olduğundan emin olmak için tamamlayıcı imza kullanır.  
  
### <a name="signing-with-sha-2-without-key-migration"></a>SHA-2, anahtar geçişi olmadan ile imzalama  
 Tanımlayıcı ad imzası geçirmeden derlemeyi imzalamak için bir komut istemi penceresinden aşağıdaki komutları çalıştırın:  
  
1.  Yeni kimlik anahtarı (gerekirse) oluşturur.  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  Kimlik ortak anahtarı ayıklayın ve SHA-2 algoritmasını bu anahtarla imzalarken kullanılacağını belirtin.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  Gecikme-oturum kimliğini ortak anahtar dosyası derleme.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  Derleme tam kimlik anahtar çifti ile yeniden oturum açın.  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a>SHA-2, anahtar geçişi ile birlikte imzalama  
 Geçirilen sağlam ad imzası ile bir derlemeyi imzalamak için bir komut istemi penceresinden aşağıdaki komutları çalıştırın.  
  
1.  Bir kimlik ve imza anahtar çifti (gerekirse) oluşturur.  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  İmza ortak anahtarı ayıklayın ve SHA-2 algoritmasını bu anahtarla imzalarken kullanılacağını belirtin.  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  Tamamlayıcı imza oluşturur karma algoritmasını belirler kimlik ortak anahtarı ayıklayın.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  Parametrelerini oluşturmak bir <xref:System.Reflection.AssemblySignatureKeyAttribute> özniteliği ve derlemeye öznitelik ekleyebilirsiniz.  
  
    ```  
    sn -ac IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  
  
5.  Gecikme-oturum kimliğini ortak anahtarla derleme.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  Derleme imza anahtar çifti ile tam olarak oturum açın.  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
