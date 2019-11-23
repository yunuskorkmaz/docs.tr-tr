---
title: WCF geliştiricileri için yeni bir ASP.NET Core gRPC projesi oluşturma-gRPC
description: Visual Studio kullanarak veya komut satırından bir gRPC projesi oluşturmayı öğrenin.
ms.date: 09/02/2019
ms.openlocfilehash: 992c3f57be25ae2517d41437170dc287f58934b6
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967888"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>Yeni bir ASP.NET Core gRPC projesi oluşturma

.NET Core, komut satırından projeler ve çözümler oluşturmanıza ve yönetmenize olanak tanıyan güçlü bir CLı aracı olan `dotnet`gelir. Araç Visual Studio ile yakından tümleşiktir, bu nedenle her şey tanıdık GUI arabirimi aracılığıyla da kullanılabilir. Bu bölümde, yeni bir ASP.NET Core gRPC projesi oluşturmak için her iki yol da gösterilir: ilk olarak Visual Studio ve sonra .NET Core CLI.

## <a name="create-the-project-using-visual-studio"></a>Visual Studio 'Yu kullanarak proje oluşturma

> [!IMPORTANT]
> ASP.NET Core 3,0 uygulaması geliştirmek için, **ASP.net ve Web geliştirme** iş yükünün yüklü olduğu Visual Studio 2019,3 veya üzeri bir sürüme sahip olmanız gerekir.

*Boş çözüm* şablonundan **tradersys** adlı boş bir çözüm oluşturun. `src`adlı bir çözüm klasörü ekleyin, sonra klasöre sağ tıklayın ve bağlam menüsünden **yeni > proje** **Ekle** ' yi seçin. Şablon arama kutusuna `grpc` girin ve `gRPC Service`adlı bir proje şablonu görmeniz gerekir.

![GRPC hizmeti proje şablonunu gösteren yeni proje iletişim kutusu Ekle](media/create-project/new-grpc-project.png)

**Projeyi Yapılandır** iletişim kutusuna devam etmek için **İleri** ' ye tıklayın ve proje `TraderSys.Portfolios`olarak adlandırın ve **konuma**bir `src` alt dizini ekleyin.

![Proje yapılandırma iletişim kutusu](media/create-project/configure-project.png)

**Yeni gRPC projesi** iletişim kutusuna devam etmek için **İleri** ' ye tıklayın.

![Yeni gRPC proje iletişim kutusu](media/create-project/create-new-grpc-service.png)

Mevcut olduğunda, hizmet oluşturma için sınırlı sayıda seçenek vardır. Docker daha sonra kitapta kullanıma sunulacaktır, bu nedenle bu onay kutusunu şimdilik işaretsiz bırakın ve **Oluştur**' a tıklayın. İlk ASP.NET Core 3,0 gRPC projeniz oluşturulur ve çözüme eklenir. `dotnet CLI`çalışma hakkında daha fazla bilgi almak istemiyorsanız [örnek kodu Temizleme](#clean-up-the-example-code) bölümüne atlayın.

## <a name="create-the-project-using-the-net-core-cli"></a>.NET Core CLI kullanarak proje oluşturun

Bu bölümde, komut satırından çözümlerin ve projelerin oluşturulması ele alınmaktadır.

Çözümü aşağıda gösterildiği gibi oluşturun. `-o` (veya `--output`) bayrağı, mevcut değilse geçerli dizinde oluşturulacak çıkış dizinini belirtir. Çözüme, dizinle aynı ad verilecek, yani `TraderSys.sln`. `-n` (veya `--name`) bayrağını kullanarak farklı bir ad sağlayabilirsiniz.

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 3,0, gRPC Hizmetleri için bir CLı şablonuyla birlikte gelir. Bu şablonu kullanarak yeni projeyi oluşturun ve ASP.NET Core projelerin kuralı olarak bir `src` alt dizinine yerleştirin. `-n` bayrağıyla farklı bir ad belirtmediğiniz müddetçe, proje dizin (yani `TraderSys.Portfolios.csproj`) sonra adlandırılır.

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

Son olarak, `dotnet sln` komutunu kullanarak projeyi çözüme ekleyin.

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> Verilen dizin yalnızca tek bir `.csproj` dosyası içerdiğinden, yazmak için yalnızca dizini belirterek kazanabilirsiniz.

Bu çözümü artık Visual Studio 2019, Visual Studio Code veya tercih ettiğiniz herhangi bir düzenleyicide açabilirsiniz.

## <a name="clean-up-the-example-code"></a>Örnek kodu Temizleme

Artık, kitapta daha önce gözden geçirilmiş olan gRPC şablonunu kullanarak bir örnek hizmet oluşturdunuz. Bu, hisse senedi ticari bağlamımızda yararlı değildir, bu nedenle ilk projemizdeki şeyleri düzenliyoruz.

### <a name="rename-and-edit-the-proto-file"></a>Proto dosyasını yeniden adlandırma ve düzenleme

Devam edin ve `Protos/greet.proto` dosyayı `Protos/portfolios.proto` olarak yeniden adlandırın ve Düzenleyicinizde açın. `package` satırdan sonra her şeyi silin, sonra `option csharp_namespace`, `package` ve `service` adlarını değiştirin ve varsayılan `SayHello` hizmetini kaldırın. böylece kod şöyle görünür.

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

### <a name="rename-the-greeterservice-class"></a>GreeterService sınıfını yeniden adlandırma

`GreeterService` sınıfı `Services` klasöründedir ve `Greeter.GreeterBase`devralır. `PortfolioService` olarak yeniden adlandırın ve temel sınıfı `Portfolios.PortfoliosBase`olacak şekilde değiştirin. `override` yöntemlerini silin.

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
