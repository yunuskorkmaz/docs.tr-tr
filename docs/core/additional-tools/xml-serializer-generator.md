---
title: Microsoft XML seri hale getirici Oluşturucusu
description: Microsoft XML seri hale getirici oluşturucusuna genel bakış. Projenizde bulunan türler için bir XML serileştirme derlemesi oluşturmak üzere XML seri hale getirici oluşturucusunu kullanın.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: efa0925a96fcdd4356109632fa77199edde73c26
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284292"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="4c04a-104">.NET Core 'da Microsoft XML serileştirici üreticisini kullanma</span><span class="sxs-lookup"><span data-stu-id="4c04a-104">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="4c04a-105">Bu öğretici, bir C# .NET Core uygulamasında Microsoft XML seri hale getirici oluşturucusunu nasıl kullanacağınızı öğretir.</span><span class="sxs-lookup"><span data-stu-id="4c04a-105">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="4c04a-106">Bu öğreticinin kursu boyunca şunları öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4c04a-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="4c04a-107">.NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="4c04a-107">How to create a .NET Core app</span></span>
> - <span data-ttu-id="4c04a-108">Microsoft.XmlSerializer.Generator paketine başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="4c04a-108">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> - <span data-ttu-id="4c04a-109">Bağımlılık eklemek için MyApp.csproj dosyanızı düzenleme</span><span class="sxs-lookup"><span data-stu-id="4c04a-109">How to edit your MyApp.csproj to add dependencies</span></span>
> - <span data-ttu-id="4c04a-110">Sınıf ve XmlSerializer ekleme</span><span class="sxs-lookup"><span data-stu-id="4c04a-110">How to add a class and an XmlSerializer</span></span>
> - <span data-ttu-id="4c04a-111">Uygulamayı derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4c04a-111">How to build and run the application</span></span>

