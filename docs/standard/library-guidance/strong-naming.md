---
title: Güçlü adlandırma ve .NET kitaplıkları
description: Güçlü adlandırma .NET kitaplıkları için en iyi uygulama önerileri.
ms.date: 10/16/2018
ms.openlocfilehash: db268093b07a2ece7cdb8329fd789b52da9c5c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744528"
---
# <a name="strong-naming"></a>Kesin adlandırma

Güçlü adlandırma, bir derlemeyi anahtarla imzalamayı ve [güçlü adlandırılmış](../assembly/strong-named.md)bir derleme oluşturmayı ifade eder. Bir derleme güçlü adlandırılmış olduğunda, ad ve derleme sürüm numarasını temel alan benzersiz bir kimlik oluşturur ve derleme çakışmalarını önlemeye yardımcı olabilir.

Güçlü adlandırmanın dezavantajı, Windows'daki .NET Framework'ün, bir derleme güçlü adlandırılmış olduğunda derlemelerin katı yüklenmesine olanak sağlamasıdır. Güçlü adlandırılmış derleme başvurusu, derleme tarafından başvurulan sürümle tam olarak eşleşmeli ve geliştiricileri derlemeyi kullanırken [bağlama yönlendirmelerini yapılandırmaya](../../framework/configure-apps/redirect-assembly-versions.md) zorlar:

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

.NET geliştiricileri güçlü adlandırmahakkında şikayette bulunduklarında, genellikle şikayet ettikleri şey sıkı montaj yüklemesidir. Neyse ki, bu sorun .NET Framework için yalıtılır. .NET Core, Xamarin, UWP ve diğer birçok .NET uygulamaları sıkı montaj yükleme yok ve güçlü adlandırma ana dezavantajı kaldırır.

Güçlü adlandırma önemli bir yönü viral olmasıdır: güçlü bir adlı derleme sadece diğer güçlü adlı derlemeler referans olabilir. Kitaplığınız güçlü adlandırılmış değilse, güçlü adlandırılması gereken bir uygulama veya kitaplık oluşturan geliştiricileri hariç tardınız.

Güçlü adlandırmanın yararları şunlardır:

1. Derleme başvurulabilir ve diğer güçlü adlı derlemeler tarafından kullanılabilir.
2. Derleme, Genel Montaj Önbelleğinde (GAC) depolanabilir.
3. Montaj, derlemenin diğer sürümleriyle yan yana yüklenebilir. Yan yana montaj yüklemegenellikle eklenti mimarileri ile uygulamalar tarafından gereklidir.

## <a name="create-strong-named-net-libraries"></a>Güçlü adlı .NET kitaplıkları oluşturma

Açık kaynak kodlu .NET kitaplıklarınızı güçlü bir şekilde adlandırmalısınız. Bir derlemeyi güçlü adlandırma, çoğu kişinin onu kullanabileceğini ve sıkı derleme yüklemesinin yalnızca .NET Framework'üni etkilemesini sağlar.

> [!NOTE]
> Bu kılavuz, NuGet.org'da yayınlanan .NET kitaplıkları gibi herkese açık olarak dağıtılan .NET kitaplıklarına özgüdür. Güçlü adlandırma çoğu .NET uygulamaları tarafından gerekli değildir ve varsayılan olarak yapılmaması gerekir.

✔️ kitaplığınızın derlemelerine güçlü bir isim vermeyi düşünün.

✔️ kaynak denetim sisteminize güçlü adlandırma anahtarı eklemeyi düşünün.

> Genel kullanıma açık bir anahtar, geliştiricilerin kitaplık kaynak kodunuzu aynı anahtarla değiştirmesine ve yeniden derlemesini sağlar.
>
> Geçmişte [kısmi güven senaryolarında](../../framework/misc/using-libraries-from-partially-trusted-code.md)özel izinler vermek için kullanılmışsa, güçlü adlandırma anahtarını herkese açık hale getirmemeniz gerekir. Aksi takdirde, varolan ortamları tehlikeye atabilirsiniz.

> [!IMPORTANT]
> Kodun yayımcısının kimliği istendiğinde, [Authenticode](/windows-hardware/drivers/install/authenticode) ve [NuGet Paket İmzalama](/nuget/create-packages/sign-a-package) önerilir. Kod Erişim Güvenliği (CAS) güvenlik azaltma olarak kullanılmamalıdır.

✔️ kullanıcıların bağlama yönlendirmelerini ve ne sıklıkta güncelleştirildiklerini azaltmalarına yardımcı olmak için yalnızca ana sürüm değişikliklerinde derleme sürümünü niçin artımlı olarak düşünün.

> [Sürüm ve derleme sürümü](./versioning.md#assembly-version)hakkında daha fazla bilgi edinin.

❌Güçlü adlandırma anahtarını eklemeYIN, kaldırmayın veya değiştirmeyin.

> Bir derlemenin güçlü adlandırma anahtarını değiştirmek, derlemenin kimliğini değiştirir ve onu kullanan derlenmiş kodu kırar. Daha fazla bilgi için [ikili kesme değişikliklerine](./breaking-changes.md#binary-breaking-change)bakın.

❌Kitaplığınızın güçlü adlandırılmış ve güçlü olmayan adlandırılmış sürümlerini yayımlamayın. Örneğin, `Contoso.Api` ve `Contoso.Api.StrongNamed`.

> İki paket yayınlamak geliştirici eko-sisteminizi çatallar. Ayrıca, bir uygulama her iki pakete bağlı olarak biterse geliştirici tür adı çakışmaları karşılaşabilirsiniz. .NET'e göre farklı derlemelerde farklı türlerdedirler.

>[!div class="step-by-step"]
>[Önceki](cross-platform-targeting.md)
>[Sonraki](nuget.md)
