---
title: Yönetilen hata ayıklayıcıları-.NET Core
description: Visual Studio 'ya genel bakış ve yönetilen hata ayıklayıcıları Visual Studio Code.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 3741011d22ab6c4240b7f88a9ab790ea61ecd0d2
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926436"
---
# <a name="net-core-managed-debuggers"></a><span data-ttu-id="c8f99-103">.NET Core yönetilen hata ayıklayıcıları</span><span class="sxs-lookup"><span data-stu-id="c8f99-103">.NET Core managed debuggers</span></span>

<span data-ttu-id="c8f99-104">Hata ayıklayıcılar, programların duraklatılmasını veya bir adım adım yürütülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8f99-104">Debuggers allow programs to be paused or executed step-by-step.</span></span> <span data-ttu-id="c8f99-105">Duraklatıldığında işlemin geçerli durumu görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="c8f99-105">When paused, the current state of the process can be viewed.</span></span> <span data-ttu-id="c8f99-106">Anahtar bölümleri aracılığıyla Adımlayarak, kodunuzun öğrenmiş olduğunu ve bunun nedenini neden ürettiğini elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="c8f99-106">By stepping through key sections, you gain understanding of your code and why it produces the result that it does.</span></span>

<span data-ttu-id="c8f99-107">Microsoft, **Visual Studio** ve **Visual Studio Code**yönetilen kod için hata ayıklayıcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8f99-107">Microsoft provides debuggers for managed code in **Visual Studio** and **Visual Studio Code**.</span></span>

## <a name="visual-studio-managed-debugger"></a><span data-ttu-id="c8f99-108">Visual Studio yönetilen hata ayıklayıcı</span><span class="sxs-lookup"><span data-stu-id="c8f99-108">Visual Studio managed debugger</span></span>

<span data-ttu-id="c8f99-109">**Visual Studio** , en kapsamlı hata ayıklayıcı bulunan tümleşik bir geliştirme ortamıdır.</span><span class="sxs-lookup"><span data-stu-id="c8f99-109">**Visual Studio** is an integrated development environment with the most comprehensive debugger available.</span></span> <span data-ttu-id="c8f99-110">Visual Studio, Windows üzerinde çalışan geliştiriciler için harika bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="c8f99-110">Visual Studio is an excellent choice for developers working on Windows.</span></span>

- [<span data-ttu-id="c8f99-111">Öğretici-Visual Studio ile Windows 'da .NET Core uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c8f99-111">Tutorial - Debugging a .NET Core application on Windows with Visual Studio</span></span>](../tutorials/debugging-with-visual-studio.md)

<span data-ttu-id="c8f99-112">Visual Studio bir Windows uygulaması olduğu sürece, Linux ve macOS uygulamalarında uzaktan hata ayıklamak için yine de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8f99-112">While Visual Studio is a Windows application, it can still be used to debug Linux and macOS apps remotely.</span></span>

- [<span data-ttu-id="c8f99-113">Visual Studio ile Linux/OSX üzerinde .NET Core uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c8f99-113">Debugging a .NET Core application on Linux/OSX with Visual Studio</span></span>](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 <span data-ttu-id="c8f99-114">ASP.NET Core uygulamalarda hata ayıklama biraz farklı yönergeler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c8f99-114">Debugging ASP.NET Core apps require slightly different instructions.</span></span>

- [<span data-ttu-id="c8f99-115">Visual Studio 'da ASP.NET Core uygulamalarda hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c8f99-115">Debug ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a><span data-ttu-id="c8f99-116">Visual Studio Code yönetilen hata ayıklayıcı</span><span class="sxs-lookup"><span data-stu-id="c8f99-116">Visual Studio Code managed debugger</span></span>

<span data-ttu-id="c8f99-117">**Visual Studio Code** , hafif bir platformlar arası kod düzenleyicidir.</span><span class="sxs-lookup"><span data-stu-id="c8f99-117">**Visual Studio Code** is a lightweight cross-platform code editor.</span></span> <span data-ttu-id="c8f99-118">Visual Studio ile aynı .NET Core hata ayıklayıcı uygulamasını, ancak basitleştirilmiş bir kullanıcı arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c8f99-118">It uses the same .NET Core debugger implementation as Visual Studio, but with a simplified user interface.</span></span>

- [<span data-ttu-id="c8f99-119">Öğretici-Visual Studio Code bir .NET Core uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c8f99-119">Tutorial - Debugging a .NET Core application with Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md#debug)
- [<span data-ttu-id="c8f99-120">Visual Studio Code 'de hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c8f99-120">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)
