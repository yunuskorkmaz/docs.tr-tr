---
title: Windows 8'de .NET Framework 2.0'ı hedefleme
description: "F # kullanırken .NET Framework'ün daha eski sürümünü hedefleme hakkında bilgi edinin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 7c9bd8087da94a476105729b6f5b050fc66629a2
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="targeting-older-versions-of-net"></a><span data-ttu-id="8928d-103">.NET hedefleme eski sürümleri</span><span class="sxs-lookup"><span data-stu-id="8928d-103">Targeting Older Versions of .NET</span></span>

> [!NOTE]
<span data-ttu-id="8928d-104">Bu makale, en son Visual Studio ile güncel değil.</span><span class="sxs-lookup"><span data-stu-id="8928d-104">This article is not up to date with the latest Visual Studio.</span></span>  <span data-ttu-id="8928d-105">Güncelleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="8928d-105">It will be updated.</span></span>

<span data-ttu-id="8928d-106">.NET Framework 2.0 hedef çalışırsanız, Visual Studio üzerinde Windows 8.1 yüklendiğinde 3.0 veya 3.5 bir F # proje aşağıdaki hata görünebilir:</span><span class="sxs-lookup"><span data-stu-id="8928d-106">The following error might appear if you try to target the .NET Framework 2.0, 3.0, or 3.5 in an F# project when Visual Studio is installed on Windows 8.1:</span></span> 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

<span data-ttu-id="8928d-107">Bu hata, aşağıdaki koşullar bileşimi altında oluştuğu bilinmektedir:</span><span class="sxs-lookup"><span data-stu-id="8928d-107">This error is known to occur under the following combination of conditions:</span></span>


- <span data-ttu-id="8928d-108">Visual Studio Windows 8.1 üzerinde yüklü.</span><span class="sxs-lookup"><span data-stu-id="8928d-108">You installed Visual Studio on Windows 8.1.</span></span>
<br />

- <span data-ttu-id="8928d-109">Visual Studio yüklemeden önce .NET Framework 3.5 etkinleştirin alamadık.</span><span class="sxs-lookup"><span data-stu-id="8928d-109">You didn’t enable the .NET Framework 3.5 before you installed Visual Studio.</span></span>
<br />

- <span data-ttu-id="8928d-110">Projeniz .NET Framework 2.0, 3.0 veya 3.5 hedefler.</span><span class="sxs-lookup"><span data-stu-id="8928d-110">Your project targets the .NET Framework 2.0, 3.0, or 3.5.</span></span>
<br />

<span data-ttu-id="8928d-111">Visual Studio yüklediğinizde, .NET Framework'ün yüklü sürümleri algılar ve .NET Framework 3.5 yalnızca yüklü ve etkinse F # 2.0 çalışma zamanı yükler.</span><span class="sxs-lookup"><span data-stu-id="8928d-111">When you install Visual Studio, it detects the installed versions of the .NET Framework and installs the F# 2.0 Runtime only if the .NET Framework 3.5 is installed and enabled.</span></span>


## <a name="resolving-the-error"></a><span data-ttu-id="8928d-112">Hatayı giderme</span><span class="sxs-lookup"><span data-stu-id="8928d-112">Resolving the Error</span></span>
<span data-ttu-id="8928d-113">Bu hatayı gidermek için her iki hedef .NET Framework daha yeni bir sürümü olabilir veya Windows 8.1 üzerinde .NET Framework 3.5 etkinleştirin ve sonra F # 2.0 ile Visual Studio için Kurulum programını çalıştırarak yükleyin **onarım** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="8928d-113">To resolve this error, you can either target a newer version of the .NET Framework, or you can enable the .NET Framework 3.5 on Windows 8.1 and then install the F# 2.0 runtime by running the setup program for Visual Studio with the **Repair** option.</span></span>


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a><span data-ttu-id="8928d-114">Windows 8.1 üzerinde .NET Framework 3.5 etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="8928d-114">To enable the .NET Framework 3.5 on Windows 8.1</span></span>

1. <span data-ttu-id="8928d-115">Üzerinde **Başlat** ekranında, girmek başlangıç **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="8928d-115">On the **Start** screen, start to enter **Control Panel**.</span></span>
<br />  <span data-ttu-id="8928d-116">Bu ada girerken **Denetim Masası** simgesi görünür altında **uygulamaları** başlığı.</span><span class="sxs-lookup"><span data-stu-id="8928d-116">As you enter that name, the **Control Panel** icon appears under the **Apps** heading.</span></span>
<br />

2. <span data-ttu-id="8928d-117">Seçin **Denetim Masası** simgesini seçin **programlar** simgesine ve ardından **kapatma Windows özelliklerini aç veya Kapat** bağlantı.</span><span class="sxs-lookup"><span data-stu-id="8928d-117">Choose the **Control Panel** icon, choose the **Programs** icon, and then choose the **Turn Windows features on or off** link.</span></span>
<br />

3. <span data-ttu-id="8928d-118">Olduğundan emin olun **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir)** onay kutusu seçilidir ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="8928d-118">Make sure that the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box is selected, and then choose the **OK** button.</span></span>
<br />  <span data-ttu-id="8928d-119">.NET Framework'ün isteğe bağlı bileşenler için herhangi bir alt düğüm için onay kutularını seçin gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="8928d-119">You don’t need to select the check boxes for any child nodes for optional components of the .NET Framework.</span></span>
<br />  <span data-ttu-id="8928d-120">Zaten yapmadıysanız, .NET Framework 3.5 etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8928d-120">The .NET Framework 3.5 is enabled if it wasn't already.</span></span>
<br />


#### <a name="to-install-the-f-20-runtime"></a><span data-ttu-id="8928d-121">F # 2.0 çalışma zamanını yüklemek için</span><span class="sxs-lookup"><span data-stu-id="8928d-121">To install the F# 2.0 runtime</span></span>

1. <span data-ttu-id="8928d-122">Denetim Masası'nda seçin **programları** bağlamak ve ardından **programlar ve Özellikler** bağlantı.</span><span class="sxs-lookup"><span data-stu-id="8928d-122">In the Control Panel, choose the **Programs** link, and then choose the **Programs and Features** link.</span></span>
<br />

2. <span data-ttu-id="8928d-123">Yüklü programlar listesinde, yüklü ve ardından Visual Studio sürümü seçin **değişiklik** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="8928d-123">In the list of installed programs, choose the edition of Visual Studio that you installed, and then choose the **Change** button.</span></span>
<br />

3. <span data-ttu-id="8928d-124">Kurulum başladıktan sonra seçin **onarım** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="8928d-124">After setup starts, choose the **Repair** button.</span></span>
<br />  <span data-ttu-id="8928d-125">Daha fazla bilgi için bkz: [Visual Studio'yu yükleme](https://msdn.microsoft.com/library/e2h7fzkw.aspx).</span><span class="sxs-lookup"><span data-stu-id="8928d-125">For more information, see [Installing Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).</span></span>
<br />
## <a name="see-also"></a><span data-ttu-id="8928d-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8928d-126">See Also</span></span>
[<span data-ttu-id="8928d-127">Visual F#</span><span class="sxs-lookup"><span data-stu-id="8928d-127">Visual F#</span></span>](../index.md)
