---
title: Visual Studio ile .NET Core uygulamalarını dağıtın
description: Visual Studio ile bir .NET Core uygulaması dağıtmayı öğrenin.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: f2299ac807c845dab482306cc4c710560bb7f1e7
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607868"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a>Visual Studio ile .NET Core uygulamalarını dağıtın

Bir .NET Core uygulamasını, uygulama ikililerinizi içeren, ancak hedef sistemde .NET Core'un varlığına bağlı olan bir *çerçeveye bağımlı dağıtım*olarak veya hem uygulamanızı hem de .NET Core ikililerini içeren bağımsız bir *dağıtım*olarak dağıtabilirsiniz. .NET Core uygulama dağıtımına genel bakış için [bkz.](index.md)

Aşağıdaki bölümlerde, aşağıdaki türde dağıtımlar oluşturmak için Microsoft Visual Studio'nun nasıl kullanılacağı gösteriş verilmiştir:

- Çerçeveye bağımlı dağıtım
- Üçüncü taraf bağımlılıkları ile çerçeveye bağımlı dağıtım
- Bağımsız dağıtım
- Üçüncü taraf bağımlılıkları ile bağımsız dağıtım

.NET Core uygulamalarını geliştirmek için Visual Studio'yu kullanma hakkında bilgi için [.NET Core bağımlılıkları ve gereksinimlerine](../install/dependencies.md?pivots=os-windows)bakın.

## <a name="framework-dependent-deployment"></a>Çerçeveye bağımlı dağıtım

Üçüncü taraf bağımlılıkları olmayan bir çerçeveye bağımlı dağıtım dağıtmak yalnızca uygulamanın oluşturulmasını, test edilmesini ve yayımlanmasını içerir. C# ile yazılmış basit bir örnek işlemi göstermektedir.

1. Projeyi oluşturun.

   **Dosya** > **Yeni** > **Proje'yi**seçin. Yeni **Proje** iletişim kutusunda, **yüklü** proje türleri bölmesinde dilinizin (C# veya Visual Basic) proje kategorilerini genişletin, **.NET Core'u**seçin ve ardından orta bölmedeki **Konsol Uygulaması (.NET Core)** şablonunu seçin. **Ad** metin kutusuna "FDD" gibi bir proje adı girin. **Tamam** düğmesini seçin.

1. Uygulamanın kaynak kodunu ekleyin.

   Program.cs *veya* *Program.vb* dosyasını düzenleyicide açın ve otomatik oluşturulan kodu aşağıdaki kodla değiştirin. Kullanıcıdan metin girmesini ister ve kullanıcı tarafından girilen tek tek sözcükleri görüntüler. Giriş metnindeki `\w+` sözcükleri ayırmak için normal ifadeyi kullanır.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Uygulamanızın hata ayıklama yapısı oluşturun.

   **Yapı** > **Çözümünü**Seçin. Ayrıca Hata **Debug** > **Ayıklama Başlatma Hata Ayıklama'yı**seçerek uygulamanızın Hata Ayıklama oluşturma sını derleyebilir ve çalıştırabilirsiniz.

1. Uygulamanızı dağıtın.

   Programı debugged ve test ettikten sonra, uygulamaile dağıtılacak dosyaları oluşturun. Visual Studio'dan yayınlamak için aşağıdakileri yapın:

      1. Uygulamanızın Sürüm (Hata Ayıklama yerine) sürümünü oluşturmak için çözüm yapılandırmasını araç çubuğunda **Hata Ayıklama'dan** **Sürüm'e** değiştirin.

      1. **Solution Explorer'da** projeye (çözüm değil) sağ tıklayın ve **Yayımla'yı**seçin.

      1. **Yayımla** sekmesinde **Yayımla'yı**seçin. Visual Studio, uygulamanızı oluşturan dosyaları yerel dosya sistemine yazar.

      1. **Yayımla** sekmesi artık tek bir profil, **FolderProfile**gösterir. Profilin yapılandırma ayarları sekenin **Özet** bölümünde gösterilir.

   Elde edilen dosyalar, Windows'da `Publish` ve `publish` projenizin *.\bin\release\netcoreapp2.1* alt dizininin alt dizininde bulunan Unix sistemlerinde adlı bir dizine yerleştirilir.

