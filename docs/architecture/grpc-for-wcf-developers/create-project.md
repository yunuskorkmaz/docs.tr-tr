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
# <a name="create-a-new-aspnet-core-grpc-project"></a><span data-ttu-id="352ce-103">Yeni bir ASP.NET Core gRPC projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="352ce-103">Create a new ASP.NET Core gRPC project</span></span>

<span data-ttu-id="352ce-104">.NET Core SDK, komut satırından projeler ve çözümler oluşturmanıza ve yönetmenize olanak tanıyan güçlü bir CLı aracı `dotnet`sunar.</span><span class="sxs-lookup"><span data-stu-id="352ce-104">The .NET Core SDK comes with a powerful CLI tool, `dotnet`, which enables you to create and manage projects and solutions from the command line.</span></span> <span data-ttu-id="352ce-105">SDK, Visual Studio ile yakından tümleşiktir, böylece her şey tanıdık grafik kullanıcı arabirimi aracılığıyla da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="352ce-105">The SDK is closely integrated with Visual Studio, so everything is also available through the familiar graphical user interface.</span></span> <span data-ttu-id="352ce-106">Bu bölümde, yeni bir ASP.NET Core gRPC projesi oluşturmanın her iki yolu da gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="352ce-106">This chapter shows both ways to create a new ASP.NET Core gRPC project.</span></span>

## <a name="create-the-project-by-using-visual-studio"></a><span data-ttu-id="352ce-107">Visual Studio 'Yu kullanarak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="352ce-107">Create the project by using Visual Studio</span></span>

> [!IMPORTANT]
> <span data-ttu-id="352ce-108">ASP.NET Core 3,0 uygulaması geliştirmek için, **ASP.net ve Web geliştirme** iş yükü yüklüyken Visual Studio 2019 16,3 veya sonraki bir sürüme sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="352ce-108">To develop any ASP.NET Core 3.0 app, you need Visual Studio 2019 16.3 or later, with the **ASP.NET and web development** workload installed.</span></span>

<span data-ttu-id="352ce-109">*Boş çözüm* şablonundan **tradersys** adlı boş bir çözüm oluşturun.</span><span class="sxs-lookup"><span data-stu-id="352ce-109">Create an empty solution called **TraderSys** from the *Blank Solution* template.</span></span> <span data-ttu-id="352ce-110">`src`adlı bir çözüm klasörü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="352ce-110">Add a solution folder called `src`.</span></span> <span data-ttu-id="352ce-111">Ardından, klasöre sağ tıklayıp > **Yeni proje** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="352ce-111">Then, right-click on the folder and choose **Add** > **New Project**.</span></span> <span data-ttu-id="352ce-112">Şablon arama kutusuna `grpc` girin ve `gRPC Service`adlı bir proje şablonu görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="352ce-112">Enter `grpc` in the template search box, and you should see a project template called `gRPC Service`.</span></span>

![Yeni Proje Ekle iletişim kutusunun ekran görüntüsü](media/create-project/new-grpc-project.png)

<span data-ttu-id="352ce-114">**Yeni projeyi Yapılandır** iletişim kutusunu kullanmaya devam etmek için **İleri ' yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="352ce-114">Select **Next** to continue to the **Configure your new project** dialog box.</span></span> <span data-ttu-id="352ce-115">Projeyi `TraderSys.Portfolios`olarak adlandırın ve **konuma**bir `src` alt dizini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="352ce-115">Name the project `TraderSys.Portfolios`, and add an `src` subdirectory to the **Location**.</span></span>

![Yeni projenizi yapılandırma iletişim kutusunun ekran görüntüsü](media/create-project/configure-project.png)

<span data-ttu-id="352ce-117">**Yeni bir gRPC hizmeti oluştur** iletişim kutusuna devam etmek için **İleri ' yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="352ce-117">Select **Next** to continue to the **Create a new gRPC service** dialog box.</span></span>

![Yeni bir gRPC hizmeti oluştur iletişim kutusunun ekran görüntüsü](media/create-project/create-new-grpc-service.png)

