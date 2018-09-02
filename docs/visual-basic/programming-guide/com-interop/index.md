---
title: COM Birlikte Çalışma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
ms.openlocfilehash: b6da65a0c94875f73c8e1094448d76a72823404d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405956"
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="bba7f-102">COM Birlikte Çalışma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bba7f-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="bba7f-103">Bileşen Nesne Modeli (COM) diğer bileşenleri ve uygulamaları barındırmak için işlevselliği göstermek bir nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="bba7f-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="bba7f-104">Günümüzün yazılımlarının çoğunu, COM nesnelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="bba7f-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="bba7f-105">.NET derlemeleri yeni uygulamalar için en iyi seçenek olsa da, bazen COM nesnelerini kullanmak istemiyorsunuz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="bba7f-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="bba7f-106">Bu bölümde bazı oluşturma ve Visual Basic ile COM nesneleri kullanma ile ilgili sorunlar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bba7f-106">This section covers some of the issues associated with creating and using COM objects with Visual Basic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bba7f-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bba7f-107">In This Section</span></span>  
 [<span data-ttu-id="bba7f-108">COM Birlikte Çalışma'ya Giriş</span><span class="sxs-lookup"><span data-stu-id="bba7f-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="bba7f-109">COM birlikte çalışabilirlik genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="bba7f-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="bba7f-110">Nasıl yapılır: Visual Basic'den COM nesnelerine başvuru</span><span class="sxs-lookup"><span data-stu-id="bba7f-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="bba7f-111">Tür kitaplıkları olan COM nesneleri başvuruları eklemek nasıl etkinleştireceğinizi de açıklar.</span><span class="sxs-lookup"><span data-stu-id="bba7f-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="bba7f-112">Nasıl yapılır: ActiveX Denetimleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="bba7f-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="bba7f-113">Visual Studio araç kutusu özellikler eklemek için mevcut ActiveX denetimleri nasıl yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="bba7f-113">Demonstrates how to use existing ActiveX controls to add features to the Visual Studio Toolbox.</span></span>  
  
 [<span data-ttu-id="bba7f-114">İzlenecek yol: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="bba7f-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="bba7f-115">Windows işletim sisteminin parçası olan API'leri çağırma işleminde size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="bba7f-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="bba7f-116">Nasıl yapılır: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="bba7f-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="bba7f-117">Tanımlar ve çağrı anlatılmıştır `MessageBox` User32.dll işlevi.</span><span class="sxs-lookup"><span data-stu-id="bba7f-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="bba7f-118">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="bba7f-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="bba7f-119">Bir işaretsiz türünde bir parametreye sahip bir Windows işlevi çağırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bba7f-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="bba7f-120">İzlenecek yol: Visual Basic ile COM nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="bba7f-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="bba7f-121">COM sınıf şablonu olmadan ve COM nesneleri oluşturma işleminde adımları.</span><span class="sxs-lookup"><span data-stu-id="bba7f-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="bba7f-122">Birlikte Çalışabilirlik İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="bba7f-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="bba7f-123">Bazı com kullanırken karşılaşabileceğiniz sorunları ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bba7f-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="bba7f-124">.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="bba7f-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="bba7f-125">COM nesneleri ve .NET Framework nesnelerini aynı uygulamada nasıl kullanılacağını genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="bba7f-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="bba7f-126">İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama</span><span class="sxs-lookup"><span data-stu-id="bba7f-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="bba7f-127">Mevcut COM nesneleri, yeni nesneler için temel olarak kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="bba7f-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bba7f-128">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="bba7f-128">Related Sections</span></span>  
 [<span data-ttu-id="bba7f-129">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="bba7f-129">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="bba7f-130">Ortak dil çalışma zamanı tarafından sağlanan birlikte çalışabilirlik hizmetlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="bba7f-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="bba7f-131">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="bba7f-131">Exposing COM Components to the .NET Framework</span></span>](https://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730)  
 <span data-ttu-id="bba7f-132">COM birlikte çalışma aracılığıyla COM tür arama işlemi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="bba7f-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="bba7f-133">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="bba7f-133">Exposing .NET Framework Components to COM</span></span>](https://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6)  
 <span data-ttu-id="bba7f-134">Hazırlama ve yönetilen türlerden com kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bba7f-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="bba7f-135">Birlikte Çalışma Özniteliklerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="bba7f-135">Applying Interop Attributes</span></span>](../../../framework/interop/applying-interop-attributes.md)  
 <span data-ttu-id="bba7f-136">Yönetilmeyen kod ile çalışırken kullanabileceğiniz öznitelikleri kapsar.</span><span class="sxs-lookup"><span data-stu-id="bba7f-136">Covers attributes you can use when working with unmanaged code.</span></span>
