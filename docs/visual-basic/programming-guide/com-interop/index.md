---
title: COM Birlikte Çalışma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
ms.openlocfilehash: 1bcfba25c86c46f986c061241a5d09f9aaa6d248
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627076"
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="6ad51-102">COM Birlikte Çalışma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ad51-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="6ad51-103">Bileşen nesne modeli (COM), bir nesnenin işlevselliğini diğer bileşenlere sunma ve uygulamaları barındırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6ad51-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="6ad51-104">Günümüzün yazılımlarının çoğu COM nesnelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6ad51-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="6ad51-105">.NET derlemeleri yeni uygulamalar için en iyi seçenek olsa da, her zaman COM nesneleri kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="6ad51-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="6ad51-106">Bu bölümde, Visual Basic ile COM nesneleri oluşturma ve kullanma ile ilgili bazı sorunlar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6ad51-106">This section covers some of the issues associated with creating and using COM objects with Visual Basic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ad51-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6ad51-107">In This Section</span></span>  
 [<span data-ttu-id="6ad51-108">COM Birlikte Çalışma'ya Giriş</span><span class="sxs-lookup"><span data-stu-id="6ad51-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="6ad51-109">COM birlikte çalışabilirliğine genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ad51-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="6ad51-110">Nasıl yapılır: Visual Basic COM nesnelerine başvuru</span><span class="sxs-lookup"><span data-stu-id="6ad51-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="6ad51-111">Tür kitaplıkları olan COM nesnelerine başvuruların nasıl ekleneceğini ele alır.</span><span class="sxs-lookup"><span data-stu-id="6ad51-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="6ad51-112">Nasıl yapılır: ActiveX Denetimleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="6ad51-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="6ad51-113">Visual Studio araç kutusu 'na özellik eklemek için mevcut ActiveX denetimlerini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ad51-113">Demonstrates how to use existing ActiveX controls to add features to the Visual Studio Toolbox.</span></span>  
  
 [<span data-ttu-id="6ad51-114">İzlenecek yol: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="6ad51-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="6ad51-115">Windows işletim sisteminin bir parçası olan API 'Leri çağırma sürecinde adım adım adımları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6ad51-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="6ad51-116">Nasıl yapılır: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="6ad51-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="6ad51-117">User32. dll içinde `MessageBox` işlevin nasıl tanımlanacağını ve çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ad51-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="6ad51-118">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="6ad51-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="6ad51-119">İmzasız bir tür parametresine sahip bir Windows işlevinin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ad51-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="6ad51-120">İzlenecek yol: Visual Basic ile COM nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ad51-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="6ad51-121">COM sınıf şablonuyla ve olmadan COM nesneleri oluşturma sürecinde size adım adım.</span><span class="sxs-lookup"><span data-stu-id="6ad51-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="6ad51-122">Birlikte Çalışabilirlik İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="6ad51-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="6ad51-123">COM kullanırken karşılaşabileceğiniz bazı sorunları ele alır.</span><span class="sxs-lookup"><span data-stu-id="6ad51-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="6ad51-124">.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="6ad51-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="6ad51-125">Aynı uygulamadaki COM nesnelerinin ve .NET Framework nesnelerinin nasıl kullanılacağına ilişkin bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ad51-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="6ad51-126">İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama</span><span class="sxs-lookup"><span data-stu-id="6ad51-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="6ad51-127">Mevcut COM nesnelerinin yeni nesneler için temel olarak kullanılmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ad51-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6ad51-128">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6ad51-128">Related Sections</span></span>  
 [<span data-ttu-id="6ad51-129">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="6ad51-129">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="6ad51-130">Ortak dil çalışma zamanı tarafından sunulan birlikte çalışabilirlik hizmetlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ad51-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="6ad51-131">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="6ad51-131">Exposing COM Components to the .NET Framework</span></span>](../../../framework/interop/exposing-com-components.md)  
 <span data-ttu-id="6ad51-132">Com birlikte çalışabilirliğine COM türlerini çağırma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ad51-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="6ad51-133">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="6ad51-133">Exposing .NET Framework Components to COM</span></span>](../../../framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="6ad51-134">Yönetilen türlerin COM 'dan hazırlanmasını ve kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ad51-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="6ad51-135">Birlikte Çalışma Özniteliklerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="6ad51-135">Applying Interop Attributes</span></span>](../../../standard/native-interop/apply-interop-attributes.md)  
 <span data-ttu-id="6ad51-136">, Yönetilmeyen kodla çalışırken kullanabileceğiniz öznitelikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6ad51-136">Covers attributes you can use when working with unmanaged code.</span></span>