<span data-ttu-id="352ce-119">Mevcut olduğunda, hizmet oluşturma için sınırlı seçenekleriniz vardır.</span><span class="sxs-lookup"><span data-stu-id="352ce-119">At present, you have limited options for the service creation.</span></span> <span data-ttu-id="352ce-120">Docker daha sonra kullanıma sunulacaktır, bu nedenle şimdilik bu seçeneği işaretsiz bırakın.</span><span class="sxs-lookup"><span data-stu-id="352ce-120">Docker will be introduced later, so for now, leave that option unselected.</span></span> <span data-ttu-id="352ce-121">**Oluştur**' u seçmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="352ce-121">Just select **Create**.</span></span> <span data-ttu-id="352ce-122">İlk ASP.NET Core 3,0 gRPC projeniz oluşturulur ve çözüme eklenir.</span><span class="sxs-lookup"><span data-stu-id="352ce-122">Your first ASP.NET Core 3.0 gRPC project is generated and added to the solution.</span></span> <span data-ttu-id="352ce-123">`dotnet CLI`çalışma hakkında daha fazla bilgi almak istemiyorsanız [örnek kodu Temizleme](#clean-up-the-example-code) bölümüne atlayın.</span><span class="sxs-lookup"><span data-stu-id="352ce-123">If you don't want to know about working with the `dotnet CLI`, skip to the [Clean up the example code](#clean-up-the-example-code) section.</span></span>

## <a name="create-the-project-by-using-the-net-core-cli"></a><span data-ttu-id="352ce-124">.NET Core CLI kullanarak proje oluşturun</span><span class="sxs-lookup"><span data-stu-id="352ce-124">Create the project by using the .NET Core CLI</span></span>

<span data-ttu-id="352ce-125">Bu bölümde, komut satırından çözümlerin ve projelerin oluşturulması ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="352ce-125">This section covers the creation of solutions and projects from the command line.</span></span>

<span data-ttu-id="352ce-126">Aşağıdaki komutta gösterildiği gibi çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="352ce-126">Create the solution as shown in the following command.</span></span> <span data-ttu-id="352ce-127">`-o` (veya `--output`) bayrağı, zaten mevcut değilse geçerli dizinde oluşturulan çıkış dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="352ce-127">The `-o` (or `--output`) flag specifies the output directory, which is created in the current directory if it doesn't already exist.</span></span> <span data-ttu-id="352ce-128">Çözüm şu dizinle aynı ada sahip: `TraderSys.sln`.</span><span class="sxs-lookup"><span data-stu-id="352ce-128">The solution has the same name as the directory: `TraderSys.sln`.</span></span> <span data-ttu-id="352ce-129">`-n` (veya `--name`) bayrağını kullanarak farklı bir ad sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="352ce-129">You can provide a different name by using the `-n` (or `--name`) flag.</span></span>

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

<span data-ttu-id="352ce-130">ASP.NET Core 3,0, gRPC Hizmetleri için bir CLı şablonuyla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="352ce-130">ASP.NET Core 3.0 comes with a CLI template for gRPC services.</span></span> <span data-ttu-id="352ce-131">Bu şablonu kullanarak yeni projeyi oluşturun ve ASP.NET Core projeler için geleneksel olarak bir `src` alt dizinine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="352ce-131">Create the new project by using this template, putting it into an `src` subdirectory as is conventional for ASP.NET Core projects.</span></span> <span data-ttu-id="352ce-132">`-n` bayrağıyla farklı bir ad belirtmediğiniz müddetçe, proje dizinden (`TraderSys.Portfolios.csproj`) sonra adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="352ce-132">The project is named after the directory (`TraderSys.Portfolios.csproj`), unless you specify a different name with the `-n` flag.</span></span>

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

<span data-ttu-id="352ce-133">Son olarak, `dotnet sln` komutunu kullanarak projeyi çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="352ce-133">Finally, add the project to the solution by using the `dotnet sln` command:</span></span>

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> <span data-ttu-id="352ce-134">Belirli dizin yalnızca tek bir `.csproj` dosyası içerdiğinden, yazmayı kaydetmek için yalnızca dizini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="352ce-134">Because the particular directory only contains a single `.csproj` file, you can specify just the directory, to save typing.</span></span>

<span data-ttu-id="352ce-135">Bu çözümü artık Visual Studio 2019, Visual Studio Code veya tercih ettiğiniz herhangi bir düzenleyicide açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="352ce-135">You can now open this solution in Visual Studio 2019, Visual Studio Code, or whatever editor you prefer.</span></span>

## <a name="clean-up-the-example-code"></a><span data-ttu-id="352ce-136">Örnek kodu Temizleme</span><span class="sxs-lookup"><span data-stu-id="352ce-136">Clean up the example code</span></span>

<span data-ttu-id="352ce-137">Artık, kitapta daha önce gözden geçirilmiş olan gRPC şablonunu kullanarak bir örnek hizmet oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="352ce-137">You've now created an example service by using the gRPC template, which was reviewed earlier in the book.</span></span> <span data-ttu-id="352ce-138">Bu, hisse senedi ticari bağlamımızda yararlı değildir, bu nedenle ilk projemizdeki şeyleri düzenliyoruz.</span><span class="sxs-lookup"><span data-stu-id="352ce-138">This isn't useful in our stock trading context, so we'll edit things for our first project.</span></span>

### <a name="rename-and-edit-the-proto-file"></a><span data-ttu-id="352ce-139">Proto dosyasını yeniden adlandırma ve düzenleme</span><span class="sxs-lookup"><span data-stu-id="352ce-139">Rename and edit the proto file</span></span>

<span data-ttu-id="352ce-140">Devam edin ve `Protos/greet.proto` dosyayı `Protos/portfolios.proto`olarak yeniden adlandırın ve Düzenleyicinizde açın.</span><span class="sxs-lookup"><span data-stu-id="352ce-140">Go ahead and rename the `Protos/greet.proto` file to `Protos/portfolios.proto`, and open it in your editor.</span></span> <span data-ttu-id="352ce-141">`package` satırdan sonra her şeyi silin.</span><span class="sxs-lookup"><span data-stu-id="352ce-141">Delete everything after the `package` line.</span></span> <span data-ttu-id="352ce-142">`option csharp_namespace`, `package` ve `service` adlarını değiştirin ve varsayılan `SayHello` hizmetini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="352ce-142">Then change the `option csharp_namespace`, `package` and `service` names, and remove the default `SayHello` service.</span></span> <span data-ttu-id="352ce-143">Kod artık aşağıdakine benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="352ce-143">The code now looks like the following:</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> <span data-ttu-id="352ce-144">Şablon, varsayılan olarak `Protos` ad alanı bölümünü eklemez, ancak eklemek, gRPC tarafından oluşturulan sınıfların ve kendi sınıflarınızın kodunuzda açıkça ayrılabilmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="352ce-144">The template doesn't add the `Protos` namespace part by default, but adding it makes it easier to keep gRPC-generated classes and your own classes clearly separated in your code.</span></span>

<span data-ttu-id="352ce-145">Visual Studio gibi tümleşik bir geliştirme ortamında (IDE) `greet.proto` dosyasını yeniden adlandırırsanız, bu dosyaya yönelik bir başvuru `.csproj` dosyasında otomatik olarak güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="352ce-145">If you rename the `greet.proto` file in an integrated development environment (IDE) like Visual Studio, a reference to this file is automatically updated in the `.csproj` file.</span></span> <span data-ttu-id="352ce-146">Ancak Visual Studio Code gibi bazı başka düzenleyicide bu başvuru otomatik olarak güncellenmez, bu nedenle proje dosyasını el ile düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="352ce-146">But in some other editor, such as Visual Studio Code, this reference isn't updated automatically, so you need to edit the project file manually.</span></span>

<span data-ttu-id="352ce-147">GRPC derleme hedefleri ' nde, hangi `.proto` dosyalarının derlenmesi gerektiğini ve hangi kod üretimi (yani "sunucu" veya "Istemci") gerektiğini belirtmenize olanak tanıyan bir `Protobuf` öğe öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="352ce-147">In the gRPC build targets, there's a `Protobuf` item element that lets you specify which `.proto` files should be compiled, and which form of code generation is required (that is, "Server" or "Client").</span></span>

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a><span data-ttu-id="352ce-148">`GreeterService` sınıfını yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="352ce-148">Rename the `GreeterService` class</span></span>

<span data-ttu-id="352ce-149">`GreeterService` sınıfı `Services` klasöründedir ve `Greeter.GreeterBase`devralır.</span><span class="sxs-lookup"><span data-stu-id="352ce-149">The `GreeterService` class is in the `Services` folder and inherits from `Greeter.GreeterBase`.</span></span> <span data-ttu-id="352ce-150">`PortfolioService`olarak yeniden adlandırın ve temel sınıfı `Portfolios.PortfoliosBase`olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="352ce-150">Rename it to `PortfolioService`, and change the base class to `Portfolios.PortfoliosBase`.</span></span> <span data-ttu-id="352ce-151">`override` yöntemlerini silin.</span><span class="sxs-lookup"><span data-stu-id="352ce-151">Delete the `override` methods.</span></span>

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

<span data-ttu-id="352ce-152">`Startup` sınıfındaki `Configure` yönteminde `GreeterService` sınıfına bir başvuru vardı.</span><span class="sxs-lookup"><span data-stu-id="352ce-152">There was a reference to the `GreeterService` class in the `Configure` method in the `Startup` class.</span></span> <span data-ttu-id="352ce-153">Sınıfı yeniden adlandırmak için yeniden düzenleme kullandıysanız, bu başvurunun otomatik olarak güncelleştirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="352ce-153">If you used refactoring to rename the class, this reference should have been updated automatically.</span></span> <span data-ttu-id="352ce-154">Ancak, yapmadıysanız, el ile düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="352ce-154">However, if you didn't, you need to edit it manually.</span></span>

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

<span data-ttu-id="352ce-155">Sonraki bölümde, bu yeni hizmete işlevsellik ekleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="352ce-155">In the next section, we'll add functionality to this new service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="352ce-156">[Önceki](migrate-wcf-to-grpc.md)
>[İleri](migrate-request-reply.md)</span><span class="sxs-lookup"><span data-stu-id="352ce-156">[Previous](migrate-wcf-to-grpc.md)
[Next](migrate-request-reply.md)</span></span>
