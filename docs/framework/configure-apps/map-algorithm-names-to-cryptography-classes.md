---
title: Algoritma Adlarını Şifreleme Sınıflarıyla Eşleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 49f4b5b4b3634df5e648b5208448d644168e9d19
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566729"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>Algoritma Adlarını Şifreleme Sınıflarıyla Eşleştirme
Bir geliştiricinin Windows SDK kullanarak bir şifreleme nesnesi oluştur, dört yolu vardır:  
  
- **New** işlecini kullanarak bir nesne oluşturun.  
  
- Bu algoritmanın soyut sınıfında **Create** yöntemini çağırarak belirli bir şifreleme algoritmasını uygulayan bir nesne oluşturun.  
  
- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> Yöntemini çağırarak belirli bir şifreleme algoritmasını uygulayan bir nesne oluşturun.  
  
- Bir şifreleme algoritmaları sınıfı (simetrik blok şifresi gibi) uygulayan bir nesne oluşturun (örneğin, <xref:System.Security.Cryptography.SymmetricAlgorithm>) bu tür algoritma Için soyut sınıfta **Create** yöntemini çağırarak.  
  
 Örneğin, bir geliştiricinin bir bayt kümesinin SHA1 karmasını hesaplamak istediğini varsayalım. <xref:System.Security.Cryptography> Ad alanı, tek bir yönetilen uygulama ve CryptoAPI 'yi sarmalayan bir SHA1 algoritmasının iki uygulamasını içerir. Geliştirici, <xref:System.Security.Cryptography.SHA1Managed> **Yeni** işleci çağırarak belirli bir SHA1 uygulamasının (örneğin,) örneğini oluşturmaya seçim yapabilir. Ancak, sınıf, SHA1 karma algoritmasını uyguladığı sürece ortak dil çalışma zamanının hangi sınıftan yüklendiğine bakılmaksızın, Geliştirici <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> yöntemini çağırarak bir nesne oluşturabilir. Bu yöntem, SHA1 karma algoritmasının bir uygulamasını döndürmesi gereken **System. Security. Cryptography. CryptoConfig. CreateFromName ("System. Security. Cryptography. SHA1")** öğesini çağırır.  
  
 Geliştirici, varsayılan olarak, .NET Framework gelen algoritmaların kısa adlarını içerdiğinden, **sistem. Security. Cryptography. CryptoConfig. CreateFromName ("SHA1")** öğesini de çağırabilir.  
  
 Hangi karma algoritmanın kullanıldığına bakılmaksızın geliştirici, karma dönüşüm uygulayan bir nesne döndüren <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> yöntemini çağırabilir.  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>Yapılandırma dosyalarında algoritma adlarını eşleme  
 Varsayılan olarak, çalışma zamanı dört senaryo <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> için bir nesne döndürür. Ancak, bir makine Yöneticisi son iki senaryodaki yöntemlerin döndürdüğü nesne türünü değiştirebilir. Bunu yapmak için, bir kolay algoritma adını makine yapılandırma dosyasında (Machine. config) kullanmak istediğiniz sınıfa eşlemeniz gerekir.  
  
 Aşağıdaki örnek, **System. Security. Cryptography. SHA1. Create**, **System. Security. CryptoConfig. CreateFromName ("SHA1")** ve **System. Security. Cryptography. HashAlgorithm. Create için çalışma zamanının nasıl yapılandırılacağını gösterir.**  bir`MySHA1HashClass` nesne döndürür.  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 [< CryptoClass\> öğesinde](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) özniteliğin adını belirtebilirsiniz (önceki örnek, özniteliğini `MySHA1Hash`adlandırır). CryptoClass > öğesindeki özniteliğin  **\<** değeri, ortak dil çalışma zamanının sınıfı bulmak için kullandığı bir dizedir. [Tam nitelikli tür adlarını belirtirken](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan herhangi bir dizeyi kullanabilirsiniz.  
  
 Birçok algoritma adı aynı sınıfa eşleyebilir. NameEntry > öğesi bir sınıfı bir kolay algoritma adıyla eşleştirir. [ \<](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) **Name** özniteliği, **System. Security. Cryptography. CryptoConfig. CreateFromName** yöntemi veya <xref:System.Security.Cryptography> ad alanındaki bir soyut şifreleme sınıfının adı çağrılırken kullanılan bir dize olabilir. **Sınıf** özniteliğinin değeri,  **\<CryptoClass >** öğesindeki özniteliğin adıdır.  
  
> [!NOTE]
>  <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> Veya **Security. CryptoConfig. CreateFromName ("SHA1")** yöntemini çağırarak bir SHA1 algoritması edinebilirsiniz. Her yöntem yalnızca SHA1 algoritmasını uygulayan bir nesne döndüren garantisi verir. Bir algoritmaların kolay adlarını yapılandırma dosyasındaki aynı sınıfa eşlemek zorunda değilsiniz.  
  
 Varsayılan adların ve eşlendikleri sınıfların listesi için bkz <xref:System.Security.Cryptography.CryptoConfig>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
- [Şifreleme Sınıflarını Yapılandırma](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
