---
title: Uygulamasına C# giriş-geliştirme araçları hakkında bilgi sahibi olma
description: Bu makalede, makinenizde .NET uygulamaları geliştirmek C# için kullanacağınız araçlara temel bir giriş sunulmaktadır.
ms.date: 10/23/2018
ms.openlocfilehash: b18c71c54e4450902f576a1074058abcd5e8aa91
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834086"
---
# <a name="become-familiar-with-the-net-development-tools"></a><span data-ttu-id="64b84-103">.NET geliştirme araçları hakkında bilgi sahibi olun</span><span class="sxs-lookup"><span data-stu-id="64b84-103">Become familiar with the .NET development tools</span></span>

<span data-ttu-id="64b84-104">Makinenizde bir öğretici çalıştırmanın ilk adımı bir geliştirme ortamı kurmak.</span><span class="sxs-lookup"><span data-stu-id="64b84-104">The first step in running a tutorial on your machine is to set up a development environment.</span></span>
<span data-ttu-id="64b84-105">[10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="64b84-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span>

<span data-ttu-id="64b84-106">Alternatif olarak, [.NET Core SDK](https://dotnet.microsoft.com/download) ve [Visual Studio Code](https://code.visualstudio.com/)yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64b84-106">Alternatively, you can install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="basic-application-development-flow"></a><span data-ttu-id="64b84-107">Temel uygulama geliştirme akışı</span><span class="sxs-lookup"><span data-stu-id="64b84-107">Basic application development flow</span></span>

<span data-ttu-id="64b84-108">[@No__t-1](../../../core/tools/dotnet-new.md) komutunu kullanarak uygulamalar oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="64b84-108">You'll create applications using the [`dotnet new`](../../../core/tools/dotnet-new.md) command.</span></span> <span data-ttu-id="64b84-109">Bu komut, uygulamanız için gerekli olan dosyaları ve varlıkları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="64b84-109">This command generates the files and assets necessary for your application.</span></span> <span data-ttu-id="64b84-110">C# Öğreticilere giriş, `console` uygulama türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="64b84-110">The introduction to C# tutorials all use the `console` application type.</span></span> <span data-ttu-id="64b84-111">Temel bilgileri aldıktan sonra diğer uygulama türlerine genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64b84-111">Once you've got the basics, you can expand to other application types.</span></span>

<span data-ttu-id="64b84-112">Kullanacağınız diğer komutlar yürütülebilir dosyayı oluşturmak için [`dotnet build`](../../../core/tools/dotnet-build.md) ve çalıştırılabilir dosyayı çalıştırmak için [3 @no__t](../../../core/tools/dotnet-run.md) .</span><span class="sxs-lookup"><span data-stu-id="64b84-112">The other commands you'll use are [`dotnet build`](../../../core/tools/dotnet-build.md) to build the executable, and [`dotnet run`](../../../core/tools/dotnet-run.md) to run the executable.</span></span>

## <a name="pick-your-tutorial"></a><span data-ttu-id="64b84-113">Öğreticinizi seçin</span><span class="sxs-lookup"><span data-stu-id="64b84-113">Pick your tutorial</span></span>

<span data-ttu-id="64b84-114">Aşağıdaki öğreticilerden herhangi biriyle başlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="64b84-114">You can start with any of the following tutorials:</span></span>

## <a name="numbers-in-cnumbers-in-csharp-localmd"></a>[<span data-ttu-id="64b84-115">İçindeki sayılarC#</span><span class="sxs-lookup"><span data-stu-id="64b84-115">Numbers in C#</span></span>](numbers-in-csharp-local.md)

<span data-ttu-id="64b84-116">Öğreticideki [sayılarda C# ](numbers-in-csharp-local.md) , bilgisayarların sayıları nasıl depolayacağınızı ve farklı sayısal türlerle hesaplamaların nasıl gerçekleştirileceğini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="64b84-116">In the [Numbers in C#](numbers-in-csharp-local.md) tutorial, you'll learn how computers store numbers and how to perform calculations with different numeric types.</span></span> <span data-ttu-id="64b84-117">' İ yuvarlama hakkında temel bilgileri ve kullanarak C#matematik hesaplamaları yapmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="64b84-117">You'll learn the basics of rounding and how to perform mathematical calculations using C#.</span></span>

<span data-ttu-id="64b84-118">Bu öğreticide, [Hello World](hello-world.yml) ders 'i tamamladığınız varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="64b84-118">This tutorial assumes that you have finished the [Hello world](hello-world.yml) lesson.</span></span>

## <a name="branches-and-loopsbranches-and-loops-localmd"></a>[<span data-ttu-id="64b84-119">Dallar ve döngüler</span><span class="sxs-lookup"><span data-stu-id="64b84-119">Branches and loops</span></span>](branches-and-loops-local.md)

<span data-ttu-id="64b84-120">[Dallar ve döngüler](branches-and-loops-local.md) öğreticisinde, değişkenlerde depolanan değerlere göre farklı kod yürütme yolları seçmenin temelleri öğretilir.</span><span class="sxs-lookup"><span data-stu-id="64b84-120">The [Branches and loops](branches-and-loops-local.md) tutorial teaches the basics of selecting different paths of code execution based on the values stored in variables.</span></span> <span data-ttu-id="64b84-121">Denetim akışının temel bilgilerini öğrenirsiniz. Bu, programların kararlar alma ve farklı eylemler seçme işlemlerinin temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="64b84-121">You'll learn the basics of control flow, which is the basis of how programs make decisions and choose different actions.</span></span>

<span data-ttu-id="64b84-122">Bu öğreticide, [Merhaba Dünya](hello-world.yml) ve derslerin [numaralarını C# ](numbers-in-csharp-local.md) tamamladığınız varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="64b84-122">This tutorial assumes that you have finished the [Hello world](hello-world.yml) and [Numbers in C#](numbers-in-csharp-local.md) lessons.</span></span>

## <a name="list-collectionarrays-and-collectionsmd"></a>[<span data-ttu-id="64b84-123">Liste koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="64b84-123">List collection</span></span>](arrays-and-collections.md)

<span data-ttu-id="64b84-124">[Liste koleksiyonu](arrays-and-collections.md) dersi, veri dizilerini depolayan liste koleksiyonu türünün bir turuna sahip olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="64b84-124">The [List collection](arrays-and-collections.md) lesson gives you a tour of the List collection type that stores sequences of data.</span></span> <span data-ttu-id="64b84-125">Öğe ekleme ve kaldırma, öğe arama ve listeleri sıralama hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="64b84-125">You'll learn how to add and remove items, search for items, and sort the lists.</span></span> <span data-ttu-id="64b84-126">Farklı liste türleri keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64b84-126">You'll explore different kinds of lists.</span></span> 

<span data-ttu-id="64b84-127">Bu öğreticide, yukarıda listelenen dersleri tamamladığınız varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="64b84-127">This tutorial assumes that you have finished the lessons listed above.</span></span>

## <a name="introduction-to-classesintroduction-to-classesmd"></a>[<span data-ttu-id="64b84-128">Sınıflara giriş</span><span class="sxs-lookup"><span data-stu-id="64b84-128">Introduction to classes</span></span>](introduction-to-classes.md)

<span data-ttu-id="64b84-129">C# Öğreticiye en son giriş, kendi yerel geliştirme ortamınız ve .NET Core kullanılarak yalnızca makinenizde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="64b84-129">This final introduction to C# tutorial is only available to run on your machine, using your own local development environment and .NET Core.</span></span>
<span data-ttu-id="64b84-130">Bir konsol uygulaması oluşturup C# dilin parçası olan temel nesne yönelimli özellikleri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="64b84-130">You'll build a console application and see the basic object-oriented features that are part of the C# language.</span></span>
