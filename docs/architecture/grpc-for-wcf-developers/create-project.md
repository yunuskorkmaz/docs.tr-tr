---
title: WCF geliştiricileri için yeni bir ASP.NET Core gRPC projesi oluşturma-gRPC
description: Visual Studio veya komut satırını kullanarak bir gRPC projesi oluşturmayı öğrenin.
ms.date: 09/02/2019
ms.openlocfilehash: ea6d7658404f61fedb25d7de7ddedb7c51437383
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711443"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>Yeni bir ASP.NET Core gRPC projesi oluşturma

.NET Core SDK, komut satırından projeler ve çözümler oluşturmanıza ve yönetmenize olanak tanıyan güçlü bir CLı aracı `dotnet`sunar. SDK, Visual Studio ile yakından tümleşiktir, böylece her şey tanıdık grafik kullanıcı arabirimi aracılığıyla da kullanılabilir. Bu bölümde, yeni bir ASP.NET Core gRPC projesi oluşturmanın her iki yolu da gösterilmektedir.

## <a name="create-the-project-by-using-visual-studio"></a>Visual Studio 'Yu kullanarak proje oluşturma

> [!IMPORTANT]
> ASP.NET Core 3,0 uygulaması geliştirmek için, **ASP.net ve Web geliştirme** iş yükü yüklüyken Visual Studio 2019 16,3 veya sonraki bir sürüme sahip olmanız gerekir.

*Boş çözüm* şablonundan **tradersys** adlı boş bir çözüm oluşturun. `src`adlı bir çözüm klasörü ekleyin. Ardından, klasöre sağ tıklayıp > **Yeni proje** **Ekle** ' yi seçin. Şablon arama kutusuna `grpc` girin ve `gRPC Service`adlı bir proje şablonu görmeniz gerekir.

![Yeni Proje Ekle iletişim kutusunun ekran görüntüsü](media/create-project/new-grpc-project.png)

**Yeni projeyi Yapılandır** iletişim kutusunu kullanmaya devam etmek için **İleri ' yi** seçin. Projeyi `TraderSys.Portfolios`olarak adlandırın ve **konuma**bir `src` alt dizini ekleyin.

![Yeni projenizi yapılandırma iletişim kutusunun ekran görüntüsü](media/create-project/configure-project.png)

**Yeni bir gRPC hizmeti oluştur** iletişim kutusuna devam etmek için **İleri ' yi** seçin.

![Yeni bir gRPC hizmeti oluştur iletişim kutusunun ekran görüntüsü](media/create-project/create-new-grpc-service.png)

Mevcut olduğunda, hizmet oluşturma için sınırlı seçenekleriniz vardır. Docker daha sonra kullanıma sunulacaktır, bu nedenle şimdilik bu seçeneği işaretsiz bırakın. **Oluştur**' u seçmeniz yeterlidir. İlk ASP.NET Core 3,0 gRPC projeniz oluşturulur ve çözüme eklenir. `dotnet CLI`çalışma hakkında daha fazla bilgi almak istemiyorsanız [örnek kodu Temizleme](#clean-up-the-example-code) bölümüne atlayın.

## <a name="create-the-project-by-using-the-net-core-cli"></a>.NET Core CLI kullanarak proje oluşturun

Bu bölümde, komut satırından çözümlerin ve projelerin oluşturulması ele alınmaktadır.

Aşağıdaki komutta gösterildiği gibi çözümü oluşturun. `-o` (veya `--output`) bayrağı, zaten mevcut değilse geçerli dizinde oluşturulan çıkış dizinini belirtir. Çözüm şu dizinle aynı ada sahip: `TraderSys.sln`. `-n` (veya `--name`) bayrağını kullanarak farklı bir ad sağlayabilirsiniz.

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 3,0, gRPC Hizmetleri için bir CLı şablonuyla birlikte gelir. Bu şablonu kullanarak yeni projeyi oluşturun ve ASP.NET Core projeler için geleneksel olarak bir `src` alt dizinine ekleyin. `-n` bayrağıyla farklı bir ad belirtmediğiniz müddetçe, proje dizinden (`TraderSys.Portfolios.csproj`) sonra adlandırılır.

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

Son olarak, `dotnet sln` komutunu kullanarak projeyi çözüme ekleyin:

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> Belirli dizin yalnızca tek bir `.csproj` dosyası içerdiğinden, yazmayı kaydetmek için yalnızca dizini belirtebilirsiniz.

Bu çözümü artık Visual Studio 2019, Visual Studio Code veya tercih ettiğiniz herhangi bir düzenleyicide açabilirsiniz.

## <a name="clean-up-the-example-code"></a>Örnek kodu Temizleme

Artık, kitapta daha önce gözden geçirilmiş olan gRPC şablonunu kullanarak bir örnek hizmet oluşturdunuz. Bu, hisse senedi ticari bağlamımızda yararlı değildir, bu nedenle ilk projemizdeki şeyleri düzenliyoruz.

### <a name="rename-and-edit-the-proto-file"></a>Proto dosyasını yeniden adlandırma ve düzenleme

Devam edin ve `Protos/greet.proto` dosyayı `Protos/portfolios.proto`olarak yeniden adlandırın ve Düzenleyicinizde açın. `package` satırdan sonra her şeyi silin. `option csharp_namespace`, `package` ve `service` adlarını değiştirin ve varsayılan `SayHello` hizmetini kaldırın. Kod artık aşağıdakine benzer şekilde görünür:

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> Şablon, varsayılan olarak `Protos` ad alanı bölümünü eklemez, ancak eklemek, gRPC tarafından oluşturulan sınıfların ve kendi sınıflarınızın kodunuzda açıkça ayrılabilmesini kolaylaştırır.

Visual Studio gibi tümleşik bir geliştirme ortamında (IDE) `greet.proto` dosyasını yeniden adlandırırsanız, bu dosyaya yönelik bir başvuru `.csproj` dosyasında otomatik olarak güncelleştirilir. Ancak Visual Studio Code gibi bazı başka düzenleyicide bu başvuru otomatik olarak güncellenmez, bu nedenle proje dosyasını el ile düzenlemeniz gerekir.

GRPC derleme hedefleri ' nde, hangi `.proto` dosyalarının derlenmesi gerektiğini ve hangi kod üretimi (yani "sunucu" veya "Istemci") gerektiğini belirtmenize olanak tanıyan bir `Protobuf` öğe öğesi vardır.

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>`GreeterService` sınıfını yeniden adlandırma

`GreeterService` sınıfı `Services` klasöründedir ve `Greeter.GreeterBase`devralır. `PortfolioService`olarak yeniden adlandırın ve temel sınıfı `Portfolios.PortfoliosBase`olacak şekilde değiştirin. `override` yöntemlerini silin.

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

`Startup` sınıfındaki `Configure` yönteminde `GreeterService` sınıfına bir başvuru vardı. Sınıfı yeniden adlandırmak için yeniden düzenleme kullandıysanız, bu başvurunun otomatik olarak güncelleştirilmiş olması gerekir. Ancak, yapmadıysanız, el ile düzenlemeniz gerekir.

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
>[İleri](migrate-request-reply.md)
