---
title: "Yöneticiler için .NET Framework Dağıtım Kılavuzu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
caps.latest.revision: "40"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3af5e301e57350b72ac0ea50448c7a46ca6c5387
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="a577e-102">Yöneticiler için .NET Framework Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a577e-102">.NET Framework Deployment Guide for Administrators</span></span>
<span data-ttu-id="a577e-103">Bu adım adım makalede bir sistem yöneticisi nasıl dağıtabileceğini açıklar [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve Microsoft System Center Configuration Manager kullanarak ağ üzerinden sistem bağımlılıklarını.</span><span class="sxs-lookup"><span data-stu-id="a577e-103">This step-by-step article describes how a system administrator can deploy the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and its system dependencies across a network by using Microsoft System Center Configuration Manager.</span></span> <span data-ttu-id="a577e-104">Bu makalede tüm istemci bilgisayarların .NET Framework için gerekli olan minimum sistem gereksinimlerini karşıladığı varsayılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a577e-104">This article assumes that all target client computers meet the minimum requirements for the .NET Framework.</span></span> <span data-ttu-id="a577e-105">Yüklemek için yazılım ve donanım gereksinimlerinin listesi için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a577e-105">For a list of the software and hardware requirements for installing the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], see [System Requirements](../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a577e-106">Bunlarla sınırlı olmamak kaydıyla dahil olmak üzere bu belgede başvurulan yazılım [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager ve Active Directory olan her lisans hüküm ve koşullara tabidir.</span><span class="sxs-lookup"><span data-stu-id="a577e-106">The software referenced in this document, including, without limitation, the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="a577e-107">Bu yönergeler, bu tür lisans koşullarını ve koşulları gözden geçirilmiş yazılımların sahipleri tarafından kabul edildiği varsaymaktadır.</span><span class="sxs-lookup"><span data-stu-id="a577e-107">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="a577e-108">Bu yönergeler, bu tür lisans anlaşmalarının koşullarından feragat etmiş sayılmaz.</span><span class="sxs-lookup"><span data-stu-id="a577e-108">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>  
>   
>  <span data-ttu-id="a577e-109">.NET Framework desteği hakkında daha fazla bilgi için bkz: [Microsoft .NET Framework destek yaşam döngüsü ilkesi](http://go.microsoft.com/fwlink/?LinkId=196607) Microsoft Support Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="a577e-109">For information about support for the .NET Framework, see [Microsoft .NET Framework Support Lifecycle Policy](http://go.microsoft.com/fwlink/?LinkId=196607) on the Microsoft Support website.</span></span>  
  
 <span data-ttu-id="a577e-110">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="a577e-110">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="a577e-111">Dağıtım işlemi</span><span class="sxs-lookup"><span data-stu-id="a577e-111">The deployment process</span></span>](#the_deployment_process)  
 [<span data-ttu-id="a577e-112">.NET Framework'ü dağıtma</span><span class="sxs-lookup"><span data-stu-id="a577e-112">Deploying the .NET Framework</span></span>](#deploying_in_a_test_environment)  
 [<span data-ttu-id="a577e-113">Bir koleksiyon oluşturma</span><span class="sxs-lookup"><span data-stu-id="a577e-113">Create a collection</span></span>](#creating_a_collection)  
 [<span data-ttu-id="a577e-114">Bir paket ve program oluşturma</span><span class="sxs-lookup"><span data-stu-id="a577e-114">Create a package and program</span></span>](#creating_a_package)  
 [<span data-ttu-id="a577e-115">Bir dağıtım noktası seçin</span><span class="sxs-lookup"><span data-stu-id="a577e-115">Select a distribution point</span></span>](#select_dist_point)  
 [<span data-ttu-id="a577e-116">Paketi dağıtma</span><span class="sxs-lookup"><span data-stu-id="a577e-116">Deploy the package</span></span>](#deploying_package)  
[<span data-ttu-id="a577e-117">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a577e-117">Resources</span></span>](#resources)  
[<span data-ttu-id="a577e-118">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="a577e-118">Troubleshooting</span></span>](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## <a name="the-deployment-process"></a><span data-ttu-id="a577e-119">Dağıtım işlemi</span><span class="sxs-lookup"><span data-stu-id="a577e-119">The deployment process</span></span>  
 <span data-ttu-id="a577e-120">Yerinde destek altyapısı varsa, ağ üzerinden .NET Framework dağıtılabilir paketini bilgisayarlara dağıtmak için Sistem Merkezi 2012 Yapılandırma Yöneticisi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="a577e-120">When you have the supporting infrastructure in place, you use System Center 2012 Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="a577e-121">Altyapının oluşturulması, beş birincil alanın oluşturulmasını ve tanımlanmasını gerektirir: koleksiyonlar, yazılım için bir paket ve program, dağıtım noktaları ve dağıtımlar.</span><span class="sxs-lookup"><span data-stu-id="a577e-121">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>  
  
-   <span data-ttu-id="a577e-122">**Koleksiyonları** kullanıcılar, kullanıcı grupları veya bilgisayarlar, .NET Framework dağıtıldığı gibi Configuration Manager kaynakları gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="a577e-122">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which the .NET Framework is deployed.</span></span> <span data-ttu-id="a577e-123">Daha fazla bilgi için bkz: [Configuration Manager'da koleksiyonlar](http://technet.microsoft.com/library/gg682169.aspx) Configuration Manager Belge Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="a577e-123">For more information, see [Collections in Configuration Manager](http://technet.microsoft.com/library/gg682169.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="a577e-124">**Paketler ve programlar** normalde bir istemci bilgisayarda yüklü yazılım uygulamaları temsil eder, ancak ayrıca tek dosyalar, güncelleştirmeleri veya hatta tek tek komutlar içerirler.</span><span class="sxs-lookup"><span data-stu-id="a577e-124">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="a577e-125">Daha fazla bilgi için bkz: [paketleri ve programları Configuration Manager'da](http://technet.microsoft.com/library/gg699369.aspx) Configuration Manager Belge Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="a577e-125">For more information, see [Packages and Programs in Configuration Manager](http://technet.microsoft.com/library/gg699369.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="a577e-126">**Dağıtım noktaları** Configuration Manager site yazılımın istemci bilgisayarlarında çalışması gereken dosyaları depolayan sistemi rolleridir.</span><span class="sxs-lookup"><span data-stu-id="a577e-126">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="a577e-127">Yapılandırma Yöneticisi istemcisi bir yazılım dağıtımı alıp işlediğinde, yazılımla ilişkili içeriği indirmek ve kurulum işlemini başlatmak için bir dağıtım noktasıyla temasa geçer.</span><span class="sxs-lookup"><span data-stu-id="a577e-127">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="a577e-128">Daha fazla bilgi için bkz: [Configuration Manager'da içerik yönetimi giriş](http://technet.microsoft.com/library/gg682083.aspx) Configuration Manager Belge Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="a577e-128">For more information, see [Introduction to content Management in Configuration Manager](http://technet.microsoft.com/library/gg682083.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="a577e-129">**Dağıtımları** yazılım paketi yüklemek için geçerli belirtilen hedef koleksiyonun üyeleri isteyin.</span><span class="sxs-lookup"><span data-stu-id="a577e-129">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span> <span data-ttu-id="a577e-130">Daha fazla bilgi için bkz: [Configuration Manager'da uygulamaları dağıtmak için nasıl](http://technet.microsoft.com/library/gg682082.aspx) Configuration Manager Belge Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="a577e-130">For more information, see [How to Deploy Applications in Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx) in the Configuration Manager documentation library.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a577e-131">Bu konudaki yordamlar, bir paket ve program oluşturmak ve dağıtmak için normal ayarları içerir ve tüm olası ayarları kapsamayabilir.</span><span class="sxs-lookup"><span data-stu-id="a577e-131">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="a577e-132">Diğer Configuration Manager dağıtım seçenekleri için bkz: [Configuration Manager belge kitaplığı](http://technet.microsoft.com/library/gg682041.aspx).</span><span class="sxs-lookup"><span data-stu-id="a577e-132">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](http://technet.microsoft.com/library/gg682041.aspx).</span></span>  
  
<a name="deploying_in_a_test_environment"></a>   
## <a name="deploying-the-net-framework"></a><span data-ttu-id="a577e-133">.NET Framework'ü dağıtma</span><span class="sxs-lookup"><span data-stu-id="a577e-133">Deploying the .NET Framework</span></span>  
 <span data-ttu-id="a577e-134">System Center 2012 Configuration Manager bir sessiz yüklemesi dağıtmak için kullanabileceğiniz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], burada kullanıcıların yükleme işlemi ile etkileşim değil.</span><span class="sxs-lookup"><span data-stu-id="a577e-134">You can use System Center 2012 Configuration Manager to deploy a silent installation of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], where the users do not interact with the installation process.</span></span> <span data-ttu-id="a577e-135">Aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="a577e-135">Follow these steps:</span></span>  
  
1.  <span data-ttu-id="a577e-136">[Bir koleksiyon oluşturma](#creating_a_collection).</span><span class="sxs-lookup"><span data-stu-id="a577e-136">[Create a collection](#creating_a_collection).</span></span>  
  
2.  <span data-ttu-id="a577e-137">[Bir paket ve program için .NET Framework yeniden dağıtılabilir oluşturmak](#creating_a_package).</span><span class="sxs-lookup"><span data-stu-id="a577e-137">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>  
  
3.  <span data-ttu-id="a577e-138">[Bir dağıtım noktası seçin](#select_dist_point).</span><span class="sxs-lookup"><span data-stu-id="a577e-138">[Select a distribution point](#select_dist_point).</span></span>  
  
4.  <span data-ttu-id="a577e-139">[Paketi dağıtmak](#deploying_package).</span><span class="sxs-lookup"><span data-stu-id="a577e-139">[Deploy the package](#deploying_package).</span></span>  
  
<a name="creating_a_collection"></a>   
### <a name="create-a-collection"></a><span data-ttu-id="a577e-140">Koleksiyon oluşturma</span><span class="sxs-lookup"><span data-stu-id="a577e-140">Create a collection</span></span>  
 <span data-ttu-id="a577e-141">Bu adımda, paket ve program dağıtacağınız bilgisayarları seçersiniz ve onları bir aygıt koleksiyonunda gruplandırırsınız.</span><span class="sxs-lookup"><span data-stu-id="a577e-141">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="a577e-142">Yapılandırma Yöneticisi'nde bir koleksiyon oluşturmak için, doğrudan üyelik kurallarını (koleksiyon üyelerini el ile belirtirsiniz) veya sorgu kurallarını (koleksiyon üyelerini sizin belirttiğiniz ölçütlere göre Yapılandırma Yöneticisi belirler) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a577e-142">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="a577e-143">Sorgular ve doğrudan kuralları da dahil olmak üzere, üyelik kuralları hakkında daha fazla bilgi için bkz: [Configuration Manager'da koleksiyonlara giriş](http://technet.microsoft.com/library/gg682177.aspx) Configuration Manager Belge Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="a577e-143">For more information about membership rules, including queries and direct rules, see [Introduction to Collections in Configuration Manager](http://technet.microsoft.com/library/gg682177.aspx) in the Configuration Manager Documentation Library.</span></span>  
  
 <span data-ttu-id="a577e-144">Bir koleksiyon oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="a577e-144">To create a collection:</span></span>  
  
1.  <span data-ttu-id="a577e-145">Configuration Manager konsolunda seçin **varlıklar ve uyum**.</span><span class="sxs-lookup"><span data-stu-id="a577e-145">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>  
  
2.  <span data-ttu-id="a577e-146">İçinde **varlıklar ve Uyumluluk** çalışma alanı seçin **cihaz koleksiyonları**.</span><span class="sxs-lookup"><span data-stu-id="a577e-146">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>  
  
3.  <span data-ttu-id="a577e-147">Üzerinde **giriş** sekmesinde **oluşturma** grubunda, seçin **cihaz Koleksiyonu Oluştur**.</span><span class="sxs-lookup"><span data-stu-id="a577e-147">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>  
  
4.  <span data-ttu-id="a577e-148">Üzerinde **genel** sayfasında **cihaz koleksiyonu Oluşturma Sihirbazı**, koleksiyon için bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="a577e-148">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>  
  
5.  <span data-ttu-id="a577e-149">Seçin **Gözat** bir sınırlama koleksiyonu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="a577e-149">Choose **Browse** to specify a limiting collection.</span></span>  
  
6.  <span data-ttu-id="a577e-150">Üzerinde **Üyelik kuralları** sayfasında, **Kuralı Ekle**ve ardından **doğrudan kural** açmak için **doğrudan üyelik kuralı oluşturma Sihirbazı**.</span><span class="sxs-lookup"><span data-stu-id="a577e-150">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="a577e-151">Seçin **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a577e-151">Choose **Next**.</span></span>  
  
7.  <span data-ttu-id="a577e-152">Üzerinde **kaynaklar için arama** sayfasında **kaynak sınıfı** listesinde, seçin **sistem kaynağı**.</span><span class="sxs-lookup"><span data-stu-id="a577e-152">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="a577e-153">İçinde **öznitelik adı** listesinde, seçin **adı**.</span><span class="sxs-lookup"><span data-stu-id="a577e-153">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="a577e-154">İçinde **değeri** alanına, `%`ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a577e-154">In the **Value** field, enter `%`, and then choose **Next**.</span></span>  
  
8.  <span data-ttu-id="a577e-155">Üzerinde **Kaynak Seç** sayfasında, .NET Framework dağıtmak istediğiniz her bilgisayar için onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="a577e-155">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="a577e-156">Seçin **sonraki**ve ardından Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="a577e-156">Choose **Next**, and then complete the wizard.</span></span>  
  
9. <span data-ttu-id="a577e-157">Üzerinde **Üyelik kuralları** sayfasında **cihaz koleksiyonu Oluşturma Sihirbazı**, seçin **sonraki**ve ardından Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="a577e-157">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>  
  
 <span data-ttu-id="a577e-158">Koleksiyonlar hakkında daha fazla bilgi için bkz: [Configuration Manager'da koleksiyonlar](http://technet.microsoft.com/library/bb693730.aspx) Configuration Manager Belge Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="a577e-158">For more information about collections, see [Collections in Configuration Manager](http://technet.microsoft.com/library/bb693730.aspx) in the Configuration Manager Documentation Library.</span></span>  
  
<a name="creating_a_package"></a>   
### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="a577e-159">.NET Framework yeniden dağıtılabilir paketi için paket ve program oluşturma</span><span class="sxs-lookup"><span data-stu-id="a577e-159">Create a package and program for the .NET Framework redistributable package</span></span>  
 <span data-ttu-id="a577e-160">Aşağıdaki adımlar, .NET Framework yeniden dağıtılabilir için el ile bir paket oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a577e-160">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="a577e-161">Paket, .NET Framework'ün kurulumu için belirtilen parametreleri ve paketin hedef bilgisayarlara nereden dağıtılacağını içerir.</span><span class="sxs-lookup"><span data-stu-id="a577e-161">The package contains the specified parameters for installing the .NET Framework and the location from where the package will be distributed to the target computers.</span></span>  
  
 <span data-ttu-id="a577e-162">Bir paket oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="a577e-162">To create a package:</span></span>  
  
1.  <span data-ttu-id="a577e-163">Configuration Manager konsolunda seçin **yazılım Kitaplığı**...</span><span class="sxs-lookup"><span data-stu-id="a577e-163">In the Configuration Manager console, choose **Software Library**..</span></span>  
  
2.  <span data-ttu-id="a577e-164">İçinde **yazılım Kitaplığı** çalışma alanında, genişletin **Uygulama Yönetimi**ve ardından **paketleri**.</span><span class="sxs-lookup"><span data-stu-id="a577e-164">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="a577e-165">Üzerinde **giriş** sekmesinde **oluşturma** grubunda, seçin **Paket Oluştur**.</span><span class="sxs-lookup"><span data-stu-id="a577e-165">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>  
  
4.  <span data-ttu-id="a577e-166">Üzerinde **paket** sayfasında **paket ve Program Sihirbazı Oluştur**, aşağıdaki bilgileri girin:</span><span class="sxs-lookup"><span data-stu-id="a577e-166">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>  
  
    -   <span data-ttu-id="a577e-167">Ad:`.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="a577e-167">Name: `.NET Framework 4.5`</span></span>  
  
    -   <span data-ttu-id="a577e-168">Üretici:`Microsoft`</span><span class="sxs-lookup"><span data-stu-id="a577e-168">Manufacturer: `Microsoft`</span></span>  
  
    -   <span data-ttu-id="a577e-169">Dil.</span><span class="sxs-lookup"><span data-stu-id="a577e-169">Language.</span></span> `English (US)`  
  
5.  <span data-ttu-id="a577e-170">Seçin **bu paket kaynak dosyalarını içeren**ve ardından **Gözat** yerel seçin veya ağ .NET Framework yükleme dosyalarını içeren klasörü.</span><span class="sxs-lookup"><span data-stu-id="a577e-170">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="a577e-171">Klasörü seçildiğinde seçin **Tamam**ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a577e-171">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>  
  
6.  <span data-ttu-id="a577e-172">Üzerinde **Program türü** sayfasında sihirbazın seçin **standart Program**ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a577e-172">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>  
  
7.  <span data-ttu-id="a577e-173">Üzerinde **Program** sayfasında **paket ve Program Sihirbazı Oluştur**, aşağıdaki bilgileri girin:</span><span class="sxs-lookup"><span data-stu-id="a577e-173">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>  
  
    1.  <span data-ttu-id="a577e-174">**Ad:**`.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="a577e-174">**Name:** `.NET Framework 4.5`</span></span>  
  
    2.  <span data-ttu-id="a577e-175">**Komut satırı:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (komut satırı seçenekleri açıklanmıştır tabloda sonra aşağıdaki adımları)</span><span class="sxs-lookup"><span data-stu-id="a577e-175">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>  
  
    3.  <span data-ttu-id="a577e-176">**Çalıştır:** seçin **gizli**.</span><span class="sxs-lookup"><span data-stu-id="a577e-176">**Run:** Choose **Hidden**.</span></span>  
  
    4.  <span data-ttu-id="a577e-177">**Program çalışabilir:** program kullanıcının oturum açmış bağımsız olarak çalışabilir belirten seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="a577e-177">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>  
  
8.  <span data-ttu-id="a577e-178">Üzerinde **gereksinimleri** sayfasında, **sonraki** varsayılan değerleri kabul edin ve ardından Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="a577e-178">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>  
  
 <span data-ttu-id="a577e-179">Aşağıdaki tablo, 7. adımda belirtilen komut satırı seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a577e-179">The following table describes the command-line options specified in step 7.</span></span>  
  
|<span data-ttu-id="a577e-180">Seçenek</span><span class="sxs-lookup"><span data-stu-id="a577e-180">Option</span></span>|<span data-ttu-id="a577e-181">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a577e-181">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a577e-182">**/q**</span><span class="sxs-lookup"><span data-stu-id="a577e-182">**/q**</span></span>|<span data-ttu-id="a577e-183">Sessiz modu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a577e-183">Sets quiet mode.</span></span> <span data-ttu-id="a577e-184">Hiçbir kullanıcı girişine gerek yoktur ve hiçbir çıktı gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="a577e-184">No user input is required, and no output is shown.</span></span>|  
|<span data-ttu-id="a577e-185">**/ norestart**</span><span class="sxs-lookup"><span data-stu-id="a577e-185">**/norestart**</span></span>|<span data-ttu-id="a577e-186">Kurulum programının otomatik olarak yeniden başlatılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="a577e-186">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="a577e-187">Bu seçeneği kullanırsanız, Yapılandırma Yöneticisi'nin bilgisayarı yeniden başlatmayı üstlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a577e-187">If you use this option, Configuration Manager must handle the computer restart.</span></span>|  
|<span data-ttu-id="a577e-188">**/chainingpackage** *PackageName*</span><span class="sxs-lookup"><span data-stu-id="a577e-188">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="a577e-189">Zincirlemeyi yapan paketin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a577e-189">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="a577e-190">Bu bilgiler kaydolup olanlar için diğer yükleme oturum bilgileri ile bildirilen [Microsoft Müşteri Deneyimi Geliştirme Programı (CEIP)](http://go.microsoft.com/fwlink/p/?LinkId=248244).</span><span class="sxs-lookup"><span data-stu-id="a577e-190">This information is reported with other installation session information for those who have signed up for the [Microsoft Customer Experience Improvement Program (CEIP)](http://go.microsoft.com/fwlink/p/?LinkId=248244).</span></span> <span data-ttu-id="a577e-191">Paket adı boşluk içeriyorsa, çift tırnak işaretleri sınırlayıcı olarak alın; Örneğin: **/chainingpackage "Ürün zincirleme"**.</span><span class="sxs-lookup"><span data-stu-id="a577e-191">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|  
  
 <span data-ttu-id="a577e-192">Bu adımlar, .NET Framework 4.5 adlı bir paket oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a577e-192">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="a577e-193">Program, .NET Framework 4.5'in sessiz bir kurulumunu dağıtır.</span><span class="sxs-lookup"><span data-stu-id="a577e-193">The program deploys a silent installation of the .NET Framework 4.5.</span></span> <span data-ttu-id="a577e-194">Sessiz yükleme, kullanıcıların yükleme işlemi ile etkileşim değil ve dönüş kodu yakalamak ve yeniden işlemek zincirleme uygulama vardır; bkz: [ilerleme durumu bilgileri alınırken bir yükleme paketi](http://go.microsoft.com/fwlink/?LinkId=179606).</span><span class="sxs-lookup"><span data-stu-id="a577e-194">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](http://go.microsoft.com/fwlink/?LinkId=179606).</span></span>  
 
<a name="select_dist_point"></a>   
### <a name="select-a-distribution-point"></a><span data-ttu-id="a577e-195">Dağıtım noktası seçme</span><span class="sxs-lookup"><span data-stu-id="a577e-195">Select a distribution point</span></span>  
 <span data-ttu-id="a577e-196">Paketi ve programı bir sunucudan istemci bilgisayarlara dağıtmak için, önce bir site sistemini dağıtım noktası olarak belirlemeniz ve sonra paketi dağıtım noktasına dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a577e-196">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>  
  
 <span data-ttu-id="a577e-197">Bir önceki bölümde oluşturulan .NET Framework 4.5 paketi için bir dağıtım noktası seçmek üzere aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="a577e-197">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>  
  
1.  <span data-ttu-id="a577e-198">Configuration Manager konsolunda seçin **yazılım Kitaplığı**.</span><span class="sxs-lookup"><span data-stu-id="a577e-198">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2.  <span data-ttu-id="a577e-199">İçinde **yazılım Kitaplığı** çalışma alanında, genişletin **Uygulama Yönetimi**ve ardından **paketleri**.</span><span class="sxs-lookup"><span data-stu-id="a577e-199">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="a577e-200">Paket paketler listesinden seçin **.NET Framework 4.5** önceki bölümde oluşturduğunuz.</span><span class="sxs-lookup"><span data-stu-id="a577e-200">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>  
  
4.  <span data-ttu-id="a577e-201">Üzerinde **giriş** sekmesinde **dağıtım** grubunda, seçin **içeriği Dağıt**.</span><span class="sxs-lookup"><span data-stu-id="a577e-201">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>  
  
5.  <span data-ttu-id="a577e-202">Üzerinde **genel** sekmesinde **içerik Dağıtma Sihirbazı**, seçin **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a577e-202">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>  
  
6.  <span data-ttu-id="a577e-203">Üzerinde **içerik hedef** sayfasında sihirbazın seçin **Ekle**ve ardından **dağıtım noktası**.</span><span class="sxs-lookup"><span data-stu-id="a577e-203">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>  
  
7.  <span data-ttu-id="a577e-204">İçinde **Ekle dağıtım noktaları** iletişim kutusunda, paket ve program barındırmak ve ardından seçin ve dağıtım noktalarının seçin **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="a577e-204">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>  
  
8.  <span data-ttu-id="a577e-205">Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="a577e-205">Complete the wizard.</span></span>  
  
 <span data-ttu-id="a577e-206">Packagenow .NET Framework 4.5 sessiz bir şekilde dağıtmak gereken tüm bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a577e-206">The packagenow contains all the information you need to silently deploy the .NET Framework 4.5.</span></span> <span data-ttu-id="a577e-207">Paket ve program dağıtmadan önce dağıtım noktasına yüklendiğini doğrulayın; "İzleme içerik" bölümüne bakın [Configuration Manager'da içerik yönetimine yönelik işlemler ve Bakım](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) Configuration Manager Belge Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="a577e-207">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Monitor Content" section of [Operations and Maintenance for Content Management in Configuration Manager](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) in the Configuration Manager Documentation Library.</span></span>  
  
<a name="deploying_package"></a>   
### <a name="deploy-the-package"></a><span data-ttu-id="a577e-208">Paketi dağıtma</span><span class="sxs-lookup"><span data-stu-id="a577e-208">Deploy the package</span></span>  
 <span data-ttu-id="a577e-209">.NET Framework 4.5 paketini ve programını dağıtmak için:</span><span class="sxs-lookup"><span data-stu-id="a577e-209">To deploy the .NET Framework 4.5 package and program:</span></span>  
  
1.  <span data-ttu-id="a577e-210">Configuration Manager konsolunda seçin **yazılım Kitaplığı**.</span><span class="sxs-lookup"><span data-stu-id="a577e-210">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2.  <span data-ttu-id="a577e-211">İçinde **yazılım Kitaplığı** çalışma alanında, genişletin **Uygulama Yönetimi**ve ardından **paketleri**.</span><span class="sxs-lookup"><span data-stu-id="a577e-211">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="a577e-212">Paketlerin adlandırılmış oluşturduğunuz paket listesinden **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="a577e-212">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>  
  
4.  <span data-ttu-id="a577e-213">Üzerinde **giriş** sekmesinde **dağıtım** grubunda, seçin **dağıtma**.</span><span class="sxs-lookup"><span data-stu-id="a577e-213">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>  
  
5.  <span data-ttu-id="a577e-214">Üzerinde **genel** sayfasında **yazılım dağıtma Sihirbazı**, seçin **Gözat**ve ardından daha önce oluşturduğunuz koleksiyonu seçin.</span><span class="sxs-lookup"><span data-stu-id="a577e-214">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="a577e-215">Seçin **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a577e-215">Choose **Next**.</span></span>  
  
6.  <span data-ttu-id="a577e-216">Üzerinde **içerik** sayfasında sihirbazın yazılım dağıtmak istediğiniz noktasını görüntülenir ve ardından doğrulamak **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a577e-216">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>  
  
7.  <span data-ttu-id="a577e-217">Üzerinde **dağıtım ayarlarını** Sayfa Sihirbazı'nın onaylayın **eylem** ayarlanır **yükleme**, ve **amacı** içinayarlanmış**Gerekli**.</span><span class="sxs-lookup"><span data-stu-id="a577e-217">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="a577e-218">Bu, yazılım paketinin hedeflenen bilgisayarlarda zorunlu bir yükleme olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a577e-218">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="a577e-219">Seçin **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a577e-219">Choose **Next**.</span></span>  
  
8.  <span data-ttu-id="a577e-220">Üzerinde **zamanlama** Sayfa Sihirbazı'nın yüklenmesi için .NET Framework'ü istediğinizde belirtin.</span><span class="sxs-lookup"><span data-stu-id="a577e-220">On the **Scheduling** page of the wizard, specify when you want the .NET Framework to be installed.</span></span> <span data-ttu-id="a577e-221">Seçebileceğiniz **yeni** yükleme süresini atama veya kullanıcı açık veya kapalı veya mümkün olan en kısa sürede açtığında yüklemek için yazılım isteyin.</span><span class="sxs-lookup"><span data-stu-id="a577e-221">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="a577e-222">Seçin **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a577e-222">Choose **Next**.</span></span>  
  
9. <span data-ttu-id="a577e-223">Üzerinde **kullanıcı deneyimini** sihirbazın varsayılan değerlerini ve seçin sayfasında **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a577e-223">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="a577e-224">Üretim ortamınızın, dağıtım çizelgesi için farklı seçimler olmasını gerektiren ilkeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="a577e-224">Your production environment might have policies that require different selections for the deployment schedule.</span></span> <span data-ttu-id="a577e-225">Bu seçenekler hakkında daha fazla bilgi için bkz: [tanıtım adı özellikleri: zamanlama sekmesi](http://technet.microsoft.com/library/bb694016.aspx) TechNet Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="a577e-225">For information about these options, see [Advertisement Name Properties: Schedule Tab](http://technet.microsoft.com/library/bb694016.aspx) in the TechNet Library.</span></span>  
  
10. <span data-ttu-id="a577e-226">Üzerinde **dağıtım noktaları** sihirbazın varsayılan değerlerini ve seçin sayfasında **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a577e-226">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>  
  
11. <span data-ttu-id="a577e-227">Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="a577e-227">Complete the wizard.</span></span> <span data-ttu-id="a577e-228">Dağıtımının ilerlemesini izleyebilirsiniz **dağıtımları** düğümünün **izleme** çalışma.</span><span class="sxs-lookup"><span data-stu-id="a577e-228">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>  
  
 <span data-ttu-id="a577e-229">Şimdi paket hedeflenen koleksiyona dağıtılır ve .NET Framework 4.5'in sessiz yüklemesi başlar.</span><span class="sxs-lookup"><span data-stu-id="a577e-229">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="a577e-230">.NET Framework 4.5 yüklemesi hata kodları hakkında daha fazla bilgi için bkz: [dönüş kodları](#return_codes) bu konunun ilerleyen bölümlerinde.</span><span class="sxs-lookup"><span data-stu-id="a577e-230">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>  
  
<a name="resources"></a>   
## <a name="resources"></a><span data-ttu-id="a577e-231">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a577e-231">Resources</span></span>  
 <span data-ttu-id="a577e-232">Dağıtımı test etmek için altyapı hakkında daha fazla bilgi için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden dağıtılabilir paketi, aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="a577e-232">For more information about the infrastructure for testing the deployment of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable package, see the following resources.</span></span>  
  
 <span data-ttu-id="a577e-233">**Active Directory, DNS, DHCP:**</span><span class="sxs-lookup"><span data-stu-id="a577e-233">**Active Directory, DNS, DHCP:**</span></span>  
  
-   [<span data-ttu-id="a577e-234">Windows Server 2008 için Active Directory etki alanı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="a577e-234">Active Directory Domain Services for Windows Server 2008</span></span>](http://technet.microsoft.com/library/dd378891.aspx)  
  
-   [<span data-ttu-id="a577e-235">DNS sunucusu</span><span class="sxs-lookup"><span data-stu-id="a577e-235">DNS Server</span></span>](http://technet.microsoft.com/library/cc732997.aspx)  
  
-   [<span data-ttu-id="a577e-236">DHCP sunucusu</span><span class="sxs-lookup"><span data-stu-id="a577e-236">DHCP Server</span></span>](http://technet.microsoft.com/library/cc896553.aspx)  
  
 <span data-ttu-id="a577e-237">**SQL Server 2008 için:**</span><span class="sxs-lookup"><span data-stu-id="a577e-237">**SQL Server 2008:**</span></span>  
  
-   [<span data-ttu-id="a577e-238">SQL Server 2008 (SQL Server Video) yükleme</span><span class="sxs-lookup"><span data-stu-id="a577e-238">Installing SQL Server 2008 (SQL Server Video)</span></span>](http://technet.microsoft.com/library/dd299415.aspx)  
  
-   [<span data-ttu-id="a577e-239">Veritabanı yöneticileri için SQL Server 2008 güvenlik genel bakış</span><span class="sxs-lookup"><span data-stu-id="a577e-239">SQL Server 2008 Security Overview for Database Administrators</span></span>](http://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 <span data-ttu-id="a577e-240">**System Center 2012 Configuration Manager (yönetim noktası, dağıtım noktası):**</span><span class="sxs-lookup"><span data-stu-id="a577e-240">**System Center 2012 Configuration Manager (Management Point, Distribution Point):**</span></span>  
  
-   [<span data-ttu-id="a577e-241">System Center 2012 Configuration Manager için Site Yönetimi</span><span class="sxs-lookup"><span data-stu-id="a577e-241">Site Administration for System Center 2012 Configuration Manager</span></span>](http://technet.microsoft.com/library/gg681983.aspx)  
  
-   [<span data-ttu-id="a577e-242">Configuration Manager tek sitesi planlama ve dağıtım</span><span class="sxs-lookup"><span data-stu-id="a577e-242">Configuration Manager Single Site Planning and Deployment</span></span>](http://technet.microsoft.com/library/bb680961.aspx)  
  
 <span data-ttu-id="a577e-243">**System Center 2012 Configuration Manager istemcisi Windows bilgisayarları için:**</span><span class="sxs-lookup"><span data-stu-id="a577e-243">**System Center 2012 Configuration Manager client for Windows computers:**</span></span>  
  
-   [<span data-ttu-id="a577e-244">System Center 2012 Configuration Manager için istemci dağıtma</span><span class="sxs-lookup"><span data-stu-id="a577e-244">Deploying Clients for System Center 2012 Configuration Manager</span></span>](http://technet.microsoft.com/library/gg699391.aspx)  
  
<a name="troubleshooting"></a>   
## <a name="troubleshooting"></a><span data-ttu-id="a577e-245">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="a577e-245">Troubleshooting</span></span>  
  
### <a name="log-file-locations"></a><span data-ttu-id="a577e-246">Günlük dosyası konumları</span><span class="sxs-lookup"><span data-stu-id="a577e-246">Log file locations</span></span>  
 <span data-ttu-id="a577e-247">Aşağıdaki günlük dosyalarına sırasında oluşturulan [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Kurulum:</span><span class="sxs-lookup"><span data-stu-id="a577e-247">The following log files are generated during [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup:</span></span>  
  
 <span data-ttu-id="a577e-248">%temp%\Microsoft .NET Framework 4.5*.txt</span><span class="sxs-lookup"><span data-stu-id="a577e-248">%temp%\Microsoft .NET Framework 4.5*.txt</span></span>  
 <span data-ttu-id="a577e-249">%Temp%\Microsoft .NET framework 4.5\*.html</span><span class="sxs-lookup"><span data-stu-id="a577e-249">%temp%\Microsoft .NET Framework 4.5\*.html</span></span>  
  
 <span data-ttu-id="a577e-250">Kullanabileceğiniz [günlük koleksiyonu aracı](http://www.microsoft.com/download/details.aspx?id=12493) toplamak için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] günlük dosyaları ve dosyaların boyutunu azaltır Sıkıştırılmış dolap (.cab) dosya oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="a577e-250">You can use the [log collection tool](http://www.microsoft.com/download/details.aspx?id=12493) to collect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>  
  
<a name="return_codes"></a>   
### <a name="return-codes"></a><span data-ttu-id="a577e-251">Dönüş kodları</span><span class="sxs-lookup"><span data-stu-id="a577e-251">Return codes</span></span>  
 <span data-ttu-id="a577e-252">Aşağıdaki tabloda en yaygın dönüş kodları [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden dağıtılabilir yükleme programı.</span><span class="sxs-lookup"><span data-stu-id="a577e-252">The following table lists the most common return codes from the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable installation program.</span></span> <span data-ttu-id="a577e-253">Dönüş kodları yükleyicinin tüm sürümleri için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a577e-253">The return codes are the same for all versions of the installer.</span></span>  
  
 <span data-ttu-id="a577e-254">Ayrıntılı bilgi için bağlantılar görmek için bir sonraki bölüm [karşıdan hata kodları](#additional_error_codes).</span><span class="sxs-lookup"><span data-stu-id="a577e-254">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>  
  
|<span data-ttu-id="a577e-255">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="a577e-255">Return code</span></span>|<span data-ttu-id="a577e-256">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a577e-256">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a577e-257">0</span><span class="sxs-lookup"><span data-stu-id="a577e-257">0</span></span>|<span data-ttu-id="a577e-258">Yükleme başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a577e-258">Installation completed successfully.</span></span>|  
|<span data-ttu-id="a577e-259">1602</span><span class="sxs-lookup"><span data-stu-id="a577e-259">1602</span></span>|<span data-ttu-id="a577e-260">Kullanıcı yüklemeyi iptal etti.</span><span class="sxs-lookup"><span data-stu-id="a577e-260">The user canceled installation.</span></span>|  
|<span data-ttu-id="a577e-261">1603</span><span class="sxs-lookup"><span data-stu-id="a577e-261">1603</span></span>|<span data-ttu-id="a577e-262">Yükleme sırasında ciddi bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a577e-262">A fatal error occurred during installation.</span></span>|  
|<span data-ttu-id="a577e-263">1641</span><span class="sxs-lookup"><span data-stu-id="a577e-263">1641</span></span>|<span data-ttu-id="a577e-264">Yüklemenin tamamlanması için yeniden başlatma gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a577e-264">A restart is required to complete the installation.</span></span> <span data-ttu-id="a577e-265">Bu ileti başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a577e-265">This message indicates success.</span></span>|  
|<span data-ttu-id="a577e-266">3010</span><span class="sxs-lookup"><span data-stu-id="a577e-266">3010</span></span>|<span data-ttu-id="a577e-267">Yüklemenin tamamlanması için yeniden başlatma gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a577e-267">A restart is required to complete the installation.</span></span> <span data-ttu-id="a577e-268">Bu ileti başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a577e-268">This message indicates success.</span></span>|  
|<span data-ttu-id="a577e-269">5100</span><span class="sxs-lookup"><span data-stu-id="a577e-269">5100</span></span>|<span data-ttu-id="a577e-270">Kullanıcının bilgisayarı sistem gereksinimlerini karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="a577e-270">The user's computer does not meet system requirements.</span></span>|  
  
<a name="additional_error_codes"></a>   
### <a name="download-error-codes"></a><span data-ttu-id="a577e-271">İndirme hatası kodları</span><span class="sxs-lookup"><span data-stu-id="a577e-271">Download error codes</span></span>  
  
-   [<span data-ttu-id="a577e-272">Arka Plan Akıllı Aktarım Hizmeti (BITS) hata kodları</span><span class="sxs-lookup"><span data-stu-id="a577e-272">Background Intelligent Transfer Service (BITS) error codes</span></span>](http://msdn.microsoft.com/library/aa362823.aspx)  
  
-   [<span data-ttu-id="a577e-273">URL ad hata kodları</span><span class="sxs-lookup"><span data-stu-id="a577e-273">URL moniker error codes</span></span>](http://msdn.microsoft.com/library/ms775145.aspx)  
  
-   [<span data-ttu-id="a577e-274">WinHttp hata kodları</span><span class="sxs-lookup"><span data-stu-id="a577e-274">WinHttp error codes</span></span>](http://msdn.microsoft.com/library/aa383770.aspx)  
  
 <span data-ttu-id="a577e-275">Diğer hata kodları:</span><span class="sxs-lookup"><span data-stu-id="a577e-275">Other error codes:</span></span>  
  
-   [<span data-ttu-id="a577e-276">Windows Installer hata kodları</span><span class="sxs-lookup"><span data-stu-id="a577e-276">Windows Installer error codes</span></span>](http://msdn.microsoft.com/library/aa368542.aspx)  
  
-   [<span data-ttu-id="a577e-277">Windows Update Aracısı sonuç kodları</span><span class="sxs-lookup"><span data-stu-id="a577e-277">Windows Update Agent result codes</span></span>](http://technet.microsoft.com/library/cc720442.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="a577e-278">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a577e-278">See Also</span></span>  
 [<span data-ttu-id="a577e-279">Geliştiriciler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a577e-279">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [<span data-ttu-id="a577e-280">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="a577e-280">System Requirements</span></span>](../../../docs/framework/get-started/system-requirements.md)
