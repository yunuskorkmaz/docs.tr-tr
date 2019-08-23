---
title: COM Uygulamaları ile Tümleştirme Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: 6e6ff29e7d292a291c2cb4984a80c5a0927f18d2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934992"
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="ffacb-102">COM Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ffacb-102">Integrating with COM Applications Overview</span></span>
<span data-ttu-id="ffacb-103">Windows Communication Foundation (WCF), bağlı uygulamalar oluşturmak için zengin bir ortam ile yönetilen kod geliştiricisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffacb-103">Windows Communication Foundation (WCF) provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="ffacb-104">Ancak, yönetilmeyen COM tabanlı kodda önemli bir yatırımınız varsa ve geçiş yapmak istemiyorsanız, WCF hizmeti bilinen adını kullanarak yine de WCF Web hizmetlerini mevcut kodunuzla tümleştirmeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffacb-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate WCF Web services directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="ffacb-105">Hizmet bilinen adı, Office VBA, Visual Basic 6,0 veya Visual C++ 6,0 gibi çok çeşitli com tabanlı geliştirme ortamlarından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ffacb-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ffacb-106">Hizmet bilinen adı, tüm iletişimler için bir WCF iletişim kanalı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ffacb-106">The service moniker uses a WCF communication channel for all communication.</span></span> <span data-ttu-id="ffacb-107">Bu kanala yönelik güvenlik ve kimlik mekanizmaları standart COM ve DCOM proxy 'lerinde kullanılanlardan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="ffacb-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="ffacb-108">Ayrıca, hizmet bilinen adı bir WCF iletişim kanalı kullandığından, tüm çağrılar için varsayılan zaman aşımı süresi bir dakikadır.</span><span class="sxs-lookup"><span data-stu-id="ffacb-108">In addition, because the service moniker uses a WCF communication channel the default timeout period is one minute for all calls.</span></span>  
  
 <span data-ttu-id="ffacb-109">Hizmet bilinen geliştiricisi, WCF Web hizmetlerini `GetObject` çağırmak için kesin olarak belirlenmiş, com 'a özgü bir yaklaşımla birlikte yönetilmeyen geliştiriciyi sağlamak için işleviyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ffacb-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling WCF Web services.</span></span> <span data-ttu-id="ffacb-110">Bu, WCF Web hizmeti sözleşmesinin yerel, COM görünebilir tanımını ve kullanılacak bağlamayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ffacb-110">This requires a local, COM-visible definition of the WCF Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="ffacb-111">Diğer WCF istemcileri gibi, hizmet bilinen bir kanal, bu kanal oluşturma ilk yöntem çağrısında COM programcısı tarafından saydam olarak gerçekleşse de, hizmete bir türü belirtilmiş bir kanal oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ffacb-111">Like other WCF clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>  
  
 <span data-ttu-id="ffacb-112">Diğer WCF istemcileriyle ortak olarak, bilinen ad kullanıldığında, uygulamalar bir hizmetle iletişim kurmak için adresi, bağlamayı ve sözleşmeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffacb-112">In common with other WCF clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="ffacb-113">Sözleşme aşağıdaki yollarla belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="ffacb-113">The contract can be specified in one of the following ways:</span></span>  
  
- <span data-ttu-id="ffacb-114">Yazılı sözleşme – sözleşme, istemci makinesinde COM görünebilir bir tür olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ffacb-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>  
  
- <span data-ttu-id="ffacb-115">WSDL sözleşmesi – sözleşme, WSDL belgesi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ffacb-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>  
  
- <span data-ttu-id="ffacb-116">MEX sözleşmesi – sözleşme, meta veri değişimi (MEX) uç noktasından çalışma zamanında alınır.</span><span class="sxs-lookup"><span data-stu-id="ffacb-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="ffacb-117">Hizmet bilinen parametreleri tarafından desteklenen parametreler</span><span class="sxs-lookup"><span data-stu-id="ffacb-117">Parameters Supported by the Service Moniker</span></span>  
 <span data-ttu-id="ffacb-118">Aşağıdaki tabloda, hizmet bilinen adı tarafından desteklenen parametreler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ffacb-118">The following table shows the parameters that are supported by the service moniker.</span></span>  
  
