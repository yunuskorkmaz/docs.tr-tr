---
title: '&lt;allowAccounts&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 2230b8d22a14c3df5eb3aa10872246febce015e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349697"
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="f20fd-102">&lt;allowAccounts&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="f20fd-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="f20fd-103">WCF hizmetlerini barındırmak ve Paylaşım Hizmeti bağlantı erişim izni işlemleri için bir kullanıcı hesabı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f20fd-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="f20fd-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="f20fd-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f20fd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f20fd-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f20fd-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f20fd-106">Attributes and Elements</span></span>  
 <span data-ttu-id="f20fd-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f20fd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f20fd-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f20fd-108">Attributes</span></span>  
  
|<span data-ttu-id="f20fd-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f20fd-109">Attribute</span></span>|<span data-ttu-id="f20fd-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f20fd-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f20fd-111">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="f20fd-111">securityIdentifier</span></span>|<span data-ttu-id="f20fd-112">Bir kullanıcı hesabı tanımlamak için kullanılan benzersiz bir tanımlayıcı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f20fd-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="f20fd-113">Varsayılan LocalSystem, Yöneticiler, NS, LS ve ııs_usrs değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="f20fd-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f20fd-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f20fd-114">Child Elements</span></span>  
 <span data-ttu-id="f20fd-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="f20fd-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f20fd-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f20fd-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f20fd-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="f20fd-117">Element</span></span>|<span data-ttu-id="f20fd-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f20fd-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f20fd-119">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="f20fd-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="f20fd-120">Bir koleksiyon içeren yapılandırma öğelerinin bir `securityIdentifier` özniteliği barındıran WCF hizmetleri ve Paylaşım Hizmeti bağlantı erişim izni verilen işlemler için kullanıcı hesaplarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="f20fd-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f20fd-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="f20fd-121">Example</span></span>  
 <span data-ttu-id="f20fd-122">Aşağıdaki yapılandırma örneğinde kullanıcı hesapları için beş varsayılan tanımlayıcıları bu koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="f20fd-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>  
   // LocalSystem account  
   <add securityIdentifier="S-1-5-18"/>  
   // LocalService account  
   <add securityIdentifier="S-1-5-19"/>  
   // Administrators account  
   <add securityIdentifier="S-1-5-20"/>  
   // Network Service account  
   <add securityIdentifier="S-1-5-32-544" />  
   // IIS_IUSRS account (Vista only)  
   <add securityIdentifier="S-1-5-32-568"/>  
</allowAccounts>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f20fd-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f20fd-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
