---
title: Yönetilen hata ayıklayıcıları - .NET Core
description: Visual Studio ve Visual Studio Code'a genel bir bakış hata ayıklayıcıları yönetti.
ms.date: 08/05/2019
ms.openlocfilehash: 065b1b0fc32eb76b398cb3821c8592a1955c9359
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715563"
---
# <a name="net-core-managed-debuggers"></a><span data-ttu-id="9dc57-103">.NET Core yönetilen hata ayıklayıcıları</span><span class="sxs-lookup"><span data-stu-id="9dc57-103">.NET Core managed debuggers</span></span>

<span data-ttu-id="9dc57-104">Hata ayıklayıcılar programların duraklatılmasına veya adım adım yürütülmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9dc57-104">Debuggers allow programs to be paused or executed step-by-step.</span></span> <span data-ttu-id="9dc57-105">Duraklatıldığınızda, işlemin geçerli durumu görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="9dc57-105">When paused, the current state of the process can be viewed.</span></span> <span data-ttu-id="9dc57-106">Önemli bölümlere adım atarak, kodunuzu ve neden bu sonucu verdiğini anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dc57-106">By stepping through key sections, you gain understanding of your code and why it produces the result that it does.</span></span>

<span data-ttu-id="9dc57-107">Microsoft Visual Studio ve Visual **Studio** **Code**yönetilen kod için hata ayıklayıcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="9dc57-107">Microsoft provides debuggers for managed code in **Visual Studio** and **Visual Studio Code**.</span></span>

## <a name="visual-studio-managed-debugger"></a><span data-ttu-id="9dc57-108">Visual Studio hata ayıklama yönetilen</span><span class="sxs-lookup"><span data-stu-id="9dc57-108">Visual Studio managed debugger</span></span>

<span data-ttu-id="9dc57-109">**Visual Studio,** mevcut en kapsamlı hata ayıklamaya sahip entegre bir geliştirme ortamıdır.</span><span class="sxs-lookup"><span data-stu-id="9dc57-109">**Visual Studio** is an integrated development environment with the most comprehensive debugger available.</span></span> <span data-ttu-id="9dc57-110">Visual Studio, Windows üzerinde çalışan geliştiriciler için mükemmel bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="9dc57-110">Visual Studio is an excellent choice for developers working on Windows.</span></span>

- [<span data-ttu-id="9dc57-111">Öğretici - Visual Studio ile Windows'da bir .NET Core uygulamasını hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9dc57-111">Tutorial - Debugging a .NET Core application on Windows with Visual Studio</span></span>](../tutorials/debugging-with-visual-studio.md)

<span data-ttu-id="9dc57-112">Visual Studio bir Windows uygulaması olsa da, Linux ve macOS uygulamalarını uzaktan hata ayıklamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9dc57-112">While Visual Studio is a Windows application, it can still be used to debug Linux and macOS apps remotely.</span></span>

- [<span data-ttu-id="9dc57-113">Visual Studio ile Linux/OSX'te bir .NET Core uygulamasının hata ayıklanması</span><span class="sxs-lookup"><span data-stu-id="9dc57-113">Debugging a .NET Core application on Linux/OSX with Visual Studio</span></span>](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 <span data-ttu-id="9dc57-114">Core uygulamaları ASP.NET hata ayıklama biraz farklı talimatlar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9dc57-114">Debugging ASP.NET Core apps require slightly different instructions.</span></span>

- [<span data-ttu-id="9dc57-115">Visual Studio'da ASP.NET Çekirdek uygulamalarını hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9dc57-115">Debug ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a><span data-ttu-id="9dc57-116">Visual Studio Code yönetilen hata ayıklayıcı</span><span class="sxs-lookup"><span data-stu-id="9dc57-116">Visual Studio Code managed debugger</span></span>

<span data-ttu-id="9dc57-117">**Visual Studio Code** hafif bir çapraz platform kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="9dc57-117">**Visual Studio Code** is a lightweight cross-platform code editor.</span></span> <span data-ttu-id="9dc57-118">Visual Studio ile aynı .NET Core hata ayıklama uygulamasını kullanır, ancak basitleştirilmiş bir kullanıcı arabirimi ile.</span><span class="sxs-lookup"><span data-stu-id="9dc57-118">It uses the same .NET Core debugger implementation as Visual Studio, but with a simplified user interface.</span></span>

- [<span data-ttu-id="9dc57-119">Öğretici - Visual Studio Code ile bir .NET Core uygulaması hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9dc57-119">Tutorial - Debugging a .NET Core application with Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md#debug)
- [<span data-ttu-id="9dc57-120">Visual Studio Code'da Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9dc57-120">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)
