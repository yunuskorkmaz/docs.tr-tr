---
title: Bir ASP.NET Web uygulamasını bir Azure VM 'ye geçirme
description: Şirket içinden bir ASP.NET Web uygulamasını bir Azure sanal makinesine geçirmeyi öğrenin.
ms.topic: how-to
ms.date: 06/20/2020
ms.openlocfilehash: 5ef340d020b72bebe46fe598fe68e7d02d0c0363
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174250"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a><span data-ttu-id="dc26e-103">Bir ASP.NET Web uygulamasını bir Azure sanal makinesine geçirme</span><span class="sxs-lookup"><span data-stu-id="dc26e-103">Migrate an ASP.NET Web application to an Azure Virtual Machine</span></span>

<span data-ttu-id="dc26e-104">Bu belgede, ASP.NET Web uygulamalarının Şirket içinden bir Azure sanal makinesine nasıl geçirileceğiyle ilgili bir genel bakış sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dc26e-104">This document provides an overview of how to migrate an ASP.NET web application from on-premises to an Azure Virtual Machine.</span></span>

## <a name="quickstart"></a><span data-ttu-id="dc26e-105">Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="dc26e-105">Quickstart</span></span>

<span data-ttu-id="dc26e-106">Bir sanal makine oluşturmayı ve uygulamanızı nasıl yayımlayacağınızı öğrenin: [bir Azure VM 'ye yayımlama](https://tutorials.visualstudio.com/aspnet-vm/intro)</span><span class="sxs-lookup"><span data-stu-id="dc26e-106">Learn how to create a virtual machine and publish your app to it: [Publish to an Azure VM](https://tutorials.visualstudio.com/aspnet-vm/intro)</span></span>

## <a name="get-started"></a><span data-ttu-id="dc26e-107">Başlarken</span><span class="sxs-lookup"><span data-stu-id="dc26e-107">Get Started</span></span>

<span data-ttu-id="dc26e-108">Bu öğreticiler, bir sanal makine oluşturma (veya geçirme), Web uygulamanızı bu uygulamada yayımlama ve Azure 'da uygulamanızı desteklemek için gerekebilecek diğer görevleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc26e-108">These tutorials demonstrate the steps to create (or migrate) a virtual machine, publish your web application to it, and other tasks that may be required to support your application in Azure.</span></span>

- <span data-ttu-id="dc26e-109">Aşağıdaki seçeneklerden birini kullanarak Azure 'da ASP.NET uygulamanız için bir sanal makine oluşturun:</span><span class="sxs-lookup"><span data-stu-id="dc26e-109">Create a virtual machine for your ASP.NET application in Azure using one of the following options:</span></span>
  - [<span data-ttu-id="dc26e-110">ASP.NET uygulamaları için yeni bir sanal makine oluşturma</span><span class="sxs-lookup"><span data-stu-id="dc26e-110">Create a new virtual machine for ASP.NET Applications</span></span>](https://go.microsoft.com/fwlink/?linkid=863237)
  - [<span data-ttu-id="dc26e-111">Mevcut bir şirket içi VMWare sanal makinesini geçirme</span><span class="sxs-lookup"><span data-stu-id="dc26e-111">Migrate an existing on-premises VMWare virtual machine</span></span>](/azure/migrate/tutorial-migrate-vmware)
  - [<span data-ttu-id="dc26e-112">Mevcut bir şirket içi Hyper-V sanal makinesini geçirme</span><span class="sxs-lookup"><span data-stu-id="dc26e-112">Migrate an existing on-premises Hyper-V virtual machine</span></span>](/azure/migrate/tutorial-migrate-hyper-v)
- [<span data-ttu-id="dc26e-113">Visual Studio 'Yu kullanarak uygulamanızı yayımlayın</span><span class="sxs-lookup"><span data-stu-id="dc26e-113">Publish your app using Visual Studio</span></span>](https://go.microsoft.com/fwlink/?linkid=863240)
- [<span data-ttu-id="dc26e-114">VM 'niz için güvenli bir sanal ağ oluşturma</span><span class="sxs-lookup"><span data-stu-id="dc26e-114">Create a secure virtual network for your VMs</span></span>](/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [<span data-ttu-id="dc26e-115">Uygulamanız için bir CI/CD işlem hattı oluşturun</span><span class="sxs-lookup"><span data-stu-id="dc26e-115">Create a CI/CD pipeline for your application</span></span>](/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [<span data-ttu-id="dc26e-116">Yüksek kullanılabilirlik ve ölçeklenebilirlik için bir VM Ölçek kümesine taşıma</span><span class="sxs-lookup"><span data-stu-id="dc26e-116">Move to a VM scale set for high availability and scalability</span></span>](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a><span data-ttu-id="dc26e-117">Dikkat edilmesi gerekenler</span><span class="sxs-lookup"><span data-stu-id="dc26e-117">Considerations</span></span>

### <a name="benefits"></a><span data-ttu-id="dc26e-118">Avantajlar</span><span class="sxs-lookup"><span data-stu-id="dc26e-118">Benefits</span></span>

<span data-ttu-id="dc26e-119">Sanal makineler, bir uygulamayı Şirket içinden buluta geçirmek için en kolay yolu sunar.</span><span class="sxs-lookup"><span data-stu-id="dc26e-119">Virtual machines offer the easiest path to migrate an application from on-premises to the cloud.</span></span> <span data-ttu-id="dc26e-120">Kendi veri merkezlerinizi koruma gereksinimini ortadan kaldırarak, uygulamanızın şirket içinde kullandığı ortamı çoğaltmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc26e-120">They enable you to replicate the same environment your application uses on-premises, while removing the need to maintain your own data centers.</span></span> <span data-ttu-id="dc26e-121">Sanal Makine Ölçek Kümeleri, sanal makinelerde çalışan uygulamalar için yüksek kullanılabilirlik ve ölçeklenebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc26e-121">Virtual Machine Scale Sets provide high availability and scalability for applications running in Virtual Machines.</span></span>

### <a name="virtual-machine-size"></a><span data-ttu-id="dc26e-122">Sanal makine boyutu</span><span class="sxs-lookup"><span data-stu-id="dc26e-122">Virtual Machine Size</span></span>

<span data-ttu-id="dc26e-123">İş yükünüz için en iyi duruma getirilmiş sanal makine boyutunu ve türünü seçin.</span><span class="sxs-lookup"><span data-stu-id="dc26e-123">Choose the virtual machine size and type that is best optimized for your workload.</span></span> <span data-ttu-id="dc26e-124">Daha fazla bilgi için bkz. [Azure 'Da Windows sanal makineleri Için boyutlar](/azure/virtual-machines/windows/sizes).</span><span class="sxs-lookup"><span data-stu-id="dc26e-124">For more information, see [Sizes for Windows virtual machines in Azure](/azure/virtual-machines/windows/sizes).</span></span>

### <a name="maintenance"></a><span data-ttu-id="dc26e-125">Bakım</span><span class="sxs-lookup"><span data-stu-id="dc26e-125">Maintenance</span></span>

<span data-ttu-id="dc26e-126">Tıpkı şirket içi bir makine gibi, sanal makine<sup>&#42;</sup>bakım ve güncelleştirme sorumluluğunuz de sorumludur.</span><span class="sxs-lookup"><span data-stu-id="dc26e-126">Just like an on-premises machine, you are responsible for maintaining and updating the virtual machine<sup>&#42;</sup>.</span></span> <span data-ttu-id="dc26e-127">Uygulamanız, [Azure App Service](/azure/app-service/) veya bir [kapsayıcıda](/azure/app-service/containers/)bir hizmet olarak platform (PaaS) ortamında (Bu gereksinimi ortadan kaldıracak) çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc26e-127">If your application can run in a Platform as a Service (PaaS) environment such as [Azure App Service](/azure/app-service/) or in a [container](/azure/app-service/containers/), that will remove this need.</span></span>

<span data-ttu-id="dc26e-128">*<sup> </sup> [Sanal makine ölçek kümeleri için otomatik işletim sistemi yükseltmeleri](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)&#42;Şu anda bir önizleme hizmeti olarak sunulmaktadır.*</span><span class="sxs-lookup"><span data-stu-id="dc26e-128">*<sup>&#42;</sup>[Automatic OS upgrades for virtual machine scale sets](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) is currently available as a Preview service.*</span></span>

### <a name="virtual-networks"></a><span data-ttu-id="dc26e-129">Sanal Ağlar</span><span class="sxs-lookup"><span data-stu-id="dc26e-129">Virtual Networks</span></span>

<span data-ttu-id="dc26e-130">Azure sanal ağları şunları sağlar:</span><span class="sxs-lookup"><span data-stu-id="dc26e-130">Azure Virtual Networks enable you to:</span></span>

- <span data-ttu-id="dc26e-131">Denetlediğiniz bir karma altyapı oluşturun</span><span class="sxs-lookup"><span data-stu-id="dc26e-131">Build a hybrid infrastructure that you control</span></span>
- <span data-ttu-id="dc26e-132">Kendi IP adreslerinizi ve DNS sunucularınızı getirin</span><span class="sxs-lookup"><span data-stu-id="dc26e-132">Bring your own IP addresses and DNS servers</span></span>
- <span data-ttu-id="dc26e-133">Uygulamalarınız için yalıtılmış ve yüksek oranda güvenli bir ortam oluşturun</span><span class="sxs-lookup"><span data-stu-id="dc26e-133">Create an isolated and highly secure environment for your applications</span></span>
- <span data-ttu-id="dc26e-134">Çeşitli [bağlantı seçeneklerinden](/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti) bırını kullanarak Sanal ağınızı şirket içi ağınıza bağlayın</span><span class="sxs-lookup"><span data-stu-id="dc26e-134">Connect your VM to your on-premises network using one of several [connectivity options](/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span></span>
- <span data-ttu-id="dc26e-135">[ExpressRoute](https://azure.microsoft.com/services/expressroute/) kullanarak sanal makinenizi şirket içi ağınızla tümleştirin</span><span class="sxs-lookup"><span data-stu-id="dc26e-135">Integrate your virtual machine into your on-premises network using [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span></span>

<span data-ttu-id="dc26e-136">Başlamak için bkz. [sanal ağ belgeleri](/azure/virtual-network/)</span><span class="sxs-lookup"><span data-stu-id="dc26e-136">To get started, see the [Virtual Network documentation](/azure/virtual-network/)</span></span>

### <a name="active-directory"></a><span data-ttu-id="dc26e-137">Active Directory</span><span class="sxs-lookup"><span data-stu-id="dc26e-137">Active Directory</span></span>
<span data-ttu-id="dc26e-138">Birçok uygulama kimlik doğrulama ve kimlik yönetimi için Active Directory kullanır.</span><span class="sxs-lookup"><span data-stu-id="dc26e-138">Many applications use Active Directory for authentication and identity management.</span></span>

- <span data-ttu-id="dc26e-139">Azure AD Connect, şirket içi dizinlerinizi Azure Active Directory tümleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc26e-139">Azure AD Connect enables you to integrate your on-premises directories with Azure Active Directory.</span></span> <span data-ttu-id="dc26e-140">Başlamak için bkz. Şirket [içi dizinlerinizi Azure Active Directory tümleştirme](/azure/active-directory/connect/active-directory-aadconnect).</span><span class="sxs-lookup"><span data-stu-id="dc26e-140">To get started, see [Integrate your on-premises directories with Azure Active Directory](/azure/active-directory/connect/active-directory-aadconnect).</span></span>
- <span data-ttu-id="dc26e-141">Alternatif olarak, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) , uygulamanızın şirket içi Active Directory erişmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc26e-141">Alternatively, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) enables your application to access your on-premises Active Directory.</span></span>

### <a name="sql-databases"></a><span data-ttu-id="dc26e-142">SQL Veritabanları</span><span class="sxs-lookup"><span data-stu-id="dc26e-142">SQL Databases</span></span>

<span data-ttu-id="dc26e-143">Uygulamanız şirket içi bir veritabanı kullanıyorsa, uygulamanız varsayılan olarak bu uygulamayla iletişim kuramayacak.</span><span class="sxs-lookup"><span data-stu-id="dc26e-143">If your application is using an on-premises database, your app will not be able to talk to it by default.</span></span> <span data-ttu-id="dc26e-144">Şunlardan birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dc26e-144">You can either:</span></span>

- <span data-ttu-id="dc26e-145">Uygulamanızın şirket içinde çalışan veritabanınıza erişmesini sağlayan bir karma ağ yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="dc26e-145">Configure a hybrid network that enables your application to access your database running on-premises.</span></span>
- <span data-ttu-id="dc26e-146">Veritabanınızı Azure 'a geçirin.</span><span class="sxs-lookup"><span data-stu-id="dc26e-146">Migrate your database to the Azure.</span></span> <span data-ttu-id="dc26e-147">Daha fazla bilgi için bkz. [SQL Server veritabanınızı Azure 'A geçirme](sql.md).</span><span class="sxs-lookup"><span data-stu-id="dc26e-147">For more information, see [Migrate your SQL Server database to Azure](sql.md).</span></span>

### <a name="high-availability-and-scalability"></a><span data-ttu-id="dc26e-148">Yüksek kullanılabilirlik ve ölçeklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="dc26e-148">High Availability and Scalability</span></span>

#### <a name="virtual-machine-scale-sets"></a><span data-ttu-id="dc26e-149">Sanal Makine Ölçek Kümeleri</span><span class="sxs-lookup"><span data-stu-id="dc26e-149">Virtual Machine Scale Sets</span></span>
<span data-ttu-id="dc26e-150">Uygulamanızın kullanılabilirliği ve ölçeklenebilirliğini artırmak için uygulamanızın yüksek oranda kullanılabilir olduğundan ve ölçekleyebilir olduğundan emin olmak istiyorsunuz, VM görüntünüzü bir Azure sanal makine ölçek kümesine geçirin.</span><span class="sxs-lookup"><span data-stu-id="dc26e-150">You want to make sure that your application is highly available and can scale, migrate your VM image to an Azure Virtual Machine Scale Set to improve the availability and scalability of your application.</span></span> <span data-ttu-id="dc26e-151">VM Ölçek Kümeleri, önceden yapılandırdığınız mevcut bir VM 'yi kullanma veya uygulamanızla bir görüntü oluşturmak için derleme işlem hattı ayarlama olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc26e-151">VM Scale Sets provide the ability to use an existing VM you've already configured or set up a build pipeline to build an image with your application.</span></span>

<span data-ttu-id="dc26e-152">Başlamak için bkz. [sanal makine ölçek kümelerinde uygulamanızı dağıtma](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span><span class="sxs-lookup"><span data-stu-id="dc26e-152">To get started, see [Deploy your application on virtual machine scale sets](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span></span>

#### <a name="centralized-logging"></a><span data-ttu-id="dc26e-153">Merkezi günlük kaydı</span><span class="sxs-lookup"><span data-stu-id="dc26e-153">Centralized Logging</span></span>
<span data-ttu-id="dc26e-154">Uygulamanızı birden çok örnek genelinde çalıştırırken günlüklerinizi [Azure depolama](/azure/storage/)gibi merkezi bir konumda depolamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="dc26e-154">When running your application across multiple instances, consider storing your logs in a centralized location such as [Azure Storage](/azure/storage/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="dc26e-155">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="dc26e-155">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc26e-156">Azure’a SQL Server veritabanını geçirme</span><span class="sxs-lookup"><span data-stu-id="dc26e-156">Migrate a SQL Server database to Azure</span></span>](sql.md)