Uygulamanızın dosyalarıyla birlikte, yayımlama işlemi, uygulamanızla ilgili hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayar. Dosya, öncelikle hata ayıklama özel durumları için yararlıdır. Uygulamanızın dosyalarıyla paketlememeyi seçebilirsiniz. Ancak, uygulamanızın Sürüm yapısıhatasını ayıklamak istemeniz durumunda bunu kaydetmeniz gerekir.

Tüm uygulama dosyalarını istediğiniz şekilde dağıtın. Örneğin, bunları zip dosyasında paketleyebilir, basit `copy` bir komut kullanabilir veya istediğiniz herhangi bir yükleme paketiyle dağıtabilirsiniz. Kurulduktan sonra, kullanıcılar daha sonra komutu `dotnet` kullanarak ve uygulama dosya adını `dotnet fdd.dll`sağlayarak uygulamanızı yürütebilir.

Uygulama ikililerine ek olarak, yükleyiciniz paylaşılan çerçeve yükleyicisini de paketlemeli veya uygulama yüklemesinin bir parçası olarak ön koşul olarak bunu kontrol etmelidir.  Paylaşılan çerçevenin yüklenmesi, makine genelinde olduğundan Yönetici/kök erişimi gerektirir.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Üçüncü taraf bağımlılıkları ile çerçeveye bağımlı dağıtım

Bir veya daha fazla üçüncü taraf bağımlılıkla çerçeveye bağımlı bir dağıtım dağıtmak, projenizde herhangi bir bağımlılık olmasını gerektirir. Uygulamanızı oluşturmadan önce aşağıdaki ek adımlar gereklidir:

1. Projenize bir NuGet paketine başvuru eklemek için **NuGet Paket Yöneticisi'ni** kullanın; ve paket sisteminizde zaten mevcut değilse, yükleyin. Paket yöneticisini açmak için, **Araçlar** > **NuGet Paket Yöneticisi** > **Çözüm için Paketleri Yönet'i**seçin.

1. Üçüncü taraf bağımlılıklarınızın (örneğin,) `Newtonsoft.Json`sisteminize yüklenmiş olduğunu onaylayın ve değilse bunları yükleyin. **Yüklü** sekme, sisteminizde yüklü olan NuGet paketlerini listeler. Burada `Newtonsoft.Json` listelenmemişse, **Gözat** sekmesini seçin ve arama kutusuna "Newtonsoft.Json" girin. `Newtonsoft.Json` **Install'u**seçmeden önce sağ bölmede projenizi seçin.

1. Sisteminizde zaten yüklüyse, `Newtonsoft.Json` **Projenizi Çözüm için Paketleri Yönet** sekmesinin sağ bölmesinde seçerek projenize ekleyin.

Üçüncü taraf bağımlılıkları olan çerçeveye bağımlı dağıtım, yalnızca üçüncü taraf bağımlılıkları kadar taşınabilirdir. Örneğin, bir üçüncü taraf kitaplığı yalnızca macOS'u destekliyorsa, uygulama Windows sistemlerine taşınabilir değildir. Bu, üçüncü taraf bağımlılığının kendisi yerel koda bağlıysa olur. Bunun iyi bir örneği [Kestrel sunucusudur,](/aspnet/core/fundamentals/servers/kestrel) [libuv](https://github.com/libuv/libuv)üzerinde yerli bir bağımlılık gerektirir. Bu tür üçüncü taraf bağımlılığı olan bir uygulama için bir FDD oluşturulduğunda, yayımlanan çıktı, yerel bağımlılığın desteklediği (ve NuGet paketinde bulunan) her [Runtime Tanımlayıcısı (RID)](../rid-catalog.md) için bir klasör içerir.

## <a name="self-contained-deployment-without-third-party-dependencies"></a><a name="simpleSelf"></a>Üçüncü taraf bağımlılıkları olmadan bağımsız dağıtım

