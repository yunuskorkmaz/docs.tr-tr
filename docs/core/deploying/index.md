---
title: Uygulama yayımlama
description: Bir .NET Core uygulamasını yayımlama yolları hakkında bilgi edinin. .NET Core, platforma özgü veya platform lar arası uygulamalar yayınlayabilir. Bir uygulamayı bağımsız veya çalışma süresine bağlı olarak yayımlayabilirsiniz. Her mod, bir kullanıcının uygulamanızı nasıl çalıştırdığını etkiler.
ms.date: 04/01/2020
ms.openlocfilehash: a4e5f9fe048d40c751f582bd49732cb903202db4
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665534"
---
# <a name="net-core-application-publishing-overview"></a>.NET Core uygulama yayıncılığı genel bakış

.NET Core ile oluşturduğunuz uygulamalar iki farklı modda yayınlanabilir ve mod, kullanıcının uygulamanızı nasıl çalıştırdığını etkiler.

Uygulamanızı *bağımsız* olarak yayımlama, .NET Core çalışma zamanı ve kitaplıkları, uygulamanızı ve bağımlılıklarını içeren bir uygulama üretir. Uygulamanın kullanıcıları bunu .NET Core çalışma zamanı yüklü olmayan bir makinede çalıştırabilir.

Uygulamanızı *çalışma süresine bağımlı* (daha önce *çerçeveye bağımlı*olarak bilinir) olarak yayımlama, yalnızca uygulamanızın kendisini ve bağımlılıklarını içeren bir uygulama üretir. Uygulama kullanıcılarının .NET Core çalışma süresini ayrı olarak yüklemeleri gerekir.

Her iki yayımlama modu varsayılan olarak platforma özgü bir yürütülebilir üretir. Runtime bağımlı uygulamalar yürütülebilir olmadan oluşturulabilir ve bu uygulamalar çapraz platformdur.

Çalıştırılabilir bir üretildiğinde, hedef platformu çalışma zamanı tanımlayıcısı (RID) ile belirtebilirsiniz. RID'ler hakkında daha fazla bilgi için [.NET Core RID Kataloğu'na](../rid-catalog.md)bakın.

Aşağıdaki tablo, bir uygulamayı SDK sürümüne göre çalışma süresine bağlı veya bağımsız olarak yayımlamak için kullanılan komutları özetler:

