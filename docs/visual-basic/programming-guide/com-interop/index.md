---
description: 'Daha fazla bilgi edinin: COM birlikte çalışma (Visual Basic)'
title: COM Birlikte Çalışma
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
ms.openlocfilehash: 02ce21c6175f76bca17ae6ab57aa1569800167f4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460715"
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="fe92b-103">COM Birlikte Çalışma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe92b-103">COM Interop (Visual Basic)</span></span>

<span data-ttu-id="fe92b-104">Bileşen nesne modeli (COM), bir nesnenin işlevselliğini diğer bileşenlere sunma ve uygulamaları barındırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fe92b-104">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="fe92b-105">Günümüzün yazılımlarının çoğu COM nesnelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="fe92b-105">Most of today's software includes COM objects.</span></span> <span data-ttu-id="fe92b-106">.NET derlemeleri yeni uygulamalar için en iyi seçenek olsa da, her zaman COM nesneleri kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="fe92b-106">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="fe92b-107">Bu bölümde, Visual Basic ile COM nesneleri oluşturma ve kullanma ile ilgili bazı sorunlar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe92b-107">This section covers some of the issues associated with creating and using COM objects with Visual Basic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fe92b-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fe92b-108">In This Section</span></span>  

 [<span data-ttu-id="fe92b-109">COM Birlikte Çalışma'ya Giriş</span><span class="sxs-lookup"><span data-stu-id="fe92b-109">Introduction to COM Interop</span></span>](introduction-to-com-interop.md)  
 <span data-ttu-id="fe92b-110">COM birlikte çalışabilirliğine genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe92b-110">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="fe92b-111">Nasıl yapılır: Visual Basic'den COM Nesnelerine Başvuru Yapma</span><span class="sxs-lookup"><span data-stu-id="fe92b-111">How to: Reference COM Objects from Visual Basic</span></span>](how-to-reference-com-objects.md)  
 <span data-ttu-id="fe92b-112">Tür kitaplıkları olan COM nesnelerine başvuruların nasıl ekleneceğini ele alır.</span><span class="sxs-lookup"><span data-stu-id="fe92b-112">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="fe92b-113">Nasıl yapılır: ActiveX Denetimleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="fe92b-113">How to: Work with ActiveX Controls</span></span>](how-to-work-with-activex-controls.md)  
 <span data-ttu-id="fe92b-114">Visual Studio araç kutusu 'na özellik eklemek için mevcut ActiveX denetimlerini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe92b-114">Demonstrates how to use existing ActiveX controls to add features to the Visual Studio Toolbox.</span></span>  
  
 [<span data-ttu-id="fe92b-115">İzlenecek yol: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="fe92b-115">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="fe92b-116">Windows işletim sisteminin bir parçası olan API 'Leri çağırma sürecinde adım adım adımları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fe92b-116">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="fe92b-117">Nasıl yapılır: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="fe92b-117">How to: Call Windows APIs</span></span>](how-to-call-windows-apis.md)  
 <span data-ttu-id="fe92b-118">User32.dll işlevin nasıl tanımlanacağını ve çağrılacağını gösterir `MessageBox` .</span><span class="sxs-lookup"><span data-stu-id="fe92b-118">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="fe92b-119">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="fe92b-119">How to: Call a Windows Function that Takes Unsigned Types</span></span>](how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="fe92b-120">İmzasız bir tür parametresine sahip bir Windows işlevinin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe92b-120">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="fe92b-121">İzlenecek yol: Visual Basic ile COM Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe92b-121">Walkthrough: Creating COM Objects with Visual Basic</span></span>](walkthrough-creating-com-objects.md)  
 <span data-ttu-id="fe92b-122">COM sınıf şablonuyla ve olmadan COM nesneleri oluşturma sürecinde size adım adım.</span><span class="sxs-lookup"><span data-stu-id="fe92b-122">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="fe92b-123">Birlikte Çalışabilirlik İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="fe92b-123">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)  
 <span data-ttu-id="fe92b-124">COM kullanırken karşılaşabileceğiniz bazı sorunları ele alır.</span><span class="sxs-lookup"><span data-stu-id="fe92b-124">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="fe92b-125">.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="fe92b-125">COM Interoperability in .NET Framework Applications</span></span>](com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="fe92b-126">Aynı uygulamadaki COM nesnelerinin ve .NET Framework nesnelerinin nasıl kullanılacağına ilişkin bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe92b-126">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="fe92b-127">İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama</span><span class="sxs-lookup"><span data-stu-id="fe92b-127">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="fe92b-128">Mevcut COM nesnelerinin yeni nesneler için temel olarak kullanılmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="fe92b-128">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fe92b-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="fe92b-129">Related Sections</span></span>  

 [<span data-ttu-id="fe92b-130">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="fe92b-130">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="fe92b-131">Ortak dil çalışma zamanı tarafından sunulan birlikte çalışabilirlik hizmetlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="fe92b-131">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="fe92b-132">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="fe92b-132">Exposing COM Components to the .NET Framework</span></span>](../../../framework/interop/exposing-com-components.md)  
 <span data-ttu-id="fe92b-133">Com birlikte çalışabilirliğine COM türlerini çağırma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="fe92b-133">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="fe92b-134">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="fe92b-134">Exposing .NET Framework Components to COM</span></span>](../../../framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="fe92b-135">Yönetilen türlerin COM 'dan hazırlanmasını ve kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="fe92b-135">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="fe92b-136">Birlikte Çalışma Özniteliklerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="fe92b-136">Applying Interop Attributes</span></span>](../../../standard/native-interop/apply-interop-attributes.md)  
 <span data-ttu-id="fe92b-137">, Yönetilmeyen kodla çalışırken kullanabileceğiniz öznitelikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fe92b-137">Covers attributes you can use when working with unmanaged code.</span></span>
