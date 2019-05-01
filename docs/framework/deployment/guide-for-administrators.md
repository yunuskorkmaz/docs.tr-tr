---
title: Yöneticiler için .NET Framework Dağıtım Kılavuzu
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7157c1fc6084713a4a565d21beb20563b2135cd9
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807930"
---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="0b3a9-102">Yöneticiler için .NET Framework Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0b3a9-102">.NET Framework Deployment Guide for Administrators</span></span>

<span data-ttu-id="0b3a9-103">Bu makalede bir sistem yöneticisi nasıl dağıtacağınız açıklanmıştır [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve Microsoft System Center Configuration Manager'ı kullanarak bir ağ üzerindeki sistem gereksinimlerini.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-103">This step-by-step article describes how a system administrator can deploy the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and its system dependencies across a network by using Microsoft System Center Configuration Manager.</span></span> <span data-ttu-id="0b3a9-104">Bu makalede tüm istemci bilgisayarların .NET Framework için gerekli olan minimum sistem gereksinimlerini karşıladığı varsayılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-104">This article assumes that all target client computers meet the minimum requirements for the .NET Framework.</span></span> <span data-ttu-id="0b3a9-105">Yüklemeye yönelik yazılım ve donanım gereksinimleri listesi için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b3a9-105">For a list of the software and hardware requirements for installing the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], see [System Requirements](../../../docs/framework/get-started/system-requirements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0b3a9-106">Ancak bunlarla sınırlı olmaksızın bu dokümanda bahsedilen yazılımlar [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager ve Active Directory olduğunuz her lisans ve koşullarına tabidir.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-106">The software referenced in this document, including, without limitation, the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="0b3a9-107">Bu yönergeler, bu tür lisans koşullarını ve koşulları gözden geçirilmiş yazılımların sahipleri tarafından kabul edildiği varsaymaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-107">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="0b3a9-108">Bu yönergeler, bu tür lisans anlaşmalarının koşullarından feragat etmiş sayılmaz.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-108">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>
>
> <span data-ttu-id="0b3a9-109">.NET Framework desteği hakkında daha fazla bilgi için bkz: [Microsoft .NET Framework desteği yaşam döngüsü ilkesi](https://go.microsoft.com/fwlink/?LinkId=196607) Microsoft Support Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-109">For information about support for the .NET Framework, see [Microsoft .NET Framework Support Lifecycle Policy](https://go.microsoft.com/fwlink/?LinkId=196607) on the Microsoft Support website.</span></span>

<span data-ttu-id="0b3a9-110">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="0b3a9-110">This topic contains the following sections:</span></span>

- [<span data-ttu-id="0b3a9-111">Dağıtım işlemi</span><span class="sxs-lookup"><span data-stu-id="0b3a9-111">The deployment process</span></span>](#the_deployment_process)
- [<span data-ttu-id="0b3a9-112">.NET Framework'ü dağıtma</span><span class="sxs-lookup"><span data-stu-id="0b3a9-112">Deploying the .NET Framework</span></span>](#deploying_in_a_test_environment)
- [<span data-ttu-id="0b3a9-113">Koleksiyon oluşturma</span><span class="sxs-lookup"><span data-stu-id="0b3a9-113">Create a collection</span></span>](#creating_a_collection)
- [<span data-ttu-id="0b3a9-114">Bir paket ve program oluşturma</span><span class="sxs-lookup"><span data-stu-id="0b3a9-114">Create a package and program</span></span>](#creating_a_package)
- [<span data-ttu-id="0b3a9-115">Bir dağıtım noktası seçin</span><span class="sxs-lookup"><span data-stu-id="0b3a9-115">Select a distribution point</span></span>](#select_dist_point)
- [<span data-ttu-id="0b3a9-116">Paketi dağıtma</span><span class="sxs-lookup"><span data-stu-id="0b3a9-116">Deploy the package</span></span>](#deploying_package)
- [<span data-ttu-id="0b3a9-117">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0b3a9-117">Resources</span></span>](#resources)
- [<span data-ttu-id="0b3a9-118">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="0b3a9-118">Troubleshooting</span></span>](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a><span data-ttu-id="0b3a9-119">Dağıtım işlemi</span><span class="sxs-lookup"><span data-stu-id="0b3a9-119">The deployment process</span></span>

<span data-ttu-id="0b3a9-120">Yerinde destek altyapısı varsa, ağ üzerinden .NET Framework dağıtılabilir paketini bilgisayarlara dağıtmak için Sistem Merkezi 2012 Yapılandırma Yöneticisi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-120">When you have the supporting infrastructure in place, you use System Center 2012 Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="0b3a9-121">Altyapının oluşturulması, beş birincil alanın oluşturulmasını ve tanımlanmasını gerektirir: koleksiyonlar, yazılım için bir paket ve program, dağıtım noktaları ve dağıtımlar.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-121">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>

- <span data-ttu-id="0b3a9-122">**Koleksiyonları** kullanıcılar, kullanıcı grupları veya bilgisayarlar, .NET Framework dağıtıldığı gibi Configuration Manager kaynaklarına gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-122">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which the .NET Framework is deployed.</span></span> <span data-ttu-id="0b3a9-123">Daha fazla bilgi için [System Center Configuration Manager'da koleksiyonlara giriş](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) Yapılandırma Yöneticisi belge kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-123">For more information, see [Introduction to collections in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="0b3a9-124">**Paketler ve programlar** genellikle bir istemci bilgisayara yüklenecek yazılım uygulamalarını gösterir, ancak bunlar tek tek dosyaları, güncelleştirmeleri veya hatta ayrı ayrı komutları da içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-124">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="0b3a9-125">Daha fazla bilgi için [paketler ve programlar System Center Configuration Manager'da](https://docs.microsoft.com/sccm/apps/deploy-use/packages-and-programs) Yapılandırma Yöneticisi belge kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-125">For more information, see [Packages and programs in System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/deploy-use/packages-and-programs) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="0b3a9-126">**Dağıtım noktaları** Configuration Manager sitesi, yazılımın istemci bilgisayarlarda çalışması gereken dosyaları depolayan sistem rolleridir.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-126">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="0b3a9-127">Yapılandırma Yöneticisi istemcisi bir yazılım dağıtımı alıp işlediğinde, yazılımla ilişkili içeriği indirmek ve kurulum işlemini başlatmak için bir dağıtım noktasıyla temasa geçer.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-127">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="0b3a9-128">Daha fazla bilgi için [Configuration Manager'da içerik yönetimi için temel kavramlar](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) Yapılandırma Yöneticisi belge kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-128">For more information, see [Fundamental concepts for content management in Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="0b3a9-129">**Dağıtımları** belirtilen hedef koleksiyonun ilgili üyelerinden yazılım paketini yüklemek için isteyin.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-129">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b3a9-130">Bu konudaki yordamlar, bir paket ve program oluşturmak ve dağıtmak için normal ayarları içerir ve tüm olası ayarları kapsamayabilir.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-130">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="0b3a9-131">Diğer Configuration Manager dağıtım seçenekleri için bkz. [Yapılandırma Yöneticisi belge kitaplığı](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).</span><span class="sxs-lookup"><span data-stu-id="0b3a9-131">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).</span></span>

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a><span data-ttu-id="0b3a9-132">.NET Framework'ü dağıtma</span><span class="sxs-lookup"><span data-stu-id="0b3a9-132">Deploying the .NET Framework</span></span>

<span data-ttu-id="0b3a9-133">System Center 2012 Configuration Manager sessiz yüklemesini dağıtmak için kullanabileceğiniz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], burada kullanıcılar yükleme işlemiyle etkileşimde bulunmazlar.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-133">You can use System Center 2012 Configuration Manager to deploy a silent installation of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], where the users do not interact with the installation process.</span></span> <span data-ttu-id="0b3a9-134">Aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="0b3a9-134">Follow these steps:</span></span>

1. <span data-ttu-id="0b3a9-135">[Koleksiyon oluşturma](#creating_a_collection).</span><span class="sxs-lookup"><span data-stu-id="0b3a9-135">[Create a collection](#creating_a_collection).</span></span>

2. <span data-ttu-id="0b3a9-136">[Bir paket ve program için .NET Framework yeniden dağıtılabilir oluşturma](#creating_a_package).</span><span class="sxs-lookup"><span data-stu-id="0b3a9-136">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>

3. <span data-ttu-id="0b3a9-137">[Dağıtım noktası seçme](#select_dist_point).</span><span class="sxs-lookup"><span data-stu-id="0b3a9-137">[Select a distribution point](#select_dist_point).</span></span>

4. <span data-ttu-id="0b3a9-138">[Paketi dağıtma](#deploying_package).</span><span class="sxs-lookup"><span data-stu-id="0b3a9-138">[Deploy the package](#deploying_package).</span></span>

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a><span data-ttu-id="0b3a9-139">Koleksiyon oluşturma</span><span class="sxs-lookup"><span data-stu-id="0b3a9-139">Create a collection</span></span>

<span data-ttu-id="0b3a9-140">Bu adımda, paket ve program dağıtacağınız bilgisayarları seçersiniz ve onları bir aygıt koleksiyonunda gruplandırırsınız.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-140">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="0b3a9-141">Yapılandırma Yöneticisi'nde bir koleksiyon oluşturmak için, doğrudan üyelik kurallarını (koleksiyon üyelerini el ile belirtirsiniz) veya sorgu kurallarını (koleksiyon üyelerini sizin belirttiğiniz ölçütlere göre Yapılandırma Yöneticisi belirler) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-141">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="0b3a9-142">Sorgular ve doğrudan kurallar dahil, üyelik kuralları hakkında daha fazla bilgi için bkz. [System Center Configuration Manager'da koleksiyonlara giriş](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) Yapılandırma Yöneticisi belge kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-142">For more information about membership rules, including queries and direct rules, see [Introduction to collections in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager Documentation Library.</span></span>

<span data-ttu-id="0b3a9-143">Bir koleksiyon oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="0b3a9-143">To create a collection:</span></span>

1. <span data-ttu-id="0b3a9-144">Configuration Manager Konsolu'nda **varlıklar ve Uyumluluk**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-144">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>

2. <span data-ttu-id="0b3a9-145">İçinde **varlıklar ve Uyumluluk** çalışma alanı seçin **cihaz koleksiyonları**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-145">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>

3. <span data-ttu-id="0b3a9-146">Üzerinde **giriş** sekmesinde **Oluştur** Grup öğesini **cihaz Koleksiyonu Oluştur**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-146">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>

4. <span data-ttu-id="0b3a9-147">Üzerinde **genel** sayfasının **cihaz koleksiyonu Oluşturma Sihirbazı**, koleksiyon için bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-147">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>

5. <span data-ttu-id="0b3a9-148">Seçin **Gözat** bir sınırlama koleksiyonu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-148">Choose **Browse** to specify a limiting collection.</span></span>

6. <span data-ttu-id="0b3a9-149">Üzerinde **Üyelik kuralları** sayfasında **Kuralı Ekle**ve ardından **doğrudan kural** açmak için **doğrudan üyelik kuralı oluşturma Sihirbazı**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-149">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="0b3a9-150">Seçin **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-150">Choose **Next**.</span></span>

7. <span data-ttu-id="0b3a9-151">Üzerinde **kaynak Ara** sayfasında **kaynak sınıfı** listesinde **sistem kaynağı**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-151">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="0b3a9-152">İçinde **öznitelik adı** listesinde **adı**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-152">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="0b3a9-153">İçinde **değer** alanına `%`ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-153">In the **Value** field, enter `%`, and then choose **Next**.</span></span>

8. <span data-ttu-id="0b3a9-154">Üzerinde **kaynak** sayfasında, .NET Framework'ü dağıtmak istediğiniz her bilgisayar için onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-154">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="0b3a9-155">Seçin **sonraki**ve ardından Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-155">Choose **Next**, and then complete the wizard.</span></span>

9. <span data-ttu-id="0b3a9-156">Üzerinde **Üyelik kuralları** sayfasının **cihaz koleksiyonu Oluşturma Sihirbazı**, seçin **sonraki**ve ardından Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-156">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="0b3a9-157">.NET Framework yeniden dağıtılabilir paketi için paket ve program oluşturma</span><span class="sxs-lookup"><span data-stu-id="0b3a9-157">Create a package and program for the .NET Framework redistributable package</span></span>

<span data-ttu-id="0b3a9-158">Aşağıdaki adımlar, .NET Framework yeniden dağıtılabilir için el ile bir paket oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-158">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="0b3a9-159">Paket, .NET Framework'ün kurulumu için belirtilen parametreleri ve paketin hedef bilgisayarlara nereden dağıtılacağını içerir.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-159">The package contains the specified parameters for installing the .NET Framework and the location from where the package will be distributed to the target computers.</span></span>

<span data-ttu-id="0b3a9-160">Bir paket oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="0b3a9-160">To create a package:</span></span>

1. <span data-ttu-id="0b3a9-161">Configuration Manager Konsolu'nda **yazılım Kitaplığı**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-161">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="0b3a9-162">İçinde **yazılım Kitaplığı** çalışma alanında, genişletme **Uygulama Yönetimi**ve ardından **paketleri**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-162">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="0b3a9-163">Üzerinde **giriş** sekmesinde **Oluştur** Grup öğesini **Paket Oluştur**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-163">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>

4. <span data-ttu-id="0b3a9-164">Üzerinde **paket** sayfasının **paket ve Program Sihirbazı Oluştur**, aşağıdaki bilgileri girin:</span><span class="sxs-lookup"><span data-stu-id="0b3a9-164">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    - <span data-ttu-id="0b3a9-165">Adı: `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="0b3a9-165">Name: `.NET Framework 4.5`</span></span>

    - <span data-ttu-id="0b3a9-166">Üretici: `Microsoft`</span><span class="sxs-lookup"><span data-stu-id="0b3a9-166">Manufacturer: `Microsoft`</span></span>

    - <span data-ttu-id="0b3a9-167">Dil.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-167">Language.</span></span> `English (US)`

5. <span data-ttu-id="0b3a9-168">Seçin **bu paket kaynak dosyaları içerir**ve ardından **Gözat** yerel seçin veya ağ .NET Framework yükleme dosyalarını içeren klasörü.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-168">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="0b3a9-169">Klasör seçtiğinizde, seçin **Tamam**ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-169">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>

6. <span data-ttu-id="0b3a9-170">Üzerinde **Program türü** sayfasında sihirbazın seçin **standart Program**ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-170">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>

7. <span data-ttu-id="0b3a9-171">Üzerinde **Program** sayfasının **paket ve Program Sihirbazı Oluştur**, aşağıdaki bilgileri girin:</span><span class="sxs-lookup"><span data-stu-id="0b3a9-171">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    1. <span data-ttu-id="0b3a9-172">**Adı:** `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="0b3a9-172">**Name:** `.NET Framework 4.5`</span></span>

    2. <span data-ttu-id="0b3a9-173">**Komut satırı:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (komut satırı seçenekleri açıklanmıştır tabloda Bu adımlardan sonra)</span><span class="sxs-lookup"><span data-stu-id="0b3a9-173">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>

    3. <span data-ttu-id="0b3a9-174">**Çalıştırın:** Seçin **gizli**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-174">**Run:** Choose **Hidden**.</span></span>

    4. <span data-ttu-id="0b3a9-175">**Program çalışabilir:** Program, kullanıcının oturum açmış bağımsız olarak çalışabileceğini belirten seçeneği seçin.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-175">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>

8. <span data-ttu-id="0b3a9-176">Üzerinde **gereksinimleri** sayfasında **sonraki** varsayılan değerleri kabul edin ve ardından Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-176">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>

<span data-ttu-id="0b3a9-177">Aşağıdaki tablo, 7. adımda belirtilen komut satırı seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-177">The following table describes the command-line options specified in step 7.</span></span>

|<span data-ttu-id="0b3a9-178">Seçenek</span><span class="sxs-lookup"><span data-stu-id="0b3a9-178">Option</span></span>|<span data-ttu-id="0b3a9-179">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b3a9-179">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="0b3a9-180">**/q**</span><span class="sxs-lookup"><span data-stu-id="0b3a9-180">**/q**</span></span>|<span data-ttu-id="0b3a9-181">Sessiz modu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-181">Sets quiet mode.</span></span> <span data-ttu-id="0b3a9-182">Hiçbir kullanıcı girişine gerek yoktur ve hiçbir çıktı gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-182">No user input is required, and no output is shown.</span></span>|
|<span data-ttu-id="0b3a9-183">**/ norestart**</span><span class="sxs-lookup"><span data-stu-id="0b3a9-183">**/norestart**</span></span>|<span data-ttu-id="0b3a9-184">Kurulum programının otomatik olarak yeniden başlatılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-184">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="0b3a9-185">Bu seçeneği kullanırsanız, Yapılandırma Yöneticisi'nin bilgisayarı yeniden başlatmayı üstlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-185">If you use this option, Configuration Manager must handle the computer restart.</span></span>|
|<span data-ttu-id="0b3a9-186">**/chainingpackage** *PackageName*</span><span class="sxs-lookup"><span data-stu-id="0b3a9-186">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="0b3a9-187">Zincirlemeyi yapan paketin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-187">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="0b3a9-188">Bu bilgiler kaydolup kişilerin diğer yükleme oturum bilgileriyle birlikte raporlanır [Microsoft Müşteri Deneyimini Geliştirme Programı (CEIP)](https://go.microsoft.com/fwlink/p/?LinkId=248244).</span><span class="sxs-lookup"><span data-stu-id="0b3a9-188">This information is reported with other installation session information for those who have signed up for the [Microsoft Customer Experience Improvement Program (CEIP)](https://go.microsoft.com/fwlink/p/?LinkId=248244).</span></span> <span data-ttu-id="0b3a9-189">Paket adı boşluk içeriyorsa, sınırlayıcı olarak çift tırnak işareti kullanın. Örneğin: **/chainingpackage "Chaining Product"**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-189">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|

<span data-ttu-id="0b3a9-190">Bu adımlar, .NET Framework 4.5 adlı bir paket oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-190">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="0b3a9-191">Program, .NET Framework 4.5'in sessiz bir kurulumunu dağıtır.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-191">The program deploys a silent installation of the .NET Framework 4.5.</span></span> <span data-ttu-id="0b3a9-192">Sessiz yüklemede, kullanıcılar yükleme işlemiyle etkileşimde bulunmazlar ve zincirleme uygulama döndürülen kodu yakalamak ve yeniden işlemek zorundadır; bkz: [yükleme paketinden ilerleme bilgisi alma](https://go.microsoft.com/fwlink/?LinkId=179606).</span><span class="sxs-lookup"><span data-stu-id="0b3a9-192">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](https://go.microsoft.com/fwlink/?LinkId=179606).</span></span>

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a><span data-ttu-id="0b3a9-193">Dağıtım noktası seçme</span><span class="sxs-lookup"><span data-stu-id="0b3a9-193">Select a distribution point</span></span>

<span data-ttu-id="0b3a9-194">Paketi ve programı bir sunucudan istemci bilgisayarlara dağıtmak için, önce bir site sistemini dağıtım noktası olarak belirlemeniz ve sonra paketi dağıtım noktasına dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-194">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>

<span data-ttu-id="0b3a9-195">Bir önceki bölümde oluşturulan .NET Framework 4.5 paketi için bir dağıtım noktası seçmek üzere aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="0b3a9-195">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>

1. <span data-ttu-id="0b3a9-196">Configuration Manager Konsolu'nda **yazılım Kitaplığı**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-196">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="0b3a9-197">İçinde **yazılım Kitaplığı** çalışma alanında, genişletme **Uygulama Yönetimi**ve ardından **paketleri**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-197">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="0b3a9-198">Paketler listesinden, paketi seçin **.NET Framework 4.5** , önceki bölümde oluşturduğunuz.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-198">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>

4. <span data-ttu-id="0b3a9-199">Üzerinde **giriş** sekmesinde **dağıtım** Grup öğesini **içeriği Dağıt**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-199">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>

5. <span data-ttu-id="0b3a9-200">Üzerinde **genel** sekmesinde **içerik Dağıtma Sihirbazı**, seçin **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-200">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>

6. <span data-ttu-id="0b3a9-201">Üzerinde **içerik hedefi** sayfasında sihirbazın seçin **Ekle**ve ardından **dağıtım noktası**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-201">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>

7. <span data-ttu-id="0b3a9-202">İçinde **dağıtım noktaları Ekle** iletişim kutusunda, paket ve programı barındıracak ve ardından dağıtım noktaları seçin **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-202">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>

8. <span data-ttu-id="0b3a9-203">Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-203">Complete the wizard.</span></span>

<span data-ttu-id="0b3a9-204">Paket şimdi, .NET Framework 4.5'i sessizce dağıtmak gereksinim duyduğunuz tüm bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-204">The package now contains all the information you need to silently deploy the .NET Framework 4.5.</span></span> <span data-ttu-id="0b3a9-205">Paket ve programı dağıtmadan önce dağıtım noktasında yüklendiğini doğrulayın; "İçeriği izleme" bölümüne bakın [System Center Configuration Manager ile dağıttığınız içeriği izleme](https://docs.microsoft.com/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed) Yapılandırma Yöneticisi belge kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-205">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Monitor Content" section of [Monitor content you have distributed with System Center Configuration Manager](https://docs.microsoft.com/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed) in the Configuration Manager Documentation Library.</span></span>

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a><span data-ttu-id="0b3a9-206">Paketi dağıtma</span><span class="sxs-lookup"><span data-stu-id="0b3a9-206">Deploy the package</span></span>

<span data-ttu-id="0b3a9-207">.NET Framework 4.5 paketini ve programını dağıtmak için:</span><span class="sxs-lookup"><span data-stu-id="0b3a9-207">To deploy the .NET Framework 4.5 package and program:</span></span>

1. <span data-ttu-id="0b3a9-208">Configuration Manager Konsolu'nda **yazılım Kitaplığı**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-208">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="0b3a9-209">İçinde **yazılım Kitaplığı** çalışma alanında, genişletme **Uygulama Yönetimi**ve ardından **paketleri**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-209">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="0b3a9-210">Paketler listesinden, oluşturduğunuz adlı paketi seçin **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-210">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>

4. <span data-ttu-id="0b3a9-211">Üzerinde **giriş** sekmesinde **dağıtım** Grup öğesini **Dağıt**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-211">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>

5. <span data-ttu-id="0b3a9-212">Üzerinde **genel** sayfasının **yazılım dağıtma Sihirbazı**, seçin **Gözat**ve ardından daha önce oluşturduğunuz koleksiyonu seçin.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-212">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="0b3a9-213">Seçin **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-213">Choose **Next**.</span></span>

6. <span data-ttu-id="0b3a9-214">Üzerinde **içerik** sayfasında sihirbazın yazılımı dağıtmak istediğiniz noktanın görüntülendiğini ve ardından doğrulamak **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-214">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>

7. <span data-ttu-id="0b3a9-215">Üzerinde **dağıtım ayarları** Sayfası Sihirbazı'nın onaylayın **eylem** ayarlanır **yükleme**, ve **amaçlı** içinayarlanmış**Gerekli**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-215">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="0b3a9-216">Bu, yazılım paketinin hedeflenen bilgisayarlarda zorunlu bir yükleme olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-216">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="0b3a9-217">Seçin **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-217">Choose **Next**.</span></span>

8. <span data-ttu-id="0b3a9-218">Üzerinde **zamanlama** sayfasında sihirbazın yüklenmesi için .NET Framework'ü istediğinizde belirtin.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-218">On the **Scheduling** page of the wizard, specify when you want the .NET Framework to be installed.</span></span> <span data-ttu-id="0b3a9-219">Seçebileceğiniz **yeni** bir yükleme zamanı atamak ya da yazılım üzerinde veya kapattığında veya mümkün olan en kısa sürede kullanıcı oturum açtığında isteyin.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-219">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="0b3a9-220">Seçin **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-220">Choose **Next**.</span></span>

9. <span data-ttu-id="0b3a9-221">Üzerinde **kullanıcı deneyimi** sayfasında, varsayılan değerleri seçin kullanın ve **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-221">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>

    > [!WARNING]
    > <span data-ttu-id="0b3a9-222">Üretim ortamınızın, dağıtım çizelgesi için farklı seçimler olmasını gerektiren ilkeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-222">Your production environment might have policies that require different selections for the deployment schedule.</span></span> <span data-ttu-id="0b3a9-223">Bu seçenekler hakkında daha fazla bilgi için bkz: [reklam adı özellikleri: Zamanla sekmesinde](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).</span><span class="sxs-lookup"><span data-stu-id="0b3a9-223">For information about these options, see [Advertisement Name Properties: Schedule Tab](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).</span></span>

10. <span data-ttu-id="0b3a9-224">Üzerinde **dağıtım noktaları** sayfasında, varsayılan değerleri seçin kullanın ve **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-224">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>

11. <span data-ttu-id="0b3a9-225">Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-225">Complete the wizard.</span></span> <span data-ttu-id="0b3a9-226">Dağıtım ilerlemesini izleyebilirsiniz **dağıtımları** düğümünün **izleme** çalışma.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-226">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>

<span data-ttu-id="0b3a9-227">Şimdi paket hedeflenen koleksiyona dağıtılır ve .NET Framework 4.5'in sessiz yüklemesi başlar.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-227">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="0b3a9-228">.NET Framework 4.5 yükleme hatası kodları hakkında daha fazla bilgi için bkz: [dönüş kodları](#return_codes) bu konunun ilerleyen bölümlerinde.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-228">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>

<a name="resources"></a>

## <a name="resources"></a><span data-ttu-id="0b3a9-229">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0b3a9-229">Resources</span></span>

<span data-ttu-id="0b3a9-230">Dağıtımı test etmek için altyapısı hakkında daha fazla bilgi için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden dağıtılabilir paket, aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-230">For more information about the infrastructure for testing the deployment of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable package, see the following resources.</span></span>

<span data-ttu-id="0b3a9-231">**Active Directory, DNS, DHCP:**</span><span class="sxs-lookup"><span data-stu-id="0b3a9-231">**Active Directory, DNS, DHCP:**</span></span>

- [<span data-ttu-id="0b3a9-232">Active Directory etki alanı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="0b3a9-232">Active Directory Domain Services</span></span>](/windows/desktop/ad/active-directory-domain-services)

- [<span data-ttu-id="0b3a9-233">Domain Name System (DNS)</span><span class="sxs-lookup"><span data-stu-id="0b3a9-233">Domain Name System (DNS)</span></span>](/windows-server/networking/dns/dns-top)

- [<span data-ttu-id="0b3a9-234">Dinamik konak Yapılandırma Protokolü (DHCP)</span><span class="sxs-lookup"><span data-stu-id="0b3a9-234">Dynamic Host Configuration Protocol (DHCP)</span></span>](/windows-server/networking/technologies/dhcp/dhcp-top)

<span data-ttu-id="0b3a9-235">**SQL Server 2008:**</span><span class="sxs-lookup"><span data-stu-id="0b3a9-235">**SQL Server 2008:**</span></span>

- <span data-ttu-id="0b3a9-236">[SQL Server 2008 (SQL Server Video) yükleme](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="0b3a9-236">[Installing SQL Server 2008 (SQL Server Video)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span></span>

- [<span data-ttu-id="0b3a9-237">Veritabanı yöneticileri için SQL Server 2008 Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="0b3a9-237">SQL Server 2008 Security Overview for Database Administrators</span></span>](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

<span data-ttu-id="0b3a9-238">**System Center 2012 Configuration Manager (yönetim noktası, dağıtım noktası):**</span><span class="sxs-lookup"><span data-stu-id="0b3a9-238">**System Center 2012 Configuration Manager (Management Point, Distribution Point):**</span></span>

- [<span data-ttu-id="0b3a9-239">System Center 2012 Configuration Manager için Site Yönetimi</span><span class="sxs-lookup"><span data-stu-id="0b3a9-239">Site Administration for System Center 2012 Configuration Manager</span></span>](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)

- [<span data-ttu-id="0b3a9-240">Yapılandırma Yöneticisi tek Site planlama ve dağıtım</span><span class="sxs-lookup"><span data-stu-id="0b3a9-240">Configuration Manager Single Site Planning and Deployment</span></span>](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)

<span data-ttu-id="0b3a9-241">**Windows bilgisayarlar için System Center 2012 Configuration Manager istemcisi:**</span><span class="sxs-lookup"><span data-stu-id="0b3a9-241">**System Center 2012 Configuration Manager client for Windows computers:**</span></span>

- [<span data-ttu-id="0b3a9-242">System Center 2012 Configuration Manager için İstemci Dağıtma</span><span class="sxs-lookup"><span data-stu-id="0b3a9-242">Deploying Clients for System Center 2012 Configuration Manager</span></span>](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a><span data-ttu-id="0b3a9-243">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="0b3a9-243">Troubleshooting</span></span>

### <a name="log-file-locations"></a><span data-ttu-id="0b3a9-244">Günlük dosyası konumları</span><span class="sxs-lookup"><span data-stu-id="0b3a9-244">Log file locations</span></span>

<span data-ttu-id="0b3a9-245">Aşağıdaki günlük dosyalarını, .NET Framework Kurulum sırasında üretilir:</span><span class="sxs-lookup"><span data-stu-id="0b3a9-245">The following log files are generated during .NET Framework setup:</span></span>

- <span data-ttu-id="0b3a9-246">.NET framework %Temp%\Microsoft *sürüm*\*.txt</span><span class="sxs-lookup"><span data-stu-id="0b3a9-246">%temp%\Microsoft .NET Framework *version*\*.txt</span></span>
- <span data-ttu-id="0b3a9-247">.NET framework %Temp%\Microsoft *sürüm*\*.html</span><span class="sxs-lookup"><span data-stu-id="0b3a9-247">%temp%\Microsoft .NET Framework *version*\*.html</span></span>

<span data-ttu-id="0b3a9-248">Burada *sürüm* .NET Framework 4.5 veya 4.7.2 gibi güvenilirliğinden sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-248">where *version* is the version of the .NET Framework that you're installing, such as 4.5 or 4.7.2.</span></span>

<span data-ttu-id="0b3a9-249">İçin hangi günlük dosyaları yazılır kullanarak dizini belirtebilirsiniz `/log` komut satırı seçeneği, .NET Framework yükleme komutu.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-249">You can also specify the directory to which log files are written by using the `/log` command-line option in the .NET Framework installation command.</span></span> <span data-ttu-id="0b3a9-250">Daha fazla bilgi için [geliştiriciler için .NET Framework Dağıtım Kılavuzu](deployment-guide-for-developers.md#command-line-options).</span><span class="sxs-lookup"><span data-stu-id="0b3a9-250">For more information, see [.NET Framework deployment guide for developers](deployment-guide-for-developers.md#command-line-options).</span></span>

<span data-ttu-id="0b3a9-251">Kullanabileceğiniz [günlük toplama aracı](https://www.microsoft.com/download/details.aspx?id=12493) .NET Framework günlük dosyaları toplamak ve dosyaların boyutunu azaltır bir sıkıştırılmış kabin (.cab) dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-251">You can use the [log collection tool](https://www.microsoft.com/download/details.aspx?id=12493) to collect the .NET Framework log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>

<a name="return_codes"></a>

### <a name="return-codes"></a><span data-ttu-id="0b3a9-252">Dönüş kodları</span><span class="sxs-lookup"><span data-stu-id="0b3a9-252">Return codes</span></span>

<span data-ttu-id="0b3a9-253">Aşağıdaki tabloda en yaygın dönüş kodlarını listelemektedir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden dağıtılabilir yükleme programındaki.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-253">The following table lists the most common return codes from the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable installation program.</span></span> <span data-ttu-id="0b3a9-254">Dönüş kodları yükleyicinin tüm sürümleri için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-254">The return codes are the same for all versions of the installer.</span></span>

<span data-ttu-id="0b3a9-255">Ayrıntılı bilgilerin bağlantılarını görmek için bir sonraki bölüm [indirme hatası kodları](#additional_error_codes).</span><span class="sxs-lookup"><span data-stu-id="0b3a9-255">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>

|<span data-ttu-id="0b3a9-256">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="0b3a9-256">Return code</span></span>|<span data-ttu-id="0b3a9-257">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b3a9-257">Description</span></span>|
|-----------------|-----------------|
|<span data-ttu-id="0b3a9-258">0</span><span class="sxs-lookup"><span data-stu-id="0b3a9-258">0</span></span>|<span data-ttu-id="0b3a9-259">Yükleme başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-259">Installation completed successfully.</span></span>|
|<span data-ttu-id="0b3a9-260">1602</span><span class="sxs-lookup"><span data-stu-id="0b3a9-260">1602</span></span>|<span data-ttu-id="0b3a9-261">Kullanıcı yüklemeyi iptal etti.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-261">The user canceled installation.</span></span>|
|<span data-ttu-id="0b3a9-262">1603</span><span class="sxs-lookup"><span data-stu-id="0b3a9-262">1603</span></span>|<span data-ttu-id="0b3a9-263">Yükleme sırasında ciddi bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-263">A fatal error occurred during installation.</span></span>|
|<span data-ttu-id="0b3a9-264">1641</span><span class="sxs-lookup"><span data-stu-id="0b3a9-264">1641</span></span>|<span data-ttu-id="0b3a9-265">Yüklemenin tamamlanması için yeniden başlatma gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-265">A restart is required to complete the installation.</span></span> <span data-ttu-id="0b3a9-266">Bu ileti başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-266">This message indicates success.</span></span>|
|<span data-ttu-id="0b3a9-267">3010</span><span class="sxs-lookup"><span data-stu-id="0b3a9-267">3010</span></span>|<span data-ttu-id="0b3a9-268">Yüklemenin tamamlanması için yeniden başlatma gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-268">A restart is required to complete the installation.</span></span> <span data-ttu-id="0b3a9-269">Bu ileti başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-269">This message indicates success.</span></span>|
|<span data-ttu-id="0b3a9-270">5100</span><span class="sxs-lookup"><span data-stu-id="0b3a9-270">5100</span></span>|<span data-ttu-id="0b3a9-271">Kullanıcının bilgisayarı sistem gereksinimlerini karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-271">The user's computer does not meet system requirements.</span></span>|

<a name="additional_error_codes"></a>

### <a name="download-error-codes"></a><span data-ttu-id="0b3a9-272">İndirme hatası kodları</span><span class="sxs-lookup"><span data-stu-id="0b3a9-272">Download error codes</span></span>

- [<span data-ttu-id="0b3a9-273">Arka Plan Akıllı Aktarım Hizmeti (BITS) hata kodları</span><span class="sxs-lookup"><span data-stu-id="0b3a9-273">Background Intelligent Transfer Service (BITS) error codes</span></span>](/windows/desktop/Bits/bits-return-values)

- [<span data-ttu-id="0b3a9-274">URL adı hata kodları</span><span class="sxs-lookup"><span data-stu-id="0b3a9-274">URL moniker error codes</span></span>](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)

- [<span data-ttu-id="0b3a9-275">WinHttp hata kodları</span><span class="sxs-lookup"><span data-stu-id="0b3a9-275">WinHttp error codes</span></span>](/windows/desktop/WinHttp/error-messages)

<span data-ttu-id="0b3a9-276">Diğer hata kodları:</span><span class="sxs-lookup"><span data-stu-id="0b3a9-276">Other error codes:</span></span>

- [<span data-ttu-id="0b3a9-277">Windows Installer hata kodları</span><span class="sxs-lookup"><span data-stu-id="0b3a9-277">Windows Installer error codes</span></span>](/windows/desktop/msi/error-codes)

- <span data-ttu-id="0b3a9-278">[Windows Update Aracısı sonuç kodları](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="0b3a9-278">[Windows Update Agent result codes](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="0b3a9-279">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b3a9-279">See also</span></span>

- [<span data-ttu-id="0b3a9-280">Geliştiriciler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0b3a9-280">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [<span data-ttu-id="0b3a9-281">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="0b3a9-281">System Requirements</span></span>](../../../docs/framework/get-started/system-requirements.md)
