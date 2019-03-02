---
title: Microsoft XML serileştirici Oluşturucusu
description: Microsoft XML seri hale getirici oluşturucunun bir genel bakış. XML seri hale getirici oluşturucunun bir XML serileştirme derleme projenizde yer alan türleri oluşturmak için kullanın.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: e5b41b6e5d747cd99a80930bb64e36839af4ab66
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57211903"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="8bb04-104">Microsoft XML seri hale getirici oluşturucunun üzerinde .NET Core kullanma</span><span class="sxs-lookup"><span data-stu-id="8bb04-104">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="8bb04-105">Bu öğreticide, Microsoft XML seri hale getirici oluşturucunun kullanılacağını öğretir bir C# .NET Core uygulaması.</span><span class="sxs-lookup"><span data-stu-id="8bb04-105">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="8bb04-106">Bu öğreticinin Kurs sırasında şunları öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8bb04-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="8bb04-107">.NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="8bb04-107">How to create a .NET Core app</span></span>
> * <span data-ttu-id="8bb04-108">Microsoft.XmlSerializer.Generator paketine bir başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="8bb04-108">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> * <span data-ttu-id="8bb04-109">Bağımlılıklar eklemek için MyApp.csproj düzenleme</span><span class="sxs-lookup"><span data-stu-id="8bb04-109">How to edit your MyApp.csproj to add dependencies</span></span>
> * <span data-ttu-id="8bb04-110">Bir sınıf ve XmlSerializer ekleme</span><span class="sxs-lookup"><span data-stu-id="8bb04-110">How to add a class and an XmlSerializer</span></span>
> * <span data-ttu-id="8bb04-111">Nasıl uygulaması derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="8bb04-111">How to build and run the application</span></span>

<span data-ttu-id="8bb04-112">Gibi [Xml seri hale getirici oluşturucunun (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) .NET Framework için [Microsoft.XmlSerializer.Generator NuGet paketini](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) için .NET Core ve .NET Standard projelerine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="8bb04-112">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="8bb04-113">Bir XML serileştirme derleme türleri serileştirmek veya seri durumundan kullanarak bu tür nesneler XML serileştirme başlangıç performansını artırmak için bir derlemede yer alan oluşturur <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="8bb04-113">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8bb04-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="8bb04-114">Prerequisites</span></span>

<span data-ttu-id="8bb04-115">Bu öğreticiyi tamamlamak için:</span><span class="sxs-lookup"><span data-stu-id="8bb04-115">To complete this tutorial:</span></span>

* <span data-ttu-id="8bb04-116">[.NET core 2.1 SDK](https://www.microsoft.com/net/download) veya üzeri</span><span class="sxs-lookup"><span data-stu-id="8bb04-116">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later</span></span>
* <span data-ttu-id="8bb04-117">Sık kullandığınız kod düzenleyici.</span><span class="sxs-lookup"><span data-stu-id="8bb04-117">Your favorite code editor.</span></span>

> [!TIP]
> <span data-ttu-id="8bb04-118">Bir kod Düzenleyicisi'ni yüklemeniz gerekir?</span><span class="sxs-lookup"><span data-stu-id="8bb04-118">Need to install a code editor?</span></span> <span data-ttu-id="8bb04-119">Deneyin [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span><span class="sxs-lookup"><span data-stu-id="8bb04-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="8bb04-120">Microsoft XML seri hale getirici oluşturucunun bir .NET Core konsol uygulamasında kullanma</span><span class="sxs-lookup"><span data-stu-id="8bb04-120">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span>

<span data-ttu-id="8bb04-121">Aşağıdaki yönergeler, XML seri hale getirici oluşturucunun bir .NET Core konsol uygulamasında kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="8bb04-121">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="8bb04-122">Bir .NET Core konsol uygulaması oluşturun</span><span class="sxs-lookup"><span data-stu-id="8bb04-122">Create a .NET Core console application</span></span>

<span data-ttu-id="8bb04-123">Bir komut istemi açın ve adlı bir klasör oluşturun *MyApp*.</span><span class="sxs-lookup"><span data-stu-id="8bb04-123">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="8bb04-124">Oluşturduğunuz klasöre gidin ve aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="8bb04-124">Navigate to the folder you created and type the following command:</span></span>

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="8bb04-125">Uygulamam projesinde Microsoft.XmlSerializer.Generator paketine bir başvuru ekleyin</span><span class="sxs-lookup"><span data-stu-id="8bb04-125">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="8bb04-126">Kullanım [ `dotnet add package` ](../tools//dotnet-add-package.md) projenize başvuru eklemek için komutu.</span><span class="sxs-lookup"><span data-stu-id="8bb04-126">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span>

<span data-ttu-id="8bb04-127">Tür:</span><span class="sxs-lookup"><span data-stu-id="8bb04-127">Type:</span></span>

```console
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="8bb04-128">Paket ekledikten sonra değişiklikleri MyApp.csproj doğrulayın</span><span class="sxs-lookup"><span data-stu-id="8bb04-128">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="8bb04-129">Kod Düzenleyicisi'ni açın ve başlayalım!</span><span class="sxs-lookup"><span data-stu-id="8bb04-129">Open your code editor and let's get started!</span></span> <span data-ttu-id="8bb04-130">Hala gelen çalışıyoruz *MyApp* dizin içinde bir uygulama oluşturduk.</span><span class="sxs-lookup"><span data-stu-id="8bb04-130">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="8bb04-131">Açık *MyApp.csproj* metin düzenleyicinizde.</span><span class="sxs-lookup"><span data-stu-id="8bb04-131">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="8bb04-132">Çalıştırdıktan sonra [ `dotnet add package` ](../tools//dotnet-add-package.md) komutu aşağıdaki satırları eklenir, *MyApp.csproj* proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="8bb04-132">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="8bb04-133">.NET Core CLI aracı desteği için başka bir ItemGroup bölümü ekleyin</span><span class="sxs-lookup"><span data-stu-id="8bb04-133">Add another ItemGroup section for .NET Core CLI Tool support</span></span>

<span data-ttu-id="8bb04-134">Sonra aşağıdaki satırları ekleyin `ItemGroup` biz inceledi bölümü:</span><span class="sxs-lookup"><span data-stu-id="8bb04-134">Add the following lines after the `ItemGroup` section that we inspected:</span></span>

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a><span data-ttu-id="8bb04-135">Uygulamada bir sınıf ekleyin</span><span class="sxs-lookup"><span data-stu-id="8bb04-135">Add a class in the application</span></span>

<span data-ttu-id="8bb04-136">Açık *Program.cs* metin düzenleyicinizde.</span><span class="sxs-lookup"><span data-stu-id="8bb04-136">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="8bb04-137">Adlı bir sınıf ekleyin *MyClass* içinde *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="8bb04-137">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="8bb04-138">Oluşturma bir `XmlSerializer` MyClass için</span><span class="sxs-lookup"><span data-stu-id="8bb04-138">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="8bb04-139">Aşağıdaki satırı ekleyin *ana* oluşturmak için bir `XmlSerializer` MyClass için:</span><span class="sxs-lookup"><span data-stu-id="8bb04-139">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="8bb04-140">Uygulaması derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="8bb04-140">Build and run the application</span></span>

<span data-ttu-id="8bb04-141">Yine de içinde *MyApp* aracılığıyla uygulamayı çalıştırın, klasör [ `dotnet run` ](../tools/dotnet-run.md) ve otomatik olarak yükler ve seri hale getiricileri genişletme önceden oluşturulan çalışma zamanında kullanır.</span><span class="sxs-lookup"><span data-stu-id="8bb04-141">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="8bb04-142">Konsol pencerenizde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="8bb04-142">Type the following command in your console window:</span></span>

```console
dotnet run
```

> [!NOTE]
> <span data-ttu-id="8bb04-143">[`dotnet run`](../tools/dotnet-run.md) çağrıları [ `dotnet build` ](../tools/dotnet-build.md) hedefleri oluşturulan derleme ve çağrıları emin olmak için `dotnet <assembly.dll>` hedef uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8bb04-143">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb04-144">Komutlar ve uygulamanızı çalıştırmak için Bu öğreticide gösterilen adımlar yalnızca geliştirme zamanı sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8bb04-144">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="8bb04-145">Uygulamanızı dağıtmak hazır olduğunuzda, farklı bir göz atın [dağıtım stratejilerini](../deploying/index.md) .NET Core uygulamaları için ve [ `dotnet publish` ](../tools/dotnet-publish.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="8bb04-145">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="8bb04-146">Her şeyi başarılı olursa, adında bir derleme *MyApp.XmlSerializers.dll* çıktı klasöründe oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8bb04-146">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span>

<span data-ttu-id="8bb04-147">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="8bb04-147">Congratulations!</span></span> <span data-ttu-id="8bb04-148">yalnızca gerekir:</span><span class="sxs-lookup"><span data-stu-id="8bb04-148">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8bb04-149">Oluşturulan bir .NET Core uygulaması.</span><span class="sxs-lookup"><span data-stu-id="8bb04-149">Created a .NET Core app.</span></span>
> * <span data-ttu-id="8bb04-150">Microsoft.XmlSerializer.Generator paketine bir başvuru eklenir.</span><span class="sxs-lookup"><span data-stu-id="8bb04-150">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> * <span data-ttu-id="8bb04-151">Bağımlılıklar eklemek için MyApp.csproj düzenlendi.</span><span class="sxs-lookup"><span data-stu-id="8bb04-151">Edited your MyApp.csproj to add dependencies.</span></span>
> * <span data-ttu-id="8bb04-152">Bir sınıf ve XmlSerializer eklendi.</span><span class="sxs-lookup"><span data-stu-id="8bb04-152">Added a class and an XmlSerializer.</span></span>
> * <span data-ttu-id="8bb04-153">Yerleşik ve uygulamayı çalıştırdınız.</span><span class="sxs-lookup"><span data-stu-id="8bb04-153">Built and ran the application.</span></span>

## <a name="related-resources"></a><span data-ttu-id="8bb04-154">İlgili kaynaklar</span><span class="sxs-lookup"><span data-stu-id="8bb04-154">Related resources</span></span>

* [<span data-ttu-id="8bb04-155">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="8bb04-155">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
* [<span data-ttu-id="8bb04-156">Nasıl yapılır: XmlSerializer kullanarak serileştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="8bb04-156">How to: Serialize Using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
* [<span data-ttu-id="8bb04-157">Nasıl yapılır: XmlSerializer (Visual Basic) kullanarak seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="8bb04-157">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)