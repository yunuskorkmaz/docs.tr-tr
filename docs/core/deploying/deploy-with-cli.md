---
title: ".NET core CLI araçları ile uygulama dağıtımı"
description: ".NET Core uygulama dağıtım araçları komut satırı arabirimi (CLI) ile bilgi edinin"
keywords: ".NET, .NET core, .NET Core dağıtım"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 82ebe16d-5e1c-46cc-91e8-71974296429c
ms.openlocfilehash: fc7a40667c9b0a623bb0ebdf4ad60783fa58e6c5
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a>Komut satırı arabirimi (CLI) araçları ile .NET Core uygulamaları dağıtma

.NET Core uygulama dağıtabilirsiniz ya da farklı bir *framework bağımlı dağıtım*, hangi uygulama ikili dosyaları içerir, ancak hedef sistemde veya olarak .NET Core varlığına bağlıdır bir *kendi içinde bulunan Dağıtım*, uygulamanız ve .NET Core ikili dosyalarını içerir. Genel bir bakış için bkz: [.NET Core uygulama dağıtımı](index.md).

Aşağıdaki bölümlerde nasıl kullanılacağını gösteren [.NET Core komut satırı arabirimi Araçları](../tools/index.md) dağıtımları şu tür oluşturmak için:

- Framework bağımlı dağıtım
- Üçüncü taraf bağımlılıkları Framework bağımlı dağıtım
- Kendi içinde bulunan dağıtım
- Üçüncü taraf bağımlılıkları kendi içinde bulunan dağıtım

Komut satırından çalışırken, bir program düzenleyiciyi kullanabilirsiniz. Program düzenleyicinizi ise [Visual Studio Code](https://code.visualstudio.com), Visual Studio Code ortamınızın içinde bir komut konsolundan seçerek açabilirsiniz **Görünüm** > **tümleşik Terminal**.

## <a name="framework-dependent-deployment"></a>Framework bağımlı dağıtım

Hiçbir üçüncü taraf bağımlılıkları framework bağımlı dağıtım dağıtma yalnızca derleme, test etme ve uygulama yayımlama içerir. C# ile yazılmış basit bir örnek işlemi gösterilmektedir. 

1. Proje dizini oluşturun.

   Projeniz için bir dizin oluşturun ve geçerli dizininiz yapın.

1. Projesi oluşturun.

   Komut satırından yazın [dotnet yeni konsol](../tools/dotnet-new.md) bu dizinde yeni bir C# konsol projesi oluşturmak için.

1. Uygulamanın kaynak kodu ekleyin.

   Açık *Program.cs* dosya düzenleyicinizde ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin. Metin girmesini ister ve kullanıcı tarafından girilen ayrı sözcükleri görüntüler. Normal ifade kullanan `\w+` giriş metni sözcükleri ayırmak için.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Proje bağımlılıkları ve araçları güncelleştirin.
 
   Çalıştırma [dotnet geri yükleme](../tools/dotnet-restore.md) ([bkz. Not](#dotnet-restore-note)) projenizde belirtilen bağımlılıkları geri yüklemek için komutu.

1. Hata ayıklama derlemesi, uygulamanızın oluşturun.

   Kullanım [dotnet yapı](../tools/dotnet-build.md) Uygulamanızı yapılandırmak için komut veya [çalıştırmak dotnet](../tools/dotnet-run.md) oluşturmak ve çalıştırmak için komutu.

1. Uygulamanızı dağıtın.

   Hata ayıklaması ve program test sonra aşağıdaki komutu kullanarak dağıtım oluşturun:

      ```console
      dotnet publish -f netcoreapp1.1 -c Release
      ```
   Bu sürüm (bir hata ayıklama yerine) oluşturur, uygulamanızın sürümü. Ortaya çıkan dosyalar adlı bir dizinde yerleştirilir *yayımlama* projenizin bir alt dizin olan *bin* dizin.

Uygulamanızın dosyaları yanı sıra, yayımlama işlemi uygulamanız ile ilgili hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayar. Dosya, öncelikle özel durumları hata ayıklama için kullanışlıdır. Uygulamanızın dosyalarıyla dağıtmak değil seçebilirsiniz. Uygulamanızın yayın derleme hatalarını ayıklamak istediğiniz olay, ancak kaydedin gerekir.

İstediğiniz şekilde uygulama dosyalarında tamamını dağıtabilirsiniz. Örneğin, bir ZIP dosyası paketini, basit bir kullanmak `copy` komutunu veya tercih ettiğiniz herhangi bir yükleme paketi ile dağıtabilirsiniz. Yüklendikten sonra kullanıcılar, uygulamanızın kullanarak yürütebilirsiniz `dotnet` komutu ve uygulama filename gibi sağlayarak `dotnet fdd.dll`.

Uygulama ikili dosyaların yanı sıra, yükleyici de paylaşılan framework Yükleyici paketini ya da için uygulama yüklemesinin bir parçası olarak bir önkoşul olarak denetleyin.  Paylaşılan framework yüklemesi yönetici/kök erişimi gerektirir.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Üçüncü taraf bağımlılıkları Framework bağımlı dağıtım

Bir veya daha fazla üçüncü taraf bağımlılıkları framework bağımlı dağıtım dağıtma bu bağımlılıkların projeniz için kullanılabilir olmasını gerektirir. Çalıştırmadan önce iki ek adımlar gerekli `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komutu:

1. Gerekli üçüncü taraf kitaplıklarına başvurular ekleyin `<ItemGroup>` bölümü, *csproj* dosya. Aşağıdaki `<ItemGroup>` bölüm üzerinde bir bağımlılık içerir [Json.NET](http://www.newtonsoft.com/json) üçüncü taraf kitaplık olarak:

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. Henüz yapmadıysanız, üçüncü taraf bağımlılığı içeren NuGet paketini yükleyin. Paketini karşıdan yüklemek için yürütme `dotnet restore` ([bkz. Not](#dotnet-restore-note)) bağımlılık ekledikten sonra komutu. Bağımlılık yerel NuGet önbelleği dışında çözümlendiğinden zaman yayınlamak için sisteminizde kullanılabilir olmalıdır.

Üçüncü taraf bağımlılıkları framework bağımlı dağıtımla yalnızca üçüncü taraf bağımlılıkları olarak taşınabilir olduğuna dikkat edin. Örneğin, bir üçüncü taraf kitaplık yalnızca macOS destekliyorsa, uygulamayı Windows sistemleri için taşınabilir değil. Üçüncü taraf bağımlılığı yerel kodu bağımlı olması durumunda bu gerçekleşir. Bu iyi bir örnektir [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), üzerindeki yerel bir bağımlılık gerektiren [libuv](https://github.com/libuv/libuv). Üçüncü taraf bağımlılığı bu tür bir uygulama için bir FDD oluşturulduğunda, yayımlanan çıktı bir klasör için her içerir [çalışma zamanı tanımlayıcı (RID)](../rid-catalog.md) yerel bağımlılık destekleyen (ve onun NuGet paketi var).

## <a name="simpleSelf"></a>Üçüncü taraf bağımlılıkları kendi içinde bulunan dağıtımıdır

Üçüncü taraf bağımlılıkları içerir olmadan projesi oluşturma kendi içinde bulunan bir dağıtım dağıtma değiştirme *csproj* dosya oluşturma, test etme ve uygulama yayımlama. C# ile yazılmış basit bir örnek işlemi gösterilmektedir. Örnek kullanarak kendi içinde bulunan dağıtımı oluşturmak nasıl gösterir [dotnet yardımcı programı](../tools/dotnet.md) komut satırından.

1. Proje için bir dizin oluşturun.

   Projeniz için bir dizin oluşturun ve geçerli dizininiz yapın.

1. Projesi oluşturun.

   Komut satırından yazın [dotnet yeni konsol](../tools/dotnet-new.md) bu dizinde yeni bir C# konsol projesi oluşturmak için.

1. Uygulamanın kaynak kodu ekleyin.

   Açık *Program.cs* dosya düzenleyicinizde ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin. Metin girmesini ister ve kullanıcı tarafından girilen ayrı sözcükleri görüntüler. Normal ifade kullanan `\w+` giriş metni sözcükleri ayırmak için.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Uygulamanızı Hedef platformlar tanımlayın.

   Oluşturma bir `<RuntimeIdentifiers>` içinde etiketi `<PropertyGroup>` bölümü, *csproj* uygulamanızı hedefler ve hedeflediğiniz her platform için çalışma zamanı tanımlayıcı (RID) belirtin platformları tanımlayan dosyası. Aynı zamanda RID ayırmak için noktalı virgül eklemeniz gerektiğini unutmayın. Bkz: [çalışma zamanı tanımlayıcı katalog](../rid-catalog.md) çalışma zamanı tanımlayıcılarının listesi. 

   Örneğin, aşağıdaki `<PropertyGroup>` bölümü gösterir uygulama 64-bit Windows 10 işletim sistemleri ve 64-bit OS X sürüm 10.11 sürümünü işletim sisteminde çalışır.

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   Unutmayın `<RuntimeIdentifiers>` öğesi içinde görünebilir `<PropertyGroup>` içinde *csproj* dosya. Tam bir örnek *csproj* dosyası bu bölümde daha sonra görünür.

1. Proje bağımlılıkları ve araçları güncelleştirin.

   Çalıştırma [dotnet geri yükleme](../tools/dotnet-restore.md) ([bkz. Not](#dotnet-restore-note)) projenizde belirtilen bağımlılıkları geri yüklemek için komutu.

1. Hata ayıklama derlemesi, uygulamanızın oluşturun.

   Komut satırından kullanma [dotnet yapı](../tools/dotnet-build.md) komutu.

1. Hata ayıklaması ve program test sonra her platform için uygulamanız ile bu hedefler dağıtılacak dosyaları oluşturun.

   Kullanım `dotnet publish` her ikisi de aşağıdaki gibi platformları hedeflemesi için komut:

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   Bu sürüm (bir hata ayıklama yerine) oluşturur uygulamanız için her hedef platformu sürümü. Ortaya çıkan dosyalar adlı bir alt dizinde yerleştirilir *yayımlama* projenizin bir alt dizin olan *.\bin\Release\netcoreapp1.1\<runtime_identifier >* alt dizin. Her alt uygulamanızı başlatmak için gereken dosyaları (uygulama dosyalarınızı ve tüm .NET Core dosyaları) tam kümesi içerdiğini unutmayın.

Uygulamanızın dosyaları yanı sıra, yayımlama işlemi uygulamanız ile ilgili hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayar. Dosya, öncelikle özel durumları hata ayıklama için kullanışlıdır. Bu paket, uygulamanızın dosyaları ile değil seçebilirsiniz. Uygulamanızın yayın derleme hatalarını ayıklamak istediğiniz olay, ancak kaydedin gerekir.

İstediğiniz şekilde yayımlanan dosyalarında dağıtın. Örneğin, bir ZIP dosyası paketini, basit bir kullanmak `copy` komutunu veya tercih ettiğiniz herhangi bir yükleme paketi ile dağıtabilirsiniz.

Aşağıdaki tamamlandıktan *csproj* bu proje için dosya.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Üçüncü taraf bağımlılıkları kendi içinde bulunan dağıtım

Bir veya daha fazla üçüncü taraf bağımlılıkları kendi içinde bulunan bir dağıtım dağıtma bağımlılıkları ekleme içerir. Çalıştırmadan önce iki ek adımlar gerekli `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komutu:

1. Tüm üçüncü taraf kitaplıklarına başvurular ekleyin `<ItemGroup>` bölümü, *csproj* dosya. Aşağıdaki `<ItemGroup>` bölüm Json.NET üçüncü taraf kitaplık olarak kullanır.

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. Henüz yapmadıysanız, üçüncü taraf bağımlılığı sisteminize içeren NuGet paketini yükleyin. Bağımlılık uygulamanızı kullanılabilir hale getirmek için yürütme `dotnet restore` ([bkz. Not](#dotnet-restore-note)) bağımlılık ekledikten sonra komutu. Bağımlılık yerel NuGet önbelleği dışında çözümlendiğinden zaman yayınlamak için sisteminizde kullanılabilir olmalıdır.

Aşağıdaki tamamlandıktan *csproj* dosyası bu proje için:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

Uygulamanızı dağıttığınızda, uygulamanızda kullanılan tüm üçüncü taraf bağımlılıkları ile uygulama dosyalarını da yer alır. Üçüncü taraf kitaplıklar uygulama çalışırken sistemde gerekli değildir.

Yalnızca bir üçüncü taraf kitaplık müstakil dağıtımla bu kitaplığı tarafından desteklenen platformlar dağıtabileceğiniz olduğunu unutmayın. Bu burada yerel bağımlılıkları uygulamanın dağıtıldığı platform ile uyumlu olmalıdır framework bağımlı dağıtımında, üçüncü taraf bağımlılıkları yerel bağımlılıkları ile zorunda benzer.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

# <a name="see-also"></a>Ayrıca bkz.

[.NET core uygulama dağıtımı](index.md)   
[.NET çekirdeği çalışma zamanı tanımlayıcı (RID) Kataloğu](../rid-catalog.md)   

