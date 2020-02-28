---
title: Başvuru derlemeleri
description: .NET 'teki yalnızca kitaplığın ortak API yüzeyini içeren özel bir derleme türü olan başvuru derlemeleri hakkında bilgi edinin
author: MSDN-WhiteKnight
ms.date: 09/12/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 3b85e51a015cca1e53ee2503c7bfa58c504fc718
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156471"
---
# <a name="reference-assemblies"></a>Başvuru derlemeleri

*Başvuru derlemeleri* , KITAPLıĞıN ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür. Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar. Buna karşılık, normal derlemeler *uygulama derlemeleri*olarak adlandırılır.

Başvuru derlemeleri yürütme için yüklenemez, ancak uygulama Derlemeleriyle aynı şekilde derleyici girişi olarak geçirilebilir. Başvuru derlemeleri genellikle belirli bir platformun veya kitaplığın yazılım geliştirme seti (SDK) ile dağıtılır.

Başvuru derlemesi kullanmak, geliştiricilerin bu sürümü için tam uygulama derlemesine sahip olmadan belirli bir kitaplık sürümünü hedefleyen programlar oluşturmalarına olanak sağlar. Makinenizde yalnızca bir kitaplığın en son sürümüne sahip olduğunuzu, ancak söz konusu kitaplığın önceki bir sürümünü hedefleyen bir program oluşturmak istediğinizi varsayalım. Doğrudan uygulama derlemesine göre derlerseniz, eski sürümde kullanılamayan API üyelerini yanlışlıkla kullanabilirsiniz. Bu hata yalnızca programı hedef makinede sınarken bulursunuz. Önceki sürüm için başvuru derlemesine karşı derlerseniz, hemen bir derleme zamanı hatası alırsınız.

Bir başvuru bütünleştirilmiş kodu ayrıca bir sözleşmeyi, yani somut uygulama derlemesine karşılık gelen bir API kümesini temsil edebilir. *Anlaşma derlemesi*olarak adlandırılan bu tür başvuru derlemeleri, aynı API kümesini destekleyen birden çok platformu hedeflemek için kullanılabilir. Örneğin, .NET Standard, farklı .NET platformları arasında paylaşılan ortak API 'lerin kümesini temsil eden *Netstandard. dll*sözleşme derlemesini sağlar. Bu API 'lerin uygulamaları, .NET Core 'da .NET Framework veya *System. Private. CoreLib. dll* ' deki *mscorlib. dll* gibi farklı platformlarda farklı derlemelerde bulunur. .NET Standard hedefleyen bir kitaplık, .NET Standard destekleyen tüm platformlarda çalıştırılabilir.

## <a name="using-reference-assemblies"></a>Başvuru derlemelerini kullanma

Projenizdeki belirli API 'Leri kullanmak için, derlemelerine başvuruları eklemeniz gerekir. Başvuruları, uygulama derlemelerine veya başvuru derlemelerine ekleyebilirsiniz. Kullanılabilir olduğunda başvuru derlemelerini kullanmanız önerilir. Bunun yapılması, API tasarımcıları tarafından kullanılması amaçlanan hedef sürümde yalnızca desteklenen API üyelerini kullanmanızı sağlar. Başvuru derlemesini kullanmak, uygulama ayrıntılarına bir bağımlılık götürmenizi sağlar.

