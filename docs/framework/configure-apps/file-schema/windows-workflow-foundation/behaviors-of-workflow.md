---
title: <behaviors> İş akışı
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: e61a2078c5989a3b100e77e6b2f753b0ee5dd934
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271800"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="2e206-102">\<davranışlar > İş akışı</span><span class="sxs-lookup"><span data-stu-id="2e206-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="2e206-103">Bu öğeyi içeren **serviceBehaviors** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2e206-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="2e206-104">Koleksiyondaki her öğe iş akışı hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2e206-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="2e206-105">Her davranışı öğesi kendi benzersiz tarafından tanımlanır **adı** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2e206-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="2e206-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2e206-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e206-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e206-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e206-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e206-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2e206-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2e206-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e206-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2e206-110">Attributes</span></span>  
 <span data-ttu-id="2e206-111">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="2e206-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2e206-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e206-112">Child Elements</span></span>  
  
|<span data-ttu-id="2e206-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="2e206-113">Element</span></span>|<span data-ttu-id="2e206-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e206-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e206-115">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2e206-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="2e206-116">Bu yapılandırma bölümü, belirli bir iş akışı hizmeti için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2e206-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2e206-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e206-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2e206-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="2e206-118">Element</span></span>|<span data-ttu-id="2e206-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e206-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e206-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2e206-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="2e206-121">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="2e206-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e206-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e206-122">See also</span></span>
- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="2e206-123">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="2e206-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
