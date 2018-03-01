---
title: "COM Uygulamaları ile Tümleştirme Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5b20ae5329f08e9391fd7b93218c44c3c1978a48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="a3d94-102">COM Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a3d94-102">Integrating with COM Applications Overview</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="a3d94-103">yönetilen kod Geliştirici bağlı uygulamaları oluşturmak için zengin bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3d94-103"> provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="a3d94-104">Ancak, yönetilmeyen COM tabanlı kodunda önemli ölçüde yatırımınız varsa ve geçirmek istemediğiniz hala tümleştirebilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Hizmetleri doğrudan varolan kodunuza kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet bilinen adı.</span><span class="sxs-lookup"><span data-stu-id="a3d94-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services directly into your existing code by using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker.</span></span> <span data-ttu-id="a3d94-105">Hizmet adının Office VBA, Visual Basic 6.0 veya Visual C++ 6.0 gibi bir geniş aralığı, COM tabanlı geliştirme ortamlarından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3d94-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3d94-106">Hizmet bilinen adı kullanan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tüm iletişimi için iletişim kanalı.</span><span class="sxs-lookup"><span data-stu-id="a3d94-106">The service moniker uses a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication channel for all communication.</span></span> <span data-ttu-id="a3d94-107">Bu kanal için güvenlik ve kimlik mekanizmaları standart COM ve DCOM proxy'leri kullanılanlardan farklı.</span><span class="sxs-lookup"><span data-stu-id="a3d94-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="a3d94-108">Ayrıca, hizmet adının kullandığından bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iletişim kanalını varsayılan zaman aşımı süresi olan tüm çağrıları için bir dakika.</span><span class="sxs-lookup"><span data-stu-id="a3d94-108">In addition, because the service moniker uses a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication channel the default timeout period is one minute for all calls.</span></span>  
  
 <span data-ttu-id="a3d94-109">Hizmet bilinen adı ile birlikte kullanılan `GetObject` yönetilmeyen Geliştirici kesin türü belirtilmiş, COM özgü bir yaklaşım için arama sağlamak için işlevi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="a3d94-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services.</span></span> <span data-ttu-id="a3d94-110">Bu yerel, COM görünür tanımının gerektirir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web hizmet sözleşmesini ve kullanılacak bağlama.</span><span class="sxs-lookup"><span data-stu-id="a3d94-110">This requires a local, COM-visible definition of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="a3d94-111">Gibi diğer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bu kanal oluşturma ilk yöntemi çağrıda COM programcıları saydam oluşmamasına rağmen istemciler, hizmet adının hizmetine yazılan bir kanal oluşturmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3d94-111">Like other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>  
  
 <span data-ttu-id="a3d94-112">Diğer ortak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemciler, ad kullanırken uygulamaları belirtin adresi, bağlama ve hizmet ile iletişim kurmak için sözleşme.</span><span class="sxs-lookup"><span data-stu-id="a3d94-112">In common with other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="a3d94-113">Sözleşme aşağıdaki yollardan biri belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="a3d94-113">The contract can be specified in one of the following ways:</span></span>  
  
-   <span data-ttu-id="a3d94-114">Yazılı Sözleşme – Sözleşme COM görünebilir tür istemci makinesinde olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a3d94-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>  
  
-   <span data-ttu-id="a3d94-115">WSDL Sözleşme – Sözleşme WSDL Belgesi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a3d94-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="a3d94-116">Çalışma zamanında meta veri değişimi (MEX) uç noktasından MEX Sözleşme – Sözleşme alınır.</span><span class="sxs-lookup"><span data-stu-id="a3d94-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="a3d94-117">Hizmet bilinen adı tarafından desteklenen parametreleri</span><span class="sxs-lookup"><span data-stu-id="a3d94-117">Parameters Supported by the Service Moniker</span></span>  
 <span data-ttu-id="a3d94-118">Aşağıdaki tabloda hizmet bilinen adı tarafından desteklenen parametreleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="a3d94-118">The following table shows the parameters that are supported by the service moniker.</span></span>  
  
