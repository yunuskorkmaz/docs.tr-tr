---
description: 'Hakkında daha fazla bilgi <services> edinin: <workflowRuntime>'
title: <services> / <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 219a05b1-f573-45c9-849b-e86bc373b62f
ms.openlocfilehash: 87cac8903263b4588db43c15d7849dcd7443d41c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682806"
---
# <a name="services-of-workflowruntime"></a><span data-ttu-id="23ba0-103">\<services> / \<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="23ba0-103">\<services> of \<workflowRuntime></span></span>

<span data-ttu-id="23ba0-104">Altyapıya eklenecek hizmetlerin bir koleksiyonunu temsil eder <xref:System.Workflow.Runtime.WorkflowRuntime> .</span><span class="sxs-lookup"><span data-stu-id="23ba0-104">Represents a collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="23ba0-105">Öğeler türündedir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="23ba0-105">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="23ba0-106">Koleksiyonda belirtilen hizmetler, iş akışı çalışma zamanı altyapısı tarafından başlatılır ve uygun Oluşturucu çağrıldığında bu hizmetin hizmetlerine eklenir <xref:System.Workflow.Runtime.WorkflowRuntime> .</span><span class="sxs-lookup"><span data-stu-id="23ba0-106">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="23ba0-107">Bu nedenle, koleksiyonda belirtilen hizmetler oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="23ba0-107">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="23ba0-108">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="23ba0-108">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ba0-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23ba0-109">See also</span></span>

- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="23ba0-110">[İş akışı yapılandırma dosyaları](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="23ba0-110">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