Üçüncü taraf bağımlılıkları olmadan bağımsız bir dağıtım dağıtmak, projeyi oluşturmayı, *csproj* dosyasını değiştirmeyi, uygulamayı oluşturmayı, test etmeye ve yayımlamayı içerir. C# ile yazılmış basit bir örnek işlemi göstermektedir. Tıpkı çerçeveye bağımlı bir dağıtım da olduğu gibi projenizi oluşturarak, kodlayarak ve test ederek başlarsınız:

1. Projeyi oluşturun.

   **Dosya** > **Yeni** > **Proje'yi**seçin. Yeni **Proje** iletişim kutusunda, **yüklü** proje türleri bölmesinde dilinizin (C# veya Visual Basic) proje kategorilerini genişletin, **.NET Core'u**seçin ve ardından orta bölmedeki **Konsol Uygulaması (.NET Core)** şablonunu seçin. **Ad** metin kutusuna "SCD" gibi bir proje adı girin ve **Tamam** düğmesini seçin.

1. Uygulamanın kaynak kodunu ekleyin.

   Düzenleyicinizdeki *Program.cs* veya *Program.vb* dosyasını açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin. Kullanıcıdan metin girmesini ister ve kullanıcı tarafından girilen tek tek sözcükleri görüntüler. Giriş metnindeki `\w+` sözcükleri ayırmak için normal ifadeyi kullanır.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Genelleştirme değişmez modunu kullanmak isteyip istemediğinizi belirleyin.

   Özellikle uygulamanız Linux'u hedefliyorsa, [küreselleşme değişmez modundan](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)yararlanarak dağıtımınızın toplam boyutunu küçültebilirsiniz. Genelleştirme değişmez modu, genel olarak farkında olmayan ve biçimlendirme kurallarını, kasa konvansiyonlarını ve [değişken kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)dize karşılaştırma ve sıralama sırasını kullanabilen uygulamalar için yararlıdır.

   Değişmez modu etkinleştirmek **için, Solution Explorer'da**projenize (çözüm edeğil) sağ tıklayın ve **SCD.csproj'u Edit** veya **SCD.vbproj'u Edit'i**seçin. Ardından dosyaya aşağıdaki vurgulanmış satırları ekleyin:

   [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj?highlight=6-8)]

1. Uygulamanızın hata ayıklama yapısı oluşturun.

   **Yapı** > **Çözümünü**Seçin. Ayrıca Hata **Debug** > **Ayıklama Başlatma Hata Ayıklama'yı**seçerek uygulamanızın Hata Ayıklama oluşturma sını derleyebilir ve çalıştırabilirsiniz. Bu hata ayıklama adımı, ana bilgisayar platformunuzda çalışırken uygulamanızla ilgili sorunları belirlemenize olanak tanır. Yine de hedef platformlarınızın her birinde test etmek zorunda kalacak.

   Genelleştirme değişmez modunu etkinleştirdiyseniz, kültüre duyarlı verilerin yokluğunun uygulamanız için uygun olup olmadığını özellikle test edin.

Hata ayıklamayı tamamladıktan sonra, bağımsız dağıtımınızı yayımlayabilirsiniz:

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earlier"></a>[Visual Studio 15.6 ve önceki](#tab/vs156)

Programı debugged ve test ettikten sonra, hedeflenenekadar her platform için uygulamanızla dağıtılacak dosyaları oluşturun.

Uygulamanızı Visual Studio'dan yayınlamak için aşağıdakileri yapın:

