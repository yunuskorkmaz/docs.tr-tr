---
title: Algoritma Adlarını Şifreleme Sınıflarıyla Eşleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 87b428fffac98b4490a67e4713b56ec6e8fdcfe9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569199"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>Algoritma Adlarını Şifreleme Sınıflarıyla Eşleştirme
Bir geliştirici, şifreleme kullanarak nesne oluşturabilirsiniz dört yolla [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:  
  
-   Kullanarak bir nesne oluşturma **yeni** işleci.  
  
-   Belirli bir şifreleme algoritması çağırarak uygulayan bir nesne oluşturma **Oluştur** bu algoritmayı için soyut sınıf yöntemi.  
  
-   Belirli bir şifreleme algoritması çağırarak uygulayan bir nesne oluşturma <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemi.  
  
-   Bir sınıf (örneğin, bir simetrik blok şifreleme) şifreleme algoritmalarının çağırarak uygulayan bir nesne oluşturma **Oluştur** algoritma türü için soyut sınıf yöntemini (gibi <xref:System.Security.Cryptography.SymmetricAlgorithm>).  
  
 Örneğin, bir geliştirici bayt kümesinin SHA1 karması hesaplanamadı istediğini varsayalım. <xref:System.Security.Cryptography> Ad alanı, SHA1 algoritması, tamamen yönetilen bir uygulama ve CryptoAPI sarmalayan bir iki uygulamaları içerir. Belirli bir SHA1 uygulama oluşturmak Geliştirici seçebilirsiniz (gibi <xref:System.Security.Cryptography.SHA1Managed>) çağırarak **yeni** işleci. Ortak dil çalışma zamanını SHA1 karma algoritması sınıfın uyguladığı sürece hangi sınıfın önemli değildir, ancak geliştirici nesneyi çağırarak oluşturabilirsiniz <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> yöntemi. Bu yöntemin çağırdığı **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, SHA1 karma algoritması uygulaması döndürmelidir.  
  
 Geliştirici de çağırabilirsiniz **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** varsayılan olarak, .NET Framework'teki sevk algoritmalar için kısa adları şifreleme yapılandırma içerdiğinden,.  
  
 Karma algoritmayı kullanılan önemli değildir, geliştirici çağırabilirsiniz <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> yöntemi karma bir dönüştürme uygulayan bir nesne döndürür.  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>Yapılandırma dosyalarında algoritma adlarını eşleme  
 Varsayılan olarak, çalışma zamanı döndüren bir <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> tüm dört senaryo için nesne. Ancak, bir makine yöneticisinin en son iki senaryoda yöntemleri dönüş nesne türünü değiştirebilirsiniz. Bunu yapmak için makine yapılandırma dosyasındaki (Machine.config) kullanmak istediğiniz sınıf için kolay algoritma adı eşlemeniz gerekir.  
  
 Aşağıdaki örnek, çalışma zamanı yapılandırma işlemi gösterilmektedir böylece **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, ve  **System.Security.Cryptography.HashAlgorithm.Create** dönüş bir `MySHA1HashClass` nesne.  
  
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
  
 Öznitelik adı belirtebilirsiniz [< cryptoClass\> öğesi](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (önceki örnekte, öznitelik adları `MySHA1Hash`). Öznitelik değeri  **\<cryptoClass >** öğesi olan sınıfı bulmak için ortak dil çalışma zamanı kullanan bir dize. Belirtilen gereksinimleri karşılayan herhangi bir dize kullanabileceğiniz [belirtme tam olarak nitelenmiş tür adlarını](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).  
  
 Birçok algoritma adlarını aynı sınıfa eşleyebilirsiniz. [ \<NameEntry > öğesi](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) bir sınıf için bir kolay algoritma adını eşleştirir. **Adı** özniteliği ararken kullanılan bir dize olabilir **System.Security.Cryptography.CryptoConfig.CreateFromName** yöntemi veya birsoyutşifrelemesınıfınınadı<xref:System.Security.Cryptography> ad alanı. Değerini **sınıfı** adı özniteliği bir özniteliktir  **\<cryptoClass >** öğesi.  
  
> [!NOTE]
>  Çağırarak bir SHA1 algoritması alabilirsiniz <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> veya **Security.CryptoConfig.CreateFromName("SHA1")** yöntemi. Her yöntem, yalnızca SHA1 algoritması uygulayan bir nesne döndürür güvence altına alır. Aynı sınıfa yapılandırma dosyasındaki her bir algoritma kolay adı eşleme gerekmez.  
  
 Varsayılan adları ve eşlemek için sınıflar listesi için bkz. <xref:System.Security.Cryptography.CryptoConfig>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
- [Şifreleme Sınıflarını Yapılandırma](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
