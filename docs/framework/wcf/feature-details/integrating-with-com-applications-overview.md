---
description: 'Hakkında daha fazla bilgi edinin: COM uygulamalarıyla tümleştirme genel bakış'
title: COM Uygulamaları ile Tümleştirme Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: a179fd73c8065fff1e16d3f86202d717df155b81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802820"
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="20b96-103">COM Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="20b96-103">Integrating with COM Applications Overview</span></span>

<span data-ttu-id="20b96-104">Windows Communication Foundation (WCF), bağlı uygulamalar oluşturmak için zengin bir ortam ile yönetilen kod geliştiricisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="20b96-104">Windows Communication Foundation (WCF) provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="20b96-105">Ancak, yönetilmeyen COM tabanlı kodda önemli bir yatırımınız varsa ve geçiş yapmak istemiyorsanız, WCF hizmeti bilinen adını kullanarak yine de WCF Web hizmetlerini mevcut kodunuzla tümleştirmeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20b96-105">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate WCF Web services directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="20b96-106">Hizmet bilinen adı, Office VBA, Visual Basic 6,0 veya Visual C++ 6,0 gibi çok çeşitli COM tabanlı geliştirme ortamlarından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="20b96-106">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>

> [!NOTE]
> <span data-ttu-id="20b96-107">Hizmet bilinen adı, tüm iletişimler için bir WCF iletişim kanalı kullanır.</span><span class="sxs-lookup"><span data-stu-id="20b96-107">The service moniker uses a WCF communication channel for all communication.</span></span> <span data-ttu-id="20b96-108">Bu kanala yönelik güvenlik ve kimlik mekanizmaları standart COM ve DCOM proxy 'lerinde kullanılanlardan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="20b96-108">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="20b96-109">Ayrıca, hizmet bilinen adı bir WCF iletişim kanalı kullandığından, tüm çağrılar için varsayılan zaman aşımı süresi bir dakikadır.</span><span class="sxs-lookup"><span data-stu-id="20b96-109">In addition, because the service moniker uses a WCF communication channel the default timeout period is one minute for all calls.</span></span>

<span data-ttu-id="20b96-110">Hizmet bilinen `GetObject` geliştiricisi, WCF Web hizmetlerini çağırmak için kesin olarak belirlenmiş, com 'a özgü bir yaklaşımla birlikte yönetilmeyen geliştiriciyi sağlamak için işleviyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20b96-110">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling WCF Web services.</span></span> <span data-ttu-id="20b96-111">Bu, WCF Web hizmeti sözleşmesinin yerel, COM görünebilir tanımını ve kullanılacak bağlamayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="20b96-111">This requires a local, COM-visible definition of the WCF Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="20b96-112">Diğer WCF istemcileri gibi, hizmet bilinen bir kanal, bu kanal oluşturma ilk yöntem çağrısında COM programcısı tarafından saydam olarak gerçekleşse de, hizmete bir türü belirtilmiş bir kanal oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20b96-112">Like other WCF clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>

<span data-ttu-id="20b96-113">Diğer WCF istemcileriyle ortak olarak, bilinen ad kullanıldığında, uygulamalar bir hizmetle iletişim kurmak için adresi, bağlamayı ve sözleşmeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="20b96-113">In common with other WCF clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="20b96-114">Sözleşme aşağıdaki yollarla belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="20b96-114">The contract can be specified in one of the following ways:</span></span>

- <span data-ttu-id="20b96-115">Yazılı sözleşme – sözleşme, istemci makinesinde COM görünebilir bir tür olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="20b96-115">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>

- <span data-ttu-id="20b96-116">WSDL sözleşmesi – sözleşme, WSDL belgesi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="20b96-116">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>

- <span data-ttu-id="20b96-117">MEX sözleşmesi – sözleşme, meta veri değişimi (MEX) uç noktasından çalışma zamanında alınır.</span><span class="sxs-lookup"><span data-stu-id="20b96-117">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>

## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="20b96-118">Hizmet bilinen parametreleri tarafından desteklenen parametreler</span><span class="sxs-lookup"><span data-stu-id="20b96-118">Parameters Supported by the Service Moniker</span></span>

<span data-ttu-id="20b96-119">Aşağıdaki tabloda, hizmet bilinen adı tarafından desteklenen parametreler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="20b96-119">The following table shows the parameters that are supported by the service moniker.</span></span>

