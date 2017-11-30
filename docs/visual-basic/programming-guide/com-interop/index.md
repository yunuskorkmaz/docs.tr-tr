---
title: "COM Birlikte Çalışma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 87c87852024412b7a7ed55a2c429842ce75a13a8
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="dbfa9-102">COM Birlikte Çalışma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbfa9-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="dbfa9-103">Bileşen Nesne Modeli (COM) diğer bileşenler ve konak uygulamaların işlevselliğini kullanıma sunmak bir nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="dbfa9-104">Günümüzün yazılım çoğunu COM nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="dbfa9-105">.NET derlemelerini yeni uygulamalar için en iyi seçenek olmakla birlikte, bazen COM nesneleri uygulamadığınız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="dbfa9-106">Bu bölümde bazı ile COM nesneler oluşturma ve kullanma ile ilgili sorunları ele alınmaktadır [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dbfa9-106">This section covers some of the issues associated with creating and using COM objects with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dbfa9-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="dbfa9-107">In This Section</span></span>  
 [<span data-ttu-id="dbfa9-108">COM birlikte çalışma giriş</span><span class="sxs-lookup"><span data-stu-id="dbfa9-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="dbfa9-109">COM birlikte çalışabilirliği genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="dbfa9-110">Nasıl yapılır: Visual Basic'den COM nesnelerine başvuru</span><span class="sxs-lookup"><span data-stu-id="dbfa9-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="dbfa9-111">Tür kitaplıkları sahip COM nesnelerine başvurular ekleme kapsar.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="dbfa9-112">Nasıl yapılır: ActiveX denetimleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="dbfa9-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="dbfa9-113">Varolan ActiveX denetimlerini özellikleri eklemek için nasıl kullanılacağı gösterilmektedir [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] araç.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-113">Demonstrates how to use existing ActiveX controls to add features to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Toolbox.</span></span>  
  
 [<span data-ttu-id="dbfa9-114">İzlenecek yol: Windows API'larını çağırma</span><span class="sxs-lookup"><span data-stu-id="dbfa9-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="dbfa9-115">Windows işletim sisteminin parçası olan API'larını çağırma sürecinde adımları.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="dbfa9-116">Nasıl yapılır: Windows API'larını çağırma</span><span class="sxs-lookup"><span data-stu-id="dbfa9-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="dbfa9-117">Tanımlayın ve arama yapmayı gösteren `MessageBox` User32.dll işlevinde.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="dbfa9-118">Nasıl yapılır: imzalanmamış türler isteyen bir Windows işlevi çağırma</span><span class="sxs-lookup"><span data-stu-id="dbfa9-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="dbfa9-119">İmzasız bir türde bir parametreye sahip bir Windows işlevi çağırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="dbfa9-120">İzlenecek yol: Visual Basic ile COM nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="dbfa9-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="dbfa9-121">COM nesneleri ile ve COM sınıfı şablonu olmadan oluşturma sürecinde adımları.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="dbfa9-122">Birlikte çalışabilirlik sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="dbfa9-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="dbfa9-123">Bazı com kullanırken karşılaşabileceğiniz sorunları kapsar</span><span class="sxs-lookup"><span data-stu-id="dbfa9-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="dbfa9-124">.NET Framework uygulamalarında COM birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="dbfa9-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="dbfa9-125">COM ve .NET Framework nesneleri aynı uygulamada kullanmak nasıl bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="dbfa9-126">İzlenecek yol: COM nesnelerinde kalıtım uygulama</span><span class="sxs-lookup"><span data-stu-id="dbfa9-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="dbfa9-127">Var olan COM nesneleri temel olarak yeni nesneler için kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dbfa9-128">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="dbfa9-128">Related Sections</span></span>  
 [<span data-ttu-id="dbfa9-129">Yönetilmeyen kod ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="dbfa9-129">Interoperating with Unmanaged Code</span></span>](https://msdn.microsoft.com/library/sd10k43k)  
 <span data-ttu-id="dbfa9-130">Ortak dil çalışma zamanı tarafından sağlanan birlikte çalışabilirlik hizmetlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="dbfa9-131">COM bileşenlerini .NET Framework'te gösterme</span><span class="sxs-lookup"><span data-stu-id="dbfa9-131">Exposing COM Components to the .NET Framework</span></span>](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730)  
 <span data-ttu-id="dbfa9-132">COM türleri COM birlikte çalışma aracılığıyla çağırma işlemi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="dbfa9-133">.NET Framework bileşenlerini COM'da gösterme</span><span class="sxs-lookup"><span data-stu-id="dbfa9-133">Exposing .NET Framework Components to COM</span></span>](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6)  
 <span data-ttu-id="dbfa9-134">Hazırlama ve COM yönetilen türlerden kullanımını açıklar</span><span class="sxs-lookup"><span data-stu-id="dbfa9-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="dbfa9-135">Birlikte çalışma özniteliklerini uygulama</span><span class="sxs-lookup"><span data-stu-id="dbfa9-135">Applying Interop Attributes</span></span>](https://msdn.microsoft.com/library/d4w8x20h)  
 <span data-ttu-id="dbfa9-136">Yönetilmeyen kod ile çalışırken kullanabileceğiniz öznitelikler kapsar.</span><span class="sxs-lookup"><span data-stu-id="dbfa9-136">Covers attributes you can use when working with unmanaged code.</span></span>
