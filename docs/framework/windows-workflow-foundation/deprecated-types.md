---
title: "Windows Workflow Foundation kullanım dışı türleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 422e95a105978749cc56dfe6601fb4518cc11509
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="3868a-102">Windows Workflow Foundation kullanım dışı türleri</span><span class="sxs-lookup"><span data-stu-id="3868a-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="3868a-103">Tüm yeni bir iş akışı altyapısında iş akışı takım .NET 4'te yayımlanan <xref:System.Activities> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="3868a-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="3868a-104">.NET 4.5 Beta sürümünden biz "WF 3" türlerinde çoğunu işaretleme <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, ve <xref:System.Workflow.Runtime> artık kullanılmayan olarak ad alanları.</span><span class="sxs-lookup"><span data-stu-id="3868a-104">With the release of .NET 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>  
  
## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="3868a-105">Artık kullanılmayan ad alanları ve araçları</span><span class="sxs-lookup"><span data-stu-id="3868a-105">Obsolete namespaces and tools</span></span>  
 <span data-ttu-id="3868a-106">Aşağıdaki derlemeler kullanım dışı kalacaktır bir veya daha fazla genel tür vardır:</span><span class="sxs-lookup"><span data-stu-id="3868a-106">The following assemblies have one or more public types that will be deprecated:</span></span>  
  
-   <span data-ttu-id="3868a-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="3868a-107">System.Workflow.Activities.dll</span></span>  
  
-   <span data-ttu-id="3868a-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="3868a-108">System.Workflow.ComponentModel.dll</span></span>  
  
-   <span data-ttu-id="3868a-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="3868a-109">System.Workflow.Runtime.dll</span></span>  
  
-   <span data-ttu-id="3868a-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="3868a-110">System.WorkflowServices.dll</span></span>  
  
-   <span data-ttu-id="3868a-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="3868a-111">Microsoft.Workflow.DebugController.dll</span></span>  
  
-   <span data-ttu-id="3868a-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="3868a-112">Microsoft.Workflow.Compiler.exe</span></span>  
  
-   <span data-ttu-id="3868a-113">WFC.exe</span><span class="sxs-lookup"><span data-stu-id="3868a-113">Wfc.exe</span></span>  
  
 <span data-ttu-id="3868a-114">Sonuç olarak, kullanım dışı WF 3 API'lerini kullanan müşteriler oluşturma uyarıları aşağıdakine benzer bir iletiyle karşılaşırsınız:</span><span class="sxs-lookup"><span data-stu-id="3868a-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>  
  
 <span data-ttu-id="3868a-115">**Uyarı BC40000: X kullanılmıyor: WF 3 türleri dışıdır. Lütfen WF 4 kullanın.**</span><span class="sxs-lookup"><span data-stu-id="3868a-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="3868a-116">Biz türleri gelecek bir sürümde .NET Framework kaldıracak, ancak henüz o zaman çerçevesinde (değil 4.5) belirledik değil.</span><span class="sxs-lookup"><span data-stu-id="3868a-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="3868a-117">Geçerli bu adımı bize müşterilerimizin bizim yönüne iletişim kurmasını ve onu bol yeni WF4 modeline taşmanın ne zaman izin verir.</span><span class="sxs-lookup"><span data-stu-id="3868a-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="3868a-118">Elbette, altında bu WF 3 türlerini desteklemek devam [Microsoft destek yaşam döngüsü ilkesi](http://aka.ms/MicrosoftSupportLifecycle).</span><span class="sxs-lookup"><span data-stu-id="3868a-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](http://aka.ms/MicrosoftSupportLifecycle).</span></span> <span data-ttu-id="3868a-119">Varolan WF3 uygulamaları, .NET 4.5, sorun çalışır ve [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] yeni ve mevcut WF3 tabanlı çözümler destekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="3868a-119">Existing WF3 applications will run without issue on .NET 4.5, and [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] will support new and existing WF3-based solutions.</span></span>  
  
 <span data-ttu-id="3868a-120">Kuralları ilgili türlerinde <xref:System.Workflow.Activities.Rules> yenisini WF 4.5 gerekmez, ad alanı değil kullanımdan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="3868a-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>  
  
 <span data-ttu-id="3868a-121">WF 4 uygulamalarını geçirmek isteyen müşteriler, Yardım'da bulacaksınız [iş akışı 4 Geçiş Kılavuzu](migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="3868a-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
