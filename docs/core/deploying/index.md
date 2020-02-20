---
title: Uygulama yayımlama
description: .NET Core uygulaması yayımlama yolları hakkında bilgi edinin. .NET Core, platforma özgü veya platformlar arası uygulamalar yayımlayabilir. Bir uygulamayı kendi içinde veya çalışma zamanına bağlı olarak yayımlayabilirsiniz. Her mod, bir kullanıcının uygulamanızı nasıl yürüttüğünde etkiler.
ms.date: 01/31/2020
ms.openlocfilehash: 696cca436c73601a3e7825033152d43a659a7dce
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448990"
---
# <a name="net-core-application-publishing-overview"></a>.NET Core uygulama yayımlamaya genel bakış

.NET Core ile oluşturduğunuz uygulamalar iki farklı modda yayımlanabilir ve bu mod, bir kullanıcının uygulamanızı nasıl yürüttüğünde de etkili olur.

Uygulamanızı *kendi içinde* yayımlamak, .NET Core çalışma zamanı ve kitaplıklarını ve uygulamanızı ve onun bağımlılıklarını içeren bir uygulama oluşturur. Uygulamanın kullanıcıları bu uygulamayı .NET Core çalışma zamanı yüklü olmayan bir makinede çalıştırabilir. 

Uygulamanızı *çalışma zamanına bağlı* olarak yayımlamak, yalnızca uygulamanızın kendisini ve bağımlılıklarını içeren bir uygulama oluşturur. Uygulamanın kullanıcılarının .NET Core çalışma zamanını ayrı olarak yüklemesi gerekir.

Her iki yayımlama modu, varsayılan olarak platforma özgü bir yürütülebilir dosya oluşturur. Çalışma zamanına bağımlı uygulamalar yürütülebilir bir dosya olmadan oluşturulabilir ve bu uygulamalar platformlar arası bir platformdur.

Bir yürütülebilir dosya üretildiğinde, hedef platformu bir çalışma zamanı tanımlayıcısı (RID) ile belirtebilirsiniz. RID 'Ler hakkında daha fazla bilgi için bkz. [.NET Core RID kataloğu](../rid-catalog.md).

Aşağıdaki tabloda, SDK sürümü başına, bir uygulamayı çalışma zamanına bağımlı veya şirket içinde yayımlamak için kullanılan komutlar özetlenmektedir:

| Tür                                                                                 | SDK 2,1 | SDK 3. x | Komut |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| geçerli platform için [çalışma zamanına bağımlı yürütülebilir](#publish-runtime-dependent) . |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| belirli bir platform için [çalışma zamanına bağımlı yürütülebilir](#publish-runtime-dependent) .  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [çalışma zamanına bağımlı platformlar arası ikili](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [kendi kendine içerilen çalıştırılabilir](#publish-self-contained).                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

Daha fazla bilgi için bkz. [.NET Core DotNet Publish komutu](../tools/dotnet-publish.md).

## <a name="produce-an-executable"></a>Yürütülebilir bir dosya oluşturun

Yürütülebilir dosyalar platformlar arası değildir. Bunlar bir işletim sistemine ve CPU mimarisine özgüdür. Uygulamanızı yayımlarken ve yürütülebilir bir dosya oluştururken, uygulamayı [kendi içinde](#publish-self-contained) veya [çalışma zamanına bağlı](#publish-runtime-dependent)olarak yayımlayabilirsiniz. Bir uygulamayı kendi içinde yayımlamak uygulamayla birlikte .NET Core çalışma zamanı içerir ve uygulamanın kullanıcıları uygulamayı çalıştırmadan önce .NET Core 'u yükleme konusunda endişelenmenize gerek kalmaz. Çalışma zamanına bağlı olarak yayımlanan uygulamalar .NET Core çalışma zamanı ve kitaplıklarını içermez; yalnızca uygulama ve üçüncü taraf bağımlılıklar dahil edilir.

Aşağıdaki komutlar yürütülebilir bir dosya üretir:

| Tür                                                                                 | SDK 2,1 | SDK 3. x | Komut |
| ------------------------------------------------------------------------------------ | ------- | ------- | ------- |
| geçerli platform için [çalışma zamanına bağımlı yürütülebilir](#publish-runtime-dependent) . |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| belirli bir platform için [çalışma zamanına bağımlı yürütülebilir](#publish-runtime-dependent) .  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [kendi kendine içerilen çalıştırılabilir](#publish-self-contained).                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>Platformlar arası ikili oluşturun

Uygulamanızı [çalışma zamanına bağlı](#publish-runtime-dependent)olarak bir *DLL* dosyası biçiminde yayımladığınızda platformlar arası ikili dosyalar oluşturulur. *DLL* dosyası projenizden sonra adlandırılır. Örneğin, **word_reader**adlı bir uygulamanız varsa, *word_reader. dll* adlı bir dosya oluşturulur. Bu şekilde yayımlanan uygulamalar `dotnet <filename.dll>` komutuyla çalışır ve herhangi bir platformda çalıştırılabilir.

Platformlar arası ikili dosyalar, hedeflenen .NET Core çalışma zamanı zaten yüklü olduğu sürece herhangi bir işletim sisteminde çalıştırılabilir. Hedeflenen .NET Core çalışma zamanı yüklü değilse, uygulama geri almak üzere yapılandırılmışsa uygulama daha yeni bir çalışma zamanı kullanılarak çalıştırılabilir. Daha fazla bilgi için bkz. [çalışma zamanına bağımlı uygulamalar ileri alma](../versions/selection.md#framework-dependent-apps-roll-forward).

Aşağıdaki komut platformlar arası ikili dosya üretir:

| Tür                                                                                 | SDK 2,1 | SDK 3. x | Komut |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [çalışma zamanına bağımlı platformlar arası ikili](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-runtime-dependent"></a>Yayımlama çalışma zamanına bağımlı

Çalışma zamanına bağlı olarak yayımlanan uygulamalar platformlar arası ve .NET Core çalışma zamanı dahil değildir. Uygulamanızın kullanıcısı .NET Core çalışma zamanı 'nı yüklemek için gereklidir.

Bir uygulamayı çalışma zamanına bağlı olarak yayımlamak, *DLL* dosyası olarak [platformlar arası bir ikili](#produce-a-cross-platform-binary) dosya ve geçerli platformunuzu hedefleyen [platforma özgü bir yürütülebilir](#produce-an-executable) dosya oluşturur. Yürütülebilir dosya olmadığından, *DLL* platformlar arası bir platformdur. Örneğin, **word_reader** ve hedef pencereleri adlı bir uygulama yayımlarsanız, *word_reader. dll*ile birlikte bir *word_reader. exe* yürütülebilir dosyası oluşturulur. Linux veya macOS hedeflenirken, *word_reader. dll*ile birlikte *word_reader* çalıştırılabilir dosyası oluşturulur. RID 'Ler hakkında daha fazla bilgi için bkz. [.NET Core RID kataloğu](../rid-catalog.md).

> [!IMPORTANT]
> .NET Core SDK 2,1, bir uygulama çalışma zamanına bağımlı olduğunda platforma özgü yürütülebilir dosyalar oluşturmaz.

Uygulamanızın platformlar arası ikili dosyası `dotnet <filename.dll>` komutuyla çalıştırılabilir ve herhangi bir platformda çalıştırılabilir. Uygulama platforma özgü uygulamalar içeren bir NuGet paketi kullanıyorsa, tüm platformların bağımlılıkları uygulamayla birlikte yayımlama klasörüne kopyalanır.

`-r <RID> --self-contained false` parametrelerini [`dotnet publish`](../tools/dotnet-publish.md) komutuna geçirerek, belirli bir platform için yürütülebilir dosya oluşturabilirsiniz. `-r` parametresi atlandığında, geçerli platformunuz için yürütülebilir bir dosya oluşturulur. Hedeflenen platform için platforma özgü bağımlılıklara sahip tüm NuGet paketleri Yayımla klasörüne kopyalanır.

### <a name="advantages"></a>Yararları

- **Küçük dağıtım**\
Yalnızca uygulamanız ve bağımlılıkları dağıtılır. .NET Core çalışma zamanı ve kitaplıkları Kullanıcı tarafından yüklenir ve tüm uygulamalar çalışma zamanını paylaşır.

- **Platformlar arası**\
Uygulamanız ve herhangi bir. AĞ tabanlı kitaplık diğer işletim sistemlerinde çalışır. Uygulamanız için bir hedef platform tanımlamanız gerekmez. .NET dosya biçimi hakkında daha fazla bilgi için bkz. [.NET derleme dosyası biçimi](../../standard/assembly/file-format.md).

- **En son düzeltme eki uygulanmış çalışma zamanını kullanır**\
Uygulama, hedef sistemde yüklü olan en son çalışma zamanını (.NET Core 'un hedeflenen ana alt ailesi içinde) kullanır. Bu, uygulamanızın .NET Core çalışma zamanının en son düzeltme eki uygulanmış sürümünü otomatik olarak kullandığı anlamına gelir. Bu varsayılan davranış geçersiz kılınabilir. Daha fazla bilgi için bkz. [çalışma zamanına bağımlı uygulamalar ileri alma](../versions/selection.md#framework-dependent-apps-roll-forward).

### <a name="disadvantages"></a>Dezavantajlar

- **Çalışma zamanının önceden yüklenmesini gerektirir**\
Uygulamanız yalnızca .NET Core 'un uygulama hedeflerinizin sürümü konak sisteminde zaten yüklüyse çalıştırılabilir. .NET Core 'un belirli bir sürümünü gerektirmek veya .NET Core 'un daha yeni bir sürümüne izin vermek için uygulama için ilet davranışını yapılandırabilirsiniz. Daha fazla bilgi için bkz. [çalışma zamanına bağımlı uygulamalar ileri alma](../versions/selection.md#framework-dependent-apps-roll-forward).

- **.NET Core\ değişebilir**
.NET Core çalışma zamanı ve kitaplıklarının uygulamanın çalıştırıldığı makinede güncellenmesi mümkündür. Nadir durumlarda, çoğu uygulamanın yapabileceği .NET Core kitaplıklarını kullanırsanız, bu durum uygulamanızın davranışını değiştirebilir. Uygulamanızın .NET Core 'un daha yeni sürümlerini nasıl kullandığını yapılandırabilirsiniz. Daha fazla bilgi için bkz. [çalışma zamanına bağımlı uygulamalar ileri alma](../versions/selection.md#framework-dependent-apps-roll-forward).

Aşağıdaki dezavantajı yalnızca .NET Core 2,1 SDK için geçerlidir.

- **Uygulamayı başlatmak için `dotnet` komutunu kullanın**\
Kullanıcıların uygulamanızı başlatması için `dotnet <filename.dll>` komutunu çalıştırmaları gerekir. .NET Core 2,1 SDK, çalışma zamanına bağımlı uygulamalar için platforma özel yürütülebilir dosyalar üretmez.

### <a name="examples"></a>Örnekler

Uygulama yayımlama platformlar arası çalışma zamanına bağımlı. Geçerli platformunuzu hedefleyen bir yürütülebilir dosya *DLL* dosyası ile birlikte oluşturulur.

```dotnet
dotnet publish
```

Uygulama yayımlama platformlar arası çalışma zamanına bağımlı. Linux 64 bit yürütülebilir dosyası, *DLL* dosyasıyla birlikte oluşturulur. Bu komut .NET Core SDK 2,1 ile çalışmıyor.

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>Kendi içinde Yayımla

Uygulamanızı kendi içinde yayımlamak platforma özgü bir yürütülebilir dosya oluşturur. Çıkış yayımlama klasörü, .NET Core kitaplıkları ve hedef çalışma zamanı dahil olmak üzere uygulamanın tüm bileşenlerini içerir. Uygulama diğer .NET Core uygulamalarından yalıtılmıştır ve yerel olarak yüklenmiş bir paylaşılan çalışma zamanı kullanmaz. Uygulamanızın kullanıcısı .NET Core indirmek ve yüklemek için gerekli değildir.

Yürütülebilir ikili dosya belirtilen hedef platform için üretildi. Örneğin, **word_reader**adlı bir uygulamanız varsa ve Windows için kendi kendine içerilen bir yürütülebilir dosyayı yayımlarsanız, bir *word_reader. exe* dosyası oluşturulur. Linux veya macOS için yayımlama, bir *word_reader* dosyası oluşturulur. Hedef platform ve mimari, [`dotnet publish`](../tools/dotnet-publish.md) komutu için `-r <RID>` parametresiyle belirtilmiştir. RID 'Ler hakkında daha fazla bilgi için bkz. [.NET Core RID kataloğu](../rid-catalog.md).

Uygulamanın platforma özgü bağımlılıklar içeren bir NuGet paketi gibi platforma özgü bağımlılıkları varsa, bunlar uygulamayla birlikte Yayımla klasörüne kopyalanır.

### <a name="advantages"></a>Yararları

- **.NET Core sürümü\ denetleme**
Uygulamanız ile hangi .NET Core sürümünün dağıtıldığını kontrol edersiniz.

- **Platforma özel hedefleme**\
Uygulamanızı her platform için yayımlamanız gerektiğinden uygulamanızın nerede çalışacağını bilirsiniz. .NET Core yeni bir platform sunabiliyorsa, kullanıcılar bu platformu hedefleyen bir sürüm yayınlayana kadar uygulamanızı bu platformda çalıştıramıyoruz. Kullanıcılarınızın uygulamanızı yeni platformda çalıştırmadan önce uyumluluk sorunları için uygulamanızı test edebilirsiniz.

### <a name="disadvantages"></a>Dezavantajlar

- **Daha büyük dağıtımlar**\
Uygulamanız .NET Core çalışma zamanı ve tüm uygulama bağımlılıklarınızı içerdiğinden, gereken indirme boyutu ve sabit disk alanı [çalışma zamanına bağlı](#publish-runtime-dependent) sürümden daha büyük.

  > [!TIP]
  > .NET Core [*Genelleştirme sabit modunu*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)kullanarak Linux sistemlerinde dağıtımınızın boyutunu YAKLAŞıK 28 MB azaltabilirsiniz. Bu, uygulamanızı [sabit kültür](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)gibi tüm kültürleri işleyecek şekilde zorlar.

- **.NET Core sürümünü güncelleştirmek daha zordur**\
.NET Core çalışma zamanı (uygulamanızla birlikte dağıtılır) yalnızca uygulamanızın yeni bir sürümü serbest bırakılarak yükseltilebilir. .NET Core çalışma zamanına yönelik güvenlik düzeltme ekleri için uygulamanızın güncelleştirilmiş bir sürümünü sağlamaktan sorumlu olursunuz. 

### <a name="examples"></a>Örnekler

Kendisini içeren bir uygulama yayımlayın. MacOS 64 bit yürütülebilir dosyası oluşturulur.

```dotnet
dotnet publish -r osx-x64
```

Kendisini içeren bir uygulama yayımlayın. Windows 64 bit yürütülebilir dosyası oluşturulur.

```dotnet
dotnet publish -r win-x64
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core CLI ile .NET Core uygulamaları dağıtma.](deploy-with-cli.md)
- [Visual Studio ile .NET Core uygulamaları dağıtma.](deploy-with-vs.md)
- [Paketler, Metapackages ve çerçeveler.](../packages.md)
- [.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu.](../rid-catalog.md)
- [Kullanılacak .NET Core sürümünü seçin.](../versions/selection.md)
