---
description: 'Daha fazla bilgi edinin: Windows Workflow Foundation kullanım dışı türler'
title: Windows Workflow Foundation’da kullanım dışı türler
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: a536f67708c5913040848df52f178dcc2a361f6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742439"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="e5e8b-103">Windows Workflow Foundation’da kullanım dışı türler</span><span class="sxs-lookup"><span data-stu-id="e5e8b-103">Deprecated types in Windows Workflow Foundation</span></span>

<span data-ttu-id="e5e8b-104">.NET 4 ' te Iş akışı ekibi, ad alanında yeni bir Iş akışı altyapısı yayımlamıştır <xref:System.Activities> .</span><span class="sxs-lookup"><span data-stu-id="e5e8b-104">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="e5e8b-105">.NET Framework 4,5 Beta sürümü sayesinde, "WF 3" <xref:System.Workflow.Activities> , ve ad alanlarındaki türlerin çoğunu <xref:System.Workflow.ComponentModel>  <xref:System.Workflow.Runtime> eski olarak işaretliyoruz.</span><span class="sxs-lookup"><span data-stu-id="e5e8b-105">With the release of .NET Framework 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>

## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="e5e8b-106">Kullanılmayan ad alanları ve araçları</span><span class="sxs-lookup"><span data-stu-id="e5e8b-106">Obsolete namespaces and tools</span></span>

 <span data-ttu-id="e5e8b-107">Aşağıdaki derlemeler, kullanım dışı bırakılacak bir veya daha fazla ortak türe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e5e8b-107">The following assemblies have one or more public types that will be deprecated:</span></span>

- <span data-ttu-id="e5e8b-108">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="e5e8b-108">System.Workflow.Activities.dll</span></span>

- <span data-ttu-id="e5e8b-109">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="e5e8b-109">System.Workflow.ComponentModel.dll</span></span>

- <span data-ttu-id="e5e8b-110">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="e5e8b-110">System.Workflow.Runtime.dll</span></span>

- <span data-ttu-id="e5e8b-111">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="e5e8b-111">System.WorkflowServices.dll</span></span>

- <span data-ttu-id="e5e8b-112">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="e5e8b-112">Microsoft.Workflow.DebugController.dll</span></span>

- <span data-ttu-id="e5e8b-113">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="e5e8b-113">Microsoft.Workflow.Compiler.exe</span></span>

- <span data-ttu-id="e5e8b-114">Wfc.exe</span><span class="sxs-lookup"><span data-stu-id="e5e8b-114">Wfc.exe</span></span>

 <span data-ttu-id="e5e8b-115">Sonuç olarak, kullanımdan kaldırılan WF 3 API 'Leri kullanan müşteriler, aşağıdakine benzer bir iletiyle birlikte derleme uyarıları ile karşılaşacaktır:</span><span class="sxs-lookup"><span data-stu-id="e5e8b-115">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>

 <span data-ttu-id="e5e8b-116">**Uyarı BC40000: X artık kullanılmıyor: WF 3 türleri kullanım dışıdır. Lütfen bunun yerine WF 4 kullanın.**</span><span class="sxs-lookup"><span data-stu-id="e5e8b-116">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="e5e8b-117">Gelecekteki bir sürümdeki .NET Framework türleri kaldıracağız, ancak henüz bu zaman dilimini (4,5 ' de değil) belirliyoruz.</span><span class="sxs-lookup"><span data-stu-id="e5e8b-117">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="e5e8b-118">Bu geçerli adım, müşterilerimiz için yönümüzü iletmemize ve yeni WF4 modeline geçiş yapmak için yeterince zaman sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5e8b-118">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="e5e8b-119">Tabii ki, [Microsoft desteği yaşam döngüsü ilkesi](/lifecycle/)altında bu WF 3 türlerini desteklemeye devam edeceğiz.</span><span class="sxs-lookup"><span data-stu-id="e5e8b-119">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](/lifecycle/).</span></span> <span data-ttu-id="e5e8b-120">Mevcut WF3 uygulamaları .NET Framework 4,5 ' de sorun olmadan çalışacaktır ve Visual Studio 2012, yeni ve var olan WF3 tabanlı çözümleri destekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="e5e8b-120">Existing WF3 applications will run without issue on .NET Framework 4.5, and Visual Studio 2012 will support new and existing WF3-based solutions.</span></span>

 <span data-ttu-id="e5e8b-121">Ad alanındaki kurallarla ilgili türler <xref:System.Workflow.Activities.Rules> , WF 4,5 ' de değişiklik olmayan, kullanım dışı bırakılmış.</span><span class="sxs-lookup"><span data-stu-id="e5e8b-121">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>

 <span data-ttu-id="e5e8b-122">Uygulamalarını WF 4 ' e geçirmek isteyen müşteriler, [Iş akışı 4 geçiş kılavuzunda](migration-guidance.md)yardım bulacaktır.</span><span class="sxs-lookup"><span data-stu-id="e5e8b-122">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