.NET Framework kitaplıkları için başvuru bütünleştirilmiş kodları hedefleme paketleriyle dağıtılır. Bunları tek başına yükleyiciyi indirerek veya Visual Studio yükleyicisi 'nde bir bileşeni seçerek edinebilirsiniz. Daha fazla bilgi için bkz. [geliştiriciler için .NET Framework 'ı yüklemeyin](../../framework/install/guide-for-developers.md). .NET Core ve .NET Standard için, başvuru derlemeleri gerektiği şekilde otomatik olarak indirilir (NuGet aracılığıyla) ve başvurulur. .NET Core 3,0 ve üzeri için, çekirdek çerçeve için başvuru derlemeleri [Microsoft. netcore. app. ref](https://www.nuget.org/packages/Microsoft.NETCore.App.Ref) paketidir (3,0 ' den önceki sürümler için bunun yerine [Microsoft. netcore. app](https://www.nuget.org/packages/Microsoft.NETCore.App) Package kullanılır). Daha fazla bilgi için .NET Core kılavuzundaki [paketler, Metapackages ve çerçeveler](../../core/packages.md) bölümüne bakın.

**Başvuru Ekle** iletişim kutusunu kullanarak Visual studio 'da .NET Framework derlemelerine başvurular eklediğinizde, listeden bir derleme seçersiniz ve Visual Studio otomatik olarak projenizde seçilen hedef Framework sürümüne karşılık gelen başvuru derlemelerini bulur. Aynı, [başvuru](/visualstudio/msbuild/common-msbuild-project-items#reference) Proje öğesini kullanarak doğrudan MSBuild projesine başvuru eklemek için geçerlidir: tam dosya yolunu değil yalnızca derleme adını belirtmeniz gerekir. Komut satırında, `-reference` derleyici seçeneğini[kullanarak ( C# ve](../../csharp/language-reference/compiler-options/reference-compiler-option.md) [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md)) veya Roslyn API 'sindeki <xref:Microsoft.CodeAnalysis.Compilation.AddReferences%2A?displayProperty=nameWithType> yöntemini kullanarak bu derlemelere başvuru eklediğinizde, doğru hedef platform sürümü için el ile başvuru derleme dosyalarını belirtmeniz gerekir. .NET Framework başvuru derleme dosyaları, *Microsoft\\Framework\\\\% ProgramFiles (x86)%\\başvuru Derlemeleriyle bulunur. NETFramework* dizini. .NET Core için, `PreserveCompilationContext` projesi özelliğini `true`olarak ayarlayarak, hedef platformunuzun başvuru derlemelerini çıkış dizininizin *Yayımla/refs* alt dizinine kopyalamak için yayımlama işlemini zorlayabilirsiniz. Daha sonra, bu başvuru derleme dosyalarını derleyiciye geçirebilirsiniz. [Microsoft. Extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/) paketinden `DependencyContext` kullanmak, yollarının bulunmasına yardımcı olabilir.

Uygulama içermediği için başvuru derlemeleri yürütme için yüklenemez; Bunun için bir <xref:System.BadImageFormatException?displayProperty=nameWithType>sonuçlanır. Ancak, içeriklerini incelemeniz gerekiyorsa yalnızca yansıma bağlamına (<xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> yöntemi kullanılarak) yüklenebilirler.

## <a name="generating-reference-assemblies"></a>Başvuru derlemeleri oluşturma

Kitaplıklarınız için başvuru derlemeleri oluşturmak, kitaplık tüketicilerinizin, kitaplığın birçok farklı sürümüne karşı programlarını oluşturması gerektiğinde yararlı olabilir. Tüm bu sürümler için uygulama derlemelerinin dağıtılması, büyük boyutları nedeniyle pratik olabilir. Başvuru derlemelerinin boyutu küçüktür ve bunları kitaplığınızın SDK 'sının bir parçası olarak dağıtmak, indirme boyutunu azaltır ve disk alanını kaydeder.

Ides ve derleme araçları aynı zamanda birden fazla sınıf kütüphanelerinin bulunduğu büyük çözümler söz konusu olduğunda derleme sürelerini azaltmak için başvuru derlemelerinden faydalanabilir. Genellikle, Artımlı derleme senaryolarında, bağımlı olduğu derlemeler dahil olmak üzere herhangi bir giriş dosyası değiştirildiğinde bir proje yeniden oluşturulur. Uygulama derlemesi, programcı her üyenin uygulamasını değiştirdiğinde değişir. Başvuru derlemesi yalnızca ortak API 'SI etkileniyorsa değişir. Bu nedenle, başvuru derlemesini uygulama derlemesi yerine bir giriş dosyası olarak kullanmak bazı durumlarda bağımlı projenin derlemesini atlamaya izin verir.

Başvuru derlemeleri oluşturabilirsiniz:

- MSBuild projesinde, [`ProduceReferenceAssembly` projesi özelliğini](/visualstudio/msbuild/common-msbuild-project-properties)kullanarak.
- Program komut satırından derlenirken, `-refonly`[C#](../../csharp/language-reference/compiler-options/refonly-compiler-option.md) ( / [Visual Basic](../../visual-basic/reference/command-line-compiler/refonly-compiler-option.md) ) veya `-refout` ([C#](../../csharp/language-reference/compiler-options/refout-compiler-option.md) / [Visual Basic](../../visual-basic/reference/command-line-compiler/refout-compiler-option.md)) derleyici seçeneklerini belirterek.
- Roslyn API kullanırken, <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.EmitMetadataOnly?displayProperty=nameWithType> `true` ve <xref:Microsoft.CodeAnalysis.Compilation.Emit%2A?displayProperty=nameWithType> yöntemine geçirilen bir nesnedeki `false` <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.IncludePrivateMembers?displayProperty=nameWithType> ayarlayarak.

Başvuru derlemelerini NuGet paketleriyle dağıtmak istiyorsanız, bunları uygulama derlemeleri için kullanılan *lib\\* alt dizininde değil, paket dizini altındaki *ref\\* alt dizinine dahil etmeniz gerekir.

## <a name="reference-assemblies-structure"></a>Başvuru derlemeleri yapısı

Başvuru derlemeleri, *yalnızca meta veri derlemelerinin*ilgili kavramın bir genişletmesinden oluşur. Yalnızca meta veri bütünleştirilmiş kodlarının yöntem gövdeleri tek bir `throw null` gövdesiyle değiştirilmiştir, ancak anonim türler hariç tüm üyeleri içerir. `throw null` gövdeleri kullanmanın nedeni (gövdeden farklı olarak), **PEVerify** 'ın çalıştırılabilmesi ve geçebilmesi (Bu nedenle meta verilerin tamamlanmasının doğrulanması).

Başvuru derlemeleri meta verileri (özel Üyeler) yalnızca meta veri derlemelerinden daha da kaldırır:

- Bir başvuru derlemesinin yalnızca API yüzeyinde ihtiyacı olan başvurular vardır. Gerçek derlemenin belirli uygulamalarla ilgili ek başvuruları olabilir. Örneğin, `class C { private void M() { dynamic d = 1; ... } }` için başvuru derlemesi `dynamic`için gereken herhangi bir türe başvurmuyor.
- Özel işlev-Üyeler (Yöntemler, Özellikler ve olaylar) kaldırma işleminin derleme observably etkisi olmadığı durumlarda kaldırılır. [InternalsVisibleTo](xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute) özniteliği yoksa, iç işlev üyeleri de kaldırılır.

Başvuru derlemelerindeki meta veriler aşağıdaki bilgileri tutmaya devam eder:

- Özel ve iç içe türler dahil olmak üzere tüm türler.
- Tüm öznitelikler, hatta iç yorumlar.
- Tüm sanal yöntemler.
- Açık arabirim uygulamaları.
- Erişimcileri sanal olduğundan, açıkça uygulanan özellikler ve olaylar.
- Tüm yapıların alanları.

Başvuru derlemeleri derleme düzeyi [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) özniteliği içerir. Bu öznitelik, kaynakta belirtilebilir; daha sonra derleyicinin bu uygulamayı birleştirmesini gerektirmez. Bu öznitelik nedeniyle, çalışma zamanları yürütme için başvuru derlemelerini yüklemeyi reddeder (ancak bunlar yalnızca yansıma modunda yüklenebilirler).

Tam başvuru derleme yapısı ayrıntıları derleyici sürümüne bağlıdır. Daha yeni sürümler, ortak API yüzeyini etkilemediğinden, daha fazla meta veri dışlamayı tercih edebilir.

> [!NOTE]
> Bu bölümdeki bilgiler, sürüm 7,1 ' den başlayarak Roslyn derleyicileri tarafından oluşturulan başvuru Derlemeleriyle veya Visual Basic sürüm 15,3 ' den C# itibaren geçerlidir. .NET Framework ve .NET Core kitaplıkları için başvuru derlemelerinin yapısı, bazı ayrıntılarda farklılık gösterebilir, çünkü kendi başvuru derlemeleri oluşturma mekanizmalarını kullanırlar. Örneğin, `throw null` gövdesi yerine tamamen boş Yöntem gövdelerinin olması gerekebilir. Ancak genel ilke hala geçerlidir: kullanılabilir yöntem uygulamalarına sahip değildir ve yalnızca ortak API perspektifinden bir observable etkisi olan üyeler için meta veriler içerir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](index.md)
- [Çerçeve hedefleme genel bakış](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Nasıl yapılır: başvuru Yöneticisi 'ni kullanarak başvuru ekleme veya kaldırma](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)
