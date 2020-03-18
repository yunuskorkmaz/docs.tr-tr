---
title: Başvuru derlemeleri
description: .NET'te yalnızca kitaplığın genel API yüzeyini içeren özel bir derleme türü olan başvuru derlemeleri hakkında bilgi edinin
author: MSDN-WhiteKnight
ms.date: 09/12/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 938942caf81c54a8aa9207dbe87559438ffb252e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79141074"
---
# <a name="reference-assemblies"></a>Başvuru derlemeleri

*Başvuru derlemeleri,* kitaplığın genel API yüzeyini temsil etmek için gereken yalnızca minimum meta veri miktarını içeren özel bir derleme türüdür. Bunlar, yapı araçlarında bir derlemeye atıfta bulunurken önemli olan tüm üyeler için bildirimler içerir, ancak API sözleşmesi üzerinde gözlemlenebilir bir etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar. Buna karşılık, düzenli derlemeler *uygulama derlemeleri*denir.

Başvuru derlemeleri yürütme için yüklenebilir, ancak uygulama derlemeleri ile aynı şekilde derleyici girişi olarak geçirilebilir. Başvuru derlemeleri genellikle belirli bir platformun veya kitaplığın Yazılım Geliştirme Kiti (SDK) ile dağıtılır.

Başvuru derlemesi kullanmak, geliştiricilerin bu sürüm için tam uygulama derlemesine sahip olmadan belirli bir kitaplık sürümünü hedefleyen programlar oluşturmasına olanak tanır. Makinenizde yalnızca bazı kitaplığın yalnızca en son sürümü ne olduğunu varsayalım, ancak bu kitaplığın önceki bir sürümünü hedefleyen bir program oluşturmak istiyorsunuz. Doğrudan uygulama derlemesi karşı derlerseniz, yanlışlıkla önceki sürümde bulunmayan API üyelerini kullanabilirsiniz. Bu hatayı yalnızca programı hedef makinede test ederken bulabilirsiniz. Önceki sürüm için başvuru derlemesi karşı derlerseniz, hemen bir derleme zamanı hatası alırsınız.

Bir başvuru derlemesi, somut uygulama derlemesine karşılık olmayan bir dizi API'yi de temsil edebilir. *Sözleşme derlemesi*adı verilen bu tür başvuru derlemeleri, aynı API kümesini destekleyen birden çok platformu hedeflemek için kullanılabilir. Örneğin, .NET Standard, farklı .NET platformları arasında paylaşılan ortak API kümesini temsil eden sözleşme derlemesi *netstandard.dll'yi*sağlar. Bu API'lerin uygulamaları ,NET Framework veya *System.Private.CoreLib.dll* üzerinde *mscorlib.dll* gibi farklı platformlarda farklı derlemelerde yer almaktadır. .NET Standard'ı hedefleyen bir kitaplık ,NET Standard'ı destekleyen tüm platformlarda çalıştırılabilir.

## <a name="using-reference-assemblies"></a>Referans derlemelerini kullanma

Projenizdeki belirli API'leri kullanmak için derlemelerine başvurular eklemeniz gerekir. Uygulama derlemelerine veya başvuru derlemelerine başvurular ekleyebilirsiniz. Kullanılabilir olduklarında referans derlemeleri kullanmanız önerilir. Bunu yapmak, api tasarımcıları tarafından kullanılmak üzere hedef sürümde yalnızca desteklenen API üyelerini kullandığınızdan emin olur. Başvuru derlemesini kullanmak, uygulama ayrıntılarına bağımlı olmadığınızı garanti eder.

