---
title: COM Birlikte Çalışma (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a2c418855cd2e79c31301705706ff1b98f119a97
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="ff6bd-102">COM Birlikte Çalışma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff6bd-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="ff6bd-103">Bileşen Nesne Modeli (COM) diğer bileşenler ve konak uygulamaların işlevselliğini kullanıma sunmak bir nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="ff6bd-104">Günümüzün yazılım çoğunu COM nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="ff6bd-105">.NET derlemelerini yeni uygulamalar için en iyi seçenek olmakla birlikte, bazen COM nesneleri uygulamadığınız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="ff6bd-106">Bu bölümde bazı oluşturma ve Visual Basic ile COM nesneleri kullanma ile ilgili sorunları ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-106">This section covers some of the issues associated with creating and using COM objects with Visual Basic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff6bd-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ff6bd-107">In This Section</span></span>  
 [<span data-ttu-id="ff6bd-108">COM Birlikte Çalışma'ya Giriş</span><span class="sxs-lookup"><span data-stu-id="ff6bd-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="ff6bd-109">COM birlikte çalışabilirliği genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="ff6bd-110">Nasıl yapılır: Visual Basic'den COM nesnelerine başvuru</span><span class="sxs-lookup"><span data-stu-id="ff6bd-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="ff6bd-111">Tür kitaplıkları sahip COM nesnelerine başvurular ekleme kapsar.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="ff6bd-112">Nasıl yapılır: ActiveX Denetimleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="ff6bd-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="ff6bd-113">Visual Studio araç kutusuna özellikleri eklemek için var olan ActiveX denetimlerini kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-113">Demonstrates how to use existing ActiveX controls to add features to the Visual Studio Toolbox.</span></span>  
  
 [<span data-ttu-id="ff6bd-114">İzlenecek yol: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="ff6bd-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="ff6bd-115">Windows işletim sisteminin parçası olan API'larını çağırma sürecinde adımları.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="ff6bd-116">Nasıl yapılır: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="ff6bd-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="ff6bd-117">Tanımlayın ve arama yapmayı gösteren `MessageBox` User32.dll işlevinde.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="ff6bd-118">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="ff6bd-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="ff6bd-119">İmzasız bir türde bir parametreye sahip bir Windows işlevi çağırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="ff6bd-120">İzlenecek yol: Visual Basic ile COM nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff6bd-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="ff6bd-121">COM nesneleri ile ve COM sınıfı şablonu olmadan oluşturma sürecinde adımları.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="ff6bd-122">Birlikte Çalışabilirlik İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="ff6bd-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="ff6bd-123">Bazı com kullanırken karşılaşabileceğiniz sorunları kapsar</span><span class="sxs-lookup"><span data-stu-id="ff6bd-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="ff6bd-124">.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="ff6bd-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="ff6bd-125">COM ve .NET Framework nesneleri aynı uygulamada kullanmak nasıl bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="ff6bd-126">İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama</span><span class="sxs-lookup"><span data-stu-id="ff6bd-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="ff6bd-127">Var olan COM nesneleri temel olarak yeni nesneler için kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ff6bd-128">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ff6bd-128">Related Sections</span></span>  
 [<span data-ttu-id="ff6bd-129">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="ff6bd-129">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="ff6bd-130">Ortak dil çalışma zamanı tarafından sağlanan birlikte çalışabilirlik hizmetlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="ff6bd-131">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="ff6bd-131">Exposing COM Components to the .NET Framework</span></span>](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730)  
 <span data-ttu-id="ff6bd-132">COM türleri COM birlikte çalışma aracılığıyla çağırma işlemi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="ff6bd-133">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="ff6bd-133">Exposing .NET Framework Components to COM</span></span>](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6)  
 <span data-ttu-id="ff6bd-134">Hazırlama ve COM yönetilen türlerden kullanımını açıklar</span><span class="sxs-lookup"><span data-stu-id="ff6bd-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="ff6bd-135">Birlikte Çalışma Özniteliklerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="ff6bd-135">Applying Interop Attributes</span></span>](../../../framework/interop/applying-interop-attributes.md)  
 <span data-ttu-id="ff6bd-136">Yönetilmeyen kod ile çalışırken kullanabileceğiniz öznitelikler kapsar.</span><span class="sxs-lookup"><span data-stu-id="ff6bd-136">Covers attributes you can use when working with unmanaged code.</span></span>