|<span data-ttu-id="ffacb-119">Parametre</span><span class="sxs-lookup"><span data-stu-id="ffacb-119">Parameter</span></span>|<span data-ttu-id="ffacb-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffacb-120">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="ffacb-121">Hizmetin URL konumu.</span><span class="sxs-lookup"><span data-stu-id="ffacb-121">URL location of the service.</span></span>|  
|`binding`|<span data-ttu-id="ffacb-122">Uygulama yapılandırmasından bölüm adı bağlama.</span><span class="sxs-lookup"><span data-stu-id="ffacb-122">Binding section name from the application configuration.</span></span>|  
|`bindingConfiguration`|<span data-ttu-id="ffacb-123">Adlandırılmış bağlama bölümünün içinden adlandırılmış bağlama örneği.</span><span class="sxs-lookup"><span data-stu-id="ffacb-123">Named binding instance from within the named binding section.</span></span>|  
|`contract`|<span data-ttu-id="ffacb-124">Hizmet sözleşmesini veya sözleşme adını (MEX 'dan) temsil eden arabirim tanımlayıcısı (IID).</span><span class="sxs-lookup"><span data-stu-id="ffacb-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|  
|`wsdl`|<span data-ttu-id="ffacb-125">Farklı bir sözleşme tanımı biçimi sağlayan WSDL belgesi.</span><span class="sxs-lookup"><span data-stu-id="ffacb-125">WSDL document that provides an alternative form of contract definition.</span></span>|  
|`spnIdentity`|<span data-ttu-id="ffacb-126">Hizmetle iletişim kurmak için kullanılacak sunucu asıl adı (SPN) kimliği.</span><span class="sxs-lookup"><span data-stu-id="ffacb-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|  
|`upnIdentity`|<span data-ttu-id="ffacb-127">Hizmetle iletişim kurmak için kullanılacak kullanıcı asıl adı (UPN) kimliği.</span><span class="sxs-lookup"><span data-stu-id="ffacb-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|  
|`dnsIdentity`|<span data-ttu-id="ffacb-128">Hizmetle iletişim kurmak için kullanılacak DNS kimliği.</span><span class="sxs-lookup"><span data-stu-id="ffacb-128">DNS identity to be used to communicate with the service.</span></span>|  
|`mexAddress`|<span data-ttu-id="ffacb-129">Hizmetin meta veri değişimi (MEX) uç noktasının URL konumu.</span><span class="sxs-lookup"><span data-stu-id="ffacb-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|  
|`mexBinding`|<span data-ttu-id="ffacb-130">Uygulama yapılandırmasından, MEX uç noktasına bağlanmak için bölüm adı bağlama.</span><span class="sxs-lookup"><span data-stu-id="ffacb-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|  
|`mexBindingConfiguration`|<span data-ttu-id="ffacb-131">Adlandırılmış bağlama bölümünün içinden, MEX uç noktasına bağlanmak için adlandırılmış bağlama örneği.</span><span class="sxs-lookup"><span data-stu-id="ffacb-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|  
|`bindingNamespace`|<span data-ttu-id="ffacb-132">Alınan MEX 'den bağlama bölümü adının ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ffacb-132">Namespace of the binding section name from the retrieved MEX.</span></span>|  
|`contractNamespace`|<span data-ttu-id="ffacb-133">Alınan MEX 'deki sözleşmenin ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ffacb-133">Namespace of the contract from the retrieved MEX.</span></span>|  
|`mexSpnIdentity`|<span data-ttu-id="ffacb-134">MEX uç noktasıyla iletişim kurmak için kullanılacak sunucu asıl adı (SPN) kimliği.</span><span class="sxs-lookup"><span data-stu-id="ffacb-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexUpnIdentity`|<span data-ttu-id="ffacb-135">MEX uç noktasıyla iletişim kurmak için kullanılacak kullanıcı asıl adı (UPN) kimliği.</span><span class="sxs-lookup"><span data-stu-id="ffacb-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexDnsIdentity`|<span data-ttu-id="ffacb-136">MEX uç noktasıyla iletişim kurmak için kullanılacak DNS kimliği.</span><span class="sxs-lookup"><span data-stu-id="ffacb-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|  
|`serializer`|<span data-ttu-id="ffacb-137">"Xml" veya "DataContract" serileştirici kullanımını belirtin.</span><span class="sxs-lookup"><span data-stu-id="ffacb-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="ffacb-138">Tamamen COM tabanlı istemcilerle birlikte kullanıldığında, hizmet bilinen adı WCF ve destekleyici .NET Framework 2,0 ' i istemci bilgisayara yüklemek için gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffacb-138">Even when used with entirely COM-based clients, the service moniker requires WCF and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="ffacb-139">Ayrıca, hizmet bilinen adını kullanan istemci uygulamalarının .NET Framework çalışma zamanının uygun sürümünü yüklemesi de önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ffacb-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="ffacb-140">Office uygulamalarında bilinen ad kullanıldığında, doğru çerçeve sürümünün yüklendiğinden emin olmak için bir yapılandırma dosyası gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ffacb-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="ffacb-141">Örneğin, Excel 'de aşağıdaki metin, Excel. exe. config adlı bir dosyaya Excel. exe dosyası ile aynı dizinde yerleştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="ffacb-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  <span data-ttu-id="ffacb-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="ffacb-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a><span data-ttu-id="ffacb-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffacb-143">See also</span></span>

- [<span data-ttu-id="ffacb-144">Nasıl yapılır: Hizmet bilinen adını kaydetme ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ffacb-144">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