.NET Framework kitaplıkları için referans derlemeleri hedefleme paketleriyle dağıtılır. Bunları tek başına bir yükleyici indirerek veya Visual Studio yükleyicisinde bir bileşen seçerek elde edebilirsiniz. Daha fazla bilgi için [geliştiriciler için .NET Framework'e yükleyin'](../../framework/install/guide-for-developers.md)e bakın. .NET Core ve .NET Standard için referans derlemeleri gerektiğinde (NuGet üzerinden) otomatik olarak indirilir ve başvurulur. .NET Core 3.0 ve üzeri için, çekirdek çerçeve için başvuru derlemeleri [Microsoft.NETCore.App.Ref](https://www.nuget.org/packages/Microsoft.NETCore.App.Ref) paketindedir (3.0'dan önceki sürümler için [yerine Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) paketi kullanılır). Daha fazla bilgi için .NET Core Guide'daki [Paketler, meta paketler ve çerçevelere](../../core/packages.md) bakın.

**Başvuru ekle** iletişim kutusunu kullanarak Visual Studio'daki .NET Framework derlemelerine başvuru eklediğinizde, listeden bir derleme seçersiniz ve Visual Studio projenizde seçilen hedef çerçeve sürümüne karşılık gelen başvuru derlemelerini otomatik olarak bulur. Aynı [durum, Başvuru](/visualstudio/msbuild/common-msbuild-project-items#reference) projesi öğesini kullanarak doğrudan MSBuild projesine başvuru eklemek için de geçerlidir: dosya yolunun tamamını değil, yalnızca montaj adını belirtmeniz gerekir. `-reference` Bu derlemelere komut satırında derleyici seçeneğini (C# ve Visual[Basic'te)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) kullanarak veya <xref:Microsoft.CodeAnalysis.Compilation.AddReferences%2A?displayProperty=nameWithType> Roslyn API'deki yöntemi kullanarak referanslar eklediğinizde, doğru hedef platform sürümü için başvuru derleme dosyalarını el ile belirtmeniz gerekir. [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) .NET Framework referans derleme dosyaları *%ProgramFiles(x86)%\\Referans\\Derlemeler Microsoft\\Framework\\bulunur. NETFramework* dizini. .NET Core için, `PreserveCompilationContext` proje özelliğini ' ye ayarlayarak, hedef platformunuz için başvuru derlemelerini çıktı dizininizin *yayımlama/refs* alt dizinine kopyalamak için `true`yayımlama işlemini zorlayabilirsiniz. Daha sonra bu başvuru derleme dosyalarını derleyiciye geçirebilirsiniz. `DependencyContext` [Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/) paketinden kullanmak yollarını bulmalarına yardımcı olabilir.

Uygulama içermedikleri için, başvuru derlemeleri yürütme için yüklenebilir. Bunu yapmaya çalışmak bir <xref:System.BadImageFormatException?displayProperty=nameWithType>. Bir başvuru derlemesinin içeriğini incelemek istiyorsanız, bunu .NET Framework'deki <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> (yöntemi kullanarak) veya .NET <xref:System.Reflection.MetadataLoadContext> Core'daki yalnızca yansıma bağlamına yükleyebilirsiniz.

## <a name="generating-reference-assemblies"></a>Referans derlemeleri oluşturma

Kitaplıklarınız için başvuru derlemeleri oluşturmak, kitaplık tüketicilerinizin programlarını kitaplığın birçok farklı sürümüne karşı oluşturmaları gerektiğinde yararlı olabilir. Tüm bu sürümler için uygulama derlemeleri dağıtmak, büyük boyutları nedeniyle pratik olmayabilir. Başvuru derlemelerinin boyutu daha küçüktür ve bunları kitaplığınizin SDK'sının bir parçası olarak dağıtmak indirme boyutunu azaltır ve disk alanı kazandırır.

IME'ler ve oluşturma araçları, birden çok sınıf kitaplığından oluşan büyük çözümler olması durumunda yapı sürelerini azaltmak için başvuru derlemelerinden de yararlanabilir. Genellikle, artımlı yapı senaryolarında, bir proje, bağlı olduğu derlemeler de dahil olmak üzere giriş dosyalarından herhangi biri değiştirildiğinde yeniden oluşturulur. Programcı herhangi bir üyenin uygulamasını değiştirdiğinde uygulama derlemesi değişir. Başvuru derlemesi yalnızca genel API'si etkilendiğinde değişir. Bu nedenle, başvuru derlemesini uygulama derlemesi yerine giriş dosyası olarak kullanmak, bazı durumlarda bağımlı projenin oluşturulmasını atlamanızı sağlar.

Başvuru derlemeleri oluşturabilirsiniz:

