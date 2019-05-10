---
title: COM Uygulamaları ile Tümleştirme Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: 2be428f0ae83596a4398fc9830af40d05f6ab191
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638659"
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="346a7-102">COM Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="346a7-102">Integrating with COM Applications Overview</span></span>
<span data-ttu-id="346a7-103">Windows Communication Foundation (WCF), yönetilen kod geliştiriciye bağlantılı uygulamalar oluşturmaya yönelik zengin bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="346a7-103">Windows Communication Foundation (WCF) provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="346a7-104">Yönetilmeyen COM tabanlı kodunda önemli bir yatırımınız varsa ve geçirmek istiyor musunuz, ancak hala WCF Web Hizmetleri doğrudan mevcut kodunuza WCF hizmet bilinen adını kullanarak tümleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="346a7-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate WCF Web services directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="346a7-105">Hizmet bilinen adı, Office VBA, Visual Basic 6.0 veya Visual C++ 6.0 gibi bir geniş aralığı, COM tabanlı geliştirme ortamlarından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="346a7-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="346a7-106">Hizmet bilinen adı WCF iletişim kanalı tüm iletişimi için kullanır.</span><span class="sxs-lookup"><span data-stu-id="346a7-106">The service moniker uses a WCF communication channel for all communication.</span></span> <span data-ttu-id="346a7-107">Bu kanal için güvenlik ve kimlik mekanizmaları, kullanılan standart COM ve DCOM Proxy farklıdır.</span><span class="sxs-lookup"><span data-stu-id="346a7-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="346a7-108">Ayrıca, hizmet adının varsayılan zaman aşımı süresi bir WCF iletişim kanalı kullandığından tüm çağrıları için bir dakika olur.</span><span class="sxs-lookup"><span data-stu-id="346a7-108">In addition, because the service moniker uses a WCF communication channel the default timeout period is one minute for all calls.</span></span>  
  
 <span data-ttu-id="346a7-109">Hizmet bilinen adı ile kullanılan `GetObject` WCF Web hizmetlerini çağırmak için kesin türü belirtilmiş, COM özgü bir yaklaşım ile yönetilmeyen Geliştirici sağlamak için işlevi.</span><span class="sxs-lookup"><span data-stu-id="346a7-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling WCF Web services.</span></span> <span data-ttu-id="346a7-110">Bu yerel, COM görünür tanımı WCF Web hizmeti sözleşmesi ve kullanılacak bağlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="346a7-110">This requires a local, COM-visible definition of the WCF Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="346a7-111">İlk yöntem çağrısında COM programcıları bu kanal oluşturma şeffaf bir şekilde gerçekleşir, ancak diğer WCF istemcileri gibi hizmet türü belirtilmiş bir kanala hizmet bilinen adı oluşturmalıdır.</span><span class="sxs-lookup"><span data-stu-id="346a7-111">Like other WCF clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>  
  
 <span data-ttu-id="346a7-112">Bilinen ad kullanırken diğer WCF istemcileri ortak, adresi, bağlama ve hizmet ile iletişim kurmak için sözleşme uygulamaları belirtin.</span><span class="sxs-lookup"><span data-stu-id="346a7-112">In common with other WCF clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="346a7-113">Sözleşme aşağıdaki yollardan birinde belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="346a7-113">The contract can be specified in one of the following ways:</span></span>  
  
- <span data-ttu-id="346a7-114">Yazılı Sözleşme – Sözleşme, istemci makinede COM görünür türü olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="346a7-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>  
  
- <span data-ttu-id="346a7-115">WSDL sözleşme – sözleşmenin bir WSDL Belgesi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="346a7-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>  
  
- <span data-ttu-id="346a7-116">MEX Sözleşme – Sözleşme, çalışma zamanında bir meta veri değişimi (MEX) uç noktasından alınır.</span><span class="sxs-lookup"><span data-stu-id="346a7-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="346a7-117">Hizmet bilinen adı tarafından desteklenen parametreleri</span><span class="sxs-lookup"><span data-stu-id="346a7-117">Parameters Supported by the Service Moniker</span></span>  
 <span data-ttu-id="346a7-118">Hizmet bilinen adı tarafından desteklenen parametreleri aşağıdaki tabloda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="346a7-118">The following table shows the parameters that are supported by the service moniker.</span></span>  
  
