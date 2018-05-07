---
title: Visual Studio ile .NET core uygulama dağıtımı
description: .NET Core uygulama dağıtımı Visual Studio ile bilgi edinin
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.openlocfilehash: dedf04a872faf1b35a05f9da0c61b80713fdce51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-net-core-apps-with-visual-studio"></a>.NET dağıtma çekirdek Visual Studio ile uygulamaları

.NET Core uygulama dağıtabilirsiniz ya da farklı bir *framework bağımlı dağıtım*, hangi uygulama ikili dosyaları içerir, ancak hedef sistemde veya olarak .NET Core varlığına bağlıdır bir *kendi içinde bulunan Dağıtım*, hem uygulama hem de .NET Core ikili dosyalarını içerir. .NET Core uygulama dağıtımına genel bakış için bkz: [.NET Core uygulama dağıtımı](index.md).

Aşağıdaki bölümlerde Microsoft Visual Studio dağıtımları şu tür oluşturmak için nasıl kullanılacağı gösterilmektedir:

- Framework bağımlı dağıtım
- Üçüncü taraf bağımlılıkları Framework bağımlı dağıtım
- Kendi içinde bulunan dağıtım
- Üçüncü taraf bağımlılıkları kendi içinde bulunan dağıtım

.NET Core uygulamaları geliştirmek için Visual Studio kullanma hakkında daha fazla bilgi için bkz: [.NET Core Windows önkoşulları](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).

## <a name="framework-dependent-deployment"></a>Framework bağımlı dağıtım

Hiçbir üçüncü taraf bağımlılıkları framework bağımlı dağıtım dağıtma yalnızca derleme, test etme ve uygulama yayımlama içerir. C# ile yazılmış basit bir örnek işlemi gösterilmektedir.  

1. Projesi oluşturun.

   Select **File** > **New** > **Project**. İçinde **yeni proje** iletişim kutusunda **.NET Core** içinde **yüklü** Proje Türleri bölmesinde ve seçin **konsol uygulaması (.NET Core)** Orta bölmede şablonu. "FDD" gibi bir proje adı girin **adı** metin kutusu. Seçin **Tamam** düğmesi.

1. Uygulamanın kaynak kodu ekleyin.

   Açık *Program.cs* Düzenleyicisi'nde dosya ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin. Metin girmesini ister ve kullanıcı tarafından girilen ayrı sözcükleri görüntüler. Normal ifade kullanan `\w+` giriş metni sözcükleri ayırmak için.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Hata ayıklama derlemesi, uygulamanızın oluşturun.

   Seçin **yapı** > **yapı çözümü**. Ayrıca derleyin ve hata ayıklama derlemesi uygulamanızın seçerek çalıştırın **hata ayıklama** > **hata ayıklamayı Başlat**.

1. Uygulamanızı dağıtın.

   Hata ayıklaması ve program test sonra uygulamanızı dağıtılacak dosyaları oluşturun. Visual Studio'dan yayımlamak için aşağıdakileri yapın:

      1. Çözüm yapılandırmasını değiştirme **hata ayıklama** için **sürüm** uygulamanızı derleme sürüm a (yerine bir hata ayıklama) sürümü için araç çubuğundaki.

      1. Projeye (çözümü değil) sağ tıklatın, **Çözüm Gezgini**seçip **Yayımla**.

      1. İçinde **Yayımla** sekmesine **Yayımla**. Visual Studio uygulamanızı yerel dosya sistemine oluşturan dosyaların yazar.

      1. **Yayımla** sekmesi artık tek bir profil gösterir **FolderProfile**. Profilin yapılandırma ayarları'nda gösterilen **Özet** sekmesinin bölümünde.

   Ortaya çıkan dosyalar adlı bir dizinde yerleştirilir `PublishOutput` projenizin bir alt dizin olan *.\bin\release* alt dizin.

Uygulamanızın dosyaları yanı sıra, yayımlama işlemi uygulamanız ile ilgili hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayar. Dosya, öncelikle özel durumları hata ayıklama için kullanışlıdır. Bu paket, uygulamanızın dosyaları ile değil seçebilirsiniz. Uygulamanızın yayın derleme hatalarını ayıklamak istediğiniz olay, ancak kaydedin gerekir.

İstediğiniz şekilde uygulama dosyalarında tamamını dağıtın. Örneğin, bir ZIP dosyası paketini, basit bir kullanmak `copy` komutunu veya tercih ettiğiniz herhangi bir yükleme paketi ile dağıtabilirsiniz. Yüklendikten sonra kullanıcılar daha sonra uygulamanızın kullanarak yürütebilirsiniz `dotnet` komutu ve uygulama filename gibi sağlayarak `dotnet fdd.dll`.

Uygulama ikili dosyaların yanı sıra, yükleyici de paylaşılan framework Yükleyici paketini ya da için uygulama yüklemesinin bir parçası olarak bir önkoşul olarak denetleyin.  Makine genelinde olduğundan paylaşılan framework yüklemesi yönetici/kök erişimi gerektirir.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Üçüncü taraf bağımlılıkları Framework bağımlı dağıtım

Bir veya daha fazla üçüncü taraf bağımlılıkları framework bağımlı dağıtım dağıtma bağımlılıkları projeniz için kullanılabilir olmasını gerektirir. Uygulamanızı oluşturmadan önce aşağıdaki ek adımları gereklidir:

1. Kullanım **NuGet Paket Yöneticisi** projenize; NuGet paketine başvuru eklemek ve paket zaten, sisteminizde mevcut olmaması durumunda yüklemek için. Paket Yöneticisi'ni açmak için seçin **Araçları** > **NuGet Paket Yöneticisi** > **çözüm için NuGet paketlerini Yönet**.

1. Onaylayın `Newtonsoft.Json` sisteminizde yüklü ve değilse, bunu yükleyin. **Yüklü** sekmesi, sisteminizde yüklü olan NuGet paketleri listeler. Varsa `Newtonsoft.Json` listelenmiyorsa, seçin **Gözat** sekmesinde ve arama kutusuna "Newtonsoft.Json" girin. Seçin `Newtonsoft.Json` seçip, sağ bölmede, projenizin seçmeden önce **yükleme**.

1. Varsa `Newtonsoft.Json` olduğundan, sistemde zaten yüklü, projenize sağ bölmesinde, projenizin seçerek eklemek **çözüm paketlerini Yönet** sekmesi.

