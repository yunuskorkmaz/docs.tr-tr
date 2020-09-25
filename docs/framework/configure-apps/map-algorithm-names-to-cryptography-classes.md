---
title: Algoritma Adlarını Şifreleme Sınıflarıyla Eşleştirme
description: Algoritma adlarını .NET 'teki şifreleme sınıflarıyla eşleyin. Bir geliştirici, şifreleme nesnesi oluşturmak için dört seçeneğe sahiptir.
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: b67db612496e56a341dab2e5fc4b52c954ff02b4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183396"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>Algoritma Adlarını Şifreleme Sınıflarıyla Eşleştirme

Bir geliştiricinin Windows SDK kullanarak bir şifreleme nesnesi oluştur, dört yolu vardır:  
  
- **New** işlecini kullanarak bir nesne oluşturun.  
  
- Bu algoritmanın soyut sınıfında **Create** yöntemini çağırarak belirli bir şifreleme algoritmasını uygulayan bir nesne oluşturun.  
  
- Yöntemini çağırarak belirli bir şifreleme algoritmasını uygulayan bir nesne oluşturun <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> .  
  
- Bir şifreleme algoritmaları sınıfı (simetrik blok şifresi gibi) uygulayan bir nesne oluşturun (örneğin,) bu tür algoritma için soyut sınıfta **Create** yöntemini çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm> .  
  
 Örneğin, bir geliştiricinin bir bayt kümesinin SHA1 karmasını hesaplamak istediğini varsayalım. <xref:System.Security.Cryptography>Ad alanı, tek bir yönetilen uygulama ve CryptoAPI 'yi sarmalayan BIR SHA1 algoritmasının iki uygulamasını içerir. Geliştirici, <xref:System.Security.Cryptography.SHA1Managed> **Yeni** işleci ÇAĞıRARAK belirli bir SHA1 uygulamasının (örneğin,) örneğini oluşturmaya seçim yapabilir. Ancak, sınıf, SHA1 karma algoritmasını uyguladığı sürece ortak dil çalışma zamanının hangi sınıftan yüklendiğine bakılmaksızın, geliştirici yöntemini çağırarak bir nesne oluşturabilir <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> . Bu yöntem, SHA1 karma algoritmasının bir uygulamasını döndürmesi gereken **System. Security. Cryptography. CryptoConfig. CreateFromName ("System. Security. Cryptography. SHA1")** öğesini çağırır.  
  
 Geliştirici, varsayılan olarak, .NET Framework gelen algoritmaların kısa adlarını içerdiğinden, **sistem. Security. Cryptography. CryptoConfig. CreateFromName ("SHA1")** öğesini de çağırabilir.  
  
 Hangi karma algoritmanın kullanıldığına bakılmaksızın geliştirici, <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> karma dönüşüm uygulayan bir nesne döndüren yöntemini çağırabilir.  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>Yapılandırma dosyalarında algoritma adlarını eşleme  

 Varsayılan olarak, çalışma zamanı <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> dört senaryo için bir nesne döndürür. Ancak, bir makine Yöneticisi son iki senaryodaki yöntemlerin döndürdüğü nesne türünü değiştirebilir. Bunu yapmak için, bir kolay algoritma adını makine yapılandırma dosyasında (Machine.config) kullanmak istediğiniz sınıfa eşlemeniz gerekir.  
  
 Aşağıdaki örnek, **System. Security. Cryptography. SHA1. Create**, **System. Security. CryptoConfig. CreateFromName ("SHA1")** ve **System. Security. Cryptography. HashAlgorithm. Create** için bir nesne döndürmesi amacıyla çalışma zamanının nasıl yapılandırılacağını gösterir `MySHA1HashClass` .  
  
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
  
 [<cryptoClass \> öğesinde](./file-schema/cryptography/cryptoclass-element.md) özniteliğin adını belirtebilirsiniz (önceki örnek, özniteliğini adlandırır `MySHA1Hash` ). Öğesindeki özniteliğin değeri, **\<cryptoClass>** ortak dil çalışma zamanının sınıfı bulmak için kullandığı bir dizedir. [Tam nitelikli tür adlarını belirtirken](../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan herhangi bir dizeyi kullanabilirsiniz.  
  
 Birçok algoritma adı aynı sınıfa eşleyebilir. [ \<nameEntry> Öğesi](./file-schema/cryptography/nameentry-element.md) bir sınıfı bir kolay algoritma adıyla eşleştirir. **Name** özniteliği, **System. Security. Cryptography. CryptoConfig. CreateFromName** yöntemi veya ad alanındaki bir soyut şifreleme sınıfının adı çağrılırken kullanılan bir dize olabilir <xref:System.Security.Cryptography> . **Sınıf** özniteliğinin değeri, öğesindeki özniteliğin adıdır **\<cryptoClass>** .  
  
> [!NOTE]
> <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>Veya **Security. CryptoConfig. CreateFromName ("SHA1")** YÖNTEMINI çağırarak bir SHA1 algoritması edinebilirsiniz. Her yöntem yalnızca SHA1 algoritmasını uygulayan bir nesne döndüren garantisi verir. Bir algoritmaların kolay adlarını yapılandırma dosyasındaki aynı sınıfa eşlemek zorunda değilsiniz.  
  
 Varsayılan adların ve eşlendikleri sınıfların listesi için bkz <xref:System.Security.Cryptography.CryptoConfig> ..  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](../../standard/security/cryptographic-services.md)
- [Şifreleme Sınıflarını Yapılandırma](configure-cryptography-classes.md)
