---
title: 'Öğretici: Windows Communication Foundation uygulamaları kullanmaya başlama'
description: Bu öğreticiler, WCF uygulamaları oluşturmaya yönelik bir giriş sağlar.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 620a83260f01e27a19b19227165695a621c88e5e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238242"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a><span data-ttu-id="79504-103">Öğretici: Windows Communication Foundation uygulamaları kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="79504-103">Tutorial: Get started with Windows Communication Foundation applications</span></span>

<span data-ttu-id="79504-104">Aşağıdaki öğretici dizisi sizi Windows Communication Foundation (WCF) programlama deneyimine tanıtmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79504-104">The following series of tutorials introduce you to the Windows Communication Foundation (WCF) programming experience.</span></span> <span data-ttu-id="79504-105">Bu öğreticilerde sırayla çalışmak, WCF uygulamaları oluşturmak için gereken adımlara ilişkin açıklayıcı bir fikir verecektir.</span><span class="sxs-lookup"><span data-stu-id="79504-105">Working through these tutorials in order will give you an introductory understanding of the steps required to create WCF applications.</span></span> <span data-ttu-id="79504-106">Bitirdiğinizde, çalışan bir WCF hizmeti ve hizmeti çağıran bir WCF istemcisi vardır.</span><span class="sxs-lookup"><span data-stu-id="79504-106">After you finish, you'll have a running WCF service and a WCF client that calls the service.</span></span>

<span data-ttu-id="79504-107">Öğretici, Visual Studio 'Yu geliştirme ortamı olarak kullandığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="79504-107">The tutorial assumes you're using Visual Studio as the development environment.</span></span> <span data-ttu-id="79504-108">Başka bir geliştirme ortamı kullanıyorsanız, Visual Studio 'Ya özgü yönergeleri yoksayın.</span><span class="sxs-lookup"><span data-stu-id="79504-108">If you're using another development environment, ignore the Visual Studio-specific instructions.</span></span>

