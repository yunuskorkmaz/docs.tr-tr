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
# <a name="create-a-new-aspnet-core-grpc-project"></a><span data-ttu-id="88b61-103">Yeni bir ASP.NET Core gRPC projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="88b61-103">Create a new ASP.NET Core gRPC project</span></span>

<span data-ttu-id="88b61-104">.NET Core, komut satırından projeler ve çözümler oluşturmanıza ve yönetmenize olanak tanıyan güçlü bir CLı aracı olan `dotnet`gelir.</span><span class="sxs-lookup"><span data-stu-id="88b61-104">.NET Core comes with a powerful CLI tool, `dotnet`, which enables you to create and manage projects and solutions from the command line.</span></span> <span data-ttu-id="88b61-105">Araç Visual Studio ile yakından tümleşiktir, bu nedenle her şey tanıdık GUI arabirimi aracılığıyla da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="88b61-105">The tool is closely integrated with Visual Studio, so everything is also available through the familiar GUI interface.</span></span> <span data-ttu-id="88b61-106">Bu bölümde, yeni bir ASP.NET Core gRPC projesi oluşturmak için her iki yol da gösterilir: ilk olarak Visual Studio ve sonra .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="88b61-106">This chapter will show both ways to create a new ASP.NET Core gRPC project: first with Visual Studio, then with the .NET Core CLI.</span></span>

## <a name="create-the-project-using-visual-studio"></a><span data-ttu-id="88b61-107">Visual Studio 'Yu kullanarak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="88b61-107">Create the project using Visual Studio</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88b61-108">ASP.NET Core 3,0 uygulaması geliştirmek için, **ASP.net ve Web geliştirme** iş yükünün yüklü olduğu Visual Studio 2019,3 veya üzeri bir sürüme sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="88b61-108">To develop any ASP.NET Core 3.0 app, you need Visual Studio 2019.3 or later with the **ASP.NET and web development** workload installed.</span></span>

<span data-ttu-id="88b61-109">*Boş çözüm* şablonundan **tradersys** adlı boş bir çözüm oluşturun.</span><span class="sxs-lookup"><span data-stu-id="88b61-109">Create an empty solution called **TraderSys** from the *Blank Solution* template.</span></span> <span data-ttu-id="88b61-110">`src`adlı bir çözüm klasörü ekleyin, sonra klasöre sağ tıklayın ve bağlam menüsünden **yeni > proje** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="88b61-110">Add a Solution Folder called `src`, then right-click on the folder and choose **Add** > **New Project** from the context menu.</span></span> <span data-ttu-id="88b61-111">Şablon arama kutusuna `grpc` girin ve `gRPC Service`adlı bir proje şablonu görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="88b61-111">Enter `grpc` in the template search box and you should see a project template called `gRPC Service`.</span></span>

![GRPC hizmeti proje şablonunu gösteren yeni proje iletişim kutusu Ekle](media/create-project/new-grpc-project.png)

<span data-ttu-id="88b61-113">**Projeyi Yapılandır** iletişim kutusuna devam etmek için **İleri** ' ye tıklayın ve proje `TraderSys.Portfolios`olarak adlandırın ve **konuma**bir `src` alt dizini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="88b61-113">Click **Next** to continue to the **Configure project** dialog and name the project `TraderSys.Portfolios`, and add an `src` subdirectory to the **Location**.</span></span>

![Proje yapılandırma iletişim kutusu](media/create-project/configure-project.png)

<span data-ttu-id="88b61-115">**Yeni gRPC projesi** iletişim kutusuna devam etmek için **İleri** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="88b61-115">Click **Next** to continue to the **New gRPC project** dialog.</span></span>

![Yeni gRPC proje iletişim kutusu](media/create-project/create-new-grpc-service.png)

