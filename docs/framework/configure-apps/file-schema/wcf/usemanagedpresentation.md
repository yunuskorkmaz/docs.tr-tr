---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: eedf0ce6cf75b8fb56daf98f2005e66162ce10d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155661"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="b8b66-101">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="b8b66-101">\<useManagedPresentation></span></span>
<span data-ttu-id="b8b66-102">CardSpace güvenlik belirteci WS-Trust öğesinin CardSpace profilini destekleyen hizmeti ile iletişim kurmak için kullanılan bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="b8b66-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="b8b66-103">Bu öğe yok özniteliği var ve boş bir anahtar vardır.</span><span class="sxs-lookup"><span data-stu-id="b8b66-103">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="b8b66-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b8b66-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b8b66-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="b8b66-105">\<bindings></span></span>  
<span data-ttu-id="b8b66-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b8b66-106">\<customBinding></span></span>  
<span data-ttu-id="b8b66-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b8b66-107">\<binding></span></span>  
<span data-ttu-id="b8b66-108">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="b8b66-108">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8b66-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8b66-109">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8b66-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8b66-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b8b66-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b8b66-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8b66-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b8b66-112">Attributes</span></span>  
 <span data-ttu-id="b8b66-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="b8b66-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b8b66-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8b66-114">Child Elements</span></span>  
 <span data-ttu-id="b8b66-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="b8b66-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8b66-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8b66-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b8b66-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8b66-117">Element</span></span>|<span data-ttu-id="b8b66-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8b66-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8b66-119">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b8b66-119">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b8b66-120">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b8b66-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8b66-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8b66-121">Remarks</span></span>  
 <span data-ttu-id="b8b66-122">Bu öğe, WS-Trust öğesinin CardSpace profilini destekleyen olgu, ilkede ifade etmek için bir kimlik sağlayıcısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b8b66-122">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="b8b66-123">Bu tür bir ilke onaylama yayımlama kimlik sağlayıcıları, CardSpace profilini temel alan sorunu belirteçleri görüyor olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="b8b66-123">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8b66-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8b66-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b8b66-125">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b8b66-125">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b8b66-126">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="b8b66-126">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b8b66-127">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b8b66-127">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b8b66-128">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b8b66-128">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
