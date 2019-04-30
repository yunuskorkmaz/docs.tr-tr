---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 0940248364488bb38a329c5e461d72463c574e74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670384"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="ba348-101">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="ba348-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="ba348-102">Hizmet düzeyinde bir iletim, ileti veya gönderen geçerliliğini kurar ve bir iş akışı yapılandırma öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba348-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="ba348-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ba348-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ba348-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="ba348-104">\<behaviors></span></span>  
<span data-ttu-id="ba348-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ba348-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="ba348-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="ba348-106">\<behavior></span></span>  
<span data-ttu-id="ba348-107">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="ba348-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba348-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba348-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba348-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba348-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ba348-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ba348-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba348-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ba348-111">Attributes</span></span>  
  
|<span data-ttu-id="ba348-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ba348-112">Attribute</span></span>|<span data-ttu-id="ba348-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba348-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ba348-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="ba348-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="ba348-115">Şu anki davranışı için kimlik doğrulama İlkesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ba348-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba348-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba348-116">Child Elements</span></span>  
 <span data-ttu-id="ba348-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="ba348-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba348-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba348-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ba348-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="ba348-119">Element</span></span>|<span data-ttu-id="ba348-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba348-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba348-121">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="ba348-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ba348-122">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba348-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba348-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba348-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
