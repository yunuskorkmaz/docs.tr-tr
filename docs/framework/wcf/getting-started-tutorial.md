---
title: 'Öğretici: Windows Communication Foundation uygulamalarla çalışmaya başlama'
description: Bu öğreticiler WCF uygulamaları oluşturmaya yönelik bir giriş sağlar.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 66211cfcf2b742e43eccbefb2bc7c4bd1147b05b
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58408866"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a><span data-ttu-id="49f8f-103">Öğretici: Windows Communication Foundation uygulamalarla çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="49f8f-103">Tutorial: Get started with Windows Communication Foundation applications</span></span>
<span data-ttu-id="49f8f-104">Şu öğretici serisinde, Windows Communication Foundation (programlama deneyimi WCF için) sunar.</span><span class="sxs-lookup"><span data-stu-id="49f8f-104">The following series of tutorials introduce you to the Windows Communication Foundation (WCF) programming experience.</span></span> <span data-ttu-id="49f8f-105">Bu öğreticileri sırasıyla üzerinden geçmeden WCF uygulamaları oluşturmak için gerekli adımları tanıtıcı bir anlayış verir.</span><span class="sxs-lookup"><span data-stu-id="49f8f-105">Working through these tutorials in order will give you an introductory understanding of the steps required to create WCF applications.</span></span> <span data-ttu-id="49f8f-106">İşlemi tamamladığınızda, çalışan bir WCF hizmeti ve hizmetini çağıran bir WCF istemcisi sahip olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="49f8f-106">After you finish, you'll have a running WCF service and a WCF client that calls the service.</span></span> 

<span data-ttu-id="49f8f-107">Bu öğretici, geliştirme ortamı olarak Visual Studio kullanıyorsanız varsayar.</span><span class="sxs-lookup"><span data-stu-id="49f8f-107">The tutorial assumes you're using Visual Studio as the development environment.</span></span> <span data-ttu-id="49f8f-108">Başka bir geliştirme ortamı kullanıyorsanız, Visual Studio özgü yönergeleri yoksayın.</span><span class="sxs-lookup"><span data-stu-id="49f8f-108">If you're using another development environment, ignore the Visual Studio-specific instructions.</span></span> 