<span data-ttu-id="4c04a-112">.NET Framework için [XML serileştirici Oluşturucu (SGen. exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) gibi, [Microsoft. XmlSerializer. Generator NuGet paketi](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) .NET Core ve .NET Standard projelerine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="4c04a-112">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="4c04a-113">Kullanarak bu türlerin nesnelerini serileştirmek veya serileştirmek durumunda XML serileştirmesinin başlangıç performansını geliştirmek için bir derlemede bulunan türler için bir XML serileştirme bütünleştirilmiş kodu oluşturur <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="4c04a-113">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4c04a-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="4c04a-114">Prerequisites</span></span>

<span data-ttu-id="4c04a-115">Bu öğreticiyi tamamlamak için:</span><span class="sxs-lookup"><span data-stu-id="4c04a-115">To complete this tutorial:</span></span>

- <span data-ttu-id="4c04a-116">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="4c04a-116">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later.</span></span>
- <span data-ttu-id="4c04a-117">En sevdiğiniz kod düzenleyiciniz.</span><span class="sxs-lookup"><span data-stu-id="4c04a-117">Your favorite code editor.</span></span>

> [!TIP]
> <span data-ttu-id="4c04a-118">Bir kod Düzenleyicisi yüklemeniz mı gerekiyor?</span><span class="sxs-lookup"><span data-stu-id="4c04a-118">Need to install a code editor?</span></span> <span data-ttu-id="4c04a-119">[Visual Studio 'yu](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)deneyin!</span><span class="sxs-lookup"><span data-stu-id="4c04a-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="4c04a-120">.NET Core konsol uygulamasında Microsoft XML serileştirici oluşturucusunu kullanma</span><span class="sxs-lookup"><span data-stu-id="4c04a-120">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span>

<span data-ttu-id="4c04a-121">Aşağıdaki yönergelerde, bir .NET Core konsol uygulamasında XML serileştirici oluşturucunun nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4c04a-121">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="4c04a-122">.NET Core konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="4c04a-122">Create a .NET Core console application</span></span>

<span data-ttu-id="4c04a-123">Bir komut istemi açın ve *MyApp*adlı bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4c04a-123">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="4c04a-124">Oluşturduğunuz klasöre gidin ve aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="4c04a-124">Navigate to the folder you created and type the following command:</span></span>

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="4c04a-125">MyApp projesindeki Microsoft. XmlSerializer. Generator paketine bir başvuru ekleyin</span><span class="sxs-lookup"><span data-stu-id="4c04a-125">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="4c04a-126">[`dotnet add package`](../tools/dotnet-add-package.md)Başvurusunu projenize eklemek için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c04a-126">Use the [`dotnet add package`](../tools/dotnet-add-package.md) command to add the reference in your project.</span></span>

<span data-ttu-id="4c04a-127">Şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="4c04a-127">Type:</span></span>

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="4c04a-128">Paketi ekledikten sonra MyApp. csproj üzerinde yapılan değişiklikleri doğrulayın</span><span class="sxs-lookup"><span data-stu-id="4c04a-128">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="4c04a-129">Kod düzenleyicinizi açın ve Haydi başlayın!</span><span class="sxs-lookup"><span data-stu-id="4c04a-129">Open your code editor and let's get started!</span></span> <span data-ttu-id="4c04a-130">Uygulamayı geliştirdiğimiz *MyApp* dizininden çalışmaya devam ediyoruz.</span><span class="sxs-lookup"><span data-stu-id="4c04a-130">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="4c04a-131">Metin düzenleyicinizde *MyApp. csproj* ' yı açın.</span><span class="sxs-lookup"><span data-stu-id="4c04a-131">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="4c04a-132">Komutu çalıştırdıktan sonra [`dotnet add package`](../tools/dotnet-add-package.md) , aşağıdaki satırlar *MyApp. csproj* proje dosyanıza eklenir:</span><span class="sxs-lookup"><span data-stu-id="4c04a-132">After running the [`dotnet add package`](../tools/dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="4c04a-133">.NET Core CLI araç desteği için başka bir ItemGroup bölümü ekleme</span><span class="sxs-lookup"><span data-stu-id="4c04a-133">Add another ItemGroup section for .NET Core CLI Tool support</span></span>

<span data-ttu-id="4c04a-134">İncelenen bölümden sonra aşağıdaki satırları ekleyin `ItemGroup` :</span><span class="sxs-lookup"><span data-stu-id="4c04a-134">Add the following lines after the `ItemGroup` section that we inspected:</span></span>

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a><span data-ttu-id="4c04a-135">Uygulamaya bir sınıf ekleme</span><span class="sxs-lookup"><span data-stu-id="4c04a-135">Add a class in the application</span></span>

<span data-ttu-id="4c04a-136">Metin düzenleyicinizde *program.cs* öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="4c04a-136">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="4c04a-137">*Program.cs*içinde *MyClass* adlı sınıfı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c04a-137">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="4c04a-138">`XmlSerializer`MyClass için oluşturma</span><span class="sxs-lookup"><span data-stu-id="4c04a-138">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="4c04a-139">MyClass için şunu oluşturmak üzere *Main* içinde aşağıdaki satırı ekleyin `XmlSerializer` :</span><span class="sxs-lookup"><span data-stu-id="4c04a-139">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="4c04a-140">Uygulamayı derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4c04a-140">Build and run the application</span></span>

<span data-ttu-id="4c04a-141">Hala *MyApp* klasöründe, uygulamayı ile çalıştırın [`dotnet run`](../tools/dotnet-run.md) ve çalışma zamanında önceden oluşturulmuş serileştiricileri otomatik olarak yükler ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="4c04a-141">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at run time.</span></span>

<span data-ttu-id="4c04a-142">Konsol pencerenize aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="4c04a-142">Type the following command in your console window:</span></span>

```dotnetcli
dotnet run
```

> [!NOTE]
> <span data-ttu-id="4c04a-143">[`dotnet run`](../tools/dotnet-run.md)[`dotnet build`](../tools/dotnet-build.md)derleme hedeflerinin oluşturulduğundan emin olmak için çağrılar yapın ve ardından `dotnet <assembly.dll>` Hedef uygulamayı çalıştırmak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="4c04a-143">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4c04a-144">Uygulamanızı çalıştırmak için bu öğreticide gösterilen komutlar ve adımlar yalnızca geliştirme zamanı sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c04a-144">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="4c04a-145">Uygulamanızı dağıtmaya hazırsanız, .NET Core Uygulamaları ve komutu için farklı [dağıtım stratejilerine](../deploying/index.md) göz atın [`dotnet publish`](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="4c04a-145">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="4c04a-146">Her şey başarılı olursa, çıkış klasöründe *MyApp. Xmlserileştiriciler. dll* adlı bir derleme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4c04a-146">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span>

<span data-ttu-id="4c04a-147">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="4c04a-147">Congratulations!</span></span> <span data-ttu-id="4c04a-148">Yalnızca şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="4c04a-148">You have just:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="4c04a-149">.NET Core uygulaması oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="4c04a-149">Created a .NET Core app.</span></span>
> - <span data-ttu-id="4c04a-150">Microsoft. XmlSerializer. Generator paketine bir başvuru eklendi.</span><span class="sxs-lookup"><span data-stu-id="4c04a-150">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> - <span data-ttu-id="4c04a-151">Bağımlılıklar eklemek için MyApp. csproj dosyanızı düzenlendi.</span><span class="sxs-lookup"><span data-stu-id="4c04a-151">Edited your MyApp.csproj to add dependencies.</span></span>
> - <span data-ttu-id="4c04a-152">Bir sınıf ve XmlSerializer eklendi.</span><span class="sxs-lookup"><span data-stu-id="4c04a-152">Added a class and an XmlSerializer.</span></span>
> - <span data-ttu-id="4c04a-153">Uygulamayı oluşturulup çalıştırdık.</span><span class="sxs-lookup"><span data-stu-id="4c04a-153">Built and ran the application.</span></span>

## <a name="related-resources"></a><span data-ttu-id="4c04a-154">İlgili kaynaklar</span><span class="sxs-lookup"><span data-stu-id="4c04a-154">Related resources</span></span>

- [<span data-ttu-id="4c04a-155">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="4c04a-155">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="4c04a-156">XmlSerializer kullanarak serileştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="4c04a-156">How to serialize using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [<span data-ttu-id="4c04a-157">Nasıl yapılır: XmlSerializer kullanarak serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c04a-157">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
