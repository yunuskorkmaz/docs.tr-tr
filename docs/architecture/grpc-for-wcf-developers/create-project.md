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
# <a name="create-a-new-aspnet-core-grpc-project"></a><span data-ttu-id="fdd8c-103">Yeni bir ASP.NET Core gRPC projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="fdd8c-103">Create a new ASP.NET Core gRPC project</span></span>

<span data-ttu-id="fdd8c-104">.NET SDK, `dotnet` komut satırından projeler ve çözümler oluşturmanıza ve yönetmenize olanak tanıyan güçlü BIR CLI aracı ile gelir.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-104">The .NET SDK comes with a powerful CLI tool, `dotnet`, which enables you to create and manage projects and solutions from the command line.</span></span> <span data-ttu-id="fdd8c-105">SDK, Visual Studio ile yakından tümleşiktir, böylece her şey tanıdık grafik kullanıcı arabirimi aracılığıyla da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-105">The SDK is closely integrated with Visual Studio, so everything is also available through the familiar graphical user interface.</span></span> <span data-ttu-id="fdd8c-106">Bu bölümde, yeni bir ASP.NET Core gRPC projesi oluşturmanın her iki yolu da gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-106">This chapter shows both ways to create a new ASP.NET Core gRPC project.</span></span>

## <a name="create-the-project-by-using-visual-studio"></a><span data-ttu-id="fdd8c-107">Visual Studio 'Yu kullanarak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="fdd8c-107">Create the project by using Visual Studio</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fdd8c-108">ASP.NET Core 5,0 uygulaması geliştirmek için, **ASP.net ve Web geliştirme** iş yükü yüklüyken Visual Studio 2019 sürüm 16,3 veya sonraki bir sürüme sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-108">To develop any ASP.NET Core 5.0 app, you need Visual Studio 2019 version 16.3 or later, with the **ASP.NET and web development** workload installed.</span></span>

<span data-ttu-id="fdd8c-109">*Boş çözüm* şablonundan **tradersys** adlı boş bir çözüm oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-109">Create an empty solution called **TraderSys** from the *Blank Solution* template.</span></span> <span data-ttu-id="fdd8c-110">Adlı bir çözüm klasörü ekleyin `src` .</span><span class="sxs-lookup"><span data-stu-id="fdd8c-110">Add a solution folder called `src`.</span></span> <span data-ttu-id="fdd8c-111">Ardından, klasöre sağ tıklayıp   >  **Yeni proje** Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-111">Then, right-click on the folder and choose **Add** > **New Project**.</span></span> <span data-ttu-id="fdd8c-112">`grpc`Şablon arama kutusuna girin ve adlı bir proje şablonu görmeniz gerekir `gRPC Service` .</span><span class="sxs-lookup"><span data-stu-id="fdd8c-112">Enter `grpc` in the template search box, and you should see a project template called `gRPC Service`.</span></span>

![Yeni Proje Ekle iletişim kutusunun ekran görüntüsü](media/create-project/new-grpc-project.png)

<span data-ttu-id="fdd8c-114">**Yeni projeyi Yapılandır** iletişim kutusunu kullanmaya devam etmek için **İleri ' yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-114">Select **Next** to continue to the **Configure your new project** dialog box.</span></span> <span data-ttu-id="fdd8c-115">Projeyi adlandırın `TraderSys.Portfolios` ve `src` **konuma** bir alt dizin ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-115">Name the project `TraderSys.Portfolios` and add an `src` subdirectory to the **Location**.</span></span>

![Yeni projenizi yapılandırma iletişim kutusunun ekran görüntüsü](media/create-project/configure-project.png)

<span data-ttu-id="fdd8c-117">**Yeni bir gRPC hizmeti oluştur** iletişim kutusuna devam etmek için **İleri ' yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-117">Select **Next** to continue to the **Create a new gRPC service** dialog box.</span></span>

![Yeni bir gRPC hizmeti oluştur iletişim kutusunun ekran görüntüsü](media/create-project/create-new-grpc-service-v2.png)

