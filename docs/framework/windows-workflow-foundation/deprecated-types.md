---
title: Windows Workflow Foundation'da kullanım dışı türler
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: b25be26d4c0ad6c423b011cd7cad24a8728333f5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857651"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="ba984-102">Windows Workflow Foundation'da kullanım dışı türler</span><span class="sxs-lookup"><span data-stu-id="ba984-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="ba984-103">.NET 4'te iş akışı takımın tüm yeni bir iş akışı altyapısında yayımlanan <xref:System.Activities> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ba984-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="ba984-104">.NET 4.5 Beta sürümünde biz "WF 3" içindeki türlerin çoğu işaretleme <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, ve <xref:System.Workflow.Runtime> artık kullanılmıyor olarak ad alanları.</span><span class="sxs-lookup"><span data-stu-id="ba984-104">With the release of .NET 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>  
  
## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="ba984-105">Artık kullanılmayan ad alanları ve araçları</span><span class="sxs-lookup"><span data-stu-id="ba984-105">Obsolete namespaces and tools</span></span>  
 <span data-ttu-id="ba984-106">Aşağıdaki derlemelerini kullanım dışı bırakılacak bir veya daha fazla genel tür vardır:</span><span class="sxs-lookup"><span data-stu-id="ba984-106">The following assemblies have one or more public types that will be deprecated:</span></span>  
  
-   <span data-ttu-id="ba984-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="ba984-107">System.Workflow.Activities.dll</span></span>  
  
-   <span data-ttu-id="ba984-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="ba984-108">System.Workflow.ComponentModel.dll</span></span>  
  
-   <span data-ttu-id="ba984-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="ba984-109">System.Workflow.Runtime.dll</span></span>  
  
-   <span data-ttu-id="ba984-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="ba984-110">System.WorkflowServices.dll</span></span>  
  
-   <span data-ttu-id="ba984-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="ba984-111">Microsoft.Workflow.DebugController.dll</span></span>  
  
-   <span data-ttu-id="ba984-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="ba984-112">Microsoft.Workflow.Compiler.exe</span></span>  
  
-   <span data-ttu-id="ba984-113">WFC.exe</span><span class="sxs-lookup"><span data-stu-id="ba984-113">Wfc.exe</span></span>  
  
 <span data-ttu-id="ba984-114">Sonuç olarak, kullanım dışı WF 3 API'lerini kullanan müşteriler, derleme uyarıları aşağıdakine benzer bir ileti ile karşılaşırsınız:</span><span class="sxs-lookup"><span data-stu-id="ba984-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>  
  
 <span data-ttu-id="ba984-115">**Uyarı BC40000: X kullanılmıyor: WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine WF 4 kullanın.**</span><span class="sxs-lookup"><span data-stu-id="ba984-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="ba984-116">Gelecek sürümlerden birinde .NET Framework türleri kaldıracağız, ancak henüz bu zaman çerçevesi (değil, 4.5) belirledik değil.</span><span class="sxs-lookup"><span data-stu-id="ba984-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="ba984-117">Bu geçerli adımı bizim yönü müşterilerimiz için iletişim ve yeni WF4 modeline taşıma zamanı bolca izin olanak sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="ba984-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="ba984-118">Biz, altında bu WF 3 türlerini destekleyecek şekilde devam eder [Microsoft destek yaşam döngüsü ilkesi](https://aka.ms/MicrosoftSupportLifecycle).</span><span class="sxs-lookup"><span data-stu-id="ba984-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](https://aka.ms/MicrosoftSupportLifecycle).</span></span> <span data-ttu-id="ba984-119">Mevcut WF3 uygulamaları, .NET 4.5 üzerinde sorun çalışır ve [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] yeni ve mevcut WF3 tabanlı çözümlerini destekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="ba984-119">Existing WF3 applications will run without issue on .NET 4.5, and [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] will support new and existing WF3-based solutions.</span></span>  
  
 <span data-ttu-id="ba984-120">Kuralları ilgili türlerinde <xref:System.Workflow.Activities.Rules> değiştirme WF 4.5 içinde sahip, ad alanı değil kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ba984-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>  
  
 <span data-ttu-id="ba984-121">WF 4 uygulamalarını geçirmek isteyen müşteriler, Yardım'da bulacaksınız [iş akışı 4 geçiş kılavuzuna](migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="ba984-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
