---
title: Visual Studio ile .NET Core uygulamaları dağıtma
description: Visual Studio ile .NET Core uygulaması dağıtmayı öğrenin.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 73eee58a3d11f2f898a6d57cb282ccf4e802cdca
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656605"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a>Visual Studio ile .NET Core uygulamaları dağıtma

Bir .NET Core uygulamasını, uygulama ikililerini içeren, ancak hedef sistemde .NET Core varlığına ya da hem uygulamanızı hem de .NET Core ikililerini içeren bir *bağımsız dağıtım*olarak, *çerçeveye bağlı bir dağıtım*olarak dağıtabilirsiniz. .NET Core uygulama dağıtımına genel bir bakış için bkz. [.NET Core uygulama dağıtımı](index.md).

Aşağıdaki bölümlerde, aşağıdaki dağıtım türlerini oluşturmak için Microsoft Visual Studio nasıl kullanılacağı gösterilmektedir:

- Çerçeveye bağımlı dağıtım
- Üçüncü taraf bağımlılıklarla çerçeveye bağımlı dağıtım
- Kendi kendine kapsanan dağıtım
- Üçüncü taraf bağımlılıklarla kendi kendine kapsanan dağıtım

.NET Core uygulamaları geliştirmek için Visual Studio 'Yu kullanma hakkında bilgi için bkz. [.NET Core Dependencies ve Requirements](../install/dependencies.md?pivots=os-windows).

## <a name="framework-dependent-deployment"></a>Çerçeveye bağımlı dağıtım

Bir üçüncü taraf bağımlılığı olmadan çerçeveye bağlı bir dağıtımı dağıtmak, uygulamayı oluşturma, test etme ve yayımlamayı içerir. C# dilinde yazılmış basit bir örnek süreci gösterir.

