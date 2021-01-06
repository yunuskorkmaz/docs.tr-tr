---
title: WCF geliştiricileri için yeni bir ASP.NET Core gRPC projesi oluşturma-gRPC
description: Visual Studio veya komut satırını kullanarak bir gRPC projesi oluşturmayı öğrenin.
ms.date: 12/15/2020
ms.openlocfilehash: 960725a9507797f43b2c15283e384b0ad827c2b1
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938667"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>Yeni bir ASP.NET Core gRPC projesi oluşturma

.NET SDK, `dotnet` komut satırından projeler ve çözümler oluşturmanıza ve yönetmenize olanak tanıyan güçlü BIR CLI aracı ile gelir. SDK, Visual Studio ile yakından tümleşiktir, böylece her şey tanıdık grafik kullanıcı arabirimi aracılığıyla da kullanılabilir. Bu bölümde, yeni bir ASP.NET Core gRPC projesi oluşturmanın her iki yolu da gösterilmektedir.

## <a name="create-the-project-by-using-visual-studio"></a>Visual Studio 'Yu kullanarak proje oluşturma

> [!IMPORTANT]
> ASP.NET Core 5,0 uygulaması geliştirmek için, **ASP.net ve Web geliştirme** iş yükü yüklüyken Visual Studio 2019 sürüm 16,3 veya sonraki bir sürüme sahip olmanız gerekir.

*Boş çözüm* şablonundan **tradersys** adlı boş bir çözüm oluşturun. Adlı bir çözüm klasörü ekleyin `src` . Ardından, klasöre sağ tıklayıp   >  **Yeni proje** Ekle ' yi seçin. `grpc`Şablon arama kutusuna girin ve adlı bir proje şablonu görmeniz gerekir `gRPC Service` .

![Yeni Proje Ekle iletişim kutusunun ekran görüntüsü](media/create-project/new-grpc-project.png)

**Yeni projeyi Yapılandır** iletişim kutusunu kullanmaya devam etmek için **İleri ' yi** seçin. Projeyi adlandırın `TraderSys.Portfolios` ve `src` **konuma** bir alt dizin ekleyin.

![Yeni projenizi yapılandırma iletişim kutusunun ekran görüntüsü](media/create-project/configure-project.png)

**Yeni bir gRPC hizmeti oluştur** iletişim kutusuna devam etmek için **İleri ' yi** seçin.

![Yeni bir gRPC hizmeti oluştur iletişim kutusunun ekran görüntüsü](media/create-project/create-new-grpc-service-v2.png)

Mevcut olduğunda, hizmet oluşturma için sınırlı seçenekleriniz vardır. Docker daha sonra kullanıma sunulacaktır, bu nedenle şimdilik bu seçeneği işaretsiz bırakın. **Oluştur**' u seçmeniz yeterlidir. İlk ASP.NET Core 5,0 gRPC projeniz oluşturulur ve çözüme eklenir. İle çalışma hakkında bilgi almak istemiyorsanız `dotnet CLI` [örnek kodu Temizleme](#clean-up-the-example-code) bölümüne atlayın.

## <a name="create-the-project-by-using-the-net-cli"></a>.NET CLı kullanarak projeyi oluşturma

Bu bölümde, komut satırından çözümlerin ve projelerin oluşturulması ele alınmaktadır.

Aşağıdaki komutta gösterildiği gibi çözümü oluşturun. `-o`(Veya `--output` ) bayrağı, zaten mevcut değilse geçerli dizinde oluşturulan çıkış dizinini belirtir. Çözüm, şu dizinle aynı ada sahip: `TraderSys.sln` . `-n`(Veya) bayrağını kullanarak farklı bir ad sağlayabilirsiniz `--name` .

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 5,0, gRPC Hizmetleri için bir CLı şablonuyla birlikte gelir. Bu şablonu kullanarak yeni projeyi oluşturun ve bunu `src` ASP.NET Core projeler için geleneksel olarak bir alt dizine ekleyin. , `TraderSys.Portfolios.csproj` Bayrağıyla farklı bir ad belirtmediğiniz müddetçe, proje dizinden () sonra adlandırılır `-n` .

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

Son olarak, komutunu kullanarak projeyi çözüme ekleyin `dotnet sln` :

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> Belirli dizin yalnızca tek bir dosya içerdiğinden, `.csproj` yazmayı kaydetmek için yalnızca dizini belirtebilirsiniz.

Bu çözümü artık Visual Studio 2019, Visual Studio Code veya tercih ettiğiniz herhangi bir düzenleyicide açabilirsiniz.

## <a name="clean-up-the-example-code"></a>Örnek kodu Temizleme

Artık, kitapta daha önce gözden geçirilmiş olan gRPC şablonunu kullanarak bir örnek hizmet oluşturdunuz. Bu kod, hisse senedi ortamımızda yararlı değildir, bu nedenle ilk projemizdeki şeyleri düzenliyoruz.

### <a name="rename-and-edit-the-proto-file"></a>Proto dosyasını yeniden adlandırma ve düzenleme

Devam edin ve `Protos/greet.proto` dosyayı olarak yeniden adlandırın `Protos/portfolios.proto` ve Düzenleyicinizde açın. Satırdan sonraki her şeyi silin `package` . Ardından, `option csharp_namespace` `package` ve adlarını değiştirin `service` ve varsayılan `SayHello` hizmeti kaldırın. Kod artık aşağıdakine benzer şekilde görünür:

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> Şablon, `Protos` Varsayılan olarak ad alanı bölümünü eklemez, ancak eklemek, gRPC tarafından oluşturulan sınıfların ve kendi sınıflarınızın kodunuzda açık bir şekilde ayrılmış olmasını kolaylaştırır.

`greet.proto`Dosyayı Visual Studio gibi tümleşik bir geliştirme ortamında (IDE) yeniden adlandırırsanız, bu dosyanın bir başvurusu dosyada otomatik olarak güncelleştirilir `.csproj` . Ancak Visual Studio Code gibi bazı başka düzenleyicide bu başvuru otomatik olarak güncellenmez, bu nedenle proje dosyasını el ile düzenlemeniz gerekir.

GRPC derleme hedeflerinde, `Protobuf` hangi `.proto` dosyaların derlenmesi gerektiğini ve hangi kod üretimi gerektiğini (yani, "sunucu" veya "istemci") belirtmenize imkan tanıyan bir öğe öğesi vardır.

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>Sınıfı yeniden adlandır `GreeterService`

`GreeterService`Sınıfı `Services` klasöründe bulunur ve öğesinden devralır `Greeter.GreeterBase` . Olarak yeniden adlandırın `PortfolioService` ve temel sınıfını olarak değiştirin `Portfolios.PortfoliosBase` . Yöntemleri silin `override` .

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

`GreeterService`Sınıfında yönteminde sınıfına bir başvuru vardı `Configure` `Startup` . Sınıfı yeniden adlandırmak için yeniden düzenleme kullandıysanız, bu başvurunun otomatik olarak güncelleştirilmiş olması gerekir. Ancak, yapmadıysanız, el ile düzenlemeniz gerekir.

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

Sonraki bölümde, bu yeni hizmete işlevsellik ekleyeceğiz.

>[!div class="step-by-step"]
>[Önceki](migrate-wcf-to-grpc.md) 
> [Sonraki](migrate-request-reply.md)