1. Uygulamanızın hedefalacağı platformları tanımlayın.

   1. **Solution Explorer'da** projenize (çözüm değil) sağ tıklayın ve **SCD.csproj'u Edit'i**seçin.

   1. *csproj* `<PropertyGroup>` dosyanızın uygulamahedeflerinizi hedefleyen platformları tanımlayan bölümünde bir `<RuntimeIdentifiers>` etiket oluşturun ve hedeflediğiniz her platformun çalışma zamanı tanımlayıcısını (RID) belirtin. Ayrıca RID'leri ayırmak için bir yarı nokta eklemeniz gerekir. Çalışma zamanı tanımlayıcılarının listesi için [Runtime Tanımlayıcı kataloğuna](../rid-catalog.md) bakın.

   Örneğin, aşağıdaki örnek, uygulamanın 64 bit Windows 10 işletim sistemleri ve 64 bit OS X Sürüm 10.11 işletim sistemi üzerinde çalıştığını gösterir.

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   Öğe `<RuntimeIdentifiers>` `<PropertyGroup>` *csproj* dosyanızda bulunan herhangi bir içine gidebilirsiniz. Tam bir örnek *csproj* dosyası daha sonra bu bölümde görünür.

1. Uygulamanızı yayınlayın.

   Programı debugged ve test ettikten sonra, hedeflenenekadar her platform için uygulamanızla dağıtılacak dosyaları oluşturun.

   Uygulamanızı Visual Studio'dan yayınlamak için aşağıdakileri yapın:

      1. Uygulamanızın Sürüm (Hata Ayıklama yerine) sürümünü oluşturmak için çözüm yapılandırmasını araç çubuğunda **Hata Ayıklama'dan** **Sürüm'e** değiştirin.

      1. **Solution Explorer'da** projeye (çözüm değil) sağ tıklayın ve **Yayımla'yı**seçin.

      1. **Yayımla** sekmesinde **Yayımla'yı**seçin. Visual Studio, uygulamanızı oluşturan dosyaları yerel dosya sistemine yazar.

      1. **Yayımla** sekmesi artık tek bir profil, **FolderProfile**gösterir. Profilin yapılandırma ayarları sekmenin **Özet** bölümünde gösterilir. **Hedef Çalışma Zamanı** hangi çalışma zamanının yayımlandığını tanımlar ve Hedef **Konum,** bağımsız dağıtım dosyalarının nerede yazıldığını tanımlar.

      1. Visual Studio varsayılan olarak tüm yayımlanmış dosyaları tek bir dizine yazar. Kolaylık sağlamak için, her hedef çalışma zamanı için ayrı profiller oluşturmak ve yayımlanmış dosyaları platforma özgü bir dizine yerleştirmek en iyisidir. Bu, her hedef platform için ayrı bir yayımlama profili oluşturmayı içerir. Yani şimdi aşağıdakileri yaparak her platform için uygulama yeniden:

         1. **Yayımla** iletişim kutusunda **yeni profil oluştur'u** seçin.

         1. **Yayımlama hedef** iletişim kutusunda, klasör konumunu *bin\Release\PublishOutput\win10-x64*olarak **seçin'** i değiştirin. **Tamam'ı**seçin.

         1. Profiller listesindeki yeni profili **(FolderProfile1)** seçin ve **Hedef Çalışma Zamanı'nın** . `win10-x64` Değilse, **Ayarlar'ı**seçin. Profil **Ayarları** iletişim kutusunda, **Hedef Çalışma** `win10-x64` Süresini değiştirin ve **Kaydet'i**seçin. Aksi takdirde **Cancel**İptal et'i seçin.

         1. Uygulamanızı 64 bit Windows 10 platformları için yayımlamak için **Yayımla'yı** seçin.

         1. `osx.10.11-x64` Platform için bir profil oluşturmak için önceki adımları yeniden izleyin. **Hedef Konum** *bin\Release\PublishOutput\osx.10.11-x64*ve **Hedef Çalışma** `osx.10.11-x64`Zamanı . Visual Studio'nun bu profile atadığı ad **FolderProfile2'dir.**

      Her hedef konum, uygulamanızı başlatmak için gereken dosyaların (hem uygulama dosyalarınız hem de tüm .NET Core dosyaları) tüm dosya kümesini içerir.

Uygulamanızın dosyalarıyla birlikte, yayımlama işlemi, uygulamanızla ilgili hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayar. Dosya, öncelikle hata ayıklama özel durumları için yararlıdır. Uygulamanızın dosyalarıyla paketlememeyi seçebilirsiniz. Ancak, uygulamanızın Sürüm yapısıhatasını ayıklamak istemeniz durumunda bunu kaydetmeniz gerekir.