<span data-ttu-id="fdd8c-119">Mevcut olduğunda, hizmet oluşturma için sınırlı seçenekleriniz vardır.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-119">At present, you have limited options for the service creation.</span></span> <span data-ttu-id="fdd8c-120">Docker daha sonra kullanıma sunulacaktır, bu nedenle şimdilik bu seçeneği işaretsiz bırakın.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-120">Docker will be introduced later, so for now, leave that option unselected.</span></span> <span data-ttu-id="fdd8c-121">**Oluştur**' u seçmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-121">Just select **Create**.</span></span> <span data-ttu-id="fdd8c-122">İlk ASP.NET Core 5,0 gRPC projeniz oluşturulur ve çözüme eklenir.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-122">Your first ASP.NET Core 5.0 gRPC project is generated and added to the solution.</span></span> <span data-ttu-id="fdd8c-123">İle çalışma hakkında bilgi almak istemiyorsanız `dotnet CLI` [örnek kodu Temizleme](#clean-up-the-example-code) bölümüne atlayın.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-123">If you don't want to know about working with the `dotnet CLI`, skip to the [Clean up the example code](#clean-up-the-example-code) section.</span></span>

## <a name="create-the-project-by-using-the-net-cli"></a><span data-ttu-id="fdd8c-124">.NET CLı kullanarak projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="fdd8c-124">Create the project by using the .NET CLI</span></span>

<span data-ttu-id="fdd8c-125">Bu bölümde, komut satırından çözümlerin ve projelerin oluşturulması ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-125">This section covers the creation of solutions and projects from the command line.</span></span>

<span data-ttu-id="fdd8c-126">Aşağıdaki komutta gösterildiği gibi çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-126">Create the solution as shown in the following command.</span></span> <span data-ttu-id="fdd8c-127">`-o`(Veya `--output` ) bayrağı, zaten mevcut değilse geçerli dizinde oluşturulan çıkış dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-127">The `-o` (or `--output`) flag specifies the output directory, which is created in the current directory if it doesn't already exist.</span></span> <span data-ttu-id="fdd8c-128">Çözüm, şu dizinle aynı ada sahip: `TraderSys.sln` .</span><span class="sxs-lookup"><span data-stu-id="fdd8c-128">The solution has the same name as the directory: `TraderSys.sln`.</span></span> <span data-ttu-id="fdd8c-129">`-n`(Veya) bayrağını kullanarak farklı bir ad sağlayabilirsiniz `--name` .</span><span class="sxs-lookup"><span data-stu-id="fdd8c-129">You can provide a different name by using the `-n` (or `--name`) flag.</span></span>

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

<span data-ttu-id="fdd8c-130">ASP.NET Core 5,0, gRPC Hizmetleri için bir CLı şablonuyla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-130">ASP.NET Core 5.0 comes with a CLI template for gRPC services.</span></span> <span data-ttu-id="fdd8c-131">Bu şablonu kullanarak yeni projeyi oluşturun ve bunu `src` ASP.NET Core projeler için geleneksel olarak bir alt dizine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-131">Create the new project by using this template, putting it into an `src` subdirectory as is conventional for ASP.NET Core projects.</span></span> <span data-ttu-id="fdd8c-132">, `TraderSys.Portfolios.csproj` Bayrağıyla farklı bir ad belirtmediğiniz müddetçe, proje dizinden () sonra adlandırılır `-n` .</span><span class="sxs-lookup"><span data-stu-id="fdd8c-132">The project is named after the directory (`TraderSys.Portfolios.csproj`), unless you specify a different name with the `-n` flag.</span></span>

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

<span data-ttu-id="fdd8c-133">Son olarak, komutunu kullanarak projeyi çözüme ekleyin `dotnet sln` :</span><span class="sxs-lookup"><span data-stu-id="fdd8c-133">Finally, add the project to the solution by using the `dotnet sln` command:</span></span>

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> <span data-ttu-id="fdd8c-134">Belirli dizin yalnızca tek bir dosya içerdiğinden, `.csproj` yazmayı kaydetmek için yalnızca dizini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-134">Because the particular directory only contains a single `.csproj` file, you can specify just the directory, to save typing.</span></span>

<span data-ttu-id="fdd8c-135">Bu çözümü artık Visual Studio 2019, Visual Studio Code veya tercih ettiğiniz herhangi bir düzenleyicide açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-135">You can now open this solution in Visual Studio 2019, Visual Studio Code, or whatever editor you prefer.</span></span>

## <a name="clean-up-the-example-code"></a><span data-ttu-id="fdd8c-136">Örnek kodu Temizleme</span><span class="sxs-lookup"><span data-stu-id="fdd8c-136">Clean up the example code</span></span>

<span data-ttu-id="fdd8c-137">Artık, kitapta daha önce gözden geçirilmiş olan gRPC şablonunu kullanarak bir örnek hizmet oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-137">You've now created an example service by using the gRPC template, which was reviewed earlier in the book.</span></span> <span data-ttu-id="fdd8c-138">Bu kod, hisse senedi ortamımızda yararlı değildir, bu nedenle ilk projemizdeki şeyleri düzenliyoruz.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-138">This code isn't useful in our stock trading context, so we'll edit things for our first project.</span></span>

### <a name="rename-and-edit-the-proto-file"></a><span data-ttu-id="fdd8c-139">Proto dosyasını yeniden adlandırma ve düzenleme</span><span class="sxs-lookup"><span data-stu-id="fdd8c-139">Rename and edit the proto file</span></span>

<span data-ttu-id="fdd8c-140">Devam edin ve `Protos/greet.proto` dosyayı olarak yeniden adlandırın `Protos/portfolios.proto` ve Düzenleyicinizde açın.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-140">Go ahead and rename the `Protos/greet.proto` file to `Protos/portfolios.proto`, and open it in your editor.</span></span> <span data-ttu-id="fdd8c-141">Satırdan sonraki her şeyi silin `package` .</span><span class="sxs-lookup"><span data-stu-id="fdd8c-141">Delete everything after the `package` line.</span></span> <span data-ttu-id="fdd8c-142">Ardından, `option csharp_namespace` `package` ve adlarını değiştirin `service` ve varsayılan `SayHello` hizmeti kaldırın.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-142">Then change the `option csharp_namespace`, `package` and `service` names, and remove the default `SayHello` service.</span></span> <span data-ttu-id="fdd8c-143">Kod artık aşağıdakine benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="fdd8c-143">The code now looks like the following:</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> <span data-ttu-id="fdd8c-144">Şablon, `Protos` Varsayılan olarak ad alanı bölümünü eklemez, ancak eklemek, gRPC tarafından oluşturulan sınıfların ve kendi sınıflarınızın kodunuzda açık bir şekilde ayrılmış olmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-144">The template doesn't add the `Protos` namespace part by default, but adding it makes it easier to keep gRPC-generated classes and your own classes clearly separated in your code.</span></span>

<span data-ttu-id="fdd8c-145">`greet.proto`Dosyayı Visual Studio gibi tümleşik bir geliştirme ortamında (IDE) yeniden adlandırırsanız, bu dosyanın bir başvurusu dosyada otomatik olarak güncelleştirilir `.csproj` .</span><span class="sxs-lookup"><span data-stu-id="fdd8c-145">If you rename the `greet.proto` file in an integrated development environment (IDE) like Visual Studio, a reference to this file is automatically updated in the `.csproj` file.</span></span> <span data-ttu-id="fdd8c-146">Ancak Visual Studio Code gibi bazı başka düzenleyicide bu başvuru otomatik olarak güncellenmez, bu nedenle proje dosyasını el ile düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-146">But in some other editor, such as Visual Studio Code, this reference isn't updated automatically, so you need to edit the project file manually.</span></span>

<span data-ttu-id="fdd8c-147">GRPC derleme hedeflerinde, `Protobuf` hangi `.proto` dosyaların derlenmesi gerektiğini ve hangi kod üretimi gerektiğini (yani, "sunucu" veya "istemci") belirtmenize imkan tanıyan bir öğe öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-147">In the gRPC build targets, there's a `Protobuf` item element that lets you specify which `.proto` files should be compiled, and which form of code generation is required (that is, "Server" or "Client").</span></span>

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a><span data-ttu-id="fdd8c-148">Sınıfı yeniden adlandır `GreeterService`</span><span class="sxs-lookup"><span data-stu-id="fdd8c-148">Rename the `GreeterService` class</span></span>

<span data-ttu-id="fdd8c-149">`GreeterService`Sınıfı `Services` klasöründe bulunur ve öğesinden devralır `Greeter.GreeterBase` .</span><span class="sxs-lookup"><span data-stu-id="fdd8c-149">The `GreeterService` class is in the `Services` folder and inherits from `Greeter.GreeterBase`.</span></span> <span data-ttu-id="fdd8c-150">Olarak yeniden adlandırın `PortfolioService` ve temel sınıfını olarak değiştirin `Portfolios.PortfoliosBase` .</span><span class="sxs-lookup"><span data-stu-id="fdd8c-150">Rename it to `PortfolioService`, and change the base class to `Portfolios.PortfoliosBase`.</span></span> <span data-ttu-id="fdd8c-151">Yöntemleri silin `override` .</span><span class="sxs-lookup"><span data-stu-id="fdd8c-151">Delete the `override` methods.</span></span>

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

<span data-ttu-id="fdd8c-152">`GreeterService`Sınıfında yönteminde sınıfına bir başvuru vardı `Configure` `Startup` .</span><span class="sxs-lookup"><span data-stu-id="fdd8c-152">There was a reference to the `GreeterService` class in the `Configure` method in the `Startup` class.</span></span> <span data-ttu-id="fdd8c-153">Sınıfı yeniden adlandırmak için yeniden düzenleme kullandıysanız, bu başvurunun otomatik olarak güncelleştirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-153">If you used refactoring to rename the class, this reference should have been updated automatically.</span></span> <span data-ttu-id="fdd8c-154">Ancak, yapmadıysanız, el ile düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-154">However, if you didn't, you need to edit it manually.</span></span>

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

<span data-ttu-id="fdd8c-155">Sonraki bölümde, bu yeni hizmete işlevsellik ekleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="fdd8c-155">In the next section, we'll add functionality to this new service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fdd8c-156">[Önceki](migrate-wcf-to-grpc.md) 
> [Sonraki](migrate-request-reply.md)</span><span class="sxs-lookup"><span data-stu-id="fdd8c-156">[Previous](migrate-wcf-to-grpc.md)
[Next](migrate-request-reply.md)</span></span>
