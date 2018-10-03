---
title: .NET core CLI araçları ile uygulama dağıtımı
description: .NET Core uygulama dağıtımı ile komut satırı arabirimi (CLI) araçlarını edinin
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
ms.openlocfilehash: a7e810372d831699eae777186385e45fe65cdf45
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046506"
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a>Komut satırı arabirimi (CLI) araçları ile .NET Core uygulaması dağıtma

Dağıtabileceğiniz bir .NET Core uygulaması ya da farklı bir *framework bağımlı dağıtım*, uygulama ikili dosyalarını içerir, ancak hedef sistem üzerinde veya olarak .NET Core varlığını bağımlı bir *müstakil Dağıtım*, hem uygulama hem de .NET Core ikili dosyalarını içerir. Genel bakış için bkz. [.NET Core uygulaması dağıtımını](index.md).

Aşağıdaki bölümlerde nasıl kullanabileceğinizi gösteren [.NET Core komut satırı arabirimi Araçları](../tools/index.md) dağıtımları aşağıdaki türleri oluşturmak için:

- Framework bağımlı dağıtım
- Framework bağımlı dağıtım üçüncü taraf bağımlılıkları
- Kendi içinde dağıtım
- Üçüncü taraf bağımlılıkları kendi içinde dağıtım

Komut satırından çalışırken, bir program düzenleyiciyi kullanabilirsiniz. Program düzenleyiciniz ise [Visual Studio Code](https://code.visualstudio.com), Visual Studio Code ortamınız içinde komut konsolunda seçerek açabilirsiniz **görünümü** > **tümleşik Terminalini**.

## <a name="framework-dependent-deployment"></a>Framework bağımlı dağıtım

Herhangi bir üçüncü taraf bağımlılıkları olan bir framework bağımlı dağıtımının oluşturmaya, sınamaya ve uygulama yayımlama yalnızca içerir. C# dilinde yazılmış basit bir örnek işlemini gösterir.

1. Proje dizini oluşturun.

   Projeniz için bir dizin oluşturun ve geçerli dizininizi kolaylaştırır.

1. Projeyi oluşturun.

   Komut satırından yazın [dotnet yeni konsol](../tools/dotnet-new.md) yeni bir C# konsol projesi oluşturmak için veya [dotnet yeni konsol - vb dil](../tools/dotnet-new.md) bu dizinde yeni bir Visual Basic konsol projesi oluşturmak için.

1. Uygulamanın kaynak kodunu ekleyin.

   Açık *Program.cs* veya *Program.vb* Düzenleyicisi'nde dosya ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin. Kullanıcının metin girmesini ister ve kullanıcı tarafından girilen kelimeler görüntüler. Normal ifade kullanan `\w+` giriş metnindeki sözcükleri ayırmak için.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Proje bağımlılıkları ve Araçları'nı güncelleştirin.

   Çalıştırma [dotnet restore](../tools/dotnet-restore.md) ([bkz. Not](#dotnet-restore-note)), projede belirtilen bağımlılıkları geri yüklemek için komutu.

1. Uygulamanızı hata ayıklama yapısını oluşturun.

   Kullanım [dotnet derleme](../tools/dotnet-build.md) uygulamanızı oluşturmak üzere komut veya [çalıştırma dotnet](../tools/dotnet-run.md) derlemek ve çalıştırmak için komutu.

1. Uygulamanızı dağıtın.

   Hata ayıklama ve test programı sonra aşağıdaki komutu kullanarak dağıtımı oluşturun:

      ```console
      dotnet publish -f netcoreapp2.1 -c Release
      ```
   Bu, bir yayın (bir hata ayıklama yerine) oluşturur, uygulama sürümü. Ortaya çıkan dosyalar adlı bir dizinde yerleştirilir *yayımlama* projenizin alt dizininde olan *bin* dizin.

   Uygulamanızın dosyaları ile birlikte uygulamanızı hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayımlama işlemi yayar. Dosya, öncelikle bir özel durum hata ayıklama için kullanışlıdır. İle uygulamanızın dosyalarını dağıtmak değil seçebilirsiniz. Uygulamanızı yayın derlemesinin hatalarını ayıklamak istediğiniz olay, ancak kaydetmeniz gerekir.

   İstediğiniz gibi uygulama dosyalarını kümesinin tamamını dağıtabilirsiniz. Örneğin, bunları bir Zip dosyasına paketleyin, basit bir kullanın `copy` komutunu ya da bunları seçtiğiniz herhangi bir yükleme paketi ile birlikte dağıtabilirsiniz.

1. Uygulamanızı çalıştırma

   Yüklendikten sonra kullanıcılar uygulamanızı kullanarak yürütebilirsiniz `dotnet` komut ve uygulama dosya adı gibi sağlama `dotnet fdd.dll`.

   Uygulama ikili dosyalarını ek olarak, yükleyicinizi de paylaşılan framework yükleyici paket veya uygulama yüklemesinin bir parçası olarak bir önkoşul olarak için kontrol edin.  Paylaşılan framework yönetici/kök erişimi gerekir.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Framework bağımlı dağıtım üçüncü taraf bağımlılıkları

Bir framework bağımlı dağıtımının bir veya daha fazla üçüncü taraf bağımlılıkları olan bu bağımlılıkların projeniz için kullanılabilir olmasını gerektirir. Çalıştırmadan önce iki ek adımlar gerekli `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komutu:

1. Gerekli üçüncü taraf kitaplıklara başvurular eklemek `<ItemGroup>` bölümünü, *csproj* dosya. Aşağıdaki `<ItemGroup>` bölüm üzerinde bir bağımlılık içeriyor [Json.NET](http://www.newtonsoft.com/json) bir üçüncü taraf kitaplığı:

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. Henüz yapmadıysanız, üçüncü taraf bağımlılığı'nı içeren NuGet paketini indirin. Paketi indirmek için yürütme `dotnet restore` ([bkz. Not](#dotnet-restore-note)) bağımlılık ekledikten sonra komutu. Bağımlılık yerel NuGet önbelleğini dışında çözümlendiğinden zaman yayımlama, sisteminizde kullanılabilir olmalıdır.

Üçüncü taraf bağımlılıkları olan bir framework bağımlı dağıtım yalnızca üçüncü taraf bağımlılıklarını olarak taşınabilir olduğunu unutmayın. Örneğin, bir üçüncü taraf kitaplığı yalnızca macOS destekliyorsa, uygulamayı Windows sistemleri için taşınabilir değildir. Bu, üçüncü taraf bağımlılığı yerel kodu bağımlı olması durumunda gerçekleşir. Bunun iyi bir örnektir [Kestrel sunucu](/aspnet/core/fundamentals/servers/kestrel), üzerinde yerel bir bağımlılık gerektiren [libuv](https://github.com/libuv/libuv). Bu tür bir üçüncü taraf bağımlılığı bir uygulama için bir FDD oluşturulduğunda, yayımlanan çıktısını bir klasöre her biri için içeren [çalışma zamanı tanımlayıcı (RID)](../rid-catalog.md) yerel bağımlılık destekleyen (ve kendi NuGet paketini var).

## <a name="simpleSelf"></a> Üçüncü taraf bağımlılıkları olmadan kendi içinde dağıtım

Üçüncü taraf bağımlılıkları içerir olmadan projesi oluşturarak kendi içinde bir dağıtım dağıtma değiştirme *csproj* oluşturmaya, sınamaya ve uygulama yayımlama dosyası. C# dilinde yazılmış basit bir örnek işlemini gösterir. Örneğin, kullanarak kendi içinde dağıtımı oluşturma işlemi gösterilmektedir [dotnet yardımcı programı](../tools/dotnet.md) komut satırından.

1. Proje için bir dizin oluşturun.

   Projeniz için bir dizin oluşturun ve geçerli dizininizi kolaylaştırır.

1. Projeyi oluşturun.

   Komut satırından yazın [dotnet yeni konsol](../tools/dotnet-new.md) bu dizinde yeni bir C# konsol projesi oluşturmak için.

1. Uygulamanın kaynak kodunu ekleyin.

   Açık *Program.cs* Düzenleyicisi'nde dosya ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin. Kullanıcının metin girmesini ister ve kullanıcı tarafından girilen kelimeler görüntüler. Normal ifade kullanan `\w+` giriş metnindeki sözcükleri ayırmak için.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]
1. Uygulamanızı hedefleyen platformlar tanımlayın.

   Oluşturma bir `<RuntimeIdentifiers>` içindeki `<PropertyGroup>` bölümünü, *csproj* uygulamanız hedefler ve hedeflediğiniz her platform için çalışma zamanı tanımlayıcı (RID) belirtin platformları tanımlayan dosya. Aynı zamanda RID ayırmak için noktalı virgül eklemeniz gerektiğini unutmayın. Bkz: [çalışma zamanı tanımlayıcı Kataloğu](../rid-catalog.md) çalışma zamanı tanımlayıcılarının listesi.

   Örneğin, aşağıdaki `<PropertyGroup>` bölümü gösterir uygulama 64-bit Windows 10 işletim sistemleri ve OS X sürüm 10.11 64-bit işletim sistemi üzerinde çalışır.

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   Unutmayın `<RuntimeIdentifiers>` öğe görünebilir `<PropertyGroup>` içinde *csproj* dosya. Eksiksiz bir örnek *csproj* dosyası bu bölümde daha sonra görünür.

1. Proje bağımlılıkları ve Araçları'nı güncelleştirin.

   Çalıştırma [dotnet restore](../tools/dotnet-restore.md) ([bkz. Not](#dotnet-restore-note)), projede belirtilen bağımlılıkları geri yüklemek için komutu.

1. Genelleştirme sabit modu kullanmak isteyip istemediğinizi belirleyin.

   Uygulamanızı Linux hedefliyorsa, özellikle, avantajlarından yararlanarak dağıtımınızın toplam boyutunu azaltabilirsiniz [Genelleştirme sabit modu](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md). Genelleştirme sabit modu, genel olarak duyarlı değildir ve biçimlendirme kuralları, büyük/küçük harf kuralları ve dize karşılaştırma ve sıralama düzenini kullanabilen uygulamalar için kullanışlıdır [sabit kültür](xref:System.Globalization.CultureInfo.InvariantCulture).

   Sabit modunu etkinleştirmek için projenize (çözümü değil) sağ **Çözüm Gezgini**seçip **Düzenle SCD.csproj** veya **Düzenle SCD.vbproj**. Ardından aşağıdaki vurgulanan satırları dosyaya ekleyin:

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. Uygulamanızı hata ayıklama yapısını oluşturun.

   Komut satırından kullanma [dotnet derleme](../tools/dotnet-build.md) komutu.

1. Hata ayıklama ve test programı sonra her platform için uygulamanızdan bu hedefler dağıtılacak dosyaların oluşturun.

   Kullanım `dotnet publish` her ikisi de şu şekilde platformlarını hedeflemek için komutu:

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   Bu, bir yayın (bir hata ayıklama yerine) oluşturur uygulamanızın her hedef platform sürümü. Ortaya çıkan dosyalar adlı bir alt dizinine yerleştirilir *yayımlama* projenizin alt dizininde olan *.\bin\Release\netcoreapp2.1\<runtime_identifier >* alt. Her alt uygulamanızı başlatmak için gerekli dosyaları (uygulama dosyalarınızı ve tüm .NET Core dosyaları) tam kümesini içerdiğine dikkat edin.

Uygulamanızın dosyaları ile birlikte uygulamanızı hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayımlama işlemi yayar. Dosya, öncelikle bir özel durum hata ayıklama için kullanışlıdır. Bu paket, uygulamanızın dosyaları ile değil seçebilirsiniz. Uygulamanızı yayın derlemesinin hatalarını ayıklamak istediğiniz olay, ancak kaydetmeniz gerekir.

Yayımlanan dosyaları istediğiniz herhangi bir şekilde dağıtın. Örneğin, bunları bir Zip dosyasına paketleyin, basit bir kullanın `copy` komutunu ya da bunları seçtiğiniz herhangi bir yükleme paketi ile birlikte dağıtabilirsiniz.

Aşağıdaki tamamlandıktan *csproj* bu proje için dosya.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Üçüncü taraf bağımlılıkları kendi içinde dağıtım

Bir veya daha fazla üçüncü taraf bağımlılıkları kendi içinde bir dağıtımının bağımlılıkları ekleme içerir. Çalıştırmadan önce iki ek adımlar gerekli `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komutu:

1. Herhangi bir üçüncü taraf kitaplıklara başvurular eklemek `<ItemGroup>` bölümünü, *csproj* dosya. Aşağıdaki `<ItemGroup>` bölümü, bir üçüncü taraf kitaplığı olarak Json.NET kullanır.

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. Henüz yapmadıysanız, üçüncü taraf bağımlılığı sisteminize'nı içeren NuGet paketini indirin. Bağımlılık uygulamanızı kullanılabilir hale getirmek için yürütme `dotnet restore` ([bkz. Not](#dotnet-restore-note)) bağımlılık ekledikten sonra komutu. Bağımlılık yerel NuGet önbelleğini dışında çözümlendiğinden zaman yayımlama, sisteminizde kullanılabilir olmalıdır.

Aşağıdaki tamamlandıktan *csproj* bu proje için dosya:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

Uygulamanızı dağıttığınızda, uygulamanızda kullanılan herhangi bir üçüncü taraf bağımlılıkları ile uygulama dosyalarınızı de yer alır. Üçüncü taraf kitaplıklar, uygulama üzerinde çalıştığı sistemde gerekmez.

Yalnızca bir üçüncü taraf kitaplığı ile kendi içinde bir dağıtım için bu kitaplığı tarafından desteklenen platformlar dağıtabileceğinizi unutmayın. Bu yerel bağımlılıkları burada uygulamanın dağıtıldığı platform ile uyumlu olmalıdır framework bağımlı dağıtımında, üçüncü taraf bağımlılıklarının yerel bağımlılıkları olan olması için benzer.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [.NET core uygulama dağıtımı](index.md)
* [.NET core çalışma zamanı tanımlayıcı (RID) Kataloğu](../rid-catalog.md)
