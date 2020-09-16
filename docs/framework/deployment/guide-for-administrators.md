---
title: Yöneticiler için .NET Framework Dağıtım Kılavuzu
description: Yöneticiler için .NET dağıtım kılavuzunu okuyun. .NET sürüm 4,5 ve sistem bağımlılıklarını bir ağ üzerinden dağıtmak için bu bilgileri kullanın.
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
ms.openlocfilehash: b358f0909147e52293fd802bc98caa31b284d7b1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558725"
---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="3fd2b-104">Yöneticiler için .NET Framework Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3fd2b-104">.NET Framework Deployment Guide for Administrators</span></span>

<span data-ttu-id="3fd2b-105">Bu adım adım makalede, bir sistem yöneticisinin Microsoft uç noktası Configuration Manager kullanarak bir ağ üzerinde .NET Framework 4,5 ve sistem bağımlılıklarını nasıl dağıtabileceğinizi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-105">This step-by-step article describes how a system administrator can deploy the .NET Framework 4.5 and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="3fd2b-106">Bu makalede tüm istemci bilgisayarların .NET Framework için gerekli olan minimum sistem gereksinimlerini karşıladığı varsayılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-106">This article assumes that all target client computers meet the minimum requirements for the .NET Framework.</span></span> <span data-ttu-id="3fd2b-107">4,5 .NET Framework yüklemeye yönelik yazılım ve donanım gereksinimlerinin bir listesi için bkz. [sistem gereksinimleri](../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fd2b-107">For a list of the software and hardware requirements for installing the .NET Framework 4.5, see [System Requirements](../get-started/system-requirements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3fd2b-108">Bu belgede başvurulan yazılım, sınırlama olmadan, .NET Framework 4,5, Configuration Manager ve Active Directory, her biri lisans hüküm ve koşullarına tabidir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-108">The software referenced in this document, including, without limitation, the .NET Framework 4.5, Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="3fd2b-109">Bu yönergeler, bu tür lisans koşullarını ve koşulları gözden geçirilmiş yazılımların sahipleri tarafından kabul edildiği varsaymaktadır.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-109">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="3fd2b-110">Bu yönergeler, bu tür lisans anlaşmalarının koşullarından feragat etmiş sayılmaz.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-110">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>
>
> <span data-ttu-id="3fd2b-111">.NET Framework için destek hakkında daha fazla bilgi için Microsoft Desteği Web sitesinde [.NET Framework resmi destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) ' ne bakın.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-111">For information about support for the .NET Framework, see [.NET Framework official support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) on the Microsoft Support website.</span></span>

<span data-ttu-id="3fd2b-112">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="3fd2b-112">This topic contains the following sections:</span></span>

- [<span data-ttu-id="3fd2b-113">Dağıtım işlemi</span><span class="sxs-lookup"><span data-stu-id="3fd2b-113">The deployment process</span></span>](#the_deployment_process)
- [<span data-ttu-id="3fd2b-114">.NET Framework'ü dağıtma</span><span class="sxs-lookup"><span data-stu-id="3fd2b-114">Deploying the .NET Framework</span></span>](#deploying_in_a_test_environment)
- [<span data-ttu-id="3fd2b-115">Koleksiyon oluşturma</span><span class="sxs-lookup"><span data-stu-id="3fd2b-115">Create a collection</span></span>](#creating_a_collection)
- [<span data-ttu-id="3fd2b-116">Paket ve program oluşturma</span><span class="sxs-lookup"><span data-stu-id="3fd2b-116">Create a package and program</span></span>](#creating_a_package)
- [<span data-ttu-id="3fd2b-117">Dağıtım noktası seçme</span><span class="sxs-lookup"><span data-stu-id="3fd2b-117">Select a distribution point</span></span>](#select_dist_point)
- [<span data-ttu-id="3fd2b-118">Paketi dağıtma</span><span class="sxs-lookup"><span data-stu-id="3fd2b-118">Deploy the package</span></span>](#deploying_package)
- [<span data-ttu-id="3fd2b-119">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3fd2b-119">Resources</span></span>](#resources)
- [<span data-ttu-id="3fd2b-120">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="3fd2b-120">Troubleshooting</span></span>](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a><span data-ttu-id="3fd2b-121">Dağıtım işlemi</span><span class="sxs-lookup"><span data-stu-id="3fd2b-121">The deployment process</span></span>

<span data-ttu-id="3fd2b-122">Destekleyici altyapıyı kullanıyorsanız, .NET Framework yeniden dağıtılabilir paketini ağdaki bilgisayarlara dağıtmak için Configuration Manager kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-122">When you have the supporting infrastructure in place, you use Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="3fd2b-123">Altyapının oluşturulması, beş birincil alanın oluşturulmasını ve tanımlanmasını gerektirir: koleksiyonlar, yazılım için bir paket ve program, dağıtım noktaları ve dağıtımlar.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-123">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>

- <span data-ttu-id="3fd2b-124">**Koleksiyonlar** , .NET Framework dağıtıldığı kullanıcılar, Kullanıcı grupları veya bilgisayarlar gibi Configuration Manager kaynak gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-124">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which the .NET Framework is deployed.</span></span> <span data-ttu-id="3fd2b-125">Daha fazla bilgi için, Configuration Manager belge kitaplığındaki [Configuration Manager koleksiyonlara giriş](/configmgr/core/clients/manage/collections/introduction-to-collections) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-125">For more information, see [Introduction to collections in Configuration Manager](/configmgr/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="3fd2b-126">**Paketler ve programlar** , genellikle bir istemci bilgisayara yüklenecek yazılım uygulamalarını temsil eder, ancak tek tek dosyalar, güncelleştirmeler ve hatta ayrı komutlar da içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-126">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="3fd2b-127">Daha fazla bilgi için Configuration Manager belge kitaplığındaki [Configuration Manager Içindeki paketler ve programlar](/configmgr/apps/deploy-use/packages-and-programs) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-127">For more information, see [Packages and programs in Configuration Manager](/configmgr/apps/deploy-use/packages-and-programs) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="3fd2b-128">**Dağıtım noktaları** , yazılımın istemci bilgisayarlarda çalışması için gereken dosyaları depolayan site sistem rolleridir Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-128">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="3fd2b-129">Yapılandırma Yöneticisi istemcisi bir yazılım dağıtımı alıp işlediğinde, yazılımla ilişkili içeriği indirmek ve kurulum işlemini başlatmak için bir dağıtım noktasıyla temasa geçer.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-129">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="3fd2b-130">Daha fazla bilgi için bkz. Configuration Manager belge kitaplığındaki [Configuration Manager içerik yönetimi Için temel kavramlar](/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) .</span><span class="sxs-lookup"><span data-stu-id="3fd2b-130">For more information, see [Fundamental concepts for content management in Configuration Manager](/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="3fd2b-131">**Dağıtımlar** , yazılım paketini yüklemek için belirtilen hedef koleksiyonun geçerli üyelerine yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-131">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3fd2b-132">Bu konudaki yordamlar, bir paket ve program oluşturmak ve dağıtmak için normal ayarları içerir ve tüm olası ayarları kapsamayabilir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-132">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="3fd2b-133">Diğer Configuration Manager dağıtım seçenekleri için, [Configuration Manager belge kitaplığı](/previous-versions/system-center/system-center-2012-R2/gg682041(v=technet.10))' na bakın.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-133">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](/previous-versions/system-center/system-center-2012-R2/gg682041(v=technet.10)).</span></span>

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a><span data-ttu-id="3fd2b-134">.NET Framework'ü dağıtma</span><span class="sxs-lookup"><span data-stu-id="3fd2b-134">Deploying the .NET Framework</span></span>

<span data-ttu-id="3fd2b-135">Configuration Manager, kullanıcıların yükleme işlemiyle etkileşimde bulunmayan .NET Framework 4,5 sessiz yüklemesini dağıtmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-135">You can use Configuration Manager to deploy a silent installation of the .NET Framework 4.5, where the users do not interact with the installation process.</span></span> <span data-ttu-id="3fd2b-136">Şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="3fd2b-136">Follow these steps:</span></span>

1. <span data-ttu-id="3fd2b-137">[Koleksiyon oluşturun](#creating_a_collection).</span><span class="sxs-lookup"><span data-stu-id="3fd2b-137">[Create a collection](#creating_a_collection).</span></span>

2. <span data-ttu-id="3fd2b-138">[Yeniden dağıtılabilir .NET Framework için bir paket ve program oluşturun](#creating_a_package).</span><span class="sxs-lookup"><span data-stu-id="3fd2b-138">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>

3. <span data-ttu-id="3fd2b-139">[Bir dağıtım noktası seçin](#select_dist_point).</span><span class="sxs-lookup"><span data-stu-id="3fd2b-139">[Select a distribution point](#select_dist_point).</span></span>

4. <span data-ttu-id="3fd2b-140">[Paketi dağıtın](#deploying_package).</span><span class="sxs-lookup"><span data-stu-id="3fd2b-140">[Deploy the package](#deploying_package).</span></span>

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a><span data-ttu-id="3fd2b-141">Koleksiyon oluşturma</span><span class="sxs-lookup"><span data-stu-id="3fd2b-141">Create a collection</span></span>

<span data-ttu-id="3fd2b-142">Bu adımda, paket ve program dağıtacağınız bilgisayarları seçersiniz ve onları bir aygıt koleksiyonunda gruplandırırsınız.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-142">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="3fd2b-143">Yapılandırma Yöneticisi'nde bir koleksiyon oluşturmak için, doğrudan üyelik kurallarını (koleksiyon üyelerini el ile belirtirsiniz) veya sorgu kurallarını (koleksiyon üyelerini sizin belirttiğiniz ölçütlere göre Yapılandırma Yöneticisi belirler) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-143">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="3fd2b-144">Sorgular ve doğrudan kurallar dahil Üyelik kuralları hakkında daha fazla bilgi için, Configuration Manager belge kitaplığındaki [Configuration Manager koleksiyonlara giriş](/configmgr/core/clients/manage/collections/introduction-to-collections) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-144">For more information about membership rules, including queries and direct rules, see [Introduction to collections in Configuration Manager](/configmgr/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager Documentation Library.</span></span>

<span data-ttu-id="3fd2b-145">Bir koleksiyon oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="3fd2b-145">To create a collection:</span></span>

1. <span data-ttu-id="3fd2b-146">Configuration Manager konsolunda, **varlıklar ve uyumluluk**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-146">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>

2. <span data-ttu-id="3fd2b-147">**Varlıklar ve uyum** çalışma alanında, **Cihaz Koleksiyonları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-147">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>

3. <span data-ttu-id="3fd2b-148">**Oluştur** grubunun **giriş** sekmesinde, **cihaz koleksiyonu oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-148">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>

4. <span data-ttu-id="3fd2b-149">**Cihaz koleksiyonu oluşturma Sihirbazı**' nın **genel** sayfasında, koleksiyon için bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-149">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>

5. <span data-ttu-id="3fd2b-150">Sınırlama koleksiyonu belirtmek için **Gözden** geçirme ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-150">Choose **Browse** to specify a limiting collection.</span></span>

6. <span data-ttu-id="3fd2b-151">**Üyelik kuralları** sayfasında **Kural Ekle**' yi ve ardından **doğrudan kural** ' ı seçerek **doğrudan üyelik kuralı oluşturma Sihirbazı**' nı açın.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-151">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="3fd2b-152">**İleri**’yi seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-152">Choose **Next**.</span></span>

7. <span data-ttu-id="3fd2b-153">Kaynak **Ara** sayfasında, **kaynak sınıfı** listesinde **sistem kaynağı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-153">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="3fd2b-154">**Öznitelik adı** listesinde **ad**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-154">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="3fd2b-155">**Değer** alanında, girin `%` ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-155">In the **Value** field, enter `%`, and then choose **Next**.</span></span>

8. <span data-ttu-id="3fd2b-156">**Kaynak Seç** sayfasında, .NET Framework dağıtmak istediğiniz her bilgisayar için onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-156">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="3fd2b-157">**İleri**' yi seçin ve ardından Sihirbazı doldurun.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-157">Choose **Next**, and then complete the wizard.</span></span>

9. <span data-ttu-id="3fd2b-158">**Cihaz koleksiyonu oluşturma Sihirbazı**' nın **Üyelik kuralları** sayfasında, **İleri**' yi seçin ve ardından Sihirbazı doldurun.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-158">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="3fd2b-159">.NET Framework yeniden dağıtılabilir paketi için paket ve program oluşturma</span><span class="sxs-lookup"><span data-stu-id="3fd2b-159">Create a package and program for the .NET Framework redistributable package</span></span>

<span data-ttu-id="3fd2b-160">Aşağıdaki adımlar, .NET Framework yeniden dağıtılabilir için el ile bir paket oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-160">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="3fd2b-161">Paket, .NET Framework'ün kurulumu için belirtilen parametreleri ve paketin hedef bilgisayarlara nereden dağıtılacağını içerir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-161">The package contains the specified parameters for installing the .NET Framework and the location from where the package will be distributed to the target computers.</span></span>

<span data-ttu-id="3fd2b-162">Bir paket oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="3fd2b-162">To create a package:</span></span>

1. <span data-ttu-id="3fd2b-163">Configuration Manager konsolunda **yazılım kitaplığı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-163">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="3fd2b-164">**Yazılım kitaplığı** çalışma alanında **uygulama yönetimi**' ni genişletin ve **paketler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-164">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="3fd2b-165">**Giriş** sekmesinde, **Oluştur** grubunda, **paket oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-165">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>

4. <span data-ttu-id="3fd2b-166">**Paket ve program oluşturma Sihirbazı**' nın **paket** sayfasında, aşağıdaki bilgileri girin:</span><span class="sxs-lookup"><span data-stu-id="3fd2b-166">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    - <span data-ttu-id="3fd2b-167">Ad: `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="3fd2b-167">Name: `.NET Framework 4.5`</span></span>

    - <span data-ttu-id="3fd2b-168">Üreticisini `Microsoft`</span><span class="sxs-lookup"><span data-stu-id="3fd2b-168">Manufacturer: `Microsoft`</span></span>

    - <span data-ttu-id="3fd2b-169">Dil.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-169">Language.</span></span> `English (US)`

5. <span data-ttu-id="3fd2b-170">**Bu paket kaynak dosyaları içerir**' i seçin ve ardından .NET Framework yükleme dosyalarını içeren yerel veya ağ klasörünü seçmek için **Araştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-170">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="3fd2b-171">Klasörü seçtikten sonra **Tamam**' ı seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-171">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>

6. <span data-ttu-id="3fd2b-172">Sihirbazın **program türü** sayfasında, **standart program**' ı seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-172">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>

7. <span data-ttu-id="3fd2b-173">**Paket ve program oluşturma Sihirbazı**' nın **Program** sayfasında, aşağıdaki bilgileri girin:</span><span class="sxs-lookup"><span data-stu-id="3fd2b-173">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    1. <span data-ttu-id="3fd2b-174">**Ad:**`.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="3fd2b-174">**Name:** `.NET Framework 4.5`</span></span>

    2. <span data-ttu-id="3fd2b-175">**Komut satırı:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (komut satırı seçenekleri, bu adımların ardından tabloda açıklanmıştır)</span><span class="sxs-lookup"><span data-stu-id="3fd2b-175">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>

    3. <span data-ttu-id="3fd2b-176">Şunu **Çalıştır:** **Gizli**öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-176">**Run:** Choose **Hidden**.</span></span>

    4. <span data-ttu-id="3fd2b-177">**Program çalışabilir:** Kullanıcının oturum açmış olmasından bağımsız olarak programın çalıştıracağınızı belirten seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-177">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>

8. <span data-ttu-id="3fd2b-178">**Gereksinimler** sayfasında, varsayılan değerleri kabul etmek için **İleri** ' yi seçin ve ardından Sihirbazı doldurun.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-178">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>

<span data-ttu-id="3fd2b-179">Aşağıdaki tablo, 7. adımda belirtilen komut satırı seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-179">The following table describes the command-line options specified in step 7.</span></span>

|<span data-ttu-id="3fd2b-180">Seçenek</span><span class="sxs-lookup"><span data-stu-id="3fd2b-180">Option</span></span>|<span data-ttu-id="3fd2b-181">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fd2b-181">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="3fd2b-182">**anahtarın**</span><span class="sxs-lookup"><span data-stu-id="3fd2b-182">**/q**</span></span>|<span data-ttu-id="3fd2b-183">Sessiz modu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-183">Sets quiet mode.</span></span> <span data-ttu-id="3fd2b-184">Hiçbir kullanıcı girişine gerek yoktur ve hiçbir çıktı gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-184">No user input is required, and no output is shown.</span></span>|
|<span data-ttu-id="3fd2b-185">**/norestart**</span><span class="sxs-lookup"><span data-stu-id="3fd2b-185">**/norestart**</span></span>|<span data-ttu-id="3fd2b-186">Kurulum programının otomatik olarak yeniden başlatılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-186">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="3fd2b-187">Bu seçeneği kullanırsanız, Yapılandırma Yöneticisi'nin bilgisayarı yeniden başlatmayı üstlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-187">If you use this option, Configuration Manager must handle the computer restart.</span></span>|
|<span data-ttu-id="3fd2b-188">**/ChainingPackage** *PackageName*</span><span class="sxs-lookup"><span data-stu-id="3fd2b-188">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="3fd2b-189">Zincirlemeyi yapan paketin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-189">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="3fd2b-190">Bu bilgiler, Microsoft Müşteri Deneyimini Geliştirme Programı (CEIP) için kaydolup diğer yükleme oturum bilgileriyle birlikte raporlanır.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-190">This information is reported with other installation session information for those who have signed up for the Microsoft Customer Experience Improvement Program (CEIP).</span></span> <span data-ttu-id="3fd2b-191">Paket adı boşluk içeriyorsa, çift tırnak işaretlerini sınırlayıcılar olarak kullanın; Örneğin: **/chainingpackage "zincirleme ürün"**.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-191">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|

<span data-ttu-id="3fd2b-192">Bu adımlar, .NET Framework 4.5 adlı bir paket oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-192">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="3fd2b-193">Program, .NET Framework 4.5'in sessiz bir kurulumunu dağıtır.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-193">The program deploys a silent installation of the .NET Framework 4.5.</span></span> <span data-ttu-id="3fd2b-194">Sessiz yüklemede, kullanıcılar yükleme işlemiyle etkileşime girmez ve zincirleme uygulama, dönüş kodunu yakalayıp yeniden başlatmayı işleymelidir; bkz. [bir yükleme paketinden Ilerleme bilgileri alma](/previous-versions/cc825975(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3fd2b-194">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](/previous-versions/cc825975(v=vs.100)).</span></span>

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a><span data-ttu-id="3fd2b-195">Dağıtım noktası seçme</span><span class="sxs-lookup"><span data-stu-id="3fd2b-195">Select a distribution point</span></span>

<span data-ttu-id="3fd2b-196">Paketi ve programı bir sunucudan istemci bilgisayarlara dağıtmak için, önce bir site sistemini dağıtım noktası olarak belirlemeniz ve sonra paketi dağıtım noktasına dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-196">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>

<span data-ttu-id="3fd2b-197">Bir önceki bölümde oluşturulan .NET Framework 4.5 paketi için bir dağıtım noktası seçmek üzere aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="3fd2b-197">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>

1. <span data-ttu-id="3fd2b-198">Configuration Manager konsolunda **yazılım kitaplığı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-198">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="3fd2b-199">**Yazılım kitaplığı** çalışma alanında **uygulama yönetimi**' ni genişletin ve **paketler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-199">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="3fd2b-200">Paket listesinden, önceki bölümde oluşturduğunuz **4,5 .NET Framework** paketini seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-200">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>

4. <span data-ttu-id="3fd2b-201">**Giriş** sekmesinde, **dağıtım** grubunda, **içeriği dağıt**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-201">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>

5. <span data-ttu-id="3fd2b-202">**Içerik Dağıtma Sihirbazı**' nın **genel** sekmesinde, **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-202">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>

6. <span data-ttu-id="3fd2b-203">Sihirbazın **Içerik hedefi** sayfasında **Ekle**' yi ve ardından **dağıtım noktası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-203">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>

7. <span data-ttu-id="3fd2b-204">**Dağıtım noktaları Ekle** iletişim kutusunda, paketi ve programı barındıracak dağıtım noktalarını seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-204">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>

8. <span data-ttu-id="3fd2b-205">Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-205">Complete the wizard.</span></span>

<span data-ttu-id="3fd2b-206">Paket şimdi, .NET Framework 4.5'i sessizce dağıtmak gereksinim duyduğunuz tüm bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-206">The package now contains all the information you need to silently deploy the .NET Framework 4.5.</span></span> <span data-ttu-id="3fd2b-207">Paketi ve programı dağıtmadan önce, dağıtım noktasında yüklü olduğunu doğrulayın; Configuration Manager belge kitaplığındaki [Configuration Manager ile dağıttığınız Içeriği izlemek](/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) Için "içerik durumu izleme" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-207">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Content status monitoring" section of [Monitor content you distribute with Configuration Manager](/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) in the Configuration Manager Documentation Library.</span></span>

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a><span data-ttu-id="3fd2b-208">Paketi dağıtma</span><span class="sxs-lookup"><span data-stu-id="3fd2b-208">Deploy the package</span></span>

<span data-ttu-id="3fd2b-209">.NET Framework 4.5 paketini ve programını dağıtmak için:</span><span class="sxs-lookup"><span data-stu-id="3fd2b-209">To deploy the .NET Framework 4.5 package and program:</span></span>

1. <span data-ttu-id="3fd2b-210">Configuration Manager konsolunda **yazılım kitaplığı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-210">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="3fd2b-211">**Yazılım kitaplığı** çalışma alanında **uygulama yönetimi**' ni genişletin ve **paketler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-211">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="3fd2b-212">Paket listesinden **.NET Framework 4,5**adlı oluşturduğunuz paketi seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-212">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>

4. <span data-ttu-id="3fd2b-213">**Giriş** sekmesinde, **dağıtım** grubunda, **Dağıt**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-213">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>

5. <span data-ttu-id="3fd2b-214">**Yazılım Dağıtma Sihirbazı**'nın **genel** sayfasında, **Araştır**' ı seçin ve daha önce oluşturduğunuz koleksiyonu seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-214">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="3fd2b-215">**İleri**’yi seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-215">Choose **Next**.</span></span>

6. <span data-ttu-id="3fd2b-216">Sihirbazın **içerik** sayfasında, yazılımı dağıtmak istediğiniz noktanın görüntülendiğini doğrulayın ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-216">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>

7. <span data-ttu-id="3fd2b-217">Sihirbazın **dağıtım ayarları** sayfasında, **eylemin** **yüklenmek**üzere ayarlandığını ve **amacın** **gerekli**olarak ayarlandığını onaylayın.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-217">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="3fd2b-218">Bu, yazılım paketinin hedeflenen bilgisayarlarda zorunlu bir yükleme olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-218">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="3fd2b-219">**İleri**’yi seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-219">Choose **Next**.</span></span>

8. <span data-ttu-id="3fd2b-220">Sihirbazın **zamanlama** sayfasında, .NET Framework yüklenmesini istediğiniz tarihi belirtin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-220">On the **Scheduling** page of the wizard, specify when you want the .NET Framework to be installed.</span></span> <span data-ttu-id="3fd2b-221">Bir yükleme süresi atamak için **Yeni** ' yi seçebilir veya yazılımın kullanıcı oturum açtığında ya da kapalıyken veya mümkün olan en kısa sürede yüklenmesine izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-221">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="3fd2b-222">**İleri**’yi seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-222">Choose **Next**.</span></span>

9. <span data-ttu-id="3fd2b-223">Sihirbazın **Kullanıcı deneyimi** sayfasında varsayılan değerleri kullanın ve **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-223">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>

    > [!WARNING]
    > <span data-ttu-id="3fd2b-224">Üretim ortamınızın, dağıtım çizelgesi için farklı seçimler olmasını gerektiren ilkeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-224">Your production environment might have policies that require different selections for the deployment schedule.</span></span> <span data-ttu-id="3fd2b-225">Bu seçenekler hakkında daha fazla bilgi için bkz. [tanıtım adı özellikleri: Zamanlama sekmesi](/previous-versions/system-center/configuration-manager-2007/bb694016(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="3fd2b-225">For information about these options, see [Advertisement Name Properties: Schedule Tab](/previous-versions/system-center/configuration-manager-2007/bb694016(v=technet.10)).</span></span>

10. <span data-ttu-id="3fd2b-226">Sihirbazın **dağıtım noktaları** sayfasında, varsayılan değerleri kullanın ve **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-226">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>

11. <span data-ttu-id="3fd2b-227">Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-227">Complete the wizard.</span></span> <span data-ttu-id="3fd2b-228">Dağıtım ilerlemesini **izleme** çalışma alanının **dağıtımlar** düğümünde izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-228">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>

<span data-ttu-id="3fd2b-229">Şimdi paket hedeflenen koleksiyona dağıtılır ve .NET Framework 4.5'in sessiz yüklemesi başlar.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-229">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="3fd2b-230">.NET Framework 4,5 yükleme hata kodları hakkında daha fazla bilgi için bu konunun devamındaki [Return Codes](#return_codes) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-230">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>

<a name="resources"></a>

## <a name="resources"></a><span data-ttu-id="3fd2b-231">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3fd2b-231">Resources</span></span>

<span data-ttu-id="3fd2b-232">.NET Framework 4,5 yeniden dağıtılabilir paketi dağıtımını test eden altyapı hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-232">For more information about the infrastructure for testing the deployment of the .NET Framework 4.5 redistributable package, see the following resources.</span></span>

<span data-ttu-id="3fd2b-233">**Active Directory, DNS, DHCP:**</span><span class="sxs-lookup"><span data-stu-id="3fd2b-233">**Active Directory, DNS, DHCP:**</span></span>

- [<span data-ttu-id="3fd2b-234">Active Directory Domain Services</span><span class="sxs-lookup"><span data-stu-id="3fd2b-234">Active Directory Domain Services</span></span>](/windows/desktop/ad/active-directory-domain-services)

- [<span data-ttu-id="3fd2b-235">Etki Alanı Adı Sistemi (DNS)</span><span class="sxs-lookup"><span data-stu-id="3fd2b-235">Domain Name System (DNS)</span></span>](/windows-server/networking/dns/dns-top)

- [<span data-ttu-id="3fd2b-236">Dinamik Ana Bilgisayar Yapılandırma Protokolü (DHCP)</span><span class="sxs-lookup"><span data-stu-id="3fd2b-236">Dynamic Host Configuration Protocol (DHCP)</span></span>](/windows-server/networking/technologies/dhcp/dhcp-top)

<span data-ttu-id="3fd2b-237">**SQL Server 2008:**</span><span class="sxs-lookup"><span data-stu-id="3fd2b-237">**SQL Server 2008:**</span></span>

- <span data-ttu-id="3fd2b-238">[SQL Server 2008 (SQL Server video) yükleniyor](/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="3fd2b-238">[Installing SQL Server 2008 (SQL Server Video)](/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span></span>

- [<span data-ttu-id="3fd2b-239">SQL Server 2008 güvenliğe genel bakış veritabanı yöneticileri</span><span class="sxs-lookup"><span data-stu-id="3fd2b-239">SQL Server 2008 Security Overview for Database Administrators</span></span>](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

<span data-ttu-id="3fd2b-240">**System Center 2012 Configuration Manager (yönetim noktası, dağıtım noktası):**</span><span class="sxs-lookup"><span data-stu-id="3fd2b-240">**System Center 2012 Configuration Manager (Management Point, Distribution Point):**</span></span>

- <span data-ttu-id="3fd2b-241">[System Center 2012 Configuration Manager için Site Yönetimi](/previous-versions/system-center/system-center-2012-R2/gg681983(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="3fd2b-241">[Site Administration for System Center 2012 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg681983(v=technet.10))</span></span>

- <span data-ttu-id="3fd2b-242">[Tek site planlama ve dağıtım Configuration Manager](/previous-versions/system-center/configuration-manager-2007/bb680961(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="3fd2b-242">[Configuration Manager Single Site Planning and Deployment](/previous-versions/system-center/configuration-manager-2007/bb680961(v=technet.10))</span></span>

<span data-ttu-id="3fd2b-243">**Windows bilgisayarlar için System Center 2012 Configuration Manager istemcisi:**</span><span class="sxs-lookup"><span data-stu-id="3fd2b-243">**System Center 2012 Configuration Manager client for Windows computers:**</span></span>

- <span data-ttu-id="3fd2b-244">[System Center 2012 Configuration Manager için İstemci Dağıtma](/previous-versions/system-center/system-center-2012-R2/gg699391(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="3fd2b-244">[Deploying Clients for System Center 2012 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg699391(v=technet.10))</span></span>

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a><span data-ttu-id="3fd2b-245">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="3fd2b-245">Troubleshooting</span></span>

### <a name="log-file-locations"></a><span data-ttu-id="3fd2b-246">Günlük dosyası konumları</span><span class="sxs-lookup"><span data-stu-id="3fd2b-246">Log file locations</span></span>

<span data-ttu-id="3fd2b-247">Aşağıdaki günlük dosyaları .NET Framework kurulum sırasında oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="3fd2b-247">The following log files are generated during .NET Framework setup:</span></span>

- <span data-ttu-id="3fd2b-248">%temp%\Microsoft .NET Framework *Version* \* . txt</span><span class="sxs-lookup"><span data-stu-id="3fd2b-248">%temp%\Microsoft .NET Framework *version*\*.txt</span></span>
- <span data-ttu-id="3fd2b-249">%temp%\Microsoft .NET Framework *Version* \* . html</span><span class="sxs-lookup"><span data-stu-id="3fd2b-249">%temp%\Microsoft .NET Framework *version*\*.html</span></span>

<span data-ttu-id="3fd2b-250">Burada *Sürüm* , yüklemekte olduğunuz .NET Framework sürümü (4,5 veya 4.7.2 gibi).</span><span class="sxs-lookup"><span data-stu-id="3fd2b-250">where *version* is the version of the .NET Framework that you're installing, such as 4.5 or 4.7.2.</span></span>

<span data-ttu-id="3fd2b-251">Ayrıca, `/log` .NET Framework yükleme komutunda komut satırı seçeneğini kullanarak, günlük dosyalarının yazıldığı dizini de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-251">You can also specify the directory to which log files are written by using the `/log` command-line option in the .NET Framework installation command.</span></span> <span data-ttu-id="3fd2b-252">Daha fazla bilgi için bkz. [geliştiriciler için .NET Framework dağıtım kılavuzu](deployment-guide-for-developers.md#command-line-options).</span><span class="sxs-lookup"><span data-stu-id="3fd2b-252">For more information, see [.NET Framework deployment guide for developers](deployment-guide-for-developers.md#command-line-options).</span></span>

<span data-ttu-id="3fd2b-253">[Günlük toplama aracını](https://www.microsoft.com/download/details.aspx?id=12493) , .NET Framework günlük dosyalarını toplamak ve dosyaların boyutunu azaltan sıkıştırılmış dolap (. cab) dosyası oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-253">You can use the [log collection tool](https://www.microsoft.com/download/details.aspx?id=12493) to collect the .NET Framework log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>

<a name="return_codes"></a>

### <a name="return-codes"></a><span data-ttu-id="3fd2b-254">Dönüş kodları</span><span class="sxs-lookup"><span data-stu-id="3fd2b-254">Return codes</span></span>

<span data-ttu-id="3fd2b-255">Aşağıdaki tabloda, .NET Framework 4,5 yeniden dağıtılabilir yükleme programından en sık kullanılan dönüş kodları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-255">The following table lists the most common return codes from the .NET Framework 4.5 redistributable installation program.</span></span> <span data-ttu-id="3fd2b-256">Dönüş kodları yükleyicinin tüm sürümleri için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-256">The return codes are the same for all versions of the installer.</span></span>

<span data-ttu-id="3fd2b-257">Ayrıntılı bilgilerin bağlantıları için bkz. sonraki bölüm, [indirme hata kodları](#additional_error_codes).</span><span class="sxs-lookup"><span data-stu-id="3fd2b-257">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>

|<span data-ttu-id="3fd2b-258">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="3fd2b-258">Return code</span></span>|<span data-ttu-id="3fd2b-259">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fd2b-259">Description</span></span>|
|-----------------|-----------------|
|<span data-ttu-id="3fd2b-260">0</span><span class="sxs-lookup"><span data-stu-id="3fd2b-260">0</span></span>|<span data-ttu-id="3fd2b-261">Yükleme başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-261">Installation completed successfully.</span></span>|
|<span data-ttu-id="3fd2b-262">1602</span><span class="sxs-lookup"><span data-stu-id="3fd2b-262">1602</span></span>|<span data-ttu-id="3fd2b-263">Kullanıcı yüklemeyi iptal etti.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-263">The user canceled installation.</span></span>|
|<span data-ttu-id="3fd2b-264">1603</span><span class="sxs-lookup"><span data-stu-id="3fd2b-264">1603</span></span>|<span data-ttu-id="3fd2b-265">Yükleme sırasında ciddi bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-265">A fatal error occurred during installation.</span></span>|
|<span data-ttu-id="3fd2b-266">1641</span><span class="sxs-lookup"><span data-stu-id="3fd2b-266">1641</span></span>|<span data-ttu-id="3fd2b-267">Yüklemenin tamamlanması için yeniden başlatma gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-267">A restart is required to complete the installation.</span></span> <span data-ttu-id="3fd2b-268">Bu ileti başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-268">This message indicates success.</span></span>|
|<span data-ttu-id="3fd2b-269">3010</span><span class="sxs-lookup"><span data-stu-id="3fd2b-269">3010</span></span>|<span data-ttu-id="3fd2b-270">Yüklemenin tamamlanması için yeniden başlatma gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-270">A restart is required to complete the installation.</span></span> <span data-ttu-id="3fd2b-271">Bu ileti başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-271">This message indicates success.</span></span>|
|<span data-ttu-id="3fd2b-272">5100</span><span class="sxs-lookup"><span data-stu-id="3fd2b-272">5100</span></span>|<span data-ttu-id="3fd2b-273">Kullanıcının bilgisayarı sistem gereksinimlerini karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-273">The user's computer does not meet system requirements.</span></span>|

<a name="additional_error_codes"></a>

### <a name="download-error-codes"></a><span data-ttu-id="3fd2b-274">İndirme hatası kodları</span><span class="sxs-lookup"><span data-stu-id="3fd2b-274">Download error codes</span></span>

- [<span data-ttu-id="3fd2b-275">Arka Plan Akıllı Aktarım Hizmeti (BITS) hata kodları</span><span class="sxs-lookup"><span data-stu-id="3fd2b-275">Background Intelligent Transfer Service (BITS) error codes</span></span>](/windows/desktop/Bits/bits-return-values)

- <span data-ttu-id="3fd2b-276">[URL bilinen adı hata kodları](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="3fd2b-276">[URL moniker error codes](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145(v=vs.85))</span></span>

- [<span data-ttu-id="3fd2b-277">WinHttp hata kodları</span><span class="sxs-lookup"><span data-stu-id="3fd2b-277">WinHttp error codes</span></span>](/windows/desktop/WinHttp/error-messages)

<span data-ttu-id="3fd2b-278">Diğer hata kodları:</span><span class="sxs-lookup"><span data-stu-id="3fd2b-278">Other error codes:</span></span>

- [<span data-ttu-id="3fd2b-279">Windows Installer hata kodları</span><span class="sxs-lookup"><span data-stu-id="3fd2b-279">Windows Installer error codes</span></span>](/windows/desktop/msi/error-codes)

- <span data-ttu-id="3fd2b-280">[Windows Update Aracısı sonuç kodları](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="3fd2b-280">[Windows Update Agent result codes](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="3fd2b-281">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fd2b-281">See also</span></span>

- [<span data-ttu-id="3fd2b-282">Geliştiriciler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3fd2b-282">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="3fd2b-283">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="3fd2b-283">System Requirements</span></span>](../get-started/system-requirements.md)