- Bir MSBuild projesinde, [ `ProduceReferenceAssembly` proje özelliğini](/visualstudio/msbuild/common-msbuild-project-properties)kullanarak.
- Komut satırından program derlerken,[(C#](../../csharp/language-reference/compiler-options/refonly-compiler-option.md) / [Visual Basic](../../visual-basic/reference/command-line-compiler/refonly-compiler-option.md) ) `-refout` veya ([C#](../../csharp/language-reference/compiler-options/refout-compiler-option.md) / Visual[Basic](../../visual-basic/reference/command-line-compiler/refout-compiler-option.md)) derleyici seçeneklerini belirterek. `-refonly`
- Roslyn API'sini kullanırken, `true` <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.IncludePrivateMembers?displayProperty=nameWithType> bir `false` nesneye ayar <xref:Microsoft.CodeAnalysis.Compilation.Emit%2A?displayProperty=nameWithType> ve nesneye ayarlayarak <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.EmitMetadataOnly?displayProperty=nameWithType> yönteme geçer.

NuGet paketleriyle başvuru derlemelerini dağıtmak istiyorsanız, bunları uygulama derlemeleri için kullanılan *lib\\ * alt dizini yerine paket dizininin altındaki *ref\\ * alt dizinine eklemeniz gerekir.

## <a name="reference-assemblies-structure"></a>Referans derlemeyapısı

Başvuru derlemeleri, ilgili kavramın, *yalnızca meta veri derlemelerinin genişletilmesidir.* Yalnızca meta veri derlemelerinin yöntem gövdeleri tek `throw null` bir gövdeyle değiştirilir, ancak anonim türler dışındaki tüm üyeleri içerir. Organları kullanmanın `throw null` nedeni (hiçbir cisimlerin aksine) **PEVerify'in** çalıştırAbilmesi ve geçebildiği (böylece meta verilerin tamlığını doğrulayabilmeniz) dir.

Başvuru derlemeleri meta verileri (özel üyeler) yalnızca meta veri derlemelerinden daha da kaldırır:

- Bir başvuru derlemesi yalnızca API yüzeyinde ihtiyaç duyduğu referansları vardır. Gerçek derleme, belirli uygulamalarla ilgili ek referanslara sahip olabilir. Örneğin, başvuru derlemesi için `class C { private void M() { dynamic d = 1; ... } }` `dynamic`gerekli türlere başvurulmuyor.
- Özel işlev üyeleri (yöntemler, özellikler ve olaylar) kaldırma işleminin derlemeyi gözlemlemediği durumlarda kaldırılır. [InternalsVisibleTo](xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute) öznitelikleri yoksa, dahili işlev üyeleri de kaldırılır.

Başvuru derlemelerinde meta veriler aşağıdaki bilgileri tutmaya devam ediyor:

- Özel ve iç içe çeşitli türler de dahil olmak üzere tüm türler.
- Tüm özellikler, hatta iç sel özellikler.
- Tüm sanal yöntemler.
- Açık arabirim uygulamaları.
- Erişime erişimedenler sanal olduğundan, açıkça uygulanan özellikler ve olaylar.
- Yapıların tüm alanları.

Başvuru derlemeleri, derleme düzeyinde bir [Başvuru Derleme](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) özniteliği içerir. Bu öznitelik kaynakta belirtilebilir; sonra derleyicinin sentezlemesine gerek kalmaz. Bu öznitelik nedeniyle, çalışma süreleri yürütme için başvuru derlemeleri yüklemeyi reddeder (ancak yalnızca yansıma modunda yüklenebilir).

Tam başvuru derleme yapısı ayrıntıları derleyici sürümüne bağlıdır. Yeni sürümler, genel API yüzeyini etkilemediğinin belirlenmesi durumunda daha fazla meta veri hariç almayı seçebilir.

> [!NOTE]
> Bu bölümdeki bilgiler yalnızca C# sürüm 7.1 veya Visual Basic sürüm 15.3'ten başlayarak Roslyn derleyicileri tarafından oluşturulan başvuru derlemeleri için geçerlidir. .NET Framework ve .NET Core kitaplıkları için başvuru derlemelerinin yapısı, başvuru derlemeleri oluşturma kendi mekanizmalarını kullandıklarından, bazı ayrıntılarda farklılık görebilir. Örneğin, `throw null` vücut yerine tamamen boş yöntem organları olabilir. Ancak genel ilke hala geçerlidir: kullanılabilir yöntem uygulamaları yoktur ve yalnızca genel API perspektifinden gözlemlenebilir bir etkisi olan üyeler için meta veriler içerirler.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](index.md)
- [Çerçeve hedeflemegenel bakış](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Nasıl adlandırılır: Başvuru Yöneticisi'ni kullanarak referans ekleme veya kaldırma](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)