<span data-ttu-id="79504-109">İndirebileceğiniz ve çalıştırabileceğiniz örnek WCF uygulamaları için bkz. [Windows Communication Foundation Örnekleri](samples/index.md).</span><span class="sxs-lookup"><span data-stu-id="79504-109">For sample WCF applications that you can download and run, see [Windows Communication Foundation samples](samples/index.md).</span></span> <span data-ttu-id="79504-110">Örneklere giriş için bkz. Başlarken [örneği](samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="79504-110">For an introduction to the samples, see [Getting started sample](samples/getting-started-sample.md).</span></span>

<span data-ttu-id="79504-111">Hizmet ve istemci oluşturma hakkında daha ayrıntılı bilgi için bkz. [Temel WCF programlama](basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="79504-111">For more in-depth information about creating services and clients, see [Basic WCF programming](basic-wcf-programming.md).</span></span>

## <a name="wcf-tutorials"></a><span data-ttu-id="79504-112">WCF öğreticileri</span><span class="sxs-lookup"><span data-stu-id="79504-112">WCF tutorials</span></span>

<span data-ttu-id="79504-113">İlk üç öğretici, bir WCF hizmeti sözleşmesinin nasıl tanımlanacağını, nasıl uygulanacağını ve nasıl barındıralınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="79504-113">The first three tutorials describe how to define a WCF service contract, how to implement it, and how to host it.</span></span> <span data-ttu-id="79504-114">Oluşturduğunuz hizmet, bir konsol uygulaması içinde kendiliğinden barındırılır.</span><span class="sxs-lookup"><span data-stu-id="79504-114">The service that you create is self-hosted within a console application.</span></span> <span data-ttu-id="79504-115">Ayrıca, Hizmetleri Microsoft Internet Information Services (IIS) altında de barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79504-115">You can also host services under Microsoft Internet Information Services (IIS).</span></span> <span data-ttu-id="79504-116">Daha fazla bilgi için bkz. [nasıl yapılır: IIS 'de WCF hizmeti barındırma](feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="79504-116">For more information, see [How to: Host a WCF Service in IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span> <span data-ttu-id="79504-117">Öğreticide hizmeti yapılandırmak için kod kullanıyor olsanız da, [bir yapılandırma dosyası içinde hizmetleri de yapılandırabilirsiniz](configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="79504-117">Although you use code to configure the service in the tutorial, you can also [configure services within a configuration file](configuring-services-using-configuration-files.md).</span></span>

- [<span data-ttu-id="79504-118">Öğretici: hizmet sözleşmesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="79504-118">Tutorial: Define a service contract</span></span>](how-to-define-a-wcf-service-contract.md)

    <span data-ttu-id="79504-119">Kullanıcı tanımlı arabirimle bir WCF sözleşmesi oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="79504-119">You create a WCF contract with a user-defined interface.</span></span> <span data-ttu-id="79504-120">Bu sözleşme, hizmetin sunduğu işlevselliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="79504-120">This contract defines the functionality that the service exposes.</span></span>

- [<span data-ttu-id="79504-121">Öğretici: hizmet sözleşmesini uygulama</span><span class="sxs-lookup"><span data-stu-id="79504-121">Tutorial: Implement a service contract</span></span>](how-to-implement-a-wcf-contract.md)

    <span data-ttu-id="79504-122">Bir sözleşmeyi tanımladıktan sonra, bir hizmet sınıfıyla uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="79504-122">After you define a contract, you must implement it with a service class.</span></span>

- [<span data-ttu-id="79504-123">Öğretici: temel bir hizmet barındırma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="79504-123">Tutorial: Host and run a basic service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)

    <span data-ttu-id="79504-124">Hizmet için bir uç nokta yapılandırın ve hizmeti bir konsol uygulamasında barındırın.</span><span class="sxs-lookup"><span data-stu-id="79504-124">Configure an endpoint for the service and host the service in a console application.</span></span> <span data-ttu-id="79504-125">Bir hizmetin etkin hale gelmesi için, onu yapılandırmanız ve bir çalışma zamanı ortamında barındırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="79504-125">For a service to become active, you must configure it and host it within a run-time environment.</span></span> <span data-ttu-id="79504-126">Bu çalışma zamanı ortamı, hizmeti oluşturur ve bağlamını ve ömrünü denetler.</span><span class="sxs-lookup"><span data-stu-id="79504-126">This run-time environment creates the service and controls its context and lifetime.</span></span>

<span data-ttu-id="79504-127">Sonraki iki öğreticinin, hizmetin sunduğu işlemleri çağırmak için bir istemci uygulaması oluşturma, yapılandırma ve kullanma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="79504-127">The next two tutorials describe how to create, configure, and use a client application to call the operations the service exposes.</span></span> <span data-ttu-id="79504-128">Hizmetler, bir istemci uygulamasının hizmetle iletişim kurması için gereken bilgileri tanımlayan meta verileri yayımlar.</span><span class="sxs-lookup"><span data-stu-id="79504-128">Services publish metadata that define the information a client application needs to communicate with the service.</span></span> <span data-ttu-id="79504-129">Visual Studio, bu meta verilere erişme sürecini otomatikleştirir ve hizmet için istemci uygulaması oluşturmak üzere onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="79504-129">Visual Studio automates the process of accessing this metadata and uses it to construct the client application for the service.</span></span> <span data-ttu-id="79504-130">Visual Studio 'Yu kullanmamaya karar verirseniz, bunun yerine [ServiceModel meta veri yardımcı programı aracını (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79504-130">If you decide not to use Visual Studio, you can use the [ServiceModel Metadata Utility tool (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) instead.</span></span>

- [<span data-ttu-id="79504-131">Öğretici: istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="79504-131">Tutorial: Create a client</span></span>](how-to-create-a-wcf-client.md)

    <span data-ttu-id="79504-132">WCF hizmetinden bir WCF istemci proxy 'si oluşturmak için meta verileri alın.</span><span class="sxs-lookup"><span data-stu-id="79504-132">Retrieve metadata for creating a WCF client proxy from a WCF service.</span></span> <span data-ttu-id="79504-133">Bir hizmet başvurusu eklemek için Visual Studio 'Yu kullanarak meta verileri alır veya ServiceModel meta veri yardımcı programı aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79504-133">You retrieve metadata by using Visual Studio to add a service reference or you can use the ServiceModel Metadata Utility tool.</span></span> <span data-ttu-id="79504-134">İstemcinin hizmete erişmek için kullandığı uç noktayı belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79504-134">You specify the endpoint that the client uses to access the service.</span></span>

- [<span data-ttu-id="79504-135">Öğretici: istemci kullanma</span><span class="sxs-lookup"><span data-stu-id="79504-135">Tutorial: Use a client</span></span>](how-to-use-a-wcf-client.md)

    <span data-ttu-id="79504-136">Hizmet işlemlerini çağırmak için WCF istemci proxy 'sini kullanın.</span><span class="sxs-lookup"><span data-stu-id="79504-136">Use the WCF client proxy to call the service operations.</span></span>

## <a name="reference"></a><span data-ttu-id="79504-137">Başvuru</span><span class="sxs-lookup"><span data-stu-id="79504-137">Reference</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a><span data-ttu-id="79504-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79504-138">See also</span></span>

- [<span data-ttu-id="79504-139">Kavramsal genel bakış</span><span class="sxs-lookup"><span data-stu-id="79504-139">Conceptual overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="79504-140">Belge Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="79504-140">Guide to the documentation</span></span>](guide-to-the-documentation.md)
- [<span data-ttu-id="79504-141">Windows Communication Foundation nedir?</span><span class="sxs-lookup"><span data-stu-id="79504-141">What is Windows Communication Foundation</span></span>](whats-wcf.md)
- [<span data-ttu-id="79504-142">WCF özellik ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="79504-142">WCF feature details</span></span>](feature-details/index.md)
- [<span data-ttu-id="79504-143">Temel programlama yaşam döngüsü</span><span class="sxs-lookup"><span data-stu-id="79504-143">Basic programming lifecycle</span></span>](basic-programming-lifecycle.md)
- [<span data-ttu-id="79504-144">İstemcileri derleme</span><span class="sxs-lookup"><span data-stu-id="79504-144">Building clients</span></span>](building-clients.md)
- [<span data-ttu-id="79504-145">Temel WCF programlama</span><span class="sxs-lookup"><span data-stu-id="79504-145">Basic WCF programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="79504-146">Nasıl yapılır: çift yönlü sözleşme oluşturma</span><span class="sxs-lookup"><span data-stu-id="79504-146">How to: Create a duplex contract</span></span>](feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="79504-147">Nasıl yapılır: çift yönlü sözleşme ile hizmetlere erişme</span><span class="sxs-lookup"><span data-stu-id="79504-147">How to: Access services with a duplex contract</span></span>](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="79504-148">ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="79504-148">ServiceModel Metadata Utility tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="79504-149">Nasıl yapılır: meta veri belgelerini indirmek için Svcutil.exe kullanma</span><span class="sxs-lookup"><span data-stu-id="79504-149">How to: Use Svcutil.exe to download metadata documents</span></span>](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [<span data-ttu-id="79504-150">Nasıl yapılır: yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="79504-150">How to: Publish metadata for a service using a configuration file</span></span>](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="79504-151">Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="79504-151">Using bindings to configure services and clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="79504-152">Başlangıç örneği</span><span class="sxs-lookup"><span data-stu-id="79504-152">Getting started sample</span></span>](samples/getting-started-sample.md)
- [<span data-ttu-id="79504-153">Windows Communication Foundation Örnekleri</span><span class="sxs-lookup"><span data-stu-id="79504-153">Windows Communication Foundation samples</span></span>](samples/index.md)
- [<span data-ttu-id="79504-154">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="79504-154">Self-Host</span></span>](samples/self-host.md)
