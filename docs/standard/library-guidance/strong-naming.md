---
title: Güçlü adlandırma ve .NET kitaplıkları
description: Güçlü adlandırma .NET kitaplıkları için en iyi yöntem önerileri.
ms.date: 10/16/2018
ms.openlocfilehash: b72d4a8c320ac857fbcd6abe44f467805f72b5b3
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654566"
---
# <a name="strong-naming"></a>Kesin adlandırma

Tanımlayıcı adlandırma, [tanımlayıcı adlı bir derleme](../assembly/strong-named.md)üreten bir derlemeyi anahtarla imzalamayı ifade eder. Bir derleme tanımlayıcı olarak adlandırılmışsa, ad ve derleme sürüm numarasına göre benzersiz bir kimlik oluşturur ve derleme çakışmalarını önlemeye yardımcı olabilir.

Güçlü adlandırma için downsıde, derleme tanımlayıcı olarak adlandırılmış olduktan sonra Windows 'daki .NET Framework derlemelerin sıkı şekilde yüklenmesini sağlar. Tanımlayıcı adlı bütünleştirilmiş kod başvurusu, yüklü derlemenin sürümüyle tam olarak eşleşmelidir ve geliştiricilerin derlemeyi kullanırken [bağlama yeniden yönlendirmelerini yapılandırmasına](../../framework/configure-apps/redirect-assembly-versions.md) zorlanır:

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

.NET geliştiricileri tanımlayıcı adlandırmayla ilgili olarak şikayet edildiğinde, bu durum genellikle ne kadar şikayetçi, katı derleme yüklemesi. Neyse ki, bu sorun .NET Framework yalıtılmıştır. .NET Core, Xamarin, UWP ve diğer birçok .NET uygulaması katı bütünleştirilmiş kod yükleme içermez ve tanımlayıcı adlandırmanın ana alttarafını kaldırır.

Güçlü adlandırmanın önemli bir yönü, bunun viral olması olabilir: tanımlayıcı bir adlandırılmış derleme yalnızca diğer tanımlayıcı adlandırılmış derlemelere başvurabilir. Kitaplığınız tanımlayıcı olarak adlandırılmazsa, bir uygulama veya kitaplığı oluşturan geliştiricilerin onu kullanarak tanımlayıcı adlandırma yapması gerekir.

Tanımlayıcı adlandırmanın avantajları şunlardır:

1. Derlemeye, tanımlayıcı adlı diğer derlemeler tarafından başvurulabilir ve kullanılabilir.
2. Derleme, genel derleme önbelleğinde (GAC) depolanabilir.
3. Derleme diğer derleme sürümleriyle yan yana yüklenebilir. Yan yana derleme yüklemesi, eklenti mimarilerine sahip uygulamalar için yaygın olarak gereklidir.

## <a name="create-strong-named-net-libraries"></a>Tanımlayıcı adlandırılmış .NET kitaplıkları oluşturma

Açık kaynaklı .NET kitaplıklarınızı tanımlayıcı olarak adlandırın. Derlemeyi tanımlayıcı olarak adlandırma, çoğu kişinin bunu kullanmasını sağlar ve katı derleme yükleme yalnızca .NET Framework etkiler.

> [!NOTE]
> Bu kılavuz, NuGet.org üzerinde yayımlanan .NET kitaplıkları gibi genel olarak dağıtılmış .NET kitaplıklarına özgüdür. Güçlü adlandırma .NET uygulamaları için gerekli değildir ve varsayılan olarak yapılmamalıdır.

✔️ kitaplığınızın derlemelerinizi tanımlayıcı olarak adlandırmayı düşünün.

✔️, güçlü adlandırma anahtarını kaynak denetim sisteminize eklemeyi düşünün.

> Genel kullanıma açık bir anahtar, geliştiricilerin kitaplık kaynak kodunuzu aynı anahtarla değiştirmesine ve yeniden derlemenize olanak tanır.
>
> Geçmişte, [kısmi güven senaryolarında](../../framework/misc/using-libraries-from-partially-trusted-code.md)özel izinler vermek için geçmişte kullanılırsa, tanımlayıcı adlandırma anahtarını genel hale kullanmamanız gerekir. Aksi takdirde, mevcut ortamların güvenliğini tehlikeye atabilir.

> [!IMPORTANT]
> Kod yayımcısının kimliği isteniyorsa, [Authenticode](/windows-hardware/drivers/install/authenticode) ve [NuGet paket imzalama](/nuget/create-packages/sign-a-package) önerilir. Kod erişim güvenliği (CAS) güvenlik azaltma olarak kullanılmamalıdır.

✔️, kullanıcıların bağlama yeniden yönlendirmelerini azaltmaları ve güncelleştirilme sıklığı hakkında yardım almak için derleme sürümünü yalnızca önemli sürüm değişikliklerinde ARTıRMAYı düşünün.

> [Sürüm oluşturma ve derleme sürümü](./versioning.md#assembly-version)hakkında daha fazla bilgi edinin.

❌ Tanımlayıcı adlandırma anahtarını eklemeyin, kaldırmayın veya değiştirmeyin.

> Bir derlemenin tanımlayıcı adlandırma anahtarını değiştirmek derlemenin kimliğini değiştirir ve onu kullanan derlenmiş kodu keser. Daha fazla bilgi için bkz. [ikili son değişiklikler](./breaking-changes.md#binary-breaking-change).

❌ Kitaplığınızın güçlü adlandırılmış ve tanımlayıcı olmayan sürümlerini yayımlamayın. Örneğin `Contoso.Api` ve `Contoso.Api.StrongNamed`.

> İki paket yayımlandığında geliştirici ekonomik sisteminize çatalın. Ayrıca, her iki pakete bağlı olarak bir uygulama sonlanıyorsa, geliştirici tür adı çakışmaları ile karşılaşabilir. .NET, farklı derlemelerdeki farklı türlerdir.

>[!div class="step-by-step"]
>[Önceki](cross-platform-targeting.md) 
> [Sonraki](nuget.md)