| Tür                                                                                 | SDK 2.1 | SDK 3.x | Komut |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| geçerli platform için [çalıştırılabilir çalıştırılabilir çalıştırılabilir.](#publish-runtime-dependent) |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| belirli bir platform için [çalıştırılabilir çalıştırılabilir çalıştırılabilir.](#publish-runtime-dependent)  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [runtime bağımlı çapraz platform ikili](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [kendi kendine yeten yürütülebilir.](#publish-self-contained)                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

Daha fazla bilgi için [bkz.](../tools/dotnet-publish.md)

## <a name="produce-an-executable"></a>Çalıştırılabilir bir ürün üretin

Yürütülebilir ler çapraz platform değildir. İşletim sistemi ve CPU mimarisine özgüler. Uygulamanızı yayımlarken ve yürütülebilir bir uygulama oluştururken, uygulamayı [bağımsız](#publish-self-contained) veya [çalışma süresine bağlı](#publish-runtime-dependent)olarak yayımlayabilirsiniz. Bir uygulamayı bağımsız olarak yayınlamak, uygulamayla birlikte .NET Core çalışma süresini içerir ve uygulama kullanıcılarının uygulamayı çalıştırmadan önce .NET Core'u yükleme konusunda endişelenmelerine gerek yoktur. Çalışma süresine bağlı olarak yayınlanan uygulamalar .NET Core çalışma süresini ve kitaplıkları içermez; yalnızca uygulama ve üçüncü taraf bağımlılıkları dahildir.

Aşağıdaki komutlar yürütülebilir bir ürün üretir:

| Tür                                                                                 | SDK 2.1 | SDK 3.x | Komut |
| ------------------------------------------------------------------------------------ | ------- | ------- | ------- |
| geçerli platform için [çalıştırılabilir çalıştırılabilir çalıştırılabilir.](#publish-runtime-dependent) |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| belirli bir platform için [çalıştırılabilir çalıştırılabilir çalıştırılabilir.](#publish-runtime-dependent)  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [kendi kendine yeten yürütülebilir.](#publish-self-contained)                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>Çapraz platform ikilisi üretin

Uygulamanızı [çalışma süresine bağlı](#publish-runtime-dependent)olarak bir *dll* dosyası biçiminde yayımladığınızda çapraz platform ikilileri oluşturulur. *DLL* dosyası, projenizden sonra adlandırılmıştır. Örneğin, **word_reader**adında bir uygulamanız varsa, *word_reader.dll* adlı bir dosya oluşturulur. Bu şekilde yayınlanan uygulamalar `dotnet <filename.dll>` komutla çalıştırılır ve herhangi bir platformda çalıştırılabilir.

Hedeflenen .NET Core çalışma süresi zaten yüklenmiş olduğu sürece, platformlar arası ikililer herhangi bir işletim sisteminde çalıştırılabilir. Hedeflenen .NET Core çalışma zamanı yüklü değilse, uygulama roll-forward için yapılandırılırsa uygulama daha yeni bir çalışma süresi kullanarak çalışabilir. Daha fazla bilgi için [çalışma süresine bağlı uygulamaların ileri ye doğru kayda bakınız.](../versions/selection.md#framework-dependent-apps-roll-forward)

Aşağıdaki komut bir çapraz platform ikili üretir:

| Tür                                                                                 | SDK 2.1 | SDK 3.x | Komut |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [runtime bağımlı çapraz platform ikili](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-runtime-dependent"></a>Çalışma süresine bağımlı yayımlama

Çalışma süresine bağlı olarak yayınlanan uygulamalar çapraz platformdur ve .NET Core çalışma süresini içermez. Uygulamanızın kullanıcısının .NET Core çalışma süresini yüklemesi gerekir.

Bir uygulamayı çalışma süresine bağlı olarak yayımlama, *dll* dosyası olarak [bir çapraz platform ikilisi](#produce-a-cross-platform-binary) ve geçerli platformunuzu hedefleyen platforma özgü bir [yürütülebilir](#produce-an-executable) üretir. Yürütülebilir değilken *dll* çapraz platformdur. Örneğin, **word_reader** adlı bir uygulama yayımlar ve Windows'u hedeflerseniz, *word_reader.dll*ile birlikte bir *word_reader.exe* çalıştırılabilir oluşturulur. Linux veya macOS hedeflenirken, *word_reader.dll*ile birlikte bir *word_reader* çalıştırılabilir oluşturulur. RID'ler hakkında daha fazla bilgi için [.NET Core RID Kataloğu'na](../rid-catalog.md)bakın.

> [!IMPORTANT]
> .NET Core SDK 2.1, çalışma süresine bağlı bir uygulama yayımladığınızda platforma özgü yürütülebilir uygulamalar üretmez.

Uygulamanızın çapraz platform ikilisi `dotnet <filename.dll>` komutla çalıştırılabilir ve herhangi bir platformda çalıştırılabilir. Uygulama platforma özel uygulamalara sahip bir NuGet paketi kullanıyorsa, tüm platformların bağımlılıkları uygulamayla birlikte yayımlama klasörüne kopyalanır.

`-r <RID> --self-contained false` Parametreleri [`dotnet publish`](../tools/dotnet-publish.md) komuta geçirerek belirli bir platform için yürütülebilir oluşturabilirsiniz. `-r` Parametre atlandığında, geçerli platformunuz için bir çalıştırılabilir oluşturulur. Hedeflenen platform için platforma özgü bağımlılıkları olan Tüm NuGet paketleri yayımlama klasörüne kopyalanır.

### <a name="advantages"></a>Yararları

- **Küçük dağıtım**\
Yalnızca uygulamanız ve bağımlılıkları dağıtılır. .NET Core çalışma zamanı ve kitaplıklar kullanıcı tarafından yüklenir ve tüm uygulamalar çalışma süresini paylaşır.

- **Çapraz platform**\
Uygulamanız ve herhangi bir . NET tabanlı kitaplık diğer işletim sistemlerinde çalışır. Uygulamanız için bir hedef platform tanımlamanız gerekmez. .NET dosya biçimi hakkında bilgi için [bkz.](../../standard/assembly/file-format.md)

- **En son yamalı çalışma süresini kullanır**\
Uygulama, hedef sistemde yüklü en son çalışma süresini (hedeflenen büyük-küçük .CORE ailesi içinde) kullanır. Bu, uygulamanızın .NET Core çalışma zamanının en son yamalı sürümünü otomatik olarak kullandığı anlamına gelir. Bu varsayılan davranış geçersiz kılınabilir. Daha fazla bilgi için [çalışma süresine bağlı uygulamaların ileri ye doğru kayda bakınız.](../versions/selection.md#framework-dependent-apps-roll-forward)

### <a name="disadvantages"></a>Dezavantajlar

- **Çalışma süresini önceden yüklemeyi gerektirir**\
Uygulamanız yalnızca .NET Core sürümü uygulama hedefleriniz ana bilgisayar sistemine zaten yüklenmişse çalıştırılabilir. Uygulama için yuvarlanme davranışını ,NET Core'un belirli bir sürümünü gerektirecek veya .NET Core'un daha yeni bir sürümüne izin verecek şekilde yapılandırabilirsiniz. Daha fazla bilgi için [çalışma süresine bağlı uygulamaların ileri ye doğru kayda bakınız.](../versions/selection.md#framework-dependent-apps-roll-forward)

- **.NET Core değişebilir**\
.NET Core çalışma zamanı ve kitaplıkların uygulamanın çalıştırıldığı makinede güncellenmesi mümkündür. Nadir durumlarda, çoğu uygulamanın kullandığı .NET Core kitaplıklarını kullanırsanız, bu uygulamanızın davranışını değiştirebilir. Uygulamanızın .NET Core'un daha yeni sürümlerini nasıl kullandığını yapılandırabilirsiniz. Daha fazla bilgi için [çalışma süresine bağlı uygulamaların ileri ye doğru kayda bakınız.](../versions/selection.md#framework-dependent-apps-roll-forward)

Aşağıdaki dezavantaj yalnızca .NET Core 2.1 SDK için geçerlidir.

- **Uygulamayı `dotnet` başlatmak için komutu kullanın**\
Kullanıcıların uygulamanızı `dotnet <filename.dll>` başlatmak için komutu çalıştırması gerekir. .NET Core 2.1 SDK, çalışma süresine bağlı olarak yayınlanan uygulamalar için platforma özgü yürütülebilir uygulamalar üretmez.

### <a name="examples"></a>Örnekler

Bir uygulama çapraz platform çalışma süresine bağlı yayımlayın. Geçerli platformunuzu hedefleyen bir yürütülebilir *dll* dosyasıyla birlikte oluşturulur.

```dotnet
dotnet publish
```

Bir uygulama çapraz platform çalışma süresine bağlı yayımlayın. Linux 64 bit çalıştırılabilir *dll* dosyası ile birlikte oluşturulur. Bu komut .NET Core SDK 2.1 ile çalışmaz.

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>Bağımsız yayımlama

Uygulamanızı bağımsız olarak yayımlama, platforma özgü bir yürütülebilir lik üretir. Çıktı yayımlama klasörü, .NET Core kitaplıkları ve hedef çalışma süresi de dahil olmak üzere uygulamanın tüm bileşenlerini içerir. Uygulama diğer .NET Core uygulamalarından izole edilmiştir ve yerel olarak yüklenen paylaşılan çalışma süresini kullanmaz. Uygulamanızın kullanıcısının .NET Core'u indirmesi ve yüklemesi gerekmez.

Çalıştırılabilir ikili belirtilen hedef platform için üretilir. Örneğin, **word_reader**adında bir uygulamanız varsa ve Windows için bağımsız bir yürütülebilir yayımladıysanız, *word_reader.exe* dosyası oluşturulur. Linux veya macOS için yayımlama, *bir word_reader* dosyası oluşturulur. Hedef platform ve mimari `-r <RID>` [`dotnet publish`](../tools/dotnet-publish.md) komut için parametre ile belirtilir. RID'ler hakkında daha fazla bilgi için [.NET Core RID Kataloğu'na](../rid-catalog.md)bakın.

Uygulamanın platforma özgü bağımlılıkları içeren NuGet paketi gibi platforma özgü bağımlılıkları varsa, bunlar uygulamayla birlikte yayımlama klasörüne kopyalanır.

### <a name="advantages"></a>Yararları

- **Control .NET Core sürümü**\
Uygulamanızla birlikte .NET Core'un hangi sürümünün dağıtılan olduğunu siz denetlersiniz.

- **Platforma özel hedefleme**\
Uygulamanızı her platform için yayımlamanız gerektiğinden, uygulamanızın nerede yayınlayacağını bilirsiniz. .NET Core yeni bir platform sunarsa, siz bu platformu hedefleyen bir sürüm yayımlayana kadar kullanıcılar uygulamanızı bu platformda çalıştıramaz. Kullanıcılarınız uygulamanızı yeni platformda çalıştırmadan önce uygulamanızı uyumluluk sorunları için test edebilirsiniz.

### <a name="disadvantages"></a>Dezavantajlar

- **Daha büyük dağıtımlar**\
Uygulamanız .NET Core çalışma süresini ve tüm uygulama bağımlılıklarınızı içerdiğinden, gereken indirme boyutu ve sabit disk alanı [çalışma süresine bağlı](#publish-runtime-dependent) bir sürümden daha büyüktür.

  > [!TIP]
  > .NET Core [*globalization değişmez modunu*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)kullanarak Linux sistemlerindeki dağıtımınızın boyutunu yaklaşık 28 MB azaltabilirsiniz. Bu, uygulamanızı tüm kültürlere [değişmez kültür](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)gibi davranmaya zorlar.

- **.NET Core sürümünü güncelleştirmek daha zor**\
.NET Core Runtime (uygulamanızla birlikte dağıtılır) yalnızca uygulamanızın yeni bir sürümünü yayınlayarak yükseltilebilir. .NET Core Runtime'a güvenlik yamaları için uygulamanızın güncelleştirilmiş bir sürümünü sağlamaktan siz sorumlusunuz.

### <a name="examples"></a>Örnekler

Kendi kendine yeten bir uygulama yayımlayın. MacOS 64 bit çalıştırılabilir bir oluşturulur.

```dotnet
dotnet publish -r osx-x64
```

Kendi kendine yeten bir uygulama yayımlayın. Windows 64 bit çalıştırılabilir oluşturulur.

```dotnet
dotnet publish -r win-x64
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core CLI ile .NET Çekirdek Uygulamalarını dağıtma.](deploy-with-cli.md)
- [.NET Core Apps'ı Visual Studio ile dağıtma.](deploy-with-vs.md)
- [Paketler, Metapaketler ve Çerçeveler.](../packages.md)
- [.NET Core Runtime Tanımlayıcı (RID) kataloğu.](../rid-catalog.md)
- [Kullanmak için .NET Core sürümünü seçin.](../versions/selection.md)