|<span data-ttu-id="346a7-119">Parametre</span><span class="sxs-lookup"><span data-stu-id="346a7-119">Parameter</span></span>|<span data-ttu-id="346a7-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="346a7-120">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="346a7-121">Hizmet URL'si konumu.</span><span class="sxs-lookup"><span data-stu-id="346a7-121">URL location of the service.</span></span>|  
|`binding`|<span data-ttu-id="346a7-122">Bölüm adı uygulama yapılandırmasından bağlama.</span><span class="sxs-lookup"><span data-stu-id="346a7-122">Binding section name from the application configuration.</span></span>|  
|`bindingConfiguration`|<span data-ttu-id="346a7-123">Adlandırılmış bağlama bölümü içinde adlandırılmış bağlama örneğinden.</span><span class="sxs-lookup"><span data-stu-id="346a7-123">Named binding instance from within the named binding section.</span></span>|  
|`contract`|<span data-ttu-id="346a7-124">Hizmet sözleşmesi ya da sözleşme adı (MEX) temsil eden arabirim tanımlayıcısı (IID).</span><span class="sxs-lookup"><span data-stu-id="346a7-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|  
|`wsdl`|<span data-ttu-id="346a7-125">WSDL belgesi sözleşme tanımı alternatif bir form sağlar.</span><span class="sxs-lookup"><span data-stu-id="346a7-125">WSDL document that provides an alternative form of contract definition.</span></span>|  
|`spnIdentity`|<span data-ttu-id="346a7-126">Sunucu asıl adı (SPN) kimlik hizmetiyle iletişim kurmak için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="346a7-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|  
|`upnIdentity`|<span data-ttu-id="346a7-127">Kullanıcı asıl adı (UPN) hizmetiyle iletişim kurmak için kullanılacak kimlik.</span><span class="sxs-lookup"><span data-stu-id="346a7-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|  
|`dnsIdentity`|<span data-ttu-id="346a7-128">Hizmetiyle iletişim kurmak için kullanılacak DNS Kimliği'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="346a7-128">DNS identity to be used to communicate with the service.</span></span>|  
|`mexAddress`|<span data-ttu-id="346a7-129">Hizmet meta veri değişimi (MEX) uç noktası URL konumu.</span><span class="sxs-lookup"><span data-stu-id="346a7-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|  
|`mexBinding`|<span data-ttu-id="346a7-130">MEX uç noktası ile bağlanmak için uygulama yapılandırmasından bağlama bölüm adı.</span><span class="sxs-lookup"><span data-stu-id="346a7-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|  
|`mexBindingConfiguration`|<span data-ttu-id="346a7-131">MEX uç noktası ile bağlanmak için adlandırılmış bağlama bölümü içinde adlandırılmış bağlama örneğinden.</span><span class="sxs-lookup"><span data-stu-id="346a7-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|  
|`bindingNamespace`|<span data-ttu-id="346a7-132">Namespace öğesinden alınan MEX. bağlama bölüm adı</span><span class="sxs-lookup"><span data-stu-id="346a7-132">Namespace of the binding section name from the retrieved MEX.</span></span>|  
|`contractNamespace`|<span data-ttu-id="346a7-133">Namespace, alınan MEX. sözleşmeden</span><span class="sxs-lookup"><span data-stu-id="346a7-133">Namespace of the contract from the retrieved MEX.</span></span>|  
|`mexSpnIdentity`|<span data-ttu-id="346a7-134">Sunucu asıl adı (SPN) kimliğini MEX uç noktası ile iletişim kurmak için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="346a7-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexUpnIdentity`|<span data-ttu-id="346a7-135">MEX uç noktası ile iletişim kurmak için kullanılacak kullanıcı asıl adı (UPN) kimliği.</span><span class="sxs-lookup"><span data-stu-id="346a7-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexDnsIdentity`|<span data-ttu-id="346a7-136">MEX uç noktası ile iletişim kurmak için kullanılacak DNS Kimliği'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="346a7-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|  
|`serializer`|<span data-ttu-id="346a7-137">"Xml" veya "datacontract" seri hale getirici kullanımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="346a7-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="346a7-138">Hatta tamamen COM tabanlı istemciler ile kullanıldığında, hizmet bilinen adı WCF ve destekleyen .NET Framework 2.0 istemci bilgisayarda yüklü olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="346a7-138">Even when used with entirely COM-based clients, the service moniker requires WCF and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="346a7-139">Hizmet bilinen adı kullanan istemci uygulamaları uygun .NET Framework çalışma zamanı sürümünü yükleme önemlidir.</span><span class="sxs-lookup"><span data-stu-id="346a7-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="346a7-140">Office uygulamaları içinde ad kullanırken bir yapılandırma dosyası doğru framework sürümünü yüklendiğinden emin olmak için gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="346a7-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="346a7-141">Örneğin, Excel ile Excel.exe dosyasıyla aynı dizinde Excel.exe.config adlı bir dosyada aşağıdaki metni yerleştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="346a7-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  <span data-ttu-id="346a7-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="346a7-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a><span data-ttu-id="346a7-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="346a7-143">See also</span></span>

- [<span data-ttu-id="346a7-144">Nasıl yapılır: Kaydetme ve hizmet bilinen adı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="346a7-144">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
