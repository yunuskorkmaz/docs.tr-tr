---
title: .NET Framework Uygulamalarında COM Birlikte Çalışabilirliği (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3e19f8c0a06308a604d2b219f730bf175fb0c46
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="dc7a3-102">.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc7a3-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>
<span data-ttu-id="dc7a3-103">COM ve .NET Framework nesneleri aynı uygulamada kullanmak istediğinizde, nesnelerin nasıl bellekte mevcut farklar adresi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc7a3-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="dc7a3-104">.NET Framework nesne yönetilen bellekte yer alan — ortak dil çalışma zamanı tarafından denetlenen bellek — ve çalışma zamanı tarafından gerektiği şekilde taşınmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc7a3-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="dc7a3-105">Bir COM nesnesi yönetilmeyen bellekte bulunur ve başka bir bellek konumuna taşımak için beklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="dc7a3-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> <span data-ttu-id="dc7a3-106">Visual Studio ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bu etkileşimini denetlemek için Araçlar yönetilen ve yönetilmeyen bileşenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc7a3-106">Visual Studio and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="dc7a3-107">Yönetilen kodu hakkında daha fazla bilgi için bkz: [ortak dil çalışma zamanı](../../../standard/clr.md).</span><span class="sxs-lookup"><span data-stu-id="dc7a3-107">For more information about managed code, see [Common Language Runtime](../../../standard/clr.md).</span></span>  
  
 <span data-ttu-id="dc7a3-108">COM nesneleri .NET uygulamalarında kullanarak ek olarak, aynı zamanda Visual Basic nesneleri COM yoluyla yönetilmeyen koddan erişilebilir geliştirmek için kullanmak istediğiniz</span><span class="sxs-lookup"><span data-stu-id="dc7a3-108">In addition to using COM objects in .NET applications, you may also want to use Visual Basic to develop objects accessible from unmanaged code through COM.</span></span>  
  
 <span data-ttu-id="dc7a3-109">Bu sayfadaki bağlantıları COM ve .NET Framework nesneleri arasındaki etkileşimleri hakkında ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc7a3-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dc7a3-110">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="dc7a3-110">Related Sections</span></span>  
 [<span data-ttu-id="dc7a3-111">COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="dc7a3-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 <span data-ttu-id="dc7a3-112">Visual Basic'te COM nesneleri, ActiveX denetimleri, Win32 DLL'leri, yönetilen nesneleri ve COM nesnelerini devralma dahil olmak üzere, COM birlikte çalışabilirliği kapsayan konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc7a3-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span>  
  
 [<span data-ttu-id="dc7a3-113">COM birlikte çalışma sarmalayıcısı hatası</span><span class="sxs-lookup"><span data-stu-id="dc7a3-113">COM Interop Wrapper Error</span></span>](/cpp/misc/com-interop-wrapper-error)  
 <span data-ttu-id="dc7a3-114">Proje sistemi için belirli bir bileşene COM birlikte çalışabilirliği sarmalayıcı oluşturursanız sonuçları ve seçenekleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dc7a3-114">Describes the consequences and options if the project system cannot create a COM interoperability wrapper for a particular component.</span></span>  
  
 [<span data-ttu-id="dc7a3-115">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="dc7a3-115">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="dc7a3-116">Kısaca bazıları yönetilen ve yönetilmeyen kodu arasında etkileşim sorunlarına açıklar ve daha fazla olay incelemesi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc7a3-116">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span>  
  
 [<span data-ttu-id="dc7a3-117">COM Sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="dc7a3-117">COM Wrappers</span></span>](../../../framework/interop/com-wrappers.md)  
 <span data-ttu-id="dc7a3-118">COM yöntemleri çağırmak yönetilen kod izin verme, çalışma zamanı aranabilir sarmalayıcıları ve .NET nesne yöntemleri çağırmak COM istemcileri izin COM aranabilir sarmalayıcılar anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dc7a3-118">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span>  
  
 [<span data-ttu-id="dc7a3-119">Gelişmiş COM birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="dc7a3-119">Advanced COM Interoperability</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="dc7a3-120">COM birlikte çalışabilirliği sarmalayıcıları, özel durumlar, devralma, iş parçacığı oluşturma, olaylar, dönüştürme ve hazırlama göre kapsayan konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc7a3-120">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span>  
  
 [<span data-ttu-id="dc7a3-121">Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="dc7a3-121">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 <span data-ttu-id="dc7a3-122">Ortak dil çalışma zamanı derlemesi eşdeğer tanımlarında içine bir COM tür kitaplığı içinde bulunan tür tanımları dönüştürmek için kullanabileceğiniz aracı anlatılır.</span><span class="sxs-lookup"><span data-stu-id="dc7a3-122">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span>
