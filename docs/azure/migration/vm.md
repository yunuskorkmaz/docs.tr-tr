---
title: bir ASP.NET Web uygulamasını Azure VM'ye geçirme
description: Bir ASP.NET Web uygulamasını şirket içinden Azure Sanal Makinesi'ne nasıl geçirteceklerini öğrenin.
ms.topic: how-to
ms.date: 11/15/2017
ms.openlocfilehash: cc9477de92e6105762636ed3a2241949e69ac8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "82072125"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a><span data-ttu-id="bbb7a-103">bir ASP.NET Web uygulamasını Azure Sanal Makinesine geçirme</span><span class="sxs-lookup"><span data-stu-id="bbb7a-103">Migrate an ASP.NET Web application to an Azure Virtual Machine</span></span>

<span data-ttu-id="bbb7a-104">Bu belge, ASP.NET bir web uygulamasını şirket içinde bir Azure Sanal Makinesine nasıl geçirilene ilişkin genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-104">This document provides an overview of how to migrate an ASP.NET web application from on-premises to an Azure Virtual Machine.</span></span>

## <a name="quickstart"></a><span data-ttu-id="bbb7a-105">Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="bbb7a-105">Quickstart</span></span>

<span data-ttu-id="bbb7a-106">Sanal bir makine oluşturma yı ve uygulamanızı nasıl yayınlayacağınızı öğrenin: [Azure VM'de yayımlayın](https://tutorials.visualstudio.com/aspnet-vm/intro)</span><span class="sxs-lookup"><span data-stu-id="bbb7a-106">Learn how to create a virtual machine and publish your app to it: [Publish to an Azure VM](https://tutorials.visualstudio.com/aspnet-vm/intro)</span></span>

## <a name="get-started"></a><span data-ttu-id="bbb7a-107">Başlarken</span><span class="sxs-lookup"><span data-stu-id="bbb7a-107">Get Started</span></span>

<span data-ttu-id="bbb7a-108">Bu öğreticiler, sanal bir makine oluşturma (veya geçirme) adımlarını, web uygulamanızı bu makinede yayımlama adımlarını ve Azure'da uygulamanızı desteklemek için gerekli olabilecek diğer görevleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-108">These tutorials demonstrate the steps to create (or migrate) a virtual machine, publish your web application to it, and other tasks that may be required to support your application in Azure.</span></span>

- <span data-ttu-id="bbb7a-109">Aşağıdaki seçeneklerden birini kullanarak Azure'daki ASP.NET uygulamanız için sanal bir makine oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bbb7a-109">Create a virtual machine for your ASP.NET application in Azure using one of the following options:</span></span>
  - [<span data-ttu-id="bbb7a-110">ASP.NET Uygulamaları için yeni bir sanal makine oluşturun</span><span class="sxs-lookup"><span data-stu-id="bbb7a-110">Create a new virtual machine for ASP.NET Applications</span></span>](https://go.microsoft.com/fwlink/?linkid=863237)
  - [<span data-ttu-id="bbb7a-111">Mevcut bir şirket içi VMWare sanal makineyi geçirin</span><span class="sxs-lookup"><span data-stu-id="bbb7a-111">Migrate an existing on-premises VMWare virtual machine</span></span>](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware)
  - [<span data-ttu-id="bbb7a-112">Varolan bir şirket içi Hyper-V sanal makineyi geçirme</span><span class="sxs-lookup"><span data-stu-id="bbb7a-112">Migrate an existing on-premises Hyper-V virtual machine</span></span>](https://docs.microsoft.com/azure/migrate/tutorial-migrate-hyper-v)
- [<span data-ttu-id="bbb7a-113">Visual Studio'u kullanarak uygulamanızı yayımlayın</span><span class="sxs-lookup"><span data-stu-id="bbb7a-113">Publish your app using Visual Studio</span></span>](https://go.microsoft.com/fwlink/?linkid=863240)
- [<span data-ttu-id="bbb7a-114">Sanal Müşterileriniz için güvenli bir sanal ağ oluşturun</span><span class="sxs-lookup"><span data-stu-id="bbb7a-114">Create a secure virtual network for your VMs</span></span>](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [<span data-ttu-id="bbb7a-115">Uygulamanız için bir CI/CD ardışık</span><span class="sxs-lookup"><span data-stu-id="bbb7a-115">Create a CI/CD pipeline for your application</span></span>](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [<span data-ttu-id="bbb7a-116">Yüksek kullanılabilirlik ve ölçeklenebilirlik için VM ölçeğine geçme</span><span class="sxs-lookup"><span data-stu-id="bbb7a-116">Move to a VM scale set for high availability and scalability</span></span>](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a><span data-ttu-id="bbb7a-117">Dikkat edilmesi gerekenler</span><span class="sxs-lookup"><span data-stu-id="bbb7a-117">Considerations</span></span>

### <a name="benefits"></a><span data-ttu-id="bbb7a-118">Avantajlar</span><span class="sxs-lookup"><span data-stu-id="bbb7a-118">Benefits</span></span>

<span data-ttu-id="bbb7a-119">Sanal makineler, bir uygulamayı şirket içinde buluta geçirmek için en kolay yolu sunar.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-119">Virtual machines offer the easiest path to migrate an application from on-premises to the cloud.</span></span> <span data-ttu-id="bbb7a-120">Uygulamanızın şirket içinde kullandığı ortamı çoğaltmanızı sağlarken, kendi veri merkezlerinizi koruma gereksinimini de ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-120">They enable you to replicate the same environment your application uses on-premises, while removing the need to maintain your own data centers.</span></span> <span data-ttu-id="bbb7a-121">Sanal Makine Ölçek Setleri, Sanal Makinelerde çalışan uygulamalar için yüksek kullanılabilirlik ve ölçeklenebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-121">Virtual Machine Scale Sets provide high availability and scalability for applications running in Virtual Machines.</span></span>

### <a name="virtual-machine-size"></a><span data-ttu-id="bbb7a-122">Sanal Makine Boyutu</span><span class="sxs-lookup"><span data-stu-id="bbb7a-122">Virtual Machine Size</span></span>

<span data-ttu-id="bbb7a-123">İş yükünüz için en iyi şekilde optimize edilmiş sanal makine boyutunu ve türünü seçin.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-123">Choose the virtual machine size and type that is best optimized for your workload.</span></span> <span data-ttu-id="bbb7a-124">Daha fazla bilgi [için Azure'daki Windows sanal makineleri için Boyutlar'a](https://docs.microsoft.com/azure/virtual-machines/windows/sizes)bakın.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-124">For more information, see [Sizes for Windows virtual machines in Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes).</span></span>

### <a name="maintenance"></a><span data-ttu-id="bbb7a-125">Bakım</span><span class="sxs-lookup"><span data-stu-id="bbb7a-125">Maintenance</span></span>

<span data-ttu-id="bbb7a-126">Şirket içi bir makine gibi, sanal makineyi korumak ve<sup> güncellemekten&#42;. </sup></span><span class="sxs-lookup"><span data-stu-id="bbb7a-126">Just like an on-premises machine, you are responsible for maintaining and updating the virtual machine<sup>&#42;</sup>.</span></span> <span data-ttu-id="bbb7a-127">[Uygulamanız, Azure Uygulama Hizmeti](https://docs.microsoft.com/azure/app-service/) gibi bir Platform (PaaS) ortamında veya bir [kapsayıcıda](https://docs.microsoft.com/azure/app-service/containers/)çalıştırılabiliyorsa, bu gereksinimi ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-127">If your application can run in a Platform as a Service (PaaS) environment such as [Azure App Service](https://docs.microsoft.com/azure/app-service/) or in a [container](https://docs.microsoft.com/azure/app-service/containers/), that will remove this need.</span></span>

<span data-ttu-id="bbb7a-128">*<sup>sanal </sup>makine ölçek kümeleri için&#42;[Otomatik İşletim Sistemi yükseltmeleri](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) şu anda önizleme hizmeti olarak kullanılabilir.*</span><span class="sxs-lookup"><span data-stu-id="bbb7a-128">*<sup>&#42;</sup>[Automatic OS upgrades for virtual machine scale sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) is currently available as a Preview service.*</span></span>

### <a name="virtual-networks"></a><span data-ttu-id="bbb7a-129">Sanal Ağlar</span><span class="sxs-lookup"><span data-stu-id="bbb7a-129">Virtual Networks</span></span>

<span data-ttu-id="bbb7a-130">Azure Sanal Ağlar şunları yapmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="bbb7a-130">Azure Virtual Networks enable you to:</span></span>

- <span data-ttu-id="bbb7a-131">Kontrol ettiğiniz karma bir altyapı oluşturun</span><span class="sxs-lookup"><span data-stu-id="bbb7a-131">Build a hybrid infrastructure that you control</span></span>
- <span data-ttu-id="bbb7a-132">Kendi IP adreslerinizi ve DNS sunucularınızı getirin</span><span class="sxs-lookup"><span data-stu-id="bbb7a-132">Bring your own IP addresses and DNS servers</span></span>
- <span data-ttu-id="bbb7a-133">Uygulamalarınız için yalıtılmış ve son derece güvenli bir ortam oluşturun</span><span class="sxs-lookup"><span data-stu-id="bbb7a-133">Create an isolated and highly secure environment for your applications</span></span>
- <span data-ttu-id="bbb7a-134">Birkaç [bağlantı seçeneğinden](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti) birini kullanarak VM'nizi şirket içi ağınıza bağlayın</span><span class="sxs-lookup"><span data-stu-id="bbb7a-134">Connect your VM to your on-premises network using one of several [connectivity options](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span></span>
- <span data-ttu-id="bbb7a-135">[ExpressRoute'u](https://azure.microsoft.com/services/expressroute/) kullanarak sanal makinenizi şirket içi ağınıza entegre edin</span><span class="sxs-lookup"><span data-stu-id="bbb7a-135">Integrate your virtual machine into your on-premises network using [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span></span>

<span data-ttu-id="bbb7a-136">Başlamak için Sanal [Ağ belgelerine](https://docs.microsoft.com/azure/virtual-network/) bakın</span><span class="sxs-lookup"><span data-stu-id="bbb7a-136">To get started, see the [Virtual Network documentation](https://docs.microsoft.com/azure/virtual-network/)</span></span>

### <a name="active-directory"></a><span data-ttu-id="bbb7a-137">Active Directory</span><span class="sxs-lookup"><span data-stu-id="bbb7a-137">Active Directory</span></span>
<span data-ttu-id="bbb7a-138">Birçok uygulama kimlik doğrulama ve kimlik yönetimi için Active Directory kullanın.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-138">Many applications use Active Directory for authentication and identity management.</span></span>

- <span data-ttu-id="bbb7a-139">Azure AD Connect, şirket içi dizinlerinizi Azure Etkin Dizini ile tümleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-139">Azure AD Connect enables you to integrate your on-premises directories with Azure Active Directory.</span></span> <span data-ttu-id="bbb7a-140">Başlamak için bkz. [Şirket içi dizinlerinizi Azure Etkin Dizini ile tümleştirin.](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)</span><span class="sxs-lookup"><span data-stu-id="bbb7a-140">To get started, see [Integrate your on-premises directories with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).</span></span>
- <span data-ttu-id="bbb7a-141">Alternatif olarak, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) uygulamanızın şirket içi Active Directory'nize erişmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-141">Alternatively, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) enables your application to access your on-premises Active Directory.</span></span>

### <a name="sql-databases"></a><span data-ttu-id="bbb7a-142">SQL Veritabanları</span><span class="sxs-lookup"><span data-stu-id="bbb7a-142">SQL Databases</span></span>

<span data-ttu-id="bbb7a-143">Uygulamanız şirket içi bir veritabanı kullanıyorsa, uygulamanız varsayılan olarak uygulamayla konuşamaz.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-143">If your application is using an on-premises database, your app will not be able to talk to it by default.</span></span> <span data-ttu-id="bbb7a-144">Şunlardan birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bbb7a-144">You can either:</span></span>

- <span data-ttu-id="bbb7a-145">Uygulamanızın şirket içinde çalışan veritabanınıza erişmesini sağlayan karma bir ağ yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-145">Configure a hybrid network that enables your application to access your database running on-premises.</span></span>
- <span data-ttu-id="bbb7a-146">Veritabanınızı Azure'a geçirin.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-146">Migrate your database to the Azure.</span></span> <span data-ttu-id="bbb7a-147">Daha fazla bilgi için [bkz.](sql.md)</span><span class="sxs-lookup"><span data-stu-id="bbb7a-147">For more information, see [Migrate your SQL Server database to Azure](sql.md).</span></span>

### <a name="high-availability-and-scalability"></a><span data-ttu-id="bbb7a-148">Yüksek Kullanılabilirlik ve Ölçeklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="bbb7a-148">High Availability and Scalability</span></span>

#### <a name="virtual-machine-scale-sets"></a><span data-ttu-id="bbb7a-149">Sanal Makine Ölçek Kümeleri</span><span class="sxs-lookup"><span data-stu-id="bbb7a-149">Virtual Machine Scale Sets</span></span>
<span data-ttu-id="bbb7a-150">Uygulamanızın yüksek oranda kullanılabilir olduğundan emin olmak istersiniz ve uygulamanızın kullanılabilirliğini ve ölçeklenebilirliğini artırmak için VM görüntünüzü ölçeklendirebilir, Azure Sanal Makine Ölçeği Seti'ne geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-150">You want to make sure that your application is highly available and can scale, migrate your VM image to an Azure Virtual Machine Scale Set to improve the availability and scalability of your application.</span></span> <span data-ttu-id="bbb7a-151">VM Ölçek Setleri, uygulamanızla birlikte bir görüntü oluşturmak için önceden yapılandırdığınız veya bir yapı ardışık hattı oluşturduğunuz varolan vm'yi kullanma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-151">VM Scale Sets provide the ability to use an existing VM you've already configured or set up a build pipeline to build an image with your application.</span></span>

<span data-ttu-id="bbb7a-152">Başlamak için bkz: [Uygulamanızı sanal makine ölçeği kümelerinde dağıtın.](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)</span><span class="sxs-lookup"><span data-stu-id="bbb7a-152">To get started, see [Deploy your application on virtual machine scale sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span></span>

#### <a name="centralized-logging"></a><span data-ttu-id="bbb7a-153">Merkezi Ağaç Kesimi</span><span class="sxs-lookup"><span data-stu-id="bbb7a-153">Centralized Logging</span></span>
<span data-ttu-id="bbb7a-154">Uygulamanızı birden çok örnekte çalıştırırken, günlüklerinizi [Azure Depolama](https://docs.microsoft.com/azure/storage/)gibi merkezi bir konumda depolamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="bbb7a-154">When running your application across multiple instances, consider storing your logs in a centralized location such as [Azure Storage](https://docs.microsoft.com/azure/storage/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="bbb7a-155">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="bbb7a-155">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bbb7a-156">Azure’a SQL Server veritabanını geçirme</span><span class="sxs-lookup"><span data-stu-id="bbb7a-156">Migrate a SQL Server database to Azure</span></span>](sql.md)