<span data-ttu-id="88b61-117">Mevcut olduğunda, hizmet oluşturma için sınırlı sayıda seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="88b61-117">At present, there are limited options for the service creation.</span></span> <span data-ttu-id="88b61-118">Docker daha sonra kitapta kullanıma sunulacaktır, bu nedenle bu onay kutusunu şimdilik işaretsiz bırakın ve **Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="88b61-118">Docker will be introduced later in the book, so leave that checkbox unchecked for now and just click **Create**.</span></span> <span data-ttu-id="88b61-119">İlk ASP.NET Core 3,0 gRPC projeniz oluşturulur ve çözüme eklenir.</span><span class="sxs-lookup"><span data-stu-id="88b61-119">Your first ASP.NET Core 3.0 gRPC project is generated and added to the solution.</span></span> <span data-ttu-id="88b61-120">`dotnet CLI`çalışma hakkında daha fazla bilgi almak istemiyorsanız [örnek kodu Temizleme](#clean-up-the-example-code) bölümüne atlayın.</span><span class="sxs-lookup"><span data-stu-id="88b61-120">If you don't want to know about working with the `dotnet CLI`, skip to the [Clean up the example code](#clean-up-the-example-code) section.</span></span>

## <a name="create-the-project-using-the-net-core-cli"></a><span data-ttu-id="88b61-121">.NET Core CLI kullanarak proje oluşturun</span><span class="sxs-lookup"><span data-stu-id="88b61-121">Create the project using the .NET Core CLI</span></span>

<span data-ttu-id="88b61-122">Bu bölümde, komut satırından çözümlerin ve projelerin oluşturulması ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="88b61-122">This section covers the creation of solutions and projects from the command line.</span></span>

<span data-ttu-id="88b61-123">Çözümü aşağıda gösterildiği gibi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="88b61-123">Create the solution as shown below.</span></span> <span data-ttu-id="88b61-124">`-o` (veya `--output`) bayrağı, mevcut değilse geçerli dizinde oluşturulacak çıkış dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="88b61-124">The `-o` (or `--output`) flag specifies the output directory, which will be created in the current directory if it does not exist.</span></span> <span data-ttu-id="88b61-125">Çözüme, dizinle aynı ad verilecek, yani `TraderSys.sln`. `-n` (veya `--name`) bayrağını kullanarak farklı bir ad sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88b61-125">The solution will be given the same name as the directory, i.e. `TraderSys.sln`. You can provide a different name using the `-n` (or `--name`) flag.</span></span>

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

<span data-ttu-id="88b61-126">ASP.NET Core 3,0, gRPC Hizmetleri için bir CLı şablonuyla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="88b61-126">ASP.NET Core 3.0 comes with a CLI template for gRPC services.</span></span> <span data-ttu-id="88b61-127">Bu şablonu kullanarak yeni projeyi oluşturun ve ASP.NET Core projelerin kuralı olarak bir `src` alt dizinine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="88b61-127">Create the new project using this template, putting it into an `src` subdirectory as is the convention for ASP.NET Core projects.</span></span> <span data-ttu-id="88b61-128">`-n` bayrağıyla farklı bir ad belirtmediğiniz müddetçe, proje dizin (yani `TraderSys.Portfolios.csproj`) sonra adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="88b61-128">The project will be named after the directory (i.e. `TraderSys.Portfolios.csproj`) unless you specify a different name with the `-n` flag.</span></span>

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

<span data-ttu-id="88b61-129">Son olarak, `dotnet sln` komutunu kullanarak projeyi çözüme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="88b61-129">Finally, add the project to the solution using the `dotnet sln` command.</span></span>

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> <span data-ttu-id="88b61-130">Verilen dizin yalnızca tek bir `.csproj` dosyası içerdiğinden, yazmak için yalnızca dizini belirterek kazanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88b61-130">Since the given directory only contains a single `.csproj` file, you can get away with specifying just the directory to save typing.</span></span>

<span data-ttu-id="88b61-131">Bu çözümü artık Visual Studio 2019, Visual Studio Code veya tercih ettiğiniz herhangi bir düzenleyicide açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88b61-131">You can now open this solution in Visual Studio 2019, Visual Studio Code, or whatever editor you prefer.</span></span>

## <a name="clean-up-the-example-code"></a><span data-ttu-id="88b61-132">Örnek kodu Temizleme</span><span class="sxs-lookup"><span data-stu-id="88b61-132">Clean up the example code</span></span>

<span data-ttu-id="88b61-133">Artık, kitapta daha önce gözden geçirilmiş olan gRPC şablonunu kullanarak bir örnek hizmet oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="88b61-133">You've now created an example service using the gRPC template, which was reviewed earlier in the book.</span></span> <span data-ttu-id="88b61-134">Bu, hisse senedi ticari bağlamımızda yararlı değildir, bu nedenle ilk projemizdeki şeyleri düzenliyoruz.</span><span class="sxs-lookup"><span data-stu-id="88b61-134">This isn't useful in our stock trading context, so we'll edit things for our first project.</span></span>

### <a name="rename-and-edit-the-proto-file"></a><span data-ttu-id="88b61-135">Proto dosyasını yeniden adlandırma ve düzenleme</span><span class="sxs-lookup"><span data-stu-id="88b61-135">Rename and edit the proto file</span></span>

<span data-ttu-id="88b61-136">Devam edin ve `Protos/greet.proto` dosyayı `Protos/portfolios.proto` olarak yeniden adlandırın ve Düzenleyicinizde açın.</span><span class="sxs-lookup"><span data-stu-id="88b61-136">Go ahead and rename the `Protos/greet.proto` file to `Protos/portfolios.proto` and open it in your editor.</span></span> <span data-ttu-id="88b61-137">`package` satırdan sonra her şeyi silin, sonra `option csharp_namespace`, `package` ve `service` adlarını değiştirin ve varsayılan `SayHello` hizmetini kaldırın. böylece kod şöyle görünür.</span><span class="sxs-lookup"><span data-stu-id="88b61-137">Delete everything after the `package` line, then change the `option csharp_namespace`, `package` and `service` names, and remove the default `SayHello` service, so the code looks like this.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> <span data-ttu-id="88b61-138">Şablon, varsayılan olarak `Protos` ad alanı bölümünü eklemez, ancak eklemek, gRPC tarafından oluşturulan sınıfların ve kendi sınıflarınızın kodunuzda açıkça ayrılabilmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="88b61-138">The template doesn't add the `Protos` namespace part by default, but adding it makes it easier to keep gRPC-generated classes and your own classes clearly separated in your code.</span></span>

<span data-ttu-id="88b61-139">Visual Studio gibi tümleşik bir geliştirme ortamında (IDE) `greet.proto` dosyasını yeniden adlandırırsanız, bu dosyaya yönelik bir başvuru `.csproj` dosyasında otomatik olarak güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="88b61-139">If you rename the `greet.proto` file in an integrated development environment (IDE) like Visual Studio, a reference to this file is automatically updated in the `.csproj` file.</span></span> <span data-ttu-id="88b61-140">Ancak Visual Studio Code gibi bazı başka düzenleyicide bu başvuru otomatik olarak güncellenmez, bu nedenle proje dosyasını el ile düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="88b61-140">But in some other editor, such as Visual Studio Code, this reference isn't updated automatically, so you need to edit the project file manually.</span></span>

<span data-ttu-id="88b61-141">GRPC derleme hedefleri ' nde, hangi `.proto` dosyalarının derlenmesi gerektiğini ve hangi kod üretimi (yani "sunucu" veya "Istemci") gerektiğini belirtmenize olanak tanıyan bir `Protobuf` öğe öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="88b61-141">In the gRPC build targets, there's a `Protobuf` item element that lets you specify which `.proto` files should be compiled and which form of code generation is required (that is, "Server" or "Client").</span></span>

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a><span data-ttu-id="88b61-142">GreeterService sınıfını yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="88b61-142">Rename the GreeterService class</span></span>

<span data-ttu-id="88b61-143">`GreeterService` sınıfı `Services` klasöründedir ve `Greeter.GreeterBase`devralır.</span><span class="sxs-lookup"><span data-stu-id="88b61-143">The `GreeterService` class is in the `Services` folder and inherits from `Greeter.GreeterBase`.</span></span> <span data-ttu-id="88b61-144">`PortfolioService` olarak yeniden adlandırın ve temel sınıfı `Portfolios.PortfoliosBase`olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="88b61-144">Rename it to `PortfolioService` and change the base class to `Portfolios.PortfoliosBase`.</span></span> <span data-ttu-id="88b61-145">`override` yöntemlerini silin.</span><span class="sxs-lookup"><span data-stu-id="88b61-145">Delete the `override` methods.</span></span>

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

<span data-ttu-id="88b61-146">`Startup` sınıfındaki `Configure` yönteminde `GreeterService` sınıfına bir başvuru vardı.</span><span class="sxs-lookup"><span data-stu-id="88b61-146">There was a reference to the `GreeterService` class in the `Configure` method in the `Startup` class.</span></span> <span data-ttu-id="88b61-147">Sınıfı yeniden adlandırmak için yeniden düzenleme kullandıysanız, bu başvurunun otomatik olarak güncelleştirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="88b61-147">If you used refactoring to rename the class, this reference should have been updated automatically.</span></span> <span data-ttu-id="88b61-148">Ancak, yapmadıysanız, el ile düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="88b61-148">However, if you didn't, you need to edit it manually.</span></span>

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

<span data-ttu-id="88b61-149">Sonraki bölümde, bu yeni hizmete işlevsellik ekleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="88b61-149">In the next section, we'll add functionality to this new service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="88b61-150">[Önceki](migrate-wcf-to-grpc.md)
>[İleri](migrate-request-reply.md)</span><span class="sxs-lookup"><span data-stu-id="88b61-150">[Previous](migrate-wcf-to-grpc.md)
[Next](migrate-request-reply.md)</span></span>
