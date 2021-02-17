---
title: C# ' ye giriş-geliştirme araçları hakkında bilgi sahibi olun
description: Bu makalede, makinenizde C# ve .NET uygulamaları geliştirmek için kullanacağınız araçlara temel bir giriş sunulmaktadır.
ms.date: 02/02/2021
ms.openlocfilehash: 72116154126b0a97fffe417b2807576b1d9689df
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100626811"
---
# <a name="set-up-your-local-environment"></a><span data-ttu-id="8bc5f-103">Yerel ortamınızı ayarlama</span><span class="sxs-lookup"><span data-stu-id="8bc5f-103">Set up your local environment</span></span>

<span data-ttu-id="8bc5f-104">Makinenizde bir öğretici çalıştırmanın ilk adımı bir geliştirme ortamı kurmak.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-104">The first step in running a tutorial on your machine is to set up a development environment.</span></span> <span data-ttu-id="8bc5f-105">Aşağıdaki seçeneklerden birini belirleyin:</span><span class="sxs-lookup"><span data-stu-id="8bc5f-105">Choose one of the following alternatives:</span></span>

* <span data-ttu-id="8bc5f-106">.NET CLı 'yı ve seçtiğiniz metin veya kod düzenleyicisini kullanmak için bkz. [10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).net öğreticisi Merhaba dünya.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-106">To use the .NET CLI and your choice of text or code editor, see the .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).</span></span> <span data-ttu-id="8bc5f-107">Öğreticide, Windows, Linux veya macOS 'ta bir geliştirme ortamı ayarlamaya yönelik yönergeler bulunur.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-107">The tutorial has instructions for setting up a development environment on Windows, Linux, or macOS.</span></span>
* <span data-ttu-id="8bc5f-108">.NET CLı ve Visual Studio Code kullanmak için [.NET SDK](https://dotnet.microsoft.com/download) ve [Visual Studio Code](https://code.visualstudio.com/)' yi yükleyip.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-108">To use the .NET CLI and Visual Studio Code, install the [.NET SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com/).</span></span>
* <span data-ttu-id="8bc5f-109">Visual Studio 2019 ' i kullanmak için bkz. [öğretici: Visual Studio 'da basit bir C# konsol uygulaması oluşturma](/visualstudio/get-started/csharp/tutorial-console).</span><span class="sxs-lookup"><span data-stu-id="8bc5f-109">To use Visual Studio 2019, see [Tutorial: Create a simple C# console app in Visual Studio](/visualstudio/get-started/csharp/tutorial-console).</span></span>

## <a name="basic-application-development-flow"></a><span data-ttu-id="8bc5f-110">Temel uygulama geliştirme akışı</span><span class="sxs-lookup"><span data-stu-id="8bc5f-110">Basic application development flow</span></span>

<span data-ttu-id="8bc5f-111">Bu öğreticilerde yer alan yönergeler, uygulamaları oluşturmak, derlemek ve çalıştırmak için .NET CLı kullandığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-111">The instructions in these tutorials assume that you're using the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="8bc5f-112">Aşağıdaki komutları kullanacaksınız:</span><span class="sxs-lookup"><span data-stu-id="8bc5f-112">You'll use the following commands:</span></span>

* <span data-ttu-id="8bc5f-113">[`dotnet new`](../../../core/tools/dotnet-new.md) bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-113">[`dotnet new`](../../../core/tools/dotnet-new.md) creates an application.</span></span> <span data-ttu-id="8bc5f-114">Bu komut, uygulamanız için gerekli olan dosyaları ve varlıkları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-114">This command generates the files and assets necessary for your application.</span></span> <span data-ttu-id="8bc5f-115">C# öğreticilerine giriş, `console` uygulama türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-115">The introduction to C# tutorials all use the `console` application type.</span></span> <span data-ttu-id="8bc5f-116">Temel bilgileri aldıktan sonra diğer uygulama türlerine genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-116">Once you've got the basics, you can expand to other application types.</span></span>
* <span data-ttu-id="8bc5f-117">[`dotnet build`](../../../core/tools/dotnet-build.md) yürütülebilir dosyayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-117">[`dotnet build`](../../../core/tools/dotnet-build.md) builds the executable.</span></span>
* <span data-ttu-id="8bc5f-118">[`dotnet run`](../../../core/tools/dotnet-run.md) yürütülebilir dosyayı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-118">[`dotnet run`](../../../core/tools/dotnet-run.md) runs the executable.</span></span>

<span data-ttu-id="8bc5f-119">Bu öğreticiler için Visual Studio 2019 kullanıyorsanız, bir öğretici bu CLı komutlarından birini çalıştırmaya yönlendirirse bir Visual Studio menü seçimi seçersiniz:</span><span class="sxs-lookup"><span data-stu-id="8bc5f-119">If you use Visual Studio 2019 for these tutorials, you'll choose a Visual Studio menu selection when a tutorial directs you to run one of these CLI commands:</span></span>

* <span data-ttu-id="8bc5f-120">**Dosya**  >  **Yeni**  >  **Proje** bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-120">**File** > **New** > **Project** creates an application.</span></span>
* <span data-ttu-id="8bc5f-121">**Derleme**  >   **Yapı çözümü** yürütülebilir dosyayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-121">**Build** >  **Build Solution** builds the executable.</span></span>
* <span data-ttu-id="8bc5f-122">**Hata Ayıkla**  >  **Hata ayıklama olmadan Başlat** yürütülebilir dosyayı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-122">**Debug** > **Start Without Debugging** runs the executable.</span></span>

## <a name="pick-your-tutorial"></a><span data-ttu-id="8bc5f-123">Öğreticinizi seçin</span><span class="sxs-lookup"><span data-stu-id="8bc5f-123">Pick your tutorial</span></span>

<span data-ttu-id="8bc5f-124">Aşağıdaki öğreticilerden herhangi biriyle başlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8bc5f-124">You can start with any of the following tutorials:</span></span>

## <a name="numbers-in-c"></a><span data-ttu-id="8bc5f-125">C 'deki sayılar\#</span><span class="sxs-lookup"><span data-stu-id="8bc5f-125">Numbers in C\#</span></span>

<span data-ttu-id="8bc5f-126">C# öğreticisindeki [sayılarda](numbers-in-csharp-local.md) , bilgisayarların sayıları nasıl depolayacağınızı ve farklı sayısal türlerle hesaplamaların nasıl gerçekleştirileceğini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-126">In the [Numbers in C#](numbers-in-csharp-local.md) tutorial, you'll learn how computers store numbers and how to perform calculations with different numeric types.</span></span> <span data-ttu-id="8bc5f-127">Yuvarlama hakkında temel bilgileri ve C# kullanarak matematik hesaplamaları yapmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-127">You'll learn the basics of rounding and how to perform mathematical calculations using C#.</span></span>

<span data-ttu-id="8bc5f-128">Bu öğreticide, [Hello World](hello-world.yml) ders 'i tamamladığınız varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-128">This tutorial assumes that you have finished the [Hello world](hello-world.yml) lesson.</span></span>

## <a name="branches-and-loops"></a><span data-ttu-id="8bc5f-129">Dal ve döngüler</span><span class="sxs-lookup"><span data-stu-id="8bc5f-129">Branches and loops</span></span>

<span data-ttu-id="8bc5f-130">[Dallar ve döngüler](branches-and-loops-local.md) öğreticisinde, değişkenlerde depolanan değerlere göre farklı kod yürütme yolları seçmenin temelleri öğretilir.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-130">The [Branches and loops](branches-and-loops-local.md) tutorial teaches the basics of selecting different paths of code execution based on the values stored in variables.</span></span> <span data-ttu-id="8bc5f-131">Denetim akışının temel bilgilerini öğrenirsiniz. Bu, programların kararlar alma ve farklı eylemler seçme işlemlerinin temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-131">You'll learn the basics of control flow, which is the basis of how programs make decisions and choose different actions.</span></span>

<span data-ttu-id="8bc5f-132">Bu öğreticide, [Hello World](hello-world.yml) ve C# dersleri Ile ilgili [sayıların](numbers-in-csharp-local.md) tamamlandığını varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-132">This tutorial assumes that you have finished the [Hello world](hello-world.yml) and [Numbers in C#](numbers-in-csharp-local.md) lessons.</span></span>

## <a name="list-collection"></a><span data-ttu-id="8bc5f-133">Liste koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="8bc5f-133">List collection</span></span>

<span data-ttu-id="8bc5f-134">[Liste koleksiyonu](arrays-and-collections.md) dersi, veri dizilerini depolayan liste koleksiyonu türünün bir turuna sahip olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-134">The [List collection](arrays-and-collections.md) lesson gives you a tour of the List collection type that stores sequences of data.</span></span> <span data-ttu-id="8bc5f-135">Öğe ekleme ve kaldırma, öğe arama ve listeleri sıralama hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-135">You'll learn how to add and remove items, search for items, and sort the lists.</span></span> <span data-ttu-id="8bc5f-136">Farklı liste türleri keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-136">You'll explore different kinds of lists.</span></span>

<span data-ttu-id="8bc5f-137">Bu öğreticide, yukarıda listelenen dersleri tamamladığınız varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8bc5f-137">This tutorial assumes that you have finished the lessons listed above.</span></span>