Üçüncü taraf bağımlılıkları framework bağımlı dağıtımla yalnızca üçüncü taraf bağımlılıkları olarak taşınabilir olduğuna dikkat edin. Örneğin, bir üçüncü taraf kitaplık yalnızca macOS destekliyorsa, uygulamayı Windows sistemleri için taşınabilir değil. Üçüncü taraf bağımlılığı yerel kodu bağımlı olması durumunda bu gerçekleşir. Bu iyi bir örnektir [Kestrel server](http://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), üzerindeki yerel bir bağımlılık gerektiren [libuv](https://github.com/libuv/libuv). Üçüncü taraf bağımlılığı bu tür bir uygulama için bir FDD oluşturulduğunda, yayımlanan çıktı bir klasör için her içerir [çalışma zamanı tanımlayıcı (RID)](../rid-catalog.md) yerel bağımlılık destekleyen (ve onun NuGet paketi var).

## <a name="simpleSelf"></a> Üçüncü taraf bağımlılıkları kendi içinde bulunan dağıtımıdır

Hiçbir üçüncü taraf bağımlılıkları kendi içinde bulunan bir dağıtım dağıtma içerir projesi oluşturma değiştirme *csproj* dosya oluşturma, test etme ve uygulama yayımlama. C# ile yazılmış basit bir örnek işlemi gösterilmektedir. 

1. Projesi oluşturun.

   Select **File** > **New** > **Project**. İçinde **Yeni Proje Ekle** iletişim kutusunda **.NET Core** içinde **yüklü** Proje Türleri bölmesinde ve seçin **konsol uygulaması (.NET Core)** Orta bölmede şablonu. "SCD" gibi bir proje adı girin **adı** metin kutusu ve select **Tamam** düğmesi.

1. Uygulamanın kaynak kodu ekleyin.

   Açık *Program.cs* dosya düzenleyicinizde ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin. Metin girmesini ister ve kullanıcı tarafından girilen ayrı sözcükleri görüntüler. Normal ifade kullanan `\w+` giriş metni sözcükleri ayırmak için.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Uygulamanızı Hedef platformlar tanımlayın.

   1. Projenizde (çözümü değil) sağ tıklatın, **Çözüm Gezgini**seçip **Düzenle SCD.csproj**.

   1. Oluşturma bir `<RuntimeIdentifiers>` içinde etiketi `<PropertyGroup>` bölümü, *csproj* uygulama hedeflerinizi platformları tanımlayan dosyası ve hedeflediğiniz her platform için çalışma zamanı tanımlayıcı (RID) belirtin. Aynı zamanda RID ayırmak için noktalı virgül eklemeniz gerektiğini unutmayın. Bkz: [çalışma zamanı tanımlayıcı katalog](../rid-catalog.md) çalışma zamanı tanımlayıcılarının listesi. 

   Örneğin, aşağıdaki örnek uygulama 64-bit Windows 10 işletim sistemleri ve 64-bit OS X sürüm 10.11 sürümünü işletim sistemi çalıştırıldığını gösterir.

```xml
<PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
</PropertyGroup>
```
   Unutmayın `<RuntimeIdentifiers>` öğesi hiçbir gitmek `<PropertyGroup>` sahip, *csproj* dosya. Tam bir örnek *csproj* dosyası bu bölümde daha sonra görünür.

1. Hata ayıklama derlemesi, uygulamanızın oluşturun.

   Seçin **yapı** > **yapı çözümü**. Ayrıca derleyin ve hata ayıklama derlemesi uygulamanızın seçerek çalıştırın **hata ayıklama** > **hata ayıklamayı Başlat**.

1. Uygulamanızı yayımlayın.

   Hata ayıklaması ve program test sonra her platform için uygulamanız ile bu hedefler dağıtılacak dosyaları oluşturun.

   Uygulamanızı Visual Studio'dan yayımlamak için aşağıdakileri yapın:

      1. Çözüm yapılandırmasını değiştirme **hata ayıklama** için **sürüm** uygulamanızı derleme sürüm a (yerine bir hata ayıklama) sürümü için araç çubuğundaki.

      1. Projeye (çözümü değil) sağ tıklatın, **Çözüm Gezgini** seçip **Yayımla**. 

      1. İçinde **Yayımla** sekmesine **Yayımla**. Visual Studio uygulamanızı yerel dosya sistemine oluşturan dosyaların yazar.

      1. **Yayımla** sekmesi artık tek bir profil gösterir **FolderProfile**. Profilin yapılandırma ayarları'nda gösterilen **Özet** sekmesinin bölümünde. **Hedef çalışma zamanı** hangi çalışma zamanı yayımlanan tanımlar ve **hedef konumu** müstakil dağıtımı için dosyalarını yazıldığı tanımlar.

      1. Visual Studio varsayılan olarak, tüm dosyaları için tek bir dizin yayımlanan yazar. Kolaylık olması için her hedef çalışma zamanı için ayrı profilleri oluşturmak ve platforma özgü dizinde yayımlanan dosyaları yerleştirmek için en iyisidir. Bu, her hedef platformu için ayrı bir yayımlama profili oluşturmayı içerir. Artık uygulama her platform için aşağıdakileri yaparak yeniden oluşturun:

         1. Seçin **yeni profil oluşturmak** içinde **Yayımla** iletişim.

         1. İçinde **yayımlama hedefi çekme** iletişim kutusunda, değişiklik **bir klasör seçin** konuma *bin\Release\PublishOutput\win10 x64*. Seçin **Tamam**.

         1. Yeni profili seçin (**FolderProfile1**) profilleri listesinde emin olun **hedef çalışma zamanı** olan `win10-x64`. Değilse, seçin **ayarları**. İçinde **profil ayarları** iletişim kutusunda, değişiklik **hedef çalışma zamanı** için `win10-x64` seçip **kaydetmek**. Aksi takdirde seçin **iptal**.

         1. Seçin **Yayımla** 64-bit Windows 10 platformlarını için uygulamanızı yayımlamak için.

         1. Bir profil için yeniden oluşturmak için önceki adımları `osx.10.11-x64` platform. **Hedef konumu** olan *bin\Release\PublishOutput\osx.10.11-x64*ve **hedef çalışma zamanı** olan `osx.10.11-x64`. Bu profil için Visual Studio atar adı **FolderProfile2**.

      Her hedef konumu uygulamanızı başlatmak için gereken dosyaları (uygulama dosyalarınızı ve tüm .NET Core dosyaları) tam kümesi içerdiğini unutmayın.

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

Bir veya daha fazla üçüncü taraf bağımlılıkları kendi içinde bulunan bir dağıtım dağıtma bağımlılıkları ekleme içerir. Uygulamanızı oluşturmadan önce aşağıdaki ek adımları gereklidir:

1. Kullanım **NuGet Paket Yöneticisi** projenize; NuGet paketine başvuru eklemek ve paket zaten, sisteminizde mevcut olmaması durumunda yüklemek için. Paket Yöneticisi'ni açmak için seçin **Araçları** > **NuGet Paket Yöneticisi** > **çözüm için NuGet paketlerini Yönet**.

1. Onaylayın `Newtonsoft.Json` sisteminizde yüklü ve değilse, bunu yükleyin. **Yüklü** sekmesi, sisteminizde yüklü olan NuGet paketleri listeler. Varsa `Newtonsoft.Json` listelenmiyorsa, seçin **Gözat** sekmesinde ve arama kutusuna "Newtonsoft.Json" girin. Seçin `Newtonsoft.Json` seçip, sağ bölmede, projenizin seçmeden önce **yükleme**.

1. Varsa `Newtonsoft.Json` olduğundan, sistemde zaten yüklü, projenize sağ bölmesinde, projenizin seçerek eklemek **çözüm paketlerini Yönet** sekmesi.

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

Yalnızca bir üçüncü taraf kitaplık müstakil dağıtımla bu kitaplığı tarafından desteklenen platformlar dağıtabileceğiniz olduğunu unutmayın. Bu bunlar daha önce yüklü sürece yerel bağımlılıkları hedef platformda burada var olmaz framework bağımlı dağıtımınızda yerel bağımlılıkları olan üçüncü taraf bağımlılıkları zorunda benzer.

# <a name="see-also"></a>Ayrıca bkz.
[.NET core uygulama dağıtımı](index.md)   
[.NET çekirdeği çalışma zamanı tanımlayıcı (RID) Kataloğu](../rid-catalog.md)   