<span data-ttu-id="49f8f-109">İndirip çalıştırabileceğiniz örnek WCF uygulamalar için bkz: [Windows Communication Foundation örnekleri](samples/index.md).</span><span class="sxs-lookup"><span data-stu-id="49f8f-109">For sample WCF applications that you can download and run, see [Windows Communication Foundation samples](samples/index.md).</span></span> <span data-ttu-id="49f8f-110">Örnekleri bir giriş için bkz [Başlarken örnek](samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="49f8f-110">For an introduction to the samples, see [Getting started sample](samples/getting-started-sample.md).</span></span>

<span data-ttu-id="49f8f-111">Hizmetler ve istemcileri oluşturma hakkında daha ayrıntılı bilgi için bkz: [temel WCF programlama](basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="49f8f-111">For more in-depth information about creating services and clients, see [Basic WCF programming](basic-wcf-programming.md).</span></span>

## <a name="wcf-tutorials"></a><span data-ttu-id="49f8f-112">WCF öğreticiler</span><span class="sxs-lookup"><span data-stu-id="49f8f-112">WCF tutorials</span></span>

<span data-ttu-id="49f8f-113">İlk üç öğretici, bir WCF hizmet sözleşmesini tanımlama, nasıl ve sitemi barındırmak nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="49f8f-113">The first three tutorials describe how to define a WCF service contract, how to implement it, and how to host it.</span></span> <span data-ttu-id="49f8f-114">Oluşturduğunuz bir konsol uygulaması içinde şirket içinde barındırılan hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="49f8f-114">The service that you create is self-hosted within a console application.</span></span> <span data-ttu-id="49f8f-115">Ayrıca Microsoft Internet Information Services (IIS) altında Hizmetleri barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="49f8f-115">You can also host services under Microsoft Internet Information Services (IIS).</span></span> <span data-ttu-id="49f8f-116">Daha fazla bilgi için [nasıl yapılır: IIS'de WCF Hizmeti barındırma](feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="49f8f-116">For more information, see [How to: Host a WCF Service in IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span> <span data-ttu-id="49f8f-117">Öğreticide hizmeti yapılandırmak için kod kullansa da, ayrıca [hizmetlerini yapılandırma dosyasındaki yapılandırma](configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="49f8f-117">Although you use code to configure the service in the tutorial, you can also [configure services within a configuration file](configuring-services-using-configuration-files.md).</span></span> 

- [<span data-ttu-id="49f8f-118">Öğretici: Bir hizmet sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="49f8f-118">Tutorial: Define a service contract</span></span>](how-to-define-a-wcf-service-contract.md)

    <span data-ttu-id="49f8f-119">Kullanıcı tanımlı bir arabirimle'de bir WCF sözleşmesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="49f8f-119">You create a WCF contract with a user-defined interface.</span></span> <span data-ttu-id="49f8f-120">Bu sözleşme hizmet sunan işlevleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="49f8f-120">This contract defines the functionality that the service exposes.</span></span>

- [<span data-ttu-id="49f8f-121">Öğretici: Bir hizmet sözleşmesini uygulama</span><span class="sxs-lookup"><span data-stu-id="49f8f-121">Tutorial: Implement a service contract</span></span>](how-to-implement-a-wcf-contract.md)

    <span data-ttu-id="49f8f-122">Bir sözleşme tanımladıktan sonra bir hizmet sınıfı ile uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="49f8f-122">After you define a contract, you must implement it with a service class.</span></span>

- [<span data-ttu-id="49f8f-123">Öğretici: Temel hizmet barındırma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="49f8f-123">Tutorial: Host and run a basic service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)

    <span data-ttu-id="49f8f-124">Hizmet için bir uç noktasını yapılandırın ve hizmeti bir konsol uygulamasında barındırın.</span><span class="sxs-lookup"><span data-stu-id="49f8f-124">Configure an endpoint for the service and host the service in a console application.</span></span> <span data-ttu-id="49f8f-125">Bir hizmeti etkin duruma gelmesi bir çalışma zamanı ortamında ana ve yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="49f8f-125">For a service to become active, you must configure it and host it within a run-time environment.</span></span> <span data-ttu-id="49f8f-126">Bu çalışma zamanı ortamının hizmeti oluşturur ve yaşam süresi ve bağlam denetler.</span><span class="sxs-lookup"><span data-stu-id="49f8f-126">This run-time environment creates the service and controls its context and lifetime.</span></span>

<span data-ttu-id="49f8f-127">Sonraki iki öğreticiler açıklayan oluşturma, yapılandırma ve kullanım hizmeti işlemleri çağırmak için bir istemci uygulaması kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="49f8f-127">The next two tutorials describe how to create, configure, and use a client application to call the operations the service exposes.</span></span> <span data-ttu-id="49f8f-128">Hizmetleri, bir istemci uygulama hizmeti ile iletişim için gereken bilgileri tanımlayan meta verileri yayımlama.</span><span class="sxs-lookup"><span data-stu-id="49f8f-128">Services publish metadata that define the information a client application needs to communicate with the service.</span></span> <span data-ttu-id="49f8f-129">Visual Studio bu meta verilere erişme işlemini otomatikleştiren ve hizmeti için istemci uygulaması oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="49f8f-129">Visual Studio automates the process of accessing this metadata and uses it to construct the client application for the service.</span></span> <span data-ttu-id="49f8f-130">Visual Studio kullanmamaya karar verirseniz, kullanabileceğiniz [ServiceModel meta veri yardımcı programracı (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="49f8f-130">If you decide not to use Visual Studio, you can use the [ServiceModel Metadata Utility tool (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) instead.</span></span>

- [<span data-ttu-id="49f8f-131">Öğretici: Bir istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="49f8f-131">Tutorial: Create a client</span></span>](how-to-create-a-wcf-client.md)

    <span data-ttu-id="49f8f-132">Bir WCF hizmetinden WCF istemci proxy oluşturma için meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="49f8f-132">Retrieve metadata for creating a WCF client proxy from a WCF service.</span></span> <span data-ttu-id="49f8f-133">Bir hizmet başvurusu eklemek için Visual Studio kullanarak meta verilerini almak veya ServiceModel meta veri yardımcı programracı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49f8f-133">You retrieve metadata by using Visual Studio to add a service reference or you can use the ServiceModel Metadata Utility tool.</span></span> <span data-ttu-id="49f8f-134">İstemcinin hizmete erişmek için kullandığı uç noktası belirtin.</span><span class="sxs-lookup"><span data-stu-id="49f8f-134">You specify the endpoint that the client uses to access the service.</span></span>

- [<span data-ttu-id="49f8f-135">Öğretici: Bir istemci kullanın</span><span class="sxs-lookup"><span data-stu-id="49f8f-135">Tutorial: Use a client</span></span>](how-to-use-a-wcf-client.md)

    <span data-ttu-id="49f8f-136">WCF istemci proxy hizmet işlemlerini aramak üzere kullanın.</span><span class="sxs-lookup"><span data-stu-id="49f8f-136">Use the WCF client proxy to call the service operations.</span></span>

## <a name="reference"></a><span data-ttu-id="49f8f-137">Başvuru</span><span class="sxs-lookup"><span data-stu-id="49f8f-137">Reference</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a><span data-ttu-id="49f8f-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49f8f-138">See also</span></span>

- [<span data-ttu-id="49f8f-139">Kavramsal genel bakış</span><span class="sxs-lookup"><span data-stu-id="49f8f-139">Conceptual overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="49f8f-140">Belgeler için kılavuz</span><span class="sxs-lookup"><span data-stu-id="49f8f-140">Guide to the documentation</span></span>](guide-to-the-documentation.md)
- [<span data-ttu-id="49f8f-141">Windows Communication Foundation nedir</span><span class="sxs-lookup"><span data-stu-id="49f8f-141">What is Windows Communication Foundation</span></span>](whats-wcf.md)
- [<span data-ttu-id="49f8f-142">WCF özellik ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="49f8f-142">WCF feature details</span></span>](feature-details/index.md)
- [<span data-ttu-id="49f8f-143">Temel programlama yaşam döngüsü</span><span class="sxs-lookup"><span data-stu-id="49f8f-143">Basic programming lifecycle</span></span>](basic-programming-lifecycle.md)
- [<span data-ttu-id="49f8f-144">İstemci derleme</span><span class="sxs-lookup"><span data-stu-id="49f8f-144">Building clients</span></span>](building-clients.md)
- [<span data-ttu-id="49f8f-145">Temel WCF programlama</span><span class="sxs-lookup"><span data-stu-id="49f8f-145">Basic WCF programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="49f8f-146">Nasıl yapılır: Çift yönlü sözleşme oluşturma</span><span class="sxs-lookup"><span data-stu-id="49f8f-146">How to: Create a duplex contract</span></span>](feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="49f8f-147">Nasıl yapılır: Çift yönlü sözleşme ile hizmetlere erişim</span><span class="sxs-lookup"><span data-stu-id="49f8f-147">How to: Access services with a duplex contract</span></span>](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="49f8f-148">ServiceModel meta veri yardımcı programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="49f8f-148">ServiceModel Metadata Utility tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="49f8f-149">Nasıl yapılır: Meta veri belgelerini indirmek için svcutil.exe kullanma</span><span class="sxs-lookup"><span data-stu-id="49f8f-149">How to: Use Svcutil.exe to download metadata documents</span></span>](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [<span data-ttu-id="49f8f-150">Nasıl yapılır: Bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="49f8f-150">How to: Publish metadata for a service using a configuration file</span></span>](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="49f8f-151">Hizmetler ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="49f8f-151">Using bindings to configure services and clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="49f8f-152">Başlarken örneği</span><span class="sxs-lookup"><span data-stu-id="49f8f-152">Getting started sample</span></span>](samples/getting-started-sample.md)
- [<span data-ttu-id="49f8f-153">Windows Communication Foundation örnekleri</span><span class="sxs-lookup"><span data-stu-id="49f8f-153">Windows Communication Foundation samples</span></span>](samples/index.md)
- [<span data-ttu-id="49f8f-154">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="49f8f-154">Self-Host</span></span>](samples/self-host.md)