|<span data-ttu-id="a3d94-119">Parametre</span><span class="sxs-lookup"><span data-stu-id="a3d94-119">Parameter</span></span>|<span data-ttu-id="a3d94-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3d94-120">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="a3d94-121">Hizmet konumu URL.</span><span class="sxs-lookup"><span data-stu-id="a3d94-121">URL location of the service.</span></span>|  
|`binding`|<span data-ttu-id="a3d94-122">Bölüm adı uygulama yapılandırmasından bağlama.</span><span class="sxs-lookup"><span data-stu-id="a3d94-122">Binding section name from the application configuration.</span></span>|  
|`bindingConfiguration`|<span data-ttu-id="a3d94-123">Adlandırılmış bağlama bölüm içindeki adlandırılmış bağlama örneğinden.</span><span class="sxs-lookup"><span data-stu-id="a3d94-123">Named binding instance from within the named binding section.</span></span>|  
|`contract`|<span data-ttu-id="a3d94-124">Hizmet sözleşmesi veya sözleşme adı (MEX) temsil eden arabirim tanımlayıcısı (IID).</span><span class="sxs-lookup"><span data-stu-id="a3d94-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|  
|`wsdl`|<span data-ttu-id="a3d94-125">Sözleşme tanımı alternatif bir biçimidir sağlar WSDL belgesi.</span><span class="sxs-lookup"><span data-stu-id="a3d94-125">WSDL document that provides an alternative form of contract definition.</span></span>|  
|`spnIdentity`|<span data-ttu-id="a3d94-126">Hizmet ile iletişim kurmak için kullanılacak sunucu asıl adı (SPN) kimliği.</span><span class="sxs-lookup"><span data-stu-id="a3d94-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|  
|`upnIdentity`|<span data-ttu-id="a3d94-127">Hizmet ile iletişim kurmak için kullanılacak kullanıcı asıl adı (UPN) kimliği.</span><span class="sxs-lookup"><span data-stu-id="a3d94-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|  
|`dnsIdentity`|<span data-ttu-id="a3d94-128">Hizmet ile iletişim kurmak için kullanılacak DNS Kimliği'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="a3d94-128">DNS identity to be used to communicate with the service.</span></span>|  
|`mexAddress`|<span data-ttu-id="a3d94-129">Hizmet meta veri değişimi (MEX) uç noktası URL'si konumu.</span><span class="sxs-lookup"><span data-stu-id="a3d94-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|  
|`mexBinding`|<span data-ttu-id="a3d94-130">Bölüm adı MEX bitiş noktası ile bağlanmak için uygulama yapılandırmasından bağlama.</span><span class="sxs-lookup"><span data-stu-id="a3d94-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|  
|`mexBindingConfiguration`|<span data-ttu-id="a3d94-131">MEX bitiş noktası ile bağlanmak için adlandırılmış bağlama bölüm içindeki adlandırılmış bağlama örneğinden.</span><span class="sxs-lookup"><span data-stu-id="a3d94-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|  
|`bindingNamespace`|<span data-ttu-id="a3d94-132">Alınan MEX. bağlama bölüm adından Namespace</span><span class="sxs-lookup"><span data-stu-id="a3d94-132">Namespace of the binding section name from the retrieved MEX.</span></span>|  
|`contractNamespace`|<span data-ttu-id="a3d94-133">Alınan MEX. sözleşmeden Namespace</span><span class="sxs-lookup"><span data-stu-id="a3d94-133">Namespace of the contract from the retrieved MEX.</span></span>|  
|`mexSpnIdentity`|<span data-ttu-id="a3d94-134">Sunucu asıl adı (SPN) kimliğini MEX bitiş noktası ile iletişim kurmak için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="a3d94-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexUpnIdentity`|<span data-ttu-id="a3d94-135">MEX bitiş noktası ile iletişim kurmak için kullanılacak kullanıcı asıl adı (UPN) kimliği.</span><span class="sxs-lookup"><span data-stu-id="a3d94-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexDnsIdentity`|<span data-ttu-id="a3d94-136">MEX bitiş noktası ile iletişim kurmak için kullanılan DNS Kimliği'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="a3d94-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|  
|`serializer`|<span data-ttu-id="a3d94-137">"Xml" veya "datacontract" seri hale getirici belirtin.</span><span class="sxs-lookup"><span data-stu-id="a3d94-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="a3d94-138">Tamamen COM tabanlı istemcilerle bile kullanıldığında, hizmet adının gerektirir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve istemci bilgisayarda yüklü olmasını destekleyen .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="a3d94-138">Even when used with entirely COM-based clients, the service moniker requires [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="a3d94-139">Hizmet bilinen adı kullanma istemci uygulamaları .NET Framework çalışma zamanının uygun sürümünü yükleme önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a3d94-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="a3d94-140">Office uygulamaları içinde ad kullanırken, bir yapılandırma dosyası doğru framework sürümü yüklendiğinden emin olmak için gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="a3d94-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="a3d94-141">Örneğin, Excel ile Excel.exe dosyası ile aynı dizinde Excel.exe.config adlı bir dosyada aşağıdaki metni yerleştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="a3d94-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  <span data-ttu-id="a3d94-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="a3d94-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a><span data-ttu-id="a3d94-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a3d94-143">See Also</span></span>  
 [<span data-ttu-id="a3d94-144">Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a3d94-144">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