1. Projeyi oluşturun.

   **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunda, **yüklü** proje türleri bölmesinde dilinizin (C# veya Visual Basic) Proje kategorilerini genişletin, **.NET Core**' u seçin ve ardından orta bölmedeki **konsol uygulaması (.NET Core)** şablonunu seçin. **Ad** metin kutusuna "fdd" gibi bir proje adı girin. **Tamam** düğmesini seçin.

1. Uygulamanın kaynak kodunu ekleyin.

   Düzenleyicide *program.cs* veya *program. vb* dosyasını açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin. Kullanıcıdan metin girmesini ve Kullanıcı tarafından girilen tek tek kelimeleri görüntülediğini ister. `\w+`Giriş metnindeki sözcükleri ayırmak için normal ifadeyi kullanır.

   [!code-csharp[deployment#1](./snippets/deploy-with-vs/csharp/deployment-example.cs)]
   [!code-vb[deployment#1](./snippets/deploy-with-vs/vb/deployment-example.vb)]

1. Uygulamanızın hata ayıklama derlemesini oluşturun.

   Yapı **Build**  >  **Yapı çözümünü**seçin. Ayrıca, **hata**ayıklama  >  **başlatma hata ayıklamayı**seçerek uygulamanızın hata ayıklama derlemesini derleyip çalıştırabilirsiniz.

1. Uygulamanızı dağıtın.

   Programı hata ayıkladıktan ve test ettikten sonra, uygulamanızla birlikte dağıtılacak dosyaları oluşturun. Visual Studio 'dan yayımlamak için şunları yapın:

      1. Uygulamanızın bir sürümünü (hata ayıklama yerine) oluşturmak için, araç çubuğundaki çözüm yapılandırmasını **Hata Ayıkla** 'dan **Release** olarak değiştirin.

      1. **Çözüm Gezgini** ' de projeye (çözüme değil) sağ tıklayın ve **Yayımla**' yı seçin.

      1. **Yayımla** sekmesinde **Yayımla**' yı seçin. Visual Studio, uygulamanızı oluşturan dosyaları yerel dosya sistemine yazar.

      1. **Yayımla** sekmesinde artık tek bir profil, **folderprofile**gösterilmektedir. Profilin yapılandırma ayarları, sekmesinin **Özet** bölümünde gösterilir.

   Elde edilen dosyalar, `Publish` Windows 'da ve `publish` projenizin *.\bin\release\netcoreapp2.1* alt dizininin bir alt dizininde bulunan UNIX sistemlerinde adlı bir dizine yerleştirilir.

Yayımlama işlemi, uygulamanızın dosyalarıyla birlikte, uygulamanız hakkındaki hata ayıklama bilgilerini içeren bir program veritabanı (. pdb) dosyası yayar. Dosya öncelikle hata ayıklama özel durumları için yararlıdır. Bunu uygulamanızın dosyalarıyla paketlemeyi seçemezsiniz. Ancak, uygulamanızın yayın derlemesinde hata ayıklamak istediğiniz olaya kaydetmelisiniz.

Tüm uygulama dosyalarını dilediğiniz şekilde dağıtın. Örneğin, bunları bir ZIP dosyasında paketleyebilir, basit bir komut kullanabilir veya istediğiniz `copy` herhangi bir yükleme paketiyle dağıtabilirsiniz. Kullanıcılar yüklendikten sonra, `dotnet` komutunu kullanarak ve gibi uygulama dosya adını sağlayarak uygulamanızı yürütebilir `dotnet fdd.dll` .

Uygulama ikililerinin yanı sıra, yükleyicinizin de paylaşılan çerçeve yükleyicisini paketi veya uygulama yüklemesinin bir parçası olarak bir önkoşul olarak denetlemesi gerekir.  Paylaşılan Framework 'ün yüklenmesi, makine genelinde olduğundan yönetici/kök erişimi gerektirir.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Üçüncü taraf bağımlılıklarla çerçeveye bağımlı dağıtım

Bir veya daha fazla üçüncü taraf bağımlılığı olan çerçeveye bağlı bir dağıtımı dağıtmak, tüm bağımlılıkların projeniz için kullanılabilir olmasını gerektirir. Uygulamanızı derlemek için aşağıdaki ek adımlar gereklidir:

1. Projenize bir NuGet paketine başvuru eklemek için **NuGet paket yöneticisini** kullanın; paket sisteminizde zaten yoksa, uygulamayı da yükleyemezsiniz. Paket Yöneticisi 'ni açmak için **Araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet Paketlerini Yönet**' i seçin.

1. Üçüncü taraf bağımlılıklarınızın (örneğin, `Newtonsoft.Json` ) sisteminizde yüklü olduğunu ve yoksa, bunları yüklemesini doğrulayın. **Yüklü** sekme, sisteminizde yüklü olan NuGet paketlerini listeler. `Newtonsoft.Json`Orada listelenmemişse, araştır sekmesine tıklayın ve arama **Browse** kutusuna "Newtonsoft.Json" yazın. `Newtonsoft.Json`Sağ bölmedeki ve ' yi seçerek, **yüklemeyi**seçmeden önce projenizi seçin.

1. `Newtonsoft.Json`Zaten sisteminizde yüklüyse, **çözüm Için paketleri Yönet** sekmesinin sağ bölmesinde projenizi seçerek projenize ekleyin.

Üçüncü taraf bağımlılıkları olan çerçeveye bağlı bir dağıtım, yalnızca üçüncü taraf bağımlılıkları olarak taşınabilir. Örneğin, bir üçüncü taraf kitaplığı yalnızca macOS destekliyorsa, uygulama Windows sistemlerine taşınabilir değildir. Bu durum, üçüncü taraf bağımlılığının yerel koda bağlı olması durumunda meydana gelir. Bunun iyi bir örneği, [libuv](https://github.com/libuv/libuv)üzerinde yerel bir bağımlılık gerektiren [Kestrel sunucusudur](/aspnet/core/fundamentals/servers/kestrel). Bu tür üçüncü taraf bağımlılığı olan bir uygulama için FDD oluşturulduğunda, yayımlanan çıktı, yerel bağımlılığın desteklediği (ve NuGet paketinde bulunan) her [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) için bir klasör içerir.

## <a name="self-contained-deployment-without-third-party-dependencies"></a><a name="simpleSelf"></a> Üçüncü taraf bağımlılıkları olmayan kendi kendine kapsanan dağıtım

Bir üçüncü taraf bağımlılığı olmadan kendi içinde bir dağıtımı dağıtmak, projeyi oluşturma, *csproj* dosyasını değiştirme, uygulama oluşturma, test etme ve uygulamayı yayımlamayı kapsar. C# dilinde yazılmış basit bir örnek süreci gösterir. Yalnızca çerçeveye bağımlı bir dağıtımda olduğu gibi projenizi oluşturarak, kodlayarak ve test etmeye başlayabilirsiniz:

1. Projeyi oluşturun.

   **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunda, **yüklü** proje türleri bölmesinde dilinizin (C# veya Visual Basic) Proje kategorilerini genişletin, **.NET Core**' u seçin ve ardından orta bölmedeki **konsol uygulaması (.NET Core)** şablonunu seçin. **Ad** metin kutusuna "SCD" gibi bir proje adı girin ve **Tamam** düğmesini seçin.

1. Uygulamanın kaynak kodunu ekleyin.

   Düzenleyicinizde *program.cs* veya *program. vb* dosyasını açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin. Kullanıcıdan metin girmesini ve Kullanıcı tarafından girilen tek tek kelimeleri görüntülediğini ister. `\w+`Giriş metnindeki sözcükleri ayırmak için normal ifadeyi kullanır.

   [!code-csharp[deployment#1](./snippets/deploy-with-vs/csharp/deployment-example.cs)]
   [!code-vb[deployment#1](./snippets/deploy-with-vs/vb/deployment-example.vb)]

1. Genelleştirme sabit modunu kullanmak isteyip istemediğinizi belirleme.

   Özellikle uygulamanız Linux hedefliyorsa, [Genelleştirme sabit modundan](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)yararlanarak dağıtımınızın toplam boyutunu azaltabilirsiniz. Genelleştirme sabit modu, genel olarak uyumlu olmayan ve [sabit kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)biçimlendirme kurallarını, büyük/küçük harf kurallarını ve dize karşılaştırmayı ve sıralama düzenini kullanabilen uygulamalar için yararlıdır.

   Sabit modu etkinleştirmek için, **Çözüm Gezgini**' de projenize (çözüm değil) sağ tıklayın ve **scd. csproj Düzenle** ' yi seçin veya **scd. vbproj**' i düzenleyin. Ardından, aşağıdaki vurgulanmış satırları dosyaya ekleyin:

   [!code-xml[globalization-invariant-mode](./snippets/deploy-with-vs/xml/invariant.csproj?highlight=7-9)]

1. Uygulamanızın hata ayıklama derlemesini oluşturun.

   Yapı **Build**  >  **Yapı çözümünü**seçin. Ayrıca, **hata**ayıklama  >  **başlatma hata ayıklamayı**seçerek uygulamanızın hata ayıklama derlemesini derleyip çalıştırabilirsiniz. Bu hata ayıklama adımı, ana bilgisayar platformunda çalışırken uygulamanızdaki sorunları belirlemenize olanak sağlar. Yine de hedef Platformlarınızın her birinde test etmeniz gerekir.

   Genelleştirme sabit modunu etkinleştirdiyseniz, özellikle kültüre duyarlı verilerin yokluğunun uygulamanız için uygun olup olmadığını test ettiğinizden emin olun.

Hata ayıklamayı tamamladıktan sonra, kendi içindeki dağıtımınızı yayımlayabilirsiniz:

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earlier"></a>[Visual Studio 15,6 ve öncesi](#tab/vs156)

Programı hata ayıkladıktan ve test ettikten sonra, hedeflediği her platform için uygulamanıza dağıtılacak dosyaları oluşturun.

Uygulamanızı Visual Studio 'dan yayımlamak için şunları yapın:

1. Uygulamanızın hedeflenecek platformları tanımlayın.

   1. **Çözüm Gezgini** ' de projenize (çözüm değil) sağ tıklayın ve **scd. csproj öğesini Düzenle**' yi seçin.

   1. `<RuntimeIdentifiers>` `<PropertyGroup>` *Csproj* dosyanızın bölümünde uygulamanızın hedeflediği platformları tanımlayan bir etiket oluşturun ve hedeflediğiniz her platformun çalışma zamanı tanımlayıcısını (RID) belirtin. Ayrıca, RIDs 'yi ayırmak için noktalı virgül eklemeniz gerekir. Çalışma zamanı tanımlayıcılarının listesi için bkz. [Runtime Identifier Catalog](../rid-catalog.md) .

   Örneğin, aşağıdaki örnek, uygulamanın 64 bitlik Windows 10 işletim sistemleri ve 64 bit işletim sistemi X sürümü 10,11 işletim sisteminde çalıştığını gösterir.

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   `<RuntimeIdentifiers>`Öğesi, `<PropertyGroup>` *csproj* dosyanızda sahip olduğunuz herhangi birine gidebilir. Bu bölümde daha sonra bir örnek *csproj* dosyası belirir.

1. Uygulamanızı yayımlayın.

   Programı hata ayıkladıktan ve test ettikten sonra, hedeflediği her platform için uygulamanıza dağıtılacak dosyaları oluşturun.

   Uygulamanızı Visual Studio 'dan yayımlamak için şunları yapın:

      1. Uygulamanızın bir sürümünü (hata ayıklama yerine) oluşturmak için, araç çubuğundaki çözüm yapılandırmasını **Hata Ayıkla** 'dan **Release** olarak değiştirin.

      1. **Çözüm Gezgini** ' de projeye (çözüme değil) sağ tıklayın ve **Yayımla**' yı seçin.

      1. **Yayımla** sekmesinde **Yayımla**' yı seçin. Visual Studio, uygulamanızı oluşturan dosyaları yerel dosya sistemine yazar.

      1. **Yayımla** sekmesinde artık tek bir profil, **folderprofile**gösterilmektedir. Profilin yapılandırma ayarları, sekmesinin **Özet** bölümünde gösterilir. **hedef çalışma zamanı** hangi çalışma zamanının yayımlandığını tanımlar ve **hedef konum** , kendinden bağımsız dağıtım dosyalarının yazıldığı yeri belirler.

      1. Visual Studio varsayılan olarak tüm yayımlanan dosyaları tek bir dizine yazar. Kolaylık olması için, her bir hedef çalışma zamanı için ayrı profiller oluşturmak ve yayımlanan dosyaları platforma özgü bir dizine yerleştirmek en iyisidir. Bu, her hedef platform için ayrı bir yayımlama profili oluşturmayı içerir. Bu nedenle, şimdi aşağıdakileri yaparak her platform için uygulamayı yeniden oluşturun:

         1. **Yayımla** iletişim kutusunda **Yeni Profil oluştur** ' u seçin.

         1. **Bir yayımlama hedefi seç** iletişim kutusunda, **klasör seçin** konumunu *Bin\release\publishoutput\win10-x64*olarak değiştirin. **Tamam**’ı seçin.

         1. Profiller listesinden yeni profili (**FolderProfile1**) seçin ve **hedef çalışma zamanının** olduğundan emin olun `win10-x64` . Değilse, **Ayarlar**' ı seçin. **Profil ayarları** Iletişim kutusunda **hedef çalışma zamanını** olarak değiştirip Kaydet ' i `win10-x64` seçin **Save**. Aksi takdirde **iptal**' i seçin.

         1. Uygulamanızı 64 bitlik Windows 10 platformları için yayımlamak üzere **Yayımla** ' yı seçin.

         1. Platform için bir profil oluşturmak üzere önceki adımları tekrar izleyin `osx.10.11-x64` . **Hedef konum** *Bin\Release\PublishOutput\osx.10.11-x64*ve **hedef çalışma zamanı** `osx.10.11-x64` . Visual Studio 'Nun bu profile atadığı ad **FolderProfile2**' dir.

      Her hedef konum, uygulamanızı başlatmak için gereken tüm dosya (hem uygulama dosyalarınız hem de tüm .NET Core dosyaları) kümesini içerir.

Yayımlama işlemi, uygulamanızın dosyalarıyla birlikte, uygulamanız hakkındaki hata ayıklama bilgilerini içeren bir program veritabanı (. pdb) dosyası yayar. Dosya öncelikle hata ayıklama özel durumları için yararlıdır. Bunu uygulamanızın dosyalarıyla paketlemeyi seçemezsiniz. Ancak, uygulamanızın yayın derlemesinde hata ayıklamak istediğiniz olaya kaydetmelisiniz.

Yayınlanan dosyaları dilediğiniz gibi dağıtın. Örneğin, bunları bir ZIP dosyasında paketleyebilir, basit bir komut kullanabilir veya istediğiniz `copy` herhangi bir yükleme paketiyle dağıtabilirsiniz.

Bu proje için tüm *csproj* dosyası aşağıda verilmiştir.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[Visual Studio 15,7 ve üzeri](#tab/vs157)

Programı hata ayıkladıktan ve test ettikten sonra, hedeflediği her platform için uygulamanıza dağıtılacak dosyaları oluşturun. Bu, her hedef platform için ayrı bir profil oluşturmayı içerir.

Uygulamanızın hedeflediği her platform için aşağıdakileri yapın:

1. Hedef platformunuz için bir profil oluşturun.

   Oluşturduğunuz ilk profildir, **Çözüm Gezgini** ' de projeye (çözüme değil) sağ tıklayın ve **Yayımla**' yı seçin.

   Zaten bir profil oluşturduysanız, zaten açık değilse **Yayımla** iletişim kutusunu açmak için projeye sağ tıklayın. Ardından **Yeni profil**' i seçin.

   **Bir Yayımla hedefi seç** iletişim kutusu açılır.

1. Visual Studio 'Nun uygulamanızı yayımlayıp konumunu seçin.

   Yalnızca tek bir platforma yayımlıyorsanız, **klasör seçin** metin kutusunda varsayılan değeri kabul edebilirsiniz; Bu, uygulamanızın çerçeveye bağlı dağıtımını * \<project-directory> \Bin\release\netcoreapp2,\publish* dizinine yayınlar.

   Birden fazla platforma yayımlıyorsanız, hedef platformu tanımlayan bir dize ekleyin. Örneğin, "Linux" dizesini dosya yoluna eklerseniz, Visual Studio uygulamanızın çerçeveye bağlı dağıtımını * \<project-directory> \Bin\release\netcoreapp2,\publish\linux* dizinine yayınlar.

1. **Yayımla** düğmesinin yanındaki açılan liste simgesini seçerek profili oluşturun ve **Profil oluştur**' a seçin. Sonra profili oluşturmak için **Profil oluştur** düğmesini seçin.

1. Kendinden bağımsız bir dağıtım yayımladığını ve uygulamanızın hedeflenecek bir platform tanımlacağınızı belirtin.

   1. **Yayımla** Iletişim kutusunda **profil ayarları** Iletişim kutusunu açmak için **Yapılandır** bağlantısını seçin.

   1. **Dağıtım modu** liste kutusunda **kendine ait** ' ı seçin.

   1. **Hedef çalışma zamanı** liste kutusunda, uygulamanızın hedeflediği platformlardan birini seçin.

   1. Değişikliklerinizi kabul etmek ve iletişim kutusunu kapatmak için **Kaydet** ' i seçin.

1. Profilinizi adlandırın.

   1. **Actions**  >  Profilinizi adlandırmak için eylemler**Yeniden Adlandır** ' ı seçin.

   2. Profilinize hedef platformu tanımlayan bir ad atayın ve ardından **Kaydet*' i seçin.

Uygulamanızın hedeflediği ek hedef platformları tanımlamak için bu adımları tekrarlayın.

Profillerinizi yapılandırdınız ve şimdi uygulamanızı yayımlamaya hazırsınız. Bunu yapmak için:

   1. **Yayımla** penceresi açık değilse, **Çözüm Gezgini** ' de projeye (çözüm değil) sağ tıklayın ve **Yayımla**' yı seçin.

   2. Yayınlamak istediğiniz profili seçin ve ardından **Yayımla**' yı seçin. Bu, yayımlanacak her profil için bunu yapın.

   Her hedef konum (örneğimizde, bin\release\netcoreapp2,\publish \\ *profile-Name* , uygulamanızı başlatmak için gereken tam dosya kümesini (hem uygulama dosyalarınız hem de tüm .NET Core dosyalarınız) içerir.

Yayımlama işlemi, uygulamanızın dosyalarıyla birlikte, uygulamanız hakkındaki hata ayıklama bilgilerini içeren bir program veritabanı (. pdb) dosyası yayar. Dosya öncelikle hata ayıklama özel durumları için yararlıdır. Bunu uygulamanızın dosyalarıyla paketlemeyi seçemezsiniz. Ancak, uygulamanızın yayın derlemesinde hata ayıklamak istediğiniz olaya kaydetmelisiniz.

Yayınlanan dosyaları dilediğiniz gibi dağıtın. Örneğin, bunları bir ZIP dosyasında paketleyebilir, basit bir komut kullanabilir veya istediğiniz `copy` herhangi bir yükleme paketiyle dağıtabilirsiniz.

Bu proje için tüm *csproj* dosyası aşağıda verilmiştir.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Ayrıca, Visual Studio, hedeflediğiniz her platform için ayrı bir yayımlama profili ( \* . pubxml) oluşturur. Örneğin, Linux profilimiz için dosya (Linux. pubxml) aşağıdaki gibi görünür:

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

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Üçüncü taraf bağımlılıklarla kendi kendine kapsanan dağıtım

Bir veya daha fazla üçüncü taraf bağımlılığı ile kendi içindeki bir dağıtımı dağıtmak, bağımlılıkların eklenmesini içerir. Uygulamanızı derlemek için aşağıdaki ek adımlar gereklidir:

1. Projenize bir NuGet paketine başvuru eklemek için **NuGet paket yöneticisini** kullanın; paket sisteminizde zaten yoksa, uygulamayı da yükleyemezsiniz. Paket Yöneticisi 'ni açmak için **Araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet Paketlerini Yönet**' i seçin.

1. Üçüncü taraf bağımlılıklarınızın (örneğin, `Newtonsoft.Json` ) sisteminizde yüklü olduğunu ve yoksa, bunları yüklemesini doğrulayın. **Yüklü** sekme, sisteminizde yüklü olan NuGet paketlerini listeler. `Newtonsoft.Json`Orada listelenmemişse, araştır sekmesine tıklayın ve arama **Browse** kutusuna "Newtonsoft.Json" yazın. `Newtonsoft.Json`Sağ bölmedeki ve ' yi seçerek, **yüklemeyi**seçmeden önce projenizi seçin.

1. `Newtonsoft.Json`Zaten sisteminizde yüklüyse, **çözüm Için paketleri Yönet** sekmesinin sağ bölmesinde projenizi seçerek projenize ekleyin.

Bu proje için tüm *csproj* dosyası aşağıda verilmiştir:

# <a name="visual-studio-156-and-earlier"></a>[Visual Studio 15,6 ve öncesi](#tab/vs156)

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

# <a name="visual-studio-157-and-later"></a>[Visual Studio 15,7 ve üzeri](#tab/vs157)

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

Uygulamanızı dağıttığınızda, uygulamanızda kullanılan tüm üçüncü taraf bağımlılıkları da uygulama dosyalarınıza dahil edilir. Uygulamanın üzerinde çalıştığı sistemde üçüncü taraf kitaplıkları gerekli değildir.

Bu kitaplık tarafından desteklenen platformlar için, üçüncü taraf bir kitaplıkla yalnızca kendi içindeki bir dağıtımı dağıtabilirsiniz. Bu, daha önce yüklenmedikleri müddetçe, yerel bağımlılıkların hedef platformda mevcut olmaması durumunda, çerçeveye bağımlı dağıtımda yerel bağımlılıklarla üçüncü taraf bağımlılıklara sahip olmaya benzer.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core uygulama dağıtımı](index.md)
- [.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu](../rid-catalog.md)
