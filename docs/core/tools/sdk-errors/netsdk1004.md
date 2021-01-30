---
title: 'NETSDK1004: varlıklar dosyası bulunamadı'
description: project.assets.jsdosya bulunamadığında oluşan .NET SDK hatası NETSDK1004 hakkında bilgi edinin.
ms.topic: error-reference
ms.date: 01/29/2021
f1_keywords:
- NETSDK1004
ms.openlocfilehash: 8416063fe318106cbcb4dbccacef3ecaaff5bba2
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216441"
---
# <a name="netsdk1004-assets-file-not-found"></a><span data-ttu-id="1c658-103">NETSDK1004: varlıklar dosyası bulunamadı</span><span class="sxs-lookup"><span data-stu-id="1c658-103">NETSDK1004: Assets file not found</span></span>

<span data-ttu-id="1c658-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2.1.100 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="1c658-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="1c658-105">NuGet, *obj* klasöründe *project.assets.js* adlı bir dosya yazar ve .NET SDK bunu derleyiciye geçirilecek paketler hakkında bilgi almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c658-105">NuGet writes a file named *project.assets.json* in the *obj* folder, and the .NET SDK uses it to get information about packages to pass into the compiler.</span></span> <span data-ttu-id="1c658-106">Bu hata, derleme sırasında *project.assets.js* varlıklar dosyası bulunamadığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="1c658-106">This error occurs when the assets file *project.assets.json* is not found during build.</span></span> <span data-ttu-id="1c658-107">Tam hata iletisi aşağıdaki örneğe benzer:</span><span class="sxs-lookup"><span data-stu-id="1c658-107">The full error message is similar to the following example:</span></span>

<span data-ttu-id="1c658-108">**NETSDK1004: ' C:\path\to\project.assets.json ' varlık dosyası bulunamadı. Bu dosyayı oluşturmak için bir NuGet paketi geri yükleme çalıştırın.**</span><span class="sxs-lookup"><span data-stu-id="1c658-108">**NETSDK1004: Assets file 'C:\path\to\project.assets.json' not found. Run a NuGet package restore to generate this file.**</span></span>

<span data-ttu-id="1c658-109">Hatanın olası nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1c658-109">Here are some possible causes of the error:</span></span>

* <span data-ttu-id="1c658-110">`dotnet build`Komutunu bir karakter içeren bir dizin yolundan çalıştırıyorsunuz `%` .</span><span class="sxs-lookup"><span data-stu-id="1c658-110">You are running the `dotnet build` command from a directory path that contains a `%` character.</span></span> <span data-ttu-id="1c658-111">Hatayı gidermek için, `%` öğesini klasör adından kaldırın ve yeniden çalıştırın `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="1c658-111">To resolve the error, remove the `%` from the folder name, and rerun `dotnet build`.</span></span>
* <span data-ttu-id="1c658-112">Proje dosyası değişikliği proje sistemi tarafından otomatik olarak algılanmadı ve geri yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="1c658-112">A change to the project file wasn't automatically detected and restored by the project system.</span></span> <span data-ttu-id="1c658-113">Hatayı gidermek için bir komut istemi açın ve `dotnet restore` projede çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1c658-113">To resolve the error, open a command prompt and run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="1c658-114">Bir proje, Nuget.exe eski bir sürümü tarafından ayrı olarak geri yüklendi.</span><span class="sxs-lookup"><span data-stu-id="1c658-114">A project was restored separately by an older version of Nuget.exe.</span></span> <span data-ttu-id="1c658-115">Hatayı gidermek için bir komut istemi açın ve `dotnet restore` projede çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1c658-115">To resolve the error, open a command prompt and run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="1c658-116">NETSDK1045 (kullandığınız SDK sürümü projenin hedef çerçevesini desteklemez) gibi önceki bir hata, NuGet 'in proje varlıkları dosyasını oluşturmasını engelledi.</span><span class="sxs-lookup"><span data-stu-id="1c658-116">An earlier error, such as NETSDK1045 (the version of the SDK you're using doesn't support the project's target framework), prevented NuGet from creating the project assets file.</span></span> <span data-ttu-id="1c658-117">NETSDK1004 hatasını çözümlemek için, önceki hatayı çözün ve sonra `dotnet restore` projede çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1c658-117">To resolve the NETSDK1004 error, resolve the earlier error, and then run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="1c658-118">App Center CI, NuGet içinde olmayan bir dış derlemeye sahip bir proje oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="1c658-118">App Center CI is building a project that has an external assembly that is not in NuGet.</span></span> <span data-ttu-id="1c658-119">Hatayı gidermek için, derleme için bir NuGet paketi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c658-119">To resolve the error, use a NuGet package for the assembly.</span></span>
