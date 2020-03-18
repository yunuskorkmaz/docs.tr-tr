---
title: Microsoft XML Serializer Jeneratör
description: Microsoft XML Serializer Generator'a genel bakış. Projenizde bulunan türler için bir XML serileştirme derlemesi oluşturmak için XML Serializer Generator'ı kullanın.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 094dd1227033e167050ad73121b3005a592a0ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714518"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="a395e-104">Microsoft XML Serializer Generator'ı .NET Core'da kullanma</span><span class="sxs-lookup"><span data-stu-id="a395e-104">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="a395e-105">Bu öğretici, C# .NET Core uygulamasında Microsoft XML Serializer Generator'ı nasıl kullanacağınızı öğretir.</span><span class="sxs-lookup"><span data-stu-id="a395e-105">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="a395e-106">Bu öğretici sırasında, öğrenmek:</span><span class="sxs-lookup"><span data-stu-id="a395e-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="a395e-107">.NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="a395e-107">How to create a .NET Core app</span></span>
> - <span data-ttu-id="a395e-108">Microsoft.XmlSerializer.Generator paketine başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="a395e-108">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> - <span data-ttu-id="a395e-109">Bağımlılık eklemek için MyApp.csproj dosyanızı düzenleme</span><span class="sxs-lookup"><span data-stu-id="a395e-109">How to edit your MyApp.csproj to add dependencies</span></span>
> - <span data-ttu-id="a395e-110">Sınıf ve XmlSerializer ekleme</span><span class="sxs-lookup"><span data-stu-id="a395e-110">How to add a class and an XmlSerializer</span></span>
> - <span data-ttu-id="a395e-111">Uygulamayı derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a395e-111">How to build and run the application</span></span>

<span data-ttu-id="a395e-112">.NET Framework için [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) gibi, [Microsoft.XmlSerializer.Generator NuGet paketi](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) de .NET Core ve .NET Standard projelerine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="a395e-112">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="a395e-113">Bu, bu tür nesneleri serihale veya de-serializing nesneleri kullanırken XML serileştirme başlangıç performansını artırmak için bir <xref:System.Xml.Serialization.XmlSerializer>derleme de bulunan türleri için bir XML serileştirme derlemesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a395e-113">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a395e-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="a395e-114">Prerequisites</span></span>

<span data-ttu-id="a395e-115">Bu öğreticiyi tamamlamak için:</span><span class="sxs-lookup"><span data-stu-id="a395e-115">To complete this tutorial:</span></span>

- <span data-ttu-id="a395e-116">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) veya sonrası.</span><span class="sxs-lookup"><span data-stu-id="a395e-116">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later.</span></span>
- <span data-ttu-id="a395e-117">En sevdiğin kod düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a395e-117">Your favorite code editor.</span></span>

> [!TIP]
> <span data-ttu-id="a395e-118">Bir kod düzenleyicisi yüklemeniz mi gerekiyor?</span><span class="sxs-lookup"><span data-stu-id="a395e-118">Need to install a code editor?</span></span> <span data-ttu-id="a395e-119">[Visual Studio'yı](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)deneyin!</span><span class="sxs-lookup"><span data-stu-id="a395e-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="a395e-120">Microsoft XML Serializer Generator'ı .NET Core konsol uygulamasında kullanma</span><span class="sxs-lookup"><span data-stu-id="a395e-120">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span>

<span data-ttu-id="a395e-121">Aşağıdaki yönergeler, .NET Core konsol uygulamasında XML Serializer Generator'ı nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a395e-121">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="a395e-122">.NET Core konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="a395e-122">Create a .NET Core console application</span></span>

<span data-ttu-id="a395e-123">Komut istemini açın ve *MyApp*adında bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a395e-123">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="a395e-124">Oluşturduğunuz klasöre gidin ve aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="a395e-124">Navigate to the folder you created and type the following command:</span></span>

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="a395e-125">MyApp projesinde Microsoft.XmlSerializer.Generator paketine başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="a395e-125">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="a395e-126">Projenize [`dotnet add package`](../tools//dotnet-add-package.md) başvuru eklemek için komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="a395e-126">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span>

<span data-ttu-id="a395e-127">Şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="a395e-127">Type:</span></span>

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="a395e-128">Paketi ekledikten sonra MyApp.csproj'daki değişiklikleri doğrulayın</span><span class="sxs-lookup"><span data-stu-id="a395e-128">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="a395e-129">Kod düzenleyicinizi açın ve başlayalım!</span><span class="sxs-lookup"><span data-stu-id="a395e-129">Open your code editor and let's get started!</span></span> <span data-ttu-id="a395e-130">Uygulamayı oluşturduğumuz *MyApp* dizininden çalışmaya devam ediyoruz.</span><span class="sxs-lookup"><span data-stu-id="a395e-130">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="a395e-131">Metin editörünüzde *MyApp.csproj'u* açın.</span><span class="sxs-lookup"><span data-stu-id="a395e-131">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="a395e-132">Komutu [`dotnet add package`](../tools//dotnet-add-package.md) çalıştırdıktan sonra *MyApp.csproj* proje dosyanıza aşağıdaki satırlar eklenir:</span><span class="sxs-lookup"><span data-stu-id="a395e-132">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="a395e-133">.NET Core CLI Aracı desteği için başka bir ItemGroup bölümü ekleme</span><span class="sxs-lookup"><span data-stu-id="a395e-133">Add another ItemGroup section for .NET Core CLI Tool support</span></span>

<span data-ttu-id="a395e-134">İncelediğimiz bölümden `ItemGroup` sonra aşağıdaki satırları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a395e-134">Add the following lines after the `ItemGroup` section that we inspected:</span></span>

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a><span data-ttu-id="a395e-135">Uygulamada sınıf ekleme</span><span class="sxs-lookup"><span data-stu-id="a395e-135">Add a class in the application</span></span>

<span data-ttu-id="a395e-136">Metin düzenleyicinizde *Program.cs* açın.</span><span class="sxs-lookup"><span data-stu-id="a395e-136">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="a395e-137">myclass adlı *MyClass* sınıfı *Program.cs'da*ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a395e-137">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="a395e-138">MyClass `XmlSerializer` için bir oluşturma</span><span class="sxs-lookup"><span data-stu-id="a395e-138">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="a395e-139">MyClass için bir satır `XmlSerializer` oluşturmak için *Main'in* içine aşağıdaki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a395e-139">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="a395e-140">Uygulamayı derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a395e-140">Build and run the application</span></span>

<span data-ttu-id="a395e-141">MyApp *MyApp* klasöründe hala uygulamayı çalıştırın [`dotnet run`](../tools/dotnet-run.md) ve otomatik olarak yüklenir ve çalışma zamanında önceden oluşturulmuş serializer'leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="a395e-141">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="a395e-142">Konsol pencerenize aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="a395e-142">Type the following command in your console window:</span></span>

```dotnetcli
dotnet run
```

> [!NOTE]
> <span data-ttu-id="a395e-143">[`dotnet run`](../tools/dotnet-run.md)yapı [`dotnet build`](../tools/dotnet-build.md) hedeflerinin oluşturulup, hedef uygulamayı çalıştırmak `dotnet <assembly.dll>` için çağrıda bulunulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a395e-143">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a395e-144">Uygulamanızı çalıştırmak için bu öğreticide gösterilen komutlar ve adımlar yalnızca geliştirme süresi boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a395e-144">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="a395e-145">Uygulamanızı dağıtmaya hazır olduğunuzda,.NET Core uygulamaları ve komutu için farklı [`dotnet publish`](../tools/dotnet-publish.md) [dağıtım stratejilerine](../deploying/index.md) göz atın.</span><span class="sxs-lookup"><span data-stu-id="a395e-145">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="a395e-146">Her şey başarılı olursa, çıkış klasöründe *MyApp.XmlSerializers.dll* adında bir derleme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a395e-146">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span>

<span data-ttu-id="a395e-147">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="a395e-147">Congratulations!</span></span> <span data-ttu-id="a395e-148">Sadece var:</span><span class="sxs-lookup"><span data-stu-id="a395e-148">You have just:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a395e-149">Bir .NET Core uygulaması oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="a395e-149">Created a .NET Core app.</span></span>
> - <span data-ttu-id="a395e-150">Microsoft.XmlSerializer.Generator paketine bir başvuru eklendi.</span><span class="sxs-lookup"><span data-stu-id="a395e-150">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> - <span data-ttu-id="a395e-151">Bağımlılıkları eklemek için MyApp.csproj'unuzu düzenlediniz.</span><span class="sxs-lookup"><span data-stu-id="a395e-151">Edited your MyApp.csproj to add dependencies.</span></span>
> - <span data-ttu-id="a395e-152">Bir sınıf ve xmlSerializer eklendi.</span><span class="sxs-lookup"><span data-stu-id="a395e-152">Added a class and an XmlSerializer.</span></span>
> - <span data-ttu-id="a395e-153">Uygulamayı oluşturup çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a395e-153">Built and ran the application.</span></span>

## <a name="related-resources"></a><span data-ttu-id="a395e-154">İlgili kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a395e-154">Related resources</span></span>

- [<span data-ttu-id="a395e-155">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="a395e-155">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="a395e-156">XmlSerializer (C#) kullanarak serileştirme</span><span class="sxs-lookup"><span data-stu-id="a395e-156">How to serialize using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [<span data-ttu-id="a395e-157">Nasıl yapılır: XmlSerializer kullanarak Serialize (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a395e-157">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
