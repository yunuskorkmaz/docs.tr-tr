---
title: Bağımlılık yükleme - .NET Core
description: .NET Core'da yönetilen ve yönetilmeyen bağımlılık yüklemesi genel bakış
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: f6b5fc1f92171b61dcab162b782ca7212c602d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416678"
---
# <a name="dependency-loading-in-net-core"></a><span data-ttu-id="29e11-103">.NET Core'da bağımlılık yüklemesi</span><span class="sxs-lookup"><span data-stu-id="29e11-103">Dependency loading in .NET Core</span></span>

<span data-ttu-id="29e11-104">Her .NET Core uygulamasının bağımlılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="29e11-104">Every .NET Core application has dependencies.</span></span> <span data-ttu-id="29e11-105">Basit `hello world` uygulamanın bile .NET Core sınıf kitaplıklarının bölümlerine bağımlılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="29e11-105">Even the simple `hello world` app has dependencies on portions of the .NET Core class libraries.</span></span>

<span data-ttu-id="29e11-106">.NET Core varsayılan derleme yükleme mantığını anlamak, tipik dağıtım sorunlarını anlamave hata ayıklama konusunda yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="29e11-106">Understanding .NET Core default assembly loading logic can help understanding and debugging typical deployment issues.</span></span>

<span data-ttu-id="29e11-107">Bazı uygulamalarda, bağımlılıklar çalışma zamanında dinamik olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="29e11-107">In some applications, dependencies are dynamically determined at runtime.</span></span> <span data-ttu-id="29e11-108">Bu gibi durumlarda, yönetilen derlemelerin ve yönetilmeyen bağımlılıkların nasıl yüklendiğini anlamak çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="29e11-108">In these situations, it's critical to understand how managed assemblies and unmanaged dependencies are loaded.</span></span>

## <a name="understanding-assemblyloadcontext"></a><span data-ttu-id="29e11-109">AssemblyLoadContext’i anlama</span><span class="sxs-lookup"><span data-stu-id="29e11-109">Understanding AssemblyLoadContext</span></span>

<span data-ttu-id="29e11-110"><xref:System.Runtime.Loader.AssemblyLoadContext> API,.NET Core yükleme tasarımının merkezindedir.</span><span class="sxs-lookup"><span data-stu-id="29e11-110">The <xref:System.Runtime.Loader.AssemblyLoadContext> API is central to the .NET Core loading design.</span></span> <span data-ttu-id="29e11-111">[Anlama AssemblyLoadContext](understanding-assemblyloadcontext.md) makale tasarım için kavramsal bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="29e11-111">The [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) article provides a conceptual overview to the design.</span></span>

## <a name="loading-details"></a><span data-ttu-id="29e11-112">Yükleme ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="29e11-112">Loading details</span></span>

<span data-ttu-id="29e11-113">Yükleme algoritması ayrıntıları birkaç makalede kısaca ele alınmıştır:</span><span class="sxs-lookup"><span data-stu-id="29e11-113">The loading algorithm details are covered briefly in several articles:</span></span>

- [<span data-ttu-id="29e11-114">Yönetilen montaj yükleme algoritması</span><span class="sxs-lookup"><span data-stu-id="29e11-114">Managed assembly loading algorithm</span></span>](loading-managed.md)
- [<span data-ttu-id="29e11-115">Uydu montaj yükleme algoritması</span><span class="sxs-lookup"><span data-stu-id="29e11-115">Satellite assembly loading algorithm</span></span>](loading-resources.md)
- [<span data-ttu-id="29e11-116">Yönetilmeyen (yerel) kitaplık yükleme algoritması</span><span class="sxs-lookup"><span data-stu-id="29e11-116">Unmanaged (native) library loading algorithm</span></span>](loading-unmanaged.md)
- [<span data-ttu-id="29e11-117">Varsayılan sondalama</span><span class="sxs-lookup"><span data-stu-id="29e11-117">Default probing</span></span>](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="29e11-118">Eklentilerle .NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="29e11-118">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="29e11-119">Öğretici [Eklentileri ile bir .NET Core uygulaması oluşturun](../tutorials/creating-app-with-plugin-support.md) nasıl özel bir AssemblyLoadContext oluşturmak için açıklar.</span><span class="sxs-lookup"><span data-stu-id="29e11-119">The tutorial [Create a .NET Core application with plugins](../tutorials/creating-app-with-plugin-support.md) describes how to create a custom AssemblyLoadContext.</span></span> <span data-ttu-id="29e11-120">Eklentinin <xref:System.Runtime.Loader.AssemblyDependencyResolver> bağımlılıklarını gidermek için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="29e11-120">It uses an <xref:System.Runtime.Loader.AssemblyDependencyResolver> to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="29e11-121">Öğretici, eklentinin bağımlılıklarını barındırma uygulamasından doğru bir şekilde yalıtır.</span><span class="sxs-lookup"><span data-stu-id="29e11-121">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span>

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="29e11-122">.NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama</span><span class="sxs-lookup"><span data-stu-id="29e11-122">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="29e11-123">[.NET Core makalesinde montaj yüklenebilirliğinin nasıl kullanılacağı ve hata ayıklanabilirliğinin nasıl kullanılacağı,](../../standard/assembly/unloadability.md) adım adım öğreticidir.</span><span class="sxs-lookup"><span data-stu-id="29e11-123">The [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability.md) article is a step-by-step tutorial.</span></span> <span data-ttu-id="29e11-124">Bir .NET Core uygulamasının nasıl yüklenir, yürütülür ve sonra nasıl boşaltılmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="29e11-124">It shows how to load a .NET Core application, execute, and then unload it.</span></span> <span data-ttu-id="29e11-125">Makale de hata ayıklama ipuçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="29e11-125">The article also provides debugging tips.</span></span>
