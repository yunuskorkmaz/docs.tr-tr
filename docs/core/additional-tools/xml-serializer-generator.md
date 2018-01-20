---
title: ".NET Core üzerinde Microsoft XML seri hale getirici oluşturucusunu kullanarak"
description: "Microsoft XML seri hale getirici Oluşturucu genel bakış."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2017
ms.topic: tutorial
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 4b838cafe1f4835c1c5aa6086c0997a4a9e39a9e
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2018
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="327f9-103">.NET Core üzerinde Microsoft XML seri hale getirici oluşturucusunu kullanarak</span><span class="sxs-lookup"><span data-stu-id="327f9-103">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="327f9-104">Bu öğretici bir C# .NET Core uygulamasında Microsoft XML seri hale getirici Oluşturucu kullanmayı öğretir.</span><span class="sxs-lookup"><span data-stu-id="327f9-104">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="327f9-105">Bu öğreticinin sürecinde size bilgi edinin:</span><span class="sxs-lookup"><span data-stu-id="327f9-105">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="327f9-106">.NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="327f9-106">How to create a .NET Core app</span></span>
> * <span data-ttu-id="327f9-107">Microsoft.XmlSerializer.Generator paketine başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="327f9-107">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> * <span data-ttu-id="327f9-108">Bağımlılıkları eklemek için MyApp.csproj düzenleme</span><span class="sxs-lookup"><span data-stu-id="327f9-108">How to edit your MyApp.csproj to add dependencies</span></span>
> * <span data-ttu-id="327f9-109">Bir sınıf ve XmlSerializer ekleme</span><span class="sxs-lookup"><span data-stu-id="327f9-109">How to add a class and an XmlSerializer</span></span>
> * <span data-ttu-id="327f9-110">Derleme ve uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="327f9-110">How to build and run the application</span></span> 

