---
title: 'Öğretici: Windows Communication Foundation uygulamaları ile başlayın'
description: Bu öğreticiler WCF uygulamaları oluşturmak için bir giriş sağlar.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: df73f953372202796cebce9d3e3f28bd617c67ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184118"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a><span data-ttu-id="451c8-103">Öğretici: Windows Communication Foundation uygulamaları ile başlayın</span><span class="sxs-lookup"><span data-stu-id="451c8-103">Tutorial: Get started with Windows Communication Foundation applications</span></span>
<span data-ttu-id="451c8-104">Aşağıdaki öğreticiler serisi sizi Windows Communication Foundation (WCF) programlama deneyimiyle tanıştırır.</span><span class="sxs-lookup"><span data-stu-id="451c8-104">The following series of tutorials introduce you to the Windows Communication Foundation (WCF) programming experience.</span></span> <span data-ttu-id="451c8-105">Bu öğreticiler aracılığıyla çalışmak, WCF uygulamaları oluşturmak için gereken adımları anlamanızı sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="451c8-105">Working through these tutorials in order will give you an introductory understanding of the steps required to create WCF applications.</span></span> <span data-ttu-id="451c8-106">Bitirdikten sonra, çalışan bir WCF hizmetiniz ve hizmeti çağıran bir WCF istemciniz olur.</span><span class="sxs-lookup"><span data-stu-id="451c8-106">After you finish, you'll have a running WCF service and a WCF client that calls the service.</span></span>

<span data-ttu-id="451c8-107">Öğretici, Visual Studio'yu geliştirme ortamı olarak kullandığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="451c8-107">The tutorial assumes you're using Visual Studio as the development environment.</span></span> <span data-ttu-id="451c8-108">Başka bir geliştirme ortamı kullanıyorsanız, Visual Studio'ya özgü yönergeleri yoksayın.</span><span class="sxs-lookup"><span data-stu-id="451c8-108">If you're using another development environment, ignore the Visual Studio-specific instructions.</span></span>

