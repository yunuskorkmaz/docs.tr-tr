---
title: "Hızlı Başlangıç - yerel ortam - C# Kılavuzu"
description: "Bu hızlı başlangıç hızlı başlangıçlar yerel olarak çalıştırmak için temel bilgileri sağlar."
author: billwagner
ms.topic: article
ms.date: 12/07/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: e7747941a7fb1ff43b1a259a78d82665b024a6dd
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2018
---
# <a name="local-environment"></a><span data-ttu-id="382d3-103">Yerel ortamı</span><span class="sxs-lookup"><span data-stu-id="382d3-103">Local environment</span></span>

<span data-ttu-id="382d3-104">Hızlı Başlangıç yerel olarak çalışırken ilk adım, yerel makinenizde bir geliştirme ortamı Kurulumu olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="382d3-104">The first step to trying a quick start locally is to setup a development environment on your local machine.</span></span>
<span data-ttu-id="382d3-105">.NET konu [Get Started 10 dakika içinde](https://www.microsoft.com/net/core) Mac, PC ya da Linux yerel geliştirme ortamınızı ayarlamak için yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="382d3-105">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

<span data-ttu-id="382d3-106">Alternatif olarak, yükleme [.NET Core SDK](http://dot.net/core) ve [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="382d3-106">Alternatively, you can install the [.NET Core SDK](http://dot.net/core) and [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="basic-application-development-flow"></a><span data-ttu-id="382d3-107">Temel uygulama geliştirme akışı</span><span class="sxs-lookup"><span data-stu-id="382d3-107">Basic application development flow</span></span>

<span data-ttu-id="382d3-108">Kullanarak uygulamalar oluşturacaksınız [ `dotnet new` ](../../core/tools/dotnet-new.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="382d3-108">You'll create applications using the [`dotnet new`](../../core/tools/dotnet-new.md) command.</span></span> <span data-ttu-id="382d3-109">Bu komut dosyaları ve uygulamanız için gerekli varlıkları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="382d3-109">This command generates the files and assets necessary for your application.</span></span> <span data-ttu-id="382d3-110">Tüm quickstarts kullanmak `console` uygulama türü.</span><span class="sxs-lookup"><span data-stu-id="382d3-110">The quickstarts all use the `console` application type.</span></span>

<span data-ttu-id="382d3-111">Kullandığınız diğer komutlar [ `dotnet build` ](../../core/tools/dotnet-build.md) yürütülebilir oluşturmaya ve [ `dotnet run` ](../../core/tools/dotnet-run.md) yürütülebilir dosyayı çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="382d3-111">The other commands you'll use are [`dotnet build`](../../core/tools/dotnet-build.md) to build the executable, and [`dotnet run`](../../core/tools/dotnet-run.md) to run the executable.</span></span>

## <a name="pick-your-quickstart"></a><span data-ttu-id="382d3-112">Hızlı Başlangıç seçin</span><span class="sxs-lookup"><span data-stu-id="382d3-112">Pick your quickstart</span></span>

<span data-ttu-id="382d3-113">Aşağıdaki hızlı başlangıçlar birini başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="382d3-113">You can start with any of the following quick starts:</span></span>

## <a name="numbers-in-cnumbers-in-csharp-localmd"></a>[<span data-ttu-id="382d3-114">C# numaraları</span><span class="sxs-lookup"><span data-stu-id="382d3-114">Numbers in C#</span></span>](numbers-in-csharp-local.md)

<span data-ttu-id="382d3-115">İçinde [C# numaraları](numbers-in-csharp-local.md) hızlı başlangıç, nasıl bilgisayarlar numaraları depolamak ve hesaplamalar farklı sayısal türler ile nasıl öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="382d3-115">In the [Numbers in C#](numbers-in-csharp-local.md) quick start, you'll learn how computers store numbers and how to perform calculations with different numeric types.</span></span> <span data-ttu-id="382d3-116">Yuvarlama ve C# kullanarak matematiksel hesaplamalar nasıl temel bilgileri öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="382d3-116">You'll learn the basics of rounding, and how to perform mathematical calculations using C#.</span></span> 

<span data-ttu-id="382d3-117">Bu Hızlı Başlangıç, bitirdikten varsayar [Merhaba Dünya](hello-world.yml) Öğreticisi.</span><span class="sxs-lookup"><span data-stu-id="382d3-117">This quick start assumes that you have finished the [Hello world](hello-world.yml) tutorial.</span></span>

## <a name="branches-and-loopsbranches-and-loops-localmd"></a>[<span data-ttu-id="382d3-118">Dal ve döngüler</span><span class="sxs-lookup"><span data-stu-id="382d3-118">Branches and loops</span></span>](branches-and-loops-local.md)

<span data-ttu-id="382d3-119">[Dallar ve döngüler](branches-and-loops-local.md) hızlı başlangıç değişkenleri depolanan değerlere göre kod yürütme farklı yolların seçilmesi temelleri öğretir.</span><span class="sxs-lookup"><span data-stu-id="382d3-119">The [Branches and loops](branches-and-loops-local.md) quick start teaches the basics of selecting different paths of code execution based on the values stored in variables.</span></span> <span data-ttu-id="382d3-120">Nasıl programlar kararları ve farklı eylemler seçin temelini denetim akışı temel bilgileri öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="382d3-120">You'll learn the basics of control flow, which is the basis of how programs make decisions and choose different actions.</span></span> 

<span data-ttu-id="382d3-121">Bu başlangıç Ders tamamladıktan olduğunu varsayar [Hello World](hello-world.yml) ve [C# numaraları](numbers-in-csharp-local.md) dersleri.</span><span class="sxs-lookup"><span data-stu-id="382d3-121">This beginning lesson assumes that you have finished the [Hello World](hello-world.yml) and [Numbers in C#](numbers-in-csharp-local.md) lessons.</span></span>

## <a name="list-collectionarrays-and-collectionsmd"></a>[<span data-ttu-id="382d3-122">Liste koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="382d3-122">List collection</span></span>](arrays-and-collections.md)

<span data-ttu-id="382d3-123">[Listesinde koleksiyonu](arrays-and-collections.md) Ders veri dizisini depolar liste koleksiyon türü turu sağlar.</span><span class="sxs-lookup"><span data-stu-id="382d3-123">The [List collection](arrays-and-collections.md) lesson gives you a tour of the List collection type that stores sequences of data.</span></span> <span data-ttu-id="382d3-124">Ekleme ve öğeleri kaldırma, öğeleri aramak ve listeleri sıralama öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="382d3-124">You'll learn how to add and remove items, search for items, and sort the lists.</span></span> <span data-ttu-id="382d3-125">Farklı türde listeleri ele alacağız.</span><span class="sxs-lookup"><span data-stu-id="382d3-125">You'll explore different kinds of lists.</span></span> 

<span data-ttu-id="382d3-126">Bu başlangıç hızlı başlangıç, yukarıda listelenen hızlı başlangıçlar bitirdikten varsayar.</span><span class="sxs-lookup"><span data-stu-id="382d3-126">This beginning quick start assumes that you have finished the quick starts listed above.</span></span>

## <a name="introduction-to-classesintroduction-to-classesmd"></a>[<span data-ttu-id="382d3-127">Sınıflara giriş</span><span class="sxs-lookup"><span data-stu-id="382d3-127">Introduction to classes</span></span>](introduction-to-classes.md)

<span data-ttu-id="382d3-128">Bu son hızlı başlangıç yalnızca kendi yerel geliştirme ortamı ve .NET Core kullanarak makinenizde çalıştırmak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="382d3-128">This final quickstart is only available to run on your machine, using your own local development environment and .NET Core.</span></span>
<span data-ttu-id="382d3-129">Bir konsol uygulaması oluşturun ve C# dili parçası olan temel nesne odaklı özellikleri bkz.</span><span class="sxs-lookup"><span data-stu-id="382d3-129">You'll build a console application and see the basic object-oriented features that are part of the C# language.</span></span>