<span data-ttu-id="327f9-111">Gibi [Xml seri hale getirici Oluşturucu (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) .NET Framework için [Microsoft.XmlSerializer.Generator NuGet paketi](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) .NET Core ve .NET standart projeleri için eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="327f9-111">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="327f9-112">XML serileştirme bütünleştirilmiş serileştirmek veya seri durumundan kullanarak bu tür nesneler XML serileştirme başlangıç performansını artırmak için bir derlemede bulunan türleri için oluşturduğu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="327f9-112">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="327f9-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="327f9-113">Prerequisites</span></span>

<span data-ttu-id="327f9-114">Bu öğreticiyi tamamlamak için:</span><span class="sxs-lookup"><span data-stu-id="327f9-114">To complete this tutorial:</span></span>

* <span data-ttu-id="327f9-115">Yükleme [.NET Core SDK 2.1.3 veya daha yenisi](https://www.microsoft.com/net/download)</span><span class="sxs-lookup"><span data-stu-id="327f9-115">Install [.NET Core SDK 2.1.3 or later](https://www.microsoft.com/net/download)</span></span>
* <span data-ttu-id="327f9-116">Henüz yapmadıysanız, sık kullanılan kod düzenleyicisinde yükleyin.</span><span class="sxs-lookup"><span data-stu-id="327f9-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="327f9-117">Kod Düzenleyicisi yüklemeniz gerekiyor?</span><span class="sxs-lookup"><span data-stu-id="327f9-117">Need to install a code editor?</span></span> <span data-ttu-id="327f9-118">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span><span class="sxs-lookup"><span data-stu-id="327f9-118">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>
  
## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="327f9-119">Microsoft XML seri hale getirici oluşturucuyu bir .NET Core konsol uygulamasında kullanma</span><span class="sxs-lookup"><span data-stu-id="327f9-119">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span> 

<span data-ttu-id="327f9-120">Aşağıdaki yönergeler XML seri hale getirici oluşturucuyu bir .NET Core konsol uygulamasında kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="327f9-120">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="327f9-121">Bir .NET Core konsol uygulaması oluşturun</span><span class="sxs-lookup"><span data-stu-id="327f9-121">Create a .NET Core console application</span></span>

<span data-ttu-id="327f9-122">Bir komut istemi açın ve adlı bir klasör oluşturun *Uygulamam*.</span><span class="sxs-lookup"><span data-stu-id="327f9-122">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="327f9-123">Oluşturduğunuz klasöre gidin ve aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="327f9-123">Navigate to the folder you created and type the following command:</span></span>

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="327f9-124">Uygulamam projesinde Microsoft.XmlSerializer.Generator paketine bir başvuru ekleyin</span><span class="sxs-lookup"><span data-stu-id="327f9-124">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="327f9-125">Kullanım [ `dotnet add package` ](../tools//dotnet-add-package.md) başvuru projenize eklemek için komutu.</span><span class="sxs-lookup"><span data-stu-id="327f9-125">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span> 

<span data-ttu-id="327f9-126">Tür:</span><span class="sxs-lookup"><span data-stu-id="327f9-126">Type:</span></span>
 
 ```console
 dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
 ```
 
### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="327f9-127">Paket eklendikten sonra MyApp.csproj değişiklikleri doğrulayın</span><span class="sxs-lookup"><span data-stu-id="327f9-127">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="327f9-128">Kod Düzenleyicisi'ni açın ve başlayalım!</span><span class="sxs-lookup"><span data-stu-id="327f9-128">Open your code editor and let's get started!</span></span> <span data-ttu-id="327f9-129">Hala gelen çalışıyoruz *Uygulamam* biz yerleşik uygulama dizini.</span><span class="sxs-lookup"><span data-stu-id="327f9-129">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="327f9-130">Açık *MyApp.csproj* metin düzenleyicinizde.</span><span class="sxs-lookup"><span data-stu-id="327f9-130">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="327f9-131">Çalıştırdıktan sonra [ `dotnet add package` ](../tools//dotnet-add-package.md) komutu, aşağıdaki satırları eklenir, *MyApp.csproj* proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="327f9-131">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="327f9-132">.NET Core CLI aracı desteği için başka bir ItemGroup Bölüm Ekle</span><span class="sxs-lookup"><span data-stu-id="327f9-132">Add another ItemGroup section for .NET Core CLI Tool support</span></span>
 
 <span data-ttu-id="327f9-133">Sonra aşağıdaki satırları ekleyin `ItemGroup` biz Denetlenmekte bölümü:</span><span class="sxs-lookup"><span data-stu-id="327f9-133">Add the following lines after the `ItemGroup` section that we inspected:</span></span>
 
 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-a-class-in-the-application"></a><span data-ttu-id="327f9-134">Uygulamada bir sınıf ekleyin</span><span class="sxs-lookup"><span data-stu-id="327f9-134">Add a class in the application</span></span>

<span data-ttu-id="327f9-135">Açık *Program.cs* metin düzenleyicinizde.</span><span class="sxs-lookup"><span data-stu-id="327f9-135">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="327f9-136">Adlı sınıf ekleme *MyClass* içinde *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="327f9-136">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="327f9-137">Oluşturma bir `XmlSerializer` MyClass için</span><span class="sxs-lookup"><span data-stu-id="327f9-137">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="327f9-138">İçinde aşağıdaki satırı ekleyin *ana* oluşturmak için bir `XmlSerializer` MyClass için:</span><span class="sxs-lookup"><span data-stu-id="327f9-138">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="327f9-139">Derleme ve uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="327f9-139">Build and run the application</span></span>

<span data-ttu-id="327f9-140">İçinde hala *Uygulamam* klasörü aracılığıyla uygulamayı çalıştırın, [ `dotnet run` ](../tools/dotnet-run.md) ve otomatik olarak yükler ve çalışma zamanında önceden oluşturulmuş serileştiricileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="327f9-140">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="327f9-141">Konsol penceresinde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="327f9-141">Type the following command in your console window:</span></span>

 ```console
 $ dotnet run
 ```
> [!NOTE]
> <span data-ttu-id="327f9-142">[`dotnet run`](../tools/dotnet-run.md)çağrıları [ `dotnet build` ](../tools/dotnet-build.md) hedefleri yerleşik yapı ve çağrıları emin olmak için `dotnet <assembly.dll>` hedef uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="327f9-142">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="327f9-143">Komutlar ve uygulamanızı çalıştırmak için Bu öğreticide gösterilen adımlar yalnızca geliştirme zamanı sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="327f9-143">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="327f9-144">Uygulamanızı dağıtmak hazır olduğunuzda, farklı bir göz atalım [dağıtım stratejilerini](../deploying/index.md) .NET Core uygulamaları için ve [ `dotnet publish` ](../tools/dotnet-publish.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="327f9-144">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="327f9-145">Her şeyi başarılı olursa, adlı bir derleme *MyApp.XmlSerializers.dll* çıkış klasöründe oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="327f9-145">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span> 



<span data-ttu-id="327f9-146">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="327f9-146">Congratulations!</span></span> <span data-ttu-id="327f9-147">yalnızca gerekir:</span><span class="sxs-lookup"><span data-stu-id="327f9-147">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="327f9-148">Bir .NET oluşturulan çekirdek uygulama.</span><span class="sxs-lookup"><span data-stu-id="327f9-148">Created a .NET Core app.</span></span>
> * <span data-ttu-id="327f9-149">Microsoft.XmlSerializer.Generator paketine bir başvuru eklenir.</span><span class="sxs-lookup"><span data-stu-id="327f9-149">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> * <span data-ttu-id="327f9-150">Bağımlılıkları eklemek için MyApp.csproj düzenlenemez.</span><span class="sxs-lookup"><span data-stu-id="327f9-150">Edited your MyApp.csproj to add dependencies.</span></span>
> * <span data-ttu-id="327f9-151">Bir sınıf ve XmlSerializer eklendi.</span><span class="sxs-lookup"><span data-stu-id="327f9-151">Added a class and an XmlSerializer.</span></span>
> * <span data-ttu-id="327f9-152">Yerleşik ve uygulama çalıştırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="327f9-152">Built and ran the application.</span></span> 

## <a name="related-resources"></a><span data-ttu-id="327f9-153">İlgili Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="327f9-153">Related Resources</span></span>

* [<span data-ttu-id="327f9-154">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="327f9-154">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
* [<span data-ttu-id="327f9-155">Nasıl yapılır: XmlSerializer (C#) kullanarak serileştirme</span><span class="sxs-lookup"><span data-stu-id="327f9-155">How to: Serialize Using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer)
* [<span data-ttu-id="327f9-156">Nasıl yapılır: XmlSerializer (Visual Basic) kullanarak serileştirme</span><span class="sxs-lookup"><span data-stu-id="327f9-156">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer)