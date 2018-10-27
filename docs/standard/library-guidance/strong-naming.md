---
title: Tanımlayıcı ad oluşturma ve .NET kitaplıkları
description: Tanımlayıcı adlandırma .NET kitaplıkları için en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/16/2018
ms.openlocfilehash: 6f5743c7a8c6fdbdcdcf3aa80d2f92f2e04621f2
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50041774"
---
# <a name="strong-naming"></a>Tanımlayıcı ad oluşturma

Tanımlayıcı adlandırma başvuruyor üreten bir anahtarla bir derlemeyi imzalamak için bir [tanımlayıcı adlı derleme](../../framework/app-domains/strong-named-assemblies.md). Kesin adlandırılmış bir derlemedir, adı ve derleme sürüm numarasına göre benzersiz bir kimliği oluşturur ve derleme çakışmalarının önlenmesine yardımcı olabilir.

Tanımlayıcı adlandırma için dezavantajı, bir derleme tanımlayıcı ada sonra Windows üzerinde .NET Framework derlemeleri katı yüklenmesini sağlayan ' dir. Bir tanımlayıcı adlı bütünleştirilmiş kod başvurusu geliştiricilerine zorlama, bir derleme tarafından başvurulan sürümü tam olarak eşleşmelidir [bağlama yeniden yönlendirmeleri yapılandırma](../../framework/configure-apps/redirect-assembly-versions.md) derleme kullanırken:

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly" publicKeyToken="32ab4ba45e0a69a1" culture="neutral" />
            <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

.NET geliştiricileri, güçlü adlandırma hakkında şikayet ne bunlar genellikle hakkında şikayetçi katı derleme yükleme olur. Neyse ki, bu sorun, .NET Framework yalıtılır. .NET core, Xamarin, UWP ve diğer .NET uygulamalarının çoğu katı derleme yükleme yoktur ve tanımlayıcı adlandırmanın temel dezavantajı kaldırır.

Tanımlayıcı adlandırma önemli yönlerinden biri olan viral: güçlü derleme can yalnızca başvuru diğer güçlü adlı derlemeler adlı. Kitaplığınızı adlı sağlam değilse bir uygulama ya da tanımlayıcı adlandırma kullanmasını gerektiren bir kitaplık oluşturuyorsanız geliştiriciler dışarıda.

Tanımlayıcı adlandırma avantajları şunlardır:

1. Derleme, başvurulan ve diğer tanımlayıcı adlı derlemeler tarafından kullanılır.
2. Derleme Genel Derleme Önbelleği'ne (GAC) depolanabilir.
3. Derleme, derlemenin diğer sürümlerle yan yana yüklü olabilir. Yan yana derleme yükleme, eklenti mimariler ile uygulamalar tarafından yaygın olarak gereklidir.

## <a name="create-strong-named-net-libraries"></a>.NET kitaplıkları adlı güçlü oluşturma

Ayrıca, açık kaynak .NET kitaplıkları strong adlandırmalısınız. Tanımlayıcı ad derleme oluşturma, çoğu kişi kullanın ve .NET Framework katı derleme yalnızca yükleme etkiler sağlar.

> [!NOTE]
> Nuget.org adresinden .NET kitaplıkları yayımlanan gibi bu genel olarak dağıtılmış .NET kitaplıkları için belirli bir kılavuzdur. Tanımlayıcı adlandırma çoğu .NET uygulamaları tarafından gerekli değildir ve varsayılan olarak gerçekleştirilmemelidir.

**✔️ DÜŞÜNÜN** güçlü kitaplığınızın derlemelerini adlandırma.

**✔️ DÜŞÜNÜN** kaynak denetim sisteminize güçlü adlandırma anahtar ekleme.

> Genel kullanıma açık bir anahtar geliştiricilerin değiştirmek ve aynı anahtara sahip kitaplık kaynak kodunuzu yeniden derleyin sağlar.
> 
> Güçlü adlandırma anahtar geçmişte, özel izinleri verme kullanıldıysa, genel yap olmamalıdır [kısmi güven senaryoları](/dotnet/framework/misc/using-libraries-from-partially-trusted-code). Aksi takdirde, mevcut ortamlar tehlikeye atabilir.

> [!IMPORTANT]
> Kod bir yayımcının kimliğini istendiğinde [Authenticode](/windows-hardware/drivers/install/authenticode) ve [NuGet paket imzalama](/nuget/create-packages/sign-a-package) önerilir. Kod erişim güvenliği (CAS) bir güvenlik riskini azaltma kullanılmamalıdır.

**✔️ DÜŞÜNÜN** derleme sürümü yalnızca ana sürüm değişikliklerini bağlama yeniden yönlendirmeleri ve ne sıklıkta güncelleştirilmiş kullanıcılara yardımcı olmak için artırma.

> Daha fazla bilgi edinin [sürüm oluşturma ve derleme sürümüne](./versioning.md#assembly-version).

**❌ SAĞLAMADIĞI** eklemek, kaldırmak veya tanımlayıcı adlandırma anahtarını değiştirin.

> Bir derlemenin tanımlayıcı adlandırma anahtarını değiştirerek, derlemenin kimliğini değiştirir ve kullandığı derlenmiş kodları keser. Daha fazla bilgi için [ikili bozucu değişiklikler](./breaking-changes.md#binary-breaking-change).

**❌ SAĞLAMADIĞI** kitaplığınızın tanımlayıcı adlı ve olmayan-tanımlayıcı adlı sürümler yayımlayabilir. Örneğin, `Contoso.Api` ve `Contoso.Api.StrongNamed`.

> İki paketleri çatalları Geliştirici ekonomik sistem yayımlanıyor. Ayrıca, uygulamaya bağlı olarak iki paketi de sona erecek, geliştirici türü adı çakışmaları olarak sınırlamasıyla. .NET ilgili olduğu kadar farklı derlemelerde farklı türlerini değildirler.

>[!div class="step-by-step"]
[Önceki](./cross-platform-targeting.md)
[İleri](./nuget.md)
