---
title: .NET kullanmaya başlama
description: Merhaba Dünya .NET uygulaması oluşturun.
author: adegeo
ms.author: adegeo
ms.date: 09/29/2020
ms.custom: vs-dotnet
ms.openlocfilehash: 6ad2b96e668c52ee80b707e31a63eac2433f3c9e
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756097"
---
# <a name="get-started-with-net"></a><span data-ttu-id="a0734-103">.NET kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="a0734-103">Get started with .NET</span></span>

<span data-ttu-id="a0734-104">Bu makalede bir "Merhaba Dünya!" oluşturma ve çalıştırma hakkında öğretilir</span><span class="sxs-lookup"><span data-stu-id="a0734-104">This article teaches you how to create and run a "Hello World!"</span></span> <span data-ttu-id="a0734-105">.NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="a0734-105">.NET app.</span></span>

<span data-ttu-id="a0734-106">.NET ' in ne olduğundan emin değilseniz, [.net tanıtımı](introduction.md)ile başlayın.</span><span class="sxs-lookup"><span data-stu-id="a0734-106">If you're unsure what .NET is, start with the [.NET introduction](introduction.md).</span></span>

## <a name="create-an-application"></a><span data-ttu-id="a0734-107">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="a0734-107">Create an application</span></span>

<span data-ttu-id="a0734-108">İlk olarak, bilgisayarınıza [.NET SDK 'sını](https://dotnet.microsoft.com/download/dotnet-core) indirip yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a0734-108">First, download and install the [.NET SDK](https://dotnet.microsoft.com/download/dotnet-core) on your computer.</span></span>

<span data-ttu-id="a0734-109">Ardından, **PowerShell**, **komut istemi**veya **Bash**gibi bir Terminal açın.</span><span class="sxs-lookup"><span data-stu-id="a0734-109">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="a0734-110">`dotnet`Bir C# uygulaması oluşturmak ve çalıştırmak için aşağıdaki komutları girin:</span><span class="sxs-lookup"><span data-stu-id="a0734-110">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="a0734-111">Aşağıdaki çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="a0734-111">You see the following output:</span></span>

```output
Hello World!
```

<span data-ttu-id="a0734-112">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="a0734-112">Congratulations!</span></span> <span data-ttu-id="a0734-113">Basit bir .NET uygulaması oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="a0734-113">You've created a simple .NET application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a0734-114">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a0734-114">Next steps</span></span>

<span data-ttu-id="a0734-115">Bir [adım adım öğreticiyi](../standard/get-started.md) Izleyerek veya YouTube 'da [.net 101 videolarını](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) izleyerek .NET uygulamaları geliştirmeye başlayın.</span><span class="sxs-lookup"><span data-stu-id="a0734-115">Get started developing .NET applications by following a [step-by-step tutorial](../standard/get-started.md) or by watching [.NET 101 videos](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) on YouTube.</span></span>