Yayımlanmış dosyaları istediğiniz şekilde dağıtın. Örneğin, bunları zip dosyasında paketleyebilir, basit `copy` bir komut kullanabilir veya istediğiniz herhangi bir yükleme paketiyle dağıtabilirsiniz.

Aşağıdaki bu proje için tam *csproj* dosyasıdır.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[Visual Studio 15.7 ve sonrası](#tab/vs157)

Programı debugged ve test ettikten sonra, hedeflenenekadar her platform için uygulamanızla dağıtılacak dosyaları oluşturun. Bu, her hedef platform için ayrı bir profil oluşturmayı içerir.

Uygulamanızın hedeflenen her platform için aşağıdakileri yapın:

1. Hedef platformunuz için bir profil oluşturun.

   Oluşturduğunuz ilk profil buysa, **Solution Explorer'daki** projeye (çözüm değil) sağ tıklayın ve **Yayımla'yı**seçin.

   Zaten bir profil oluşturduysanız, zaten açık değilse **Yayımla** iletişim kutusunu açmak için projeye sağ tıklayın. Ardından **Yeni Profil'i**seçin.

   Hedef **Yayımla** iletişim kutusunu seç açılır.

1. Visual Studio'nun başvurunuzu yayınladığı konumu seçin.

   Yalnızca tek bir platformda yayınlıyorsanız, klasör metin kutusu **seç'te** varsayılan değeri kabul edebilirsiniz; bu, uygulamanızın * \<>\bin\Release\netcoreapp2.1\publish* dizinine uygulamanızın çerçeveye bağlı dağıtımını yayımlar.

   Birden fazla platformda yayımlıyorsanız, hedef platformu tanımlayan bir dize ekine getirin. Örneğin, dosya yoluna "linux" dizesini eklerseniz, Visual Studio uygulamanızın çerçeveye bağlı dağıtımını * \<proje dizinine>\bin\Release\netcoreapp2.1\publish\linux* dizinine yayınlar.

1. **Yayımla** düğmesinin yanındaki açılır liste simgesini seçerek ve Profil Oluştur'u seçerek **profili oluşturun.** Ardından profili oluşturmak için **Profil Oluştur** düğmesini seçin.

1. Bağımsız bir dağıtım yayınladığınızı belirtin ve uygulamanızın hedefalacağı bir platform tanımlayın.

   1. **Yayımla** iletişim kutusunda, **Profil Ayarları** iletişim kutusunu açmak için **Yapıla** bağlantısını seçin.

   1. **Dağıtım Modu** liste kutusunda Kendi **Kendine Yeten'i** seçin.

   1. Hedef **Çalışma Zamanı** liste kutusunda, uygulamanızın hedeflenedığı platformlardan birini seçin.

   1. Değişikliklerinizi kabul etmek ve iletişim kutusunu kapatmak için **Kaydet'i** seçin.

1. Profilinize isim verebilirsiniz.

   1. Profilinize isim vermek için **Eylemler** > **Profilini Yeniden Adlandır'ı** seçin.

   2. Profilinize hedef platformu tanımlayan bir ad atayın ve ardından **Kaydet'i*seçin.

Uygulamanızın hedeflenebilen ek hedef platformlarını tanımlamak için bu adımları yineleyin.

Profillerinizi yapılandırıldınız ve artık uygulamanızı yayınlamaya hazırsınız. Bunu yapmak için:

   1. **Yayımla** penceresi şu anda açık değilse, **Solution Explorer'da** projeye (çözüm değil) sağ tıklayın ve **Yayımla'yı**seçin.

   2. Yayınlamak istediğiniz profili seçin, ardından **Yayımla'yı**seçin. Yayınlanacak her profil için bunu yapın.

   Her hedef konum (örneğimiz söz konusu olduğunda, bin\release\netcoreapp2.1\publish\\profil*adı,* uygulamanızı başlatmak için gereken dosyaların tamamını (hem uygulama dosyalarınız hem de tüm .NET Core dosyaları) içerir.

Uygulamanızın dosyalarıyla birlikte, yayımlama işlemi, uygulamanızla ilgili hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayar. Dosya, öncelikle hata ayıklama özel durumları için yararlıdır. Uygulamanızın dosyalarıyla paketlememeyi seçebilirsiniz. Ancak, uygulamanızın Sürüm yapısıhatasını ayıklamak istemeniz durumunda bunu kaydetmeniz gerekir.

Yayımlanmış dosyaları istediğiniz şekilde dağıtın. Örneğin, bunları zip dosyasında paketleyebilir, basit `copy` bir komut kullanabilir veya istediğiniz herhangi bir yükleme paketiyle dağıtabilirsiniz.

Aşağıdaki bu proje için tam *csproj* dosyasıdır.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Buna ek olarak, Visual Studio hedeflediğiniz her platform için ayrı bir yayımlama profili (.pubxml)\*oluşturur. Örneğin, linux profilimiz (linux.pubxml) için dosya aşağıdaki gibi görünür:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
https://go.microsoft.com/fwlink/?LinkID=208121.
-->
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <PublishDir>bin\Release\netcoreapp2.1\publish\linux</PublishDir>
    <RuntimeIdentifier>win-x86</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <_IsPortable>false</_IsPortable>
  </PropertyGroup>
</Project>
```

---

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Üçüncü taraf bağımlılıkları ile bağımsız dağıtım

Bir veya daha fazla üçüncü taraf bağımlılıkla bağımsız bir dağıtım dağıtmak, bağımlılıkların eklenmesini içerir. Uygulamanızı oluşturmadan önce aşağıdaki ek adımlar gereklidir:

1. Projenize bir NuGet paketine başvuru eklemek için **NuGet Paket Yöneticisi'ni** kullanın; ve paket sisteminizde zaten mevcut değilse, yükleyin. Paket yöneticisini açmak için, **Araçlar** > **NuGet Paket Yöneticisi** > **Çözüm için Paketleri Yönet'i**seçin.

1. Üçüncü taraf bağımlılıklarınızın (örneğin,) `Newtonsoft.Json`sisteminize yüklenmiş olduğunu onaylayın ve değilse bunları yükleyin. **Yüklü** sekme, sisteminizde yüklü olan NuGet paketlerini listeler. Burada `Newtonsoft.Json` listelenmemişse, **Gözat** sekmesini seçin ve arama kutusuna "Newtonsoft.Json" girin. `Newtonsoft.Json` **Install'u**seçmeden önce sağ bölmede projenizi seçin.

1. Sisteminizde zaten yüklüyse, `Newtonsoft.Json` **Projenizi Çözüm için Paketleri Yönet** sekmesinin sağ bölmesinde seçerek projenize ekleyin.

Bu proje için *csproj* dosyasının tamamı aşağıda veda edilmiştir:

# <a name="visual-studio-156-and-earlier"></a>[Visual Studio 15.6 ve önceki](#tab/vs156)

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

# <a name="visual-studio-157-and-later"></a>[Visual Studio 15.7 ve sonrası](#tab/vs157)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

---

Uygulamanızı dağıttığınızda, uygulamanızda kullanılan tüm üçüncü taraf bağımlılıkları da uygulama dosyalarınızda bulunur. Uygulamanın çalıştırıldığı sistemde üçüncü taraf kitaplıkları gerekmez.

Yalnızca, üçüncü taraf kitaplığı yla birlikte bağımsız bir dağıtımı bu kitaplık tarafından desteklenen platformlara dağıtabilirsiniz. Bu, daha önce yüklenmediği sürece yerel bağımlılıkların hedef platformda bulunamayacağı, çerçeveye bağımlı dağıtımınızda yerel bağımlılıklarla üçüncü taraf bağımlılıklara sahip olmaya benzer.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Çekirdek Uygulama Dağıtımı](index.md)
- [.NET Core Runtime Tanımlayıcı (RID) kataloğu](../rid-catalog.md)
