---
title: "Algoritma Adlarını Şifreleme Sınıflarıyla Eşleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9c9c5b1f69200d4ee5d39c98445b668813718dd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>Algoritma Adlarını Şifreleme Sınıflarıyla Eşleştirme
Bir geliştirici, şifreleme nesnesini kullanarak oluşturabilirsiniz dört yolla [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:  
  
-   Kullanarak bir nesne oluşturma **yeni** işleci.  
  
-   Belirli şifreleme algoritması çağırarak uygulayan bir nesne oluşturma **oluşturma** bu algoritma için Özet sınıf üzerinde yöntemi.  
  
-   Belirli şifreleme algoritması çağırarak uygulayan bir nesne oluşturma <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemi.  
  
-   Şifreleme algoritmalarını (örneğin, bir simetrik blok şifreleme) sınıfının çağırarak uygulayan bir nesne oluşturma **oluşturma** algoritma türü için Özet sınıf üzerinde yöntemi (gibi <xref:System.Security.Cryptography.SymmetricAlgorithm>).  
  
 Örneğin, bir geliştirici, bir dizi bayt SHA1 karmasını işlem istediğini varsayalım. <xref:System.Security.Cryptography> Ad alanı, SHA1 algoritması, tamamen yönetilen bir uygulama ve CryptoAPI saran bir, iki uygulamalarını içerir. Belirli bir SHA1 uygulama örneği oluşturmak geliştiricinin seçebilirsiniz (gibi <xref:System.Security.Cryptography.SHA1Managed>) çağırarak **yeni** işleci. Ortak dil çalışma zamanı yükler SHA1 karma algoritmasını sınıfı uygulayan sürece hangi sınıfın önemli değildir, ancak, geliştiricinin bir nesne çağırarak oluşturabilirsiniz <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> yöntemi. Bu yöntemi çağırır **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, SHA1 karma algoritmasını uygulaması döndürmelidir.  
  
 Geliştirici da çağırabilir **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** varsayılan olarak, .NET Framework'teki sevk algoritmalar için kısa adları şifreleme yapılandırması içerdiğinden.  
  
 Karma algoritmayı kullanılan önemli değildir, geliştirici çağırabilirsiniz <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> yöntemi bir karma dönüştürmesi uygulayan bir nesne döndürür.  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>Yapılandırma dosyalarında algoritma adlarını eşleme  
 Varsayılan olarak, çalışma zamanı döndüren bir <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> tüm dört senaryo için nesnesi. Ancak, bir Makine Yöneticisi son iki senaryo yöntemlerinde dönüş nesne türünü değiştirebilirsiniz. Bunu yapmak için bir kolay algoritma adı makine yapılandırma dosyasındaki (Machine.config) kullanmak istediğiniz sınıfı eşlenmelidir.  
  
 Aşağıdaki örnek çalışma zamanı yapılandırmak nasıl gösterir şekilde **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, ve  **System.Security.Cryptography.HashAlgorithm.Create** dönüş bir `MySHA1HashClass` nesnesi.  
  
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
  
 Özniteliğin adını belirtebilirsiniz [< cryptoClass\> öğesi](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (önceki örnekte öznitelik adları `MySHA1Hash`). Özniteliğin değerini  **\<cryptoClass >** öğesidir ortak dil çalışma zamanı sınıfı bulmak için kullandığı bir dize. Belirtilen gereksinimleri karşılayan herhangi bir dize kullanabilirsiniz [belirtme tam olarak nitelenmiş tür adları](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).  
  
 Çok sayıda algoritma adlarını aynı sınıfa eşleyebilirsiniz. [ \<NameEntry > öğesi](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) bir sınıf için bir kolay algoritma adı eşler. **Adı** özniteliği çağrılırken kullanılan ya da bir dize olabilir **System.Security.Cryptography.CryptoConfig.CreateFromName** soyutşifrelemesınıfındaadıveyayöntemi<xref:System.Security.Cryptography> ad alanı. Değeri **sınıfı** özniteliği özniteliğinde adıdır  **\<cryptoClass >** öğesi.  
  
> [!NOTE]
>  SHA1 algoritması çağırarak alabileceğiniz <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> veya **Security.CryptoConfig.CreateFromName("SHA1")** yöntemi. Her yöntem, yalnızca SHA1 algoritması uygulayan bir nesne döndürür güvence altına alır. Aynı sınıf yapılandırma dosyasındaki her bir algoritma kolay adını Eşle gerekmez.  
  
 Varsayılan adlarını ve eşlemek için sınıflar listesi için bkz: <xref:System.Security.Cryptography.CryptoConfig>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)  
 [Şifreleme Sınıflarını Yapılandırma](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
