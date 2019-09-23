---
title: WCF geliştiricileri için yeni bir ASP.NET Core gRPC projesi oluşturma-gRPC
description: Visual Studio kullanarak veya komut satırından bir gRPC projesi oluşturmayı öğrenin.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a0fcc3f9c4e32e87260a6bc79205c909ea3800e0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184570"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>Yeni bir ASP.NET Core gRPC projesi oluşturma

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

.NET Core, komut satırından projeler ve çözümler oluşturmanıza `dotnet`ve yönetmenize olanak tanıyan güçlü bir CLI aracı ile gelir. Araç Visual Studio ile yakından tümleşiktir, bu nedenle her şey tanıdık GUI arabirimi aracılığıyla da kullanılabilir. Bu bölümde, yeni bir ASP.NET Core gRPC projesi oluşturmak için her iki yol da gösterilir: ilk olarak Visual Studio ve sonra .NET Core CLI.

## <a name="create-the-project-using-visual-studio"></a>Visual Studio 'Yu kullanarak proje oluşturma

> [!IMPORTANT]
> ASP.NET Core 3,0 uygulaması geliştirmek için, **ASP.net ve Web geliştirme** iş yükünün yüklü olduğu Visual Studio 2019,3 veya üzeri bir sürüme sahip olmanız gerekir.

*Boş çözüm* şablonundan **tradersys** adlı boş bir çözüm oluşturun. Adlı `src`bir çözüm klasörü ekleyin, sonra klasöre sağ tıklayın ve bağlam menüsünden**Yeni proje** **Ekle** > ' yi seçin. Şablon `grpc` arama kutusuna girin ve adlı `gRPC Service`bir proje şablonu görmeniz gerekir.

![GRPC hizmeti proje şablonunu gösteren yeni proje iletişim kutusu Ekle](media/create-project/new-grpc-project.png)

**Projeyi Yapılandır** iletişim kutusuna devam etmek için **İleri** ' ye tıklayın ve projeyi `TraderSys.Portfolios`adlandırın ve **konuma**bir `src` alt dizin ekleyin.

![Proje yapılandırma iletişim kutusu](media/create-project/configure-project.png)

**Yeni gRPC projesi** iletişim kutusuna devam etmek için **İleri** ' ye tıklayın.

![Yeni gRPC proje iletişim kutusu](media/create-project/create-new-grpc-service.png)

Mevcut olduğunda, hizmet oluşturma için sınırlı sayıda seçenek vardır. Docker daha sonra kitapta kullanıma sunulacaktır, bu nedenle bu onay kutusunu şimdilik işaretsiz bırakın ve **Oluştur**' a tıklayın. İlk ASP.NET Core 3,0 gRPC projeniz oluşturulur ve çözüme eklenir. İle `dotnet CLI`çalışma hakkında bilgi almak istemiyorsanız [örnek kodu Temizleme](#clean-up-the-example-code) bölümüne atlayın.

## <a name="create-the-project-using-the-net-core-cli"></a>.NET Core CLI kullanarak proje oluşturun

Bu bölümde, komut satırından çözümlerin ve projelerin oluşturulması ele alınmaktadır.

Çözümü aşağıda gösterildiği gibi oluşturun. `-o` ( Veya`--output`) bayrağı, mevcut değilse geçerli dizinde oluşturulacak çıkış dizinini belirtir. Çözüme, dizinle aynı ad verilecek, yani `TraderSys.sln`. `-n` ( Veya`--name`) bayrağını kullanarak farklı bir ad sağlayabilirsiniz.

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 3,0, gRPC Hizmetleri için bir CLı şablonuyla birlikte gelir. Bu şablonu kullanarak yeni projeyi oluşturun ve bunu bir `src` alt dizine koyarak ASP.NET Core projelerine yönelik kural olarak ekleyin. Bu, `-n` bayrağıyla farklı bir ad belirtmediğiniz müddetçe, Dizin `TraderSys.Portfolios.csproj`(örn.) öğesinden sonra adlandırılır.

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

Son olarak, `dotnet sln` komutunu kullanarak projeyi çözüme ekleyin.

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> Verilen dizin yalnızca tek `.csproj` bir dosya içerdiğinden, yazma kaydetmek için yalnızca dizini belirterek dışarıda bırakabilirsiniz.

Bu çözümü artık Visual Studio 2019, Visual Studio Code veya tercih ettiğiniz herhangi bir düzenleyicide açabilirsiniz.

## <a name="clean-up-the-example-code"></a>Örnek kodu Temizleme

Artık, kitapta daha önce gözden geçirilmiş olan gRPC şablonunu kullanarak bir örnek hizmet oluşturdunuz. Bu, hisse senedi ticari bağlamımızda yararlı değildir, bu nedenle ilk projemizdeki şeyleri düzenliyoruz.

### <a name="rename-and-edit-the-proto-file"></a>Proto dosyasını yeniden adlandırma ve düzenleme

Devam edin ve `Protos/greet.proto` dosyayı olarak `Protos/portfolios.proto` yeniden adlandırın ve Düzenleyicinizde açın. `package` Satırdan sonraki her şeyi silin, sonra, `package` ve `option csharp_namespace` `service` adlarını değiştirin ve varsayılan `SayHello` hizmeti kaldırın. bu nedenle kod şöyle görünür.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> Şablon, varsayılan olarak `Protos` ad alanı bölümünü eklemez, ancak eklemek, GRPC tarafından oluşturulan sınıfların ve kendi sınıflarınızın kodunuzda açık bir şekilde ayrılmış olmasını kolaylaştırır.

`greet.proto` Dosyayı Visual Studio gibi tümleşik bir geliştirme ortamında (IDE) yeniden adlandırırsanız, bu dosyanın bir başvurusu `.csproj` dosyada otomatik olarak güncelleştirilir. Ancak Visual Studio Code gibi bazı başka düzenleyicide bu başvuru otomatik olarak güncellenmez, bu nedenle proje dosyasını el ile düzenlemeniz gerekir.

GRPC derleme hedeflerinde, hangi `Protobuf` `.proto` dosyaların derlenmesi gerektiğini ve hangi kod üretimi gerektiğini (yani, "sunucu" veya "istemci") belirtmenizi sağlayan bir öğe öğesi vardır.

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>GreeterService sınıfını yeniden adlandırma

Sınıfı klasöründe bulunur ve öğesinden `Greeter.GreeterBase`devralır. `GreeterService` `Services` Olarak `PortfolioService` yeniden adlandırın ve temel sınıfını olarak `Portfolios.PortfoliosBase`değiştirin. `override` Yöntemleri silin.

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

Sınıfında yönteminde `GreeterService` `Configure` sınıfına birbaşvuruvardı.`Startup` Sınıfı yeniden adlandırmak için yeniden düzenleme kullandıysanız, bu başvurunun otomatik olarak güncelleştirilmiş olması gerekir. Ancak, yapmadıysanız, el ile düzenlemeniz gerekir.

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