|<span data-ttu-id="20b96-120">Parametre</span><span class="sxs-lookup"><span data-stu-id="20b96-120">Parameter</span></span>|<span data-ttu-id="20b96-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20b96-121">Description</span></span>|
|---------------|-----------------|
|`address`|<span data-ttu-id="20b96-122">Hizmetin URL konumu.</span><span class="sxs-lookup"><span data-stu-id="20b96-122">URL location of the service.</span></span>|
|`binding`|<span data-ttu-id="20b96-123">Uygulama yapılandırmasından bölüm adı bağlama.</span><span class="sxs-lookup"><span data-stu-id="20b96-123">Binding section name from the application configuration.</span></span>|
|`bindingConfiguration`|<span data-ttu-id="20b96-124">Adlandırılmış bağlama bölümünün içinden adlandırılmış bağlama örneği.</span><span class="sxs-lookup"><span data-stu-id="20b96-124">Named binding instance from within the named binding section.</span></span>|
|`contract`|<span data-ttu-id="20b96-125">Hizmet sözleşmesini veya sözleşme adını (MEX 'dan) temsil eden arabirim tanımlayıcısı (IID).</span><span class="sxs-lookup"><span data-stu-id="20b96-125">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|
|`wsdl`|<span data-ttu-id="20b96-126">Farklı bir sözleşme tanımı biçimi sağlayan WSDL belgesi.</span><span class="sxs-lookup"><span data-stu-id="20b96-126">WSDL document that provides an alternative form of contract definition.</span></span>|
|`spnIdentity`|<span data-ttu-id="20b96-127">Hizmetle iletişim kurmak için kullanılacak sunucu asıl adı (SPN) kimliği.</span><span class="sxs-lookup"><span data-stu-id="20b96-127">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|
|`upnIdentity`|<span data-ttu-id="20b96-128">Hizmetle iletişim kurmak için kullanılacak kullanıcı asıl adı (UPN) kimliği.</span><span class="sxs-lookup"><span data-stu-id="20b96-128">User principal name (UPN) identity to be used to communicate with the service.</span></span>|
|`dnsIdentity`|<span data-ttu-id="20b96-129">Hizmetle iletişim kurmak için kullanılacak DNS kimliği.</span><span class="sxs-lookup"><span data-stu-id="20b96-129">DNS identity to be used to communicate with the service.</span></span>|
|`mexAddress`|<span data-ttu-id="20b96-130">Hizmetin meta veri değişimi (MEX) uç noktasının URL konumu.</span><span class="sxs-lookup"><span data-stu-id="20b96-130">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|
|`mexBinding`|<span data-ttu-id="20b96-131">Uygulama yapılandırmasından, MEX uç noktasına bağlanmak için bölüm adı bağlama.</span><span class="sxs-lookup"><span data-stu-id="20b96-131">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|
|`mexBindingConfiguration`|<span data-ttu-id="20b96-132">Adlandırılmış bağlama bölümünün içinden, MEX uç noktasına bağlanmak için adlandırılmış bağlama örneği.</span><span class="sxs-lookup"><span data-stu-id="20b96-132">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|
|`bindingNamespace`|<span data-ttu-id="20b96-133">Alınan MEX 'den bağlama bölümü adının ad alanı.</span><span class="sxs-lookup"><span data-stu-id="20b96-133">Namespace of the binding section name from the retrieved MEX.</span></span>|
|`contractNamespace`|<span data-ttu-id="20b96-134">Alınan MEX 'deki sözleşmenin ad alanı.</span><span class="sxs-lookup"><span data-stu-id="20b96-134">Namespace of the contract from the retrieved MEX.</span></span>|
|`mexSpnIdentity`|<span data-ttu-id="20b96-135">MEX uç noktasıyla iletişim kurmak için kullanılacak sunucu asıl adı (SPN) kimliği.</span><span class="sxs-lookup"><span data-stu-id="20b96-135">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexUpnIdentity`|<span data-ttu-id="20b96-136">MEX uç noktasıyla iletişim kurmak için kullanılacak kullanıcı asıl adı (UPN) kimliği.</span><span class="sxs-lookup"><span data-stu-id="20b96-136">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexDnsIdentity`|<span data-ttu-id="20b96-137">MEX uç noktasıyla iletişim kurmak için kullanılacak DNS kimliği.</span><span class="sxs-lookup"><span data-stu-id="20b96-137">DNS identity to be used to communicate with the MEX endpoint.</span></span>|
|`serializer`|<span data-ttu-id="20b96-138">"Xml" veya "DataContract" serileştirici kullanımını belirtin.</span><span class="sxs-lookup"><span data-stu-id="20b96-138">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|

> [!NOTE]
> <span data-ttu-id="20b96-139">Tamamen COM tabanlı istemcilerle birlikte kullanıldığında, hizmet bilinen adı WCF ve destekleyici .NET Framework 2,0 ' i istemci bilgisayara yüklemek için gerekir.</span><span class="sxs-lookup"><span data-stu-id="20b96-139">Even when used with entirely COM-based clients, the service moniker requires WCF and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="20b96-140">Ayrıca, hizmet bilinen adını kullanan istemci uygulamalarının .NET Framework çalışma zamanının uygun sürümünü yüklemesi de önemlidir.</span><span class="sxs-lookup"><span data-stu-id="20b96-140">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="20b96-141">Office uygulamalarında bilinen ad kullanıldığında, doğru çerçeve sürümünün yüklendiğinden emin olmak için bir yapılandırma dosyası gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="20b96-141">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="20b96-142">Örneğin, Excel 'de aşağıdaki metin, Excel.exe dosyası ile aynı dizinde Excel.exe.config adlı bir dosyaya yerleştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="20b96-142">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>
>
> `<?xml version="1.0" encoding="utf-8"?>`
>
> <span data-ttu-id="20b96-143">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="20b96-143">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>
>
> `<startup>`
>
> `<requiredRuntime version="v2.0.50727" />`
>
> `</startup>`
>
> `</configuration>`

## <a name="see-also"></a><span data-ttu-id="20b96-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20b96-144">See also</span></span>

- [<span data-ttu-id="20b96-145">Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="20b96-145">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)
