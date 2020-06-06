---
title: <behaviors>iş akışı
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 05a15cdf5c043eb5d94b36028324310d2b7a8413
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398872"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="d0963-102">\<behaviors>iş akışı</span><span class="sxs-lookup"><span data-stu-id="d0963-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="d0963-103">Bu öğe **Servicedavranışlar** koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d0963-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="d0963-104">Koleksiyondaki her öğe iş akışı hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0963-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="d0963-105">Her davranış öğesi, benzersiz **ad** özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d0963-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="d0963-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0963-106">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0963-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0963-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d0963-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0963-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0963-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d0963-109">Attributes</span></span>  
 <span data-ttu-id="d0963-110">Yok</span><span class="sxs-lookup"><span data-stu-id="d0963-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d0963-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0963-111">Child Elements</span></span>  
  
|<span data-ttu-id="d0963-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0963-112">Element</span></span>|<span data-ttu-id="d0963-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0963-113">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="d0963-114">Bu yapılandırma bölümü, belirli bir iş akışı hizmeti için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0963-114">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0963-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0963-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d0963-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0963-116">Element</span></span>|<span data-ttu-id="d0963-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0963-117">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|<span data-ttu-id="d0963-118">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d0963-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0963-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0963-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="d0963-120">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="d0963-120">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