<span data-ttu-id="451c8-109">İndirebileceğiniz ve çalıştırabileceğiniz örnek WCF uygulamaları için [Windows Communication Foundation örneklerine](samples/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="451c8-109">For sample WCF applications that you can download and run, see [Windows Communication Foundation samples](samples/index.md).</span></span> <span data-ttu-id="451c8-110">Örneklere giriş için [bkz.](samples/getting-started-sample.md)</span><span class="sxs-lookup"><span data-stu-id="451c8-110">For an introduction to the samples, see [Getting started sample](samples/getting-started-sample.md).</span></span>

<span data-ttu-id="451c8-111">Hizmet ve istemci oluşturma hakkında daha ayrıntılı bilgi için [Temel WCF programlamaya](basic-wcf-programming.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="451c8-111">For more in-depth information about creating services and clients, see [Basic WCF programming](basic-wcf-programming.md).</span></span>

## <a name="wcf-tutorials"></a><span data-ttu-id="451c8-112">WCF eğitimleri</span><span class="sxs-lookup"><span data-stu-id="451c8-112">WCF tutorials</span></span>

<span data-ttu-id="451c8-113">İlk üç öğretici, bir WCF hizmet sözleşmesinin nasıl tanımlanacağını, nasıl uygulanacağını ve nasıl barındırılabildiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="451c8-113">The first three tutorials describe how to define a WCF service contract, how to implement it, and how to host it.</span></span> <span data-ttu-id="451c8-114">Oluşturduğunuz hizmet, konsol uygulamasında kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="451c8-114">The service that you create is self-hosted within a console application.</span></span> <span data-ttu-id="451c8-115">Ayrıca, Microsoft Internet Information Services (IIS) altında da hizmetleri barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="451c8-115">You can also host services under Microsoft Internet Information Services (IIS).</span></span> <span data-ttu-id="451c8-116">Daha fazla bilgi için [bkz: IIS'de bir WCF Hizmeti barındırın.](feature-details/how-to-host-a-wcf-service-in-iis.md)</span><span class="sxs-lookup"><span data-stu-id="451c8-116">For more information, see [How to: Host a WCF Service in IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span> <span data-ttu-id="451c8-117">Öğreticideki hizmeti yapılandırmak için kod kullanmanıza rağmen, bir yapılandırma dosyasındaki hizmetleri de [yapılandırabilirsiniz.](configuring-services-using-configuration-files.md)</span><span class="sxs-lookup"><span data-stu-id="451c8-117">Although you use code to configure the service in the tutorial, you can also [configure services within a configuration file](configuring-services-using-configuration-files.md).</span></span>

- [<span data-ttu-id="451c8-118">Öğretici: Hizmet sözleşmesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="451c8-118">Tutorial: Define a service contract</span></span>](how-to-define-a-wcf-service-contract.md)

    <span data-ttu-id="451c8-119">Kullanıcı tanımlı arabirimiçeren bir WCF sözleşmesi oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="451c8-119">You create a WCF contract with a user-defined interface.</span></span> <span data-ttu-id="451c8-120">Bu sözleşme, hizmetin ortaya çıkardığı işlevselliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="451c8-120">This contract defines the functionality that the service exposes.</span></span>

- [<span data-ttu-id="451c8-121">Öğretici: Bir hizmet sözleşmesi uygulayın</span><span class="sxs-lookup"><span data-stu-id="451c8-121">Tutorial: Implement a service contract</span></span>](how-to-implement-a-wcf-contract.md)

    <span data-ttu-id="451c8-122">Bir sözleşme tanımladıktan sonra, bir hizmet sınıfı ile uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="451c8-122">After you define a contract, you must implement it with a service class.</span></span>

- [<span data-ttu-id="451c8-123">Öğretici: Ana bilgisayar ve temel bir hizmet çalıştırın</span><span class="sxs-lookup"><span data-stu-id="451c8-123">Tutorial: Host and run a basic service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)

    <span data-ttu-id="451c8-124">Hizmet için bir bitiş noktası yapılandırın ve hizmeti bir konsol uygulamasında barındırın.</span><span class="sxs-lookup"><span data-stu-id="451c8-124">Configure an endpoint for the service and host the service in a console application.</span></span> <span data-ttu-id="451c8-125">Bir hizmetin etkin olabilmesi için, bir hizmetin çalışma zamanı ortamında yapılandırması ve barındırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="451c8-125">For a service to become active, you must configure it and host it within a run-time environment.</span></span> <span data-ttu-id="451c8-126">Bu çalışma zamanı ortamı hizmeti oluşturur ve içeriğini ve kullanım ömrünü denetler.</span><span class="sxs-lookup"><span data-stu-id="451c8-126">This run-time environment creates the service and controls its context and lifetime.</span></span>

<span data-ttu-id="451c8-127">Sonraki iki öğretici, hizmetin ortaya çıkardığı işlemleri çağırmak için bir istemci uygulamasını nasıl oluşturup, yapılandıracak ve kullanacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="451c8-127">The next two tutorials describe how to create, configure, and use a client application to call the operations the service exposes.</span></span> <span data-ttu-id="451c8-128">Hizmetler, istemci uygulamasının hizmetle iletişim kurmak için ihtiyaç duyduğu bilgileri tanımlayan meta veriler yayımlar.</span><span class="sxs-lookup"><span data-stu-id="451c8-128">Services publish metadata that define the information a client application needs to communicate with the service.</span></span> <span data-ttu-id="451c8-129">Visual Studio bu meta verilere erişim işlemini otomatikleştirir ve hizmet için istemci uygulamasını oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="451c8-129">Visual Studio automates the process of accessing this metadata and uses it to construct the client application for the service.</span></span> <span data-ttu-id="451c8-130">Visual Studio'yu kullanmamaya karar verirseniz, bunun yerine [ServiceModel Metadata Utility aracını *(Svcutil.exe)*](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="451c8-130">If you decide not to use Visual Studio, you can use the [ServiceModel Metadata Utility tool (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) instead.</span></span>

- [<span data-ttu-id="451c8-131">Öğretici: İstemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="451c8-131">Tutorial: Create a client</span></span>](how-to-create-a-wcf-client.md)

    <span data-ttu-id="451c8-132">Bir WCF hizmetinden WCF istemci proxy'si oluşturmak için meta verileri alın.</span><span class="sxs-lookup"><span data-stu-id="451c8-132">Retrieve metadata for creating a WCF client proxy from a WCF service.</span></span> <span data-ttu-id="451c8-133">Bir hizmet başvurusu eklemek için Visual Studio'yu kullanarak meta verileri alırsınız veya ServiceModel Metadata Utility aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="451c8-133">You retrieve metadata by using Visual Studio to add a service reference or you can use the ServiceModel Metadata Utility tool.</span></span> <span data-ttu-id="451c8-134">İstemcinin hizmete erişmek için kullandığı bitiş noktasını belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="451c8-134">You specify the endpoint that the client uses to access the service.</span></span>

- [<span data-ttu-id="451c8-135">Öğretici: İstemci kullanma</span><span class="sxs-lookup"><span data-stu-id="451c8-135">Tutorial: Use a client</span></span>](how-to-use-a-wcf-client.md)

    <span data-ttu-id="451c8-136">Hizmet işlemlerini aramak için WCF istemci proxy'sini kullanın.</span><span class="sxs-lookup"><span data-stu-id="451c8-136">Use the WCF client proxy to call the service operations.</span></span>

## <a name="reference"></a><span data-ttu-id="451c8-137">Başvuru</span><span class="sxs-lookup"><span data-stu-id="451c8-137">Reference</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a><span data-ttu-id="451c8-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="451c8-138">See also</span></span>

- [<span data-ttu-id="451c8-139">Kavramsal genel bakış</span><span class="sxs-lookup"><span data-stu-id="451c8-139">Conceptual overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="451c8-140">Dokümantasyon kılavuzu</span><span class="sxs-lookup"><span data-stu-id="451c8-140">Guide to the documentation</span></span>](guide-to-the-documentation.md)
- [<span data-ttu-id="451c8-141">Windows Communication Foundation nedir</span><span class="sxs-lookup"><span data-stu-id="451c8-141">What is Windows Communication Foundation</span></span>](whats-wcf.md)
- [<span data-ttu-id="451c8-142">WCF özellik ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="451c8-142">WCF feature details</span></span>](feature-details/index.md)
- [<span data-ttu-id="451c8-143">Temel programlama yaşam döngüsü</span><span class="sxs-lookup"><span data-stu-id="451c8-143">Basic programming lifecycle</span></span>](basic-programming-lifecycle.md)
- [<span data-ttu-id="451c8-144">Müşteri oluşturma</span><span class="sxs-lookup"><span data-stu-id="451c8-144">Building clients</span></span>](building-clients.md)
- [<span data-ttu-id="451c8-145">Temel WCF programlama</span><span class="sxs-lookup"><span data-stu-id="451c8-145">Basic WCF programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="451c8-146">Nasıl?</span><span class="sxs-lookup"><span data-stu-id="451c8-146">How to: Create a duplex contract</span></span>](feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="451c8-147">Nasıl yapilir: Çift yönlü sözleşmeyle hizmetlere erişin</span><span class="sxs-lookup"><span data-stu-id="451c8-147">How to: Access services with a duplex contract</span></span>](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="451c8-148">ServiceModel Metadata Yardımcı araç (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="451c8-148">ServiceModel Metadata Utility tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="451c8-149">Nasıl kullanılır: Meta veri belgelerini indirmek için Svcutil.exe'yi kullanın</span><span class="sxs-lookup"><span data-stu-id="451c8-149">How to: Use Svcutil.exe to download metadata documents</span></span>](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [<span data-ttu-id="451c8-150">Nasıl kullanılır: Yapılandırma dosyasını kullanarak bir hizmet için meta veri yayımlama</span><span class="sxs-lookup"><span data-stu-id="451c8-150">How to: Publish metadata for a service using a configuration file</span></span>](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="451c8-151">Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="451c8-151">Using bindings to configure services and clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="451c8-152">Başlatma örneği</span><span class="sxs-lookup"><span data-stu-id="451c8-152">Getting started sample</span></span>](samples/getting-started-sample.md)
- [<span data-ttu-id="451c8-153">Windows Communication Foundation örnekleri</span><span class="sxs-lookup"><span data-stu-id="451c8-153">Windows Communication Foundation samples</span></span>](samples/index.md)
- [<span data-ttu-id="451c8-154">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="451c8-154">Self-Host</span></span>](samples/self-host.md)
