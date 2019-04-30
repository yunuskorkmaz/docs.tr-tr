---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: eedf0ce6cf75b8fb56daf98f2005e66162ce10d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769856"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="a9db8-101">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="a9db8-101">\<useManagedPresentation></span></span>
<span data-ttu-id="a9db8-102">CardSpace güvenlik belirteci WS-Trust öğesinin CardSpace profilini destekleyen hizmeti ile iletişim kurmak için kullanılan bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="a9db8-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="a9db8-103">Bu öğe yok özniteliği var ve boş bir anahtar vardır.</span><span class="sxs-lookup"><span data-stu-id="a9db8-103">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="a9db8-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a9db8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a9db8-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a9db8-105">\<bindings></span></span>  
<span data-ttu-id="a9db8-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a9db8-106">\<customBinding></span></span>  
<span data-ttu-id="a9db8-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a9db8-107">\<binding></span></span>  
<span data-ttu-id="a9db8-108">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="a9db8-108">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9db8-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9db8-109">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9db8-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9db8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a9db8-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a9db8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9db8-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a9db8-112">Attributes</span></span>  
 <span data-ttu-id="a9db8-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="a9db8-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a9db8-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9db8-114">Child Elements</span></span>  
 <span data-ttu-id="a9db8-115">None</span><span class="sxs-lookup"><span data-stu-id="a9db8-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a9db8-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9db8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a9db8-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="a9db8-117">Element</span></span>|<span data-ttu-id="a9db8-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9db8-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9db8-119">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a9db8-119">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a9db8-120">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a9db8-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9db8-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9db8-121">Remarks</span></span>  
 <span data-ttu-id="a9db8-122">Bu öğe, WS-Trust öğesinin CardSpace profilini destekleyen olgu, ilkede ifade etmek için bir kimlik sağlayıcısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a9db8-122">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="a9db8-123">Bu tür bir ilke onaylama yayımlama kimlik sağlayıcıları, CardSpace profilini temel alan sorunu belirteçleri görüyor olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="a9db8-123">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9db8-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9db8-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a9db8-125">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a9db8-125">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a9db8-126">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="a9db8-126">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a9db8-127">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a9db8-127">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a9db8-128">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a9db8-128">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
