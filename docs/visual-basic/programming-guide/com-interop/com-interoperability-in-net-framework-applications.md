---
title: ".NET Framework Uygulamalarında COM Birlikte Çalışabilirliği (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 28ec54dc062d4fdea4836b0ecc8699982dace623
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="b21e8-102">.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b21e8-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>
<span data-ttu-id="b21e8-103">COM ve .NET Framework nesneleri aynı uygulamada kullanmak istediğinizde, nesnelerin nasıl bellekte mevcut farklar adresi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b21e8-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="b21e8-104">.NET Framework nesne yönetilen bellekte yer alan — ortak dil çalışma zamanı tarafından denetlenen bellek — ve çalışma zamanı tarafından gerektiği şekilde taşınmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="b21e8-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="b21e8-105">Bir COM nesnesi yönetilmeyen bellekte bulunur ve başka bir bellek konumuna taşımak için beklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="b21e8-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="b21e8-106">ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bu etkileşimini denetlemek için Araçlar yönetilen ve yönetilmeyen bileşenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b21e8-106"> and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="b21e8-107">Yönetilen kodu hakkında daha fazla bilgi için bkz: [ortak dil çalışma zamanı](../../../standard/clr.md).</span><span class="sxs-lookup"><span data-stu-id="b21e8-107">For more information about managed code, see [Common Language Runtime](../../../standard/clr.md).</span></span>  
  
 <span data-ttu-id="b21e8-108">COM nesneleri .NET uygulamalarında kullanmanın yanı sıra, aynı zamanda kullanmak isteyebilirsiniz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nesneleri COM yoluyla yönetilmeyen koddan erişilebilir geliştirmek için</span><span class="sxs-lookup"><span data-stu-id="b21e8-108">In addition to using COM objects in .NET applications, you may also want to use [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to develop objects accessible from unmanaged code through COM.</span></span>  
  
 <span data-ttu-id="b21e8-109">Bu sayfadaki bağlantıları COM ve .NET Framework nesneleri arasındaki etkileşimleri hakkında ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b21e8-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b21e8-110">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b21e8-110">Related Sections</span></span>  
 [<span data-ttu-id="b21e8-111">COM birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="b21e8-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 <span data-ttu-id="b21e8-112">Visual Basic'te COM nesneleri, ActiveX denetimleri, Win32 DLL'leri, yönetilen nesneleri ve COM nesnelerini devralma dahil olmak üzere, COM birlikte çalışabilirliği kapsayan konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b21e8-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span>  
  
 [<span data-ttu-id="b21e8-113">COM birlikte çalışma sarmalayıcısı hatası</span><span class="sxs-lookup"><span data-stu-id="b21e8-113">COM Interop Wrapper Error</span></span>](/cpp/misc/com-interop-wrapper-error)  
 <span data-ttu-id="b21e8-114">Proje sistemi için belirli bir bileşene COM birlikte çalışabilirliği sarmalayıcı oluşturursanız sonuçları ve seçenekleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b21e8-114">Describes the consequences and options if the project system cannot create a COM interoperability wrapper for a particular component.</span></span>  
  
 [<span data-ttu-id="b21e8-115">Yönetilmeyen kod ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="b21e8-115">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)  
 <span data-ttu-id="b21e8-116">Kısaca bazıları yönetilen ve yönetilmeyen kodu arasında etkileşim sorunlarına açıklar ve daha fazla olay incelemesi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b21e8-116">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span>  
  
 [<span data-ttu-id="b21e8-117">COM sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="b21e8-117">COM Wrappers</span></span>](../../../framework/interop/com-wrappers.md)  
 <span data-ttu-id="b21e8-118">COM yöntemleri çağırmak yönetilen kod izin verme, çalışma zamanı aranabilir sarmalayıcıları ve .NET nesne yöntemleri çağırmak COM istemcileri izin COM aranabilir sarmalayıcılar anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b21e8-118">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span>  
  
 [<span data-ttu-id="b21e8-119">Gelişmiş COM birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="b21e8-119">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="b21e8-120">COM birlikte çalışabilirliği sarmalayıcıları, özel durumlar, devralma, iş parçacığı oluşturma, olaylar, dönüştürme ve hazırlama göre kapsayan konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b21e8-120">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span>  
  
 [<span data-ttu-id="b21e8-121">Tlbimp.exe (tür kitaplığı içeri Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="b21e8-121">Tlbimp.exe (Type Library Importer)</span></span>](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 <span data-ttu-id="b21e8-122">Ortak dil çalışma zamanı derlemesi eşdeğer tanımlarında içine bir COM tür kitaplığı içinde bulunan tür tanımları dönüştürmek için kullanabileceğiniz aracı anlatılır.</span><span class="sxs-lookup"><span data-stu-id="b21e8-122">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span>
