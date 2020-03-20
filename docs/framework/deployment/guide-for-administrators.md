---
title: Yöneticiler için .NET Framework Dağıtım Kılavuzu
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
ms.openlocfilehash: be15ce0b0bed37da6fe400e98bfdd118c48f7ba0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716533"
---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="0ce0f-102">Yöneticiler için .NET Framework Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0ce0f-102">.NET Framework Deployment Guide for Administrators</span></span>

<span data-ttu-id="0ce0f-103">Bu adım adım makale, bir sistem yöneticisinin Microsoft Endpoint Configuration Manager'ı kullanarak .NET Framework 4.5 ve sistem bağımlılıklarını ağ da nasıl dağıtabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-103">This step-by-step article describes how a system administrator can deploy the .NET Framework 4.5 and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="0ce0f-104">Bu makalede tüm istemci bilgisayarların .NET Framework için gerekli olan minimum sistem gereksinimlerini karşıladığı varsayılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-104">This article assumes that all target client computers meet the minimum requirements for the .NET Framework.</span></span> <span data-ttu-id="0ce0f-105">.NET Framework 4.5'i yüklemek için yazılım ve donanım gereksinimlerinin listesi için [Bkz. Sistem Gereksinimleri.](../get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="0ce0f-105">For a list of the software and hardware requirements for installing the .NET Framework 4.5, see [System Requirements](../get-started/system-requirements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0ce0f-106">.NET Framework 4.5, Configuration Manager ve Active Directory dahil ancak bunlarla sınırlı olmamak üzere bu belgede başvurulan yazılımın her biri lisans hüküm ve koşullarına tabidir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-106">The software referenced in this document, including, without limitation, the .NET Framework 4.5, Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="0ce0f-107">Bu yönergeler, bu tür lisans koşullarını ve koşulları gözden geçirilmiş yazılımların sahipleri tarafından kabul edildiği varsaymaktadır.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-107">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="0ce0f-108">Bu yönergeler, bu tür lisans anlaşmalarının koşullarından feragat etmiş sayılmaz.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-108">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>
>
> <span data-ttu-id="0ce0f-109">.NET Framework desteği hakkında daha fazla bilgi için Microsoft Destek web [sitesindeki .NET Framework resmi destek politikasına](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) bakın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-109">For information about support for the .NET Framework, see [.NET Framework official support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) on the Microsoft Support website.</span></span>

<span data-ttu-id="0ce0f-110">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="0ce0f-110">This topic contains the following sections:</span></span>

- [<span data-ttu-id="0ce0f-111">Dağıtım işlemi</span><span class="sxs-lookup"><span data-stu-id="0ce0f-111">The deployment process</span></span>](#the_deployment_process)
- [<span data-ttu-id="0ce0f-112">.NET Framework'ü dağıtma</span><span class="sxs-lookup"><span data-stu-id="0ce0f-112">Deploying the .NET Framework</span></span>](#deploying_in_a_test_environment)
- [<span data-ttu-id="0ce0f-113">Koleksiyon oluşturma</span><span class="sxs-lookup"><span data-stu-id="0ce0f-113">Create a collection</span></span>](#creating_a_collection)
- [<span data-ttu-id="0ce0f-114">Paket ve program oluşturma</span><span class="sxs-lookup"><span data-stu-id="0ce0f-114">Create a package and program</span></span>](#creating_a_package)
- [<span data-ttu-id="0ce0f-115">Dağıtım noktası seçme</span><span class="sxs-lookup"><span data-stu-id="0ce0f-115">Select a distribution point</span></span>](#select_dist_point)
- [<span data-ttu-id="0ce0f-116">Paketi dağıtma</span><span class="sxs-lookup"><span data-stu-id="0ce0f-116">Deploy the package</span></span>](#deploying_package)
- [<span data-ttu-id="0ce0f-117">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0ce0f-117">Resources</span></span>](#resources)
- [<span data-ttu-id="0ce0f-118">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="0ce0f-118">Troubleshooting</span></span>](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a><span data-ttu-id="0ce0f-119">Dağıtım işlemi</span><span class="sxs-lookup"><span data-stu-id="0ce0f-119">The deployment process</span></span>

<span data-ttu-id="0ce0f-120">Destekleyici altyapıyı yerleştirdiğinizde, .NET Framework yeniden dağıtılabilir paketini ağdaki bilgisayarlara dağıtmak için Configuration Manager'ı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-120">When you have the supporting infrastructure in place, you use Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="0ce0f-121">Altyapının oluşturulması, beş birincil alanın oluşturulmasını ve tanımlanmasını gerektirir: koleksiyonlar, yazılım için bir paket ve program, dağıtım noktaları ve dağıtımlar.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-121">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>

- <span data-ttu-id="0ce0f-122">**Koleksiyonlar,** .NET Framework'ün dağıtıldığı kullanıcılar, kullanıcı grupları veya bilgisayarlar gibi Configuration Manager kaynaklarıgruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-122">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which the .NET Framework is deployed.</span></span> <span data-ttu-id="0ce0f-123">Daha fazla bilgi için Configuration Manager dokümantasyon kitaplığında [Configuration Manager'daki koleksiyonlara giriş'e](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) bakın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-123">For more information, see [Introduction to collections in Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="0ce0f-124">**Paketler ve programlar** genellikle istemci bilgisayara yüklenecek yazılım uygulamalarını temsil eder, ancak tek tek dosyalar, güncelleştirmeler ve hatta tek tek komutlar da içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-124">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="0ce0f-125">Daha fazla bilgi için Configuration Manager belgeleri kitaplığında [Configuration Manager'daki Paketler ve programlara](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs) bakın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-125">For more information, see [Packages and programs in Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="0ce0f-126">**Dağıtım noktaları,** yazılımın istemci bilgisayarlarda çalışması için gerekli dosyaları depolayan Configuration Manager site sistem rolleridir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-126">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="0ce0f-127">Yapılandırma Yöneticisi istemcisi bir yazılım dağıtımı alıp işlediğinde, yazılımla ilişkili içeriği indirmek ve kurulum işlemini başlatmak için bir dağıtım noktasıyla temasa geçer.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-127">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="0ce0f-128">Daha fazla bilgi için Configuration Manager dokümantasyon [kitaplığında Configuration Manager'da içerik yönetimi için temel kavramlara](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) bakın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-128">For more information, see [Fundamental concepts for content management in Configuration Manager](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="0ce0f-129">**Dağıtımlar,** yazılım paketini yüklemeleri için belirtilen hedef koleksiyonun ilgili üyelerine talimat verir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-129">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0ce0f-130">Bu konudaki yordamlar, bir paket ve program oluşturmak ve dağıtmak için normal ayarları içerir ve tüm olası ayarları kapsamayabilir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-130">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="0ce0f-131">Diğer Configuration Manager dağıtım seçenekleri için [Configuration Manager Documentation Library'ye](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29)bakın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-131">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).</span></span>

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a><span data-ttu-id="0ce0f-132">.NET Framework'ü dağıtma</span><span class="sxs-lookup"><span data-stu-id="0ce0f-132">Deploying the .NET Framework</span></span>

<span data-ttu-id="0ce0f-133">.NET Framework 4.5'in sessiz bir yüklemesini dağıtmak için Configuration Manager'ı kullanabilirsiniz, burada kullanıcılar yükleme işlemiyle etkileşimde değildir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-133">You can use Configuration Manager to deploy a silent installation of the .NET Framework 4.5, where the users do not interact with the installation process.</span></span> <span data-ttu-id="0ce0f-134">Şu adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="0ce0f-134">Follow these steps:</span></span>

1. <span data-ttu-id="0ce0f-135">[Bir koleksiyon oluşturun.](#creating_a_collection)</span><span class="sxs-lookup"><span data-stu-id="0ce0f-135">[Create a collection](#creating_a_collection).</span></span>

2. <span data-ttu-id="0ce0f-136">[.NET Framework yeniden dağıtılabilir için bir paket ve program oluşturun.](#creating_a_package)</span><span class="sxs-lookup"><span data-stu-id="0ce0f-136">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>

3. <span data-ttu-id="0ce0f-137">[Bir dağıtım noktası seçin.](#select_dist_point)</span><span class="sxs-lookup"><span data-stu-id="0ce0f-137">[Select a distribution point](#select_dist_point).</span></span>

4. <span data-ttu-id="0ce0f-138">[Paketi dağıtın.](#deploying_package)</span><span class="sxs-lookup"><span data-stu-id="0ce0f-138">[Deploy the package](#deploying_package).</span></span>

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a><span data-ttu-id="0ce0f-139">Koleksiyon oluşturma</span><span class="sxs-lookup"><span data-stu-id="0ce0f-139">Create a collection</span></span>

<span data-ttu-id="0ce0f-140">Bu adımda, paket ve program dağıtacağınız bilgisayarları seçersiniz ve onları bir aygıt koleksiyonunda gruplandırırsınız.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-140">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="0ce0f-141">Yapılandırma Yöneticisi'nde bir koleksiyon oluşturmak için, doğrudan üyelik kurallarını (koleksiyon üyelerini el ile belirtirsiniz) veya sorgu kurallarını (koleksiyon üyelerini sizin belirttiğiniz ölçütlere göre Yapılandırma Yöneticisi belirler) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-141">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="0ce0f-142">Sorgular ve doğrudan kurallar da dahil olmak üzere üyelik kuralları hakkında daha fazla bilgi için Configuration Manager Documentation [Library'deki Configuration Manager'daki koleksiyonlara giriş](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) bilgisine bakın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-142">For more information about membership rules, including queries and direct rules, see [Introduction to collections in Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager Documentation Library.</span></span>

<span data-ttu-id="0ce0f-143">Bir koleksiyon oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="0ce0f-143">To create a collection:</span></span>

1. <span data-ttu-id="0ce0f-144">Configuration Manager konsolunda **Varlıklar ve Uyumluluk'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-144">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>

2. <span data-ttu-id="0ce0f-145">Varlıklar **ve Uyumluluk** çalışma alanında **Aygıt Koleksiyonları'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-145">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>

3. <span data-ttu-id="0ce0f-146">**Oluştur** **grubundaKi Giriş** sekmesinde **Aygıt Koleksiyonu Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-146">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>

4. <span data-ttu-id="0ce0f-147">Aygıt Koleksiyonu Oluşturma **Sihirbazı'nın** **Genel** sayfasında, koleksiyon için bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-147">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>

5. <span data-ttu-id="0ce0f-148">Sınırlayıcı bir koleksiyon belirtmek için **Gözat'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-148">Choose **Browse** to specify a limiting collection.</span></span>

6. <span data-ttu-id="0ce0f-149">Üyelik **Kuralları** sayfasında Kural **Ekle'yi**seçin ve ardından **Doğrudan Üyelik Kuralı Oluştur Sihirbazı'nı**açmak için **Doğrudan Kural'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-149">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="0ce0f-150">**İleri**’yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-150">Choose **Next**.</span></span>

7. <span data-ttu-id="0ce0f-151">Kaynak **Ara** sayfasında, Kaynak **sınıf** listesinde **Sistem Kaynağı'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-151">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="0ce0f-152">**Öznitelik ad** listesinde **Ad'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-152">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="0ce0f-153">**Değer** alanına girin `%`ve sonra **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-153">In the **Value** field, enter `%`, and then choose **Next**.</span></span>

8. <span data-ttu-id="0ce0f-154">Kaynakları **Seç** sayfasında, .NET Framework'e dağıtmak istediğiniz her bilgisayar için onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-154">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="0ce0f-155">**İleri'yi**seçin ve sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-155">Choose **Next**, and then complete the wizard.</span></span>

9. <span data-ttu-id="0ce0f-156">**Aygıt Toplama Sihirbazı Oluştur'un**Üyelik **Kuralları** sayfasında **İleri'yi**seçin ve ardından sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-156">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="0ce0f-157">.NET Framework yeniden dağıtılabilir paketi için paket ve program oluşturma</span><span class="sxs-lookup"><span data-stu-id="0ce0f-157">Create a package and program for the .NET Framework redistributable package</span></span>

<span data-ttu-id="0ce0f-158">Aşağıdaki adımlar, .NET Framework yeniden dağıtılabilir için el ile bir paket oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-158">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="0ce0f-159">Paket, .NET Framework'ün kurulumu için belirtilen parametreleri ve paketin hedef bilgisayarlara nereden dağıtılacağını içerir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-159">The package contains the specified parameters for installing the .NET Framework and the location from where the package will be distributed to the target computers.</span></span>

<span data-ttu-id="0ce0f-160">Bir paket oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="0ce0f-160">To create a package:</span></span>

1. <span data-ttu-id="0ce0f-161">Configuration Manager konsolunda **Yazılım Kitaplığı'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-161">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="0ce0f-162">Yazılım **Kitaplığı** çalışma alanında, **Uygulama Yönetimi'ni**genişletin ve ardından **Paketleri**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-162">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="0ce0f-163">**Giriş** sekmesinde, **Oluştur** grubunda **Paket Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-163">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>

4. <span data-ttu-id="0ce0f-164">Paket Oluştur ve **Program Sihirbazı'nın** **Paket** sayfasında aşağıdaki bilgileri girin:</span><span class="sxs-lookup"><span data-stu-id="0ce0f-164">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    - <span data-ttu-id="0ce0f-165">Adı:`.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="0ce0f-165">Name: `.NET Framework 4.5`</span></span>

    - <span data-ttu-id="0ce0f-166">Üretici:`Microsoft`</span><span class="sxs-lookup"><span data-stu-id="0ce0f-166">Manufacturer: `Microsoft`</span></span>

    - <span data-ttu-id="0ce0f-167">Dil.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-167">Language.</span></span> `English (US)`

5. <span data-ttu-id="0ce0f-168">Bu paketi seçin **kaynak dosyaları içerir**ve sonra .NET Framework yükleme dosyalarını içeren yerel veya ağ klasörünü seçmek için **Gözat'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-168">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="0ce0f-169">Klasörü seçtiğinizde **Tamam'ı**ve **sonra İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-169">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>

6. <span data-ttu-id="0ce0f-170">Sihirbazın **Program Türü** sayfasında Standart **Program'ı**seçin ve sonra **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-170">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>

7. <span data-ttu-id="0ce0f-171">Paket Oluştur ve **Program Sihirbazı'nın** **Program** sayfasında aşağıdaki bilgileri girin:</span><span class="sxs-lookup"><span data-stu-id="0ce0f-171">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    1. <span data-ttu-id="0ce0f-172">**Adı:**`.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="0ce0f-172">**Name:** `.NET Framework 4.5`</span></span>

    2. <span data-ttu-id="0ce0f-173">**Komut satırı:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (bu adımlardan sonra tabloda komut satırı seçenekleri açıklanmıştır)</span><span class="sxs-lookup"><span data-stu-id="0ce0f-173">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>

    3. <span data-ttu-id="0ce0f-174">**Çalıştır:** **Gizli'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-174">**Run:** Choose **Hidden**.</span></span>

    4. <span data-ttu-id="0ce0f-175">**Program çalıştırabilirsiniz:** Bir kullanıcının oturum açıp açmadığına bakılmaksızın programın çalıştırılayacağını belirten seçeneği seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-175">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>

8. <span data-ttu-id="0ce0f-176">**Gereksinimler** sayfasında, varsayılan değerleri kabul etmek için **İleri'yi** seçin ve ardından sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-176">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>

<span data-ttu-id="0ce0f-177">Aşağıdaki tablo, 7. adımda belirtilen komut satırı seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-177">The following table describes the command-line options specified in step 7.</span></span>

|<span data-ttu-id="0ce0f-178">Seçenek</span><span class="sxs-lookup"><span data-stu-id="0ce0f-178">Option</span></span>|<span data-ttu-id="0ce0f-179">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ce0f-179">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="0ce0f-180">**/q**</span><span class="sxs-lookup"><span data-stu-id="0ce0f-180">**/q**</span></span>|<span data-ttu-id="0ce0f-181">Sessiz modu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-181">Sets quiet mode.</span></span> <span data-ttu-id="0ce0f-182">Hiçbir kullanıcı girişine gerek yoktur ve hiçbir çıktı gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-182">No user input is required, and no output is shown.</span></span>|
|<span data-ttu-id="0ce0f-183">**/norestart**</span><span class="sxs-lookup"><span data-stu-id="0ce0f-183">**/norestart**</span></span>|<span data-ttu-id="0ce0f-184">Kurulum programının otomatik olarak yeniden başlatılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-184">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="0ce0f-185">Bu seçeneği kullanırsanız, Yapılandırma Yöneticisi'nin bilgisayarı yeniden başlatmayı üstlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-185">If you use this option, Configuration Manager must handle the computer restart.</span></span>|
|<span data-ttu-id="0ce0f-186">**/zincirleme paket** *PaketAdı*</span><span class="sxs-lookup"><span data-stu-id="0ce0f-186">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="0ce0f-187">Zincirlemeyi yapan paketin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-187">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="0ce0f-188">Bu bilgiler, Microsoft Müşteri Deneyimi Geliştirme Programı'na (CEIP) kaydolmuş olanlar için diğer yükleme oturumu bilgileriyle birlikte bildirilir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-188">This information is reported with other installation session information for those who have signed up for the Microsoft Customer Experience Improvement Program (CEIP).</span></span> <span data-ttu-id="0ce0f-189">Paket adı boşluklar içeriyorsa, sınırlayıcı olarak çift tırnak işaretleri kullanın; örneğin: **/zincirleme paket "Zincirleme Ürün"**.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-189">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|

<span data-ttu-id="0ce0f-190">Bu adımlar, .NET Framework 4.5 adlı bir paket oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-190">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="0ce0f-191">Program, .NET Framework 4.5'in sessiz bir kurulumunu dağıtır.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-191">The program deploys a silent installation of the .NET Framework 4.5.</span></span> <span data-ttu-id="0ce0f-192">Sessiz bir yüklemede, kullanıcılar yükleme işlemiyle etkileşime girmez ve zincirleme uygulaması iade kodunu yakalamak ve yeniden başlatmaişlemini işlemek zorundadır; bkz. [Yükleme Paketinden İlerleme Bilgileri Alma.](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0ce0f-192">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).</span></span>

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a><span data-ttu-id="0ce0f-193">Dağıtım noktası seçme</span><span class="sxs-lookup"><span data-stu-id="0ce0f-193">Select a distribution point</span></span>

<span data-ttu-id="0ce0f-194">Paketi ve programı bir sunucudan istemci bilgisayarlara dağıtmak için, önce bir site sistemini dağıtım noktası olarak belirlemeniz ve sonra paketi dağıtım noktasına dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-194">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>

<span data-ttu-id="0ce0f-195">Bir önceki bölümde oluşturulan .NET Framework 4.5 paketi için bir dağıtım noktası seçmek üzere aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="0ce0f-195">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>

1. <span data-ttu-id="0ce0f-196">Configuration Manager konsolunda **Yazılım Kitaplığı'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-196">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="0ce0f-197">Yazılım **Kitaplığı** çalışma alanında, **Uygulama Yönetimi'ni**genişletin ve ardından **Paketleri**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-197">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="0ce0f-198">Paket listesinden, önceki bölümde oluşturduğunuz **.NET Framework 4.5** paketini seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-198">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>

4. <span data-ttu-id="0ce0f-199">**Giriş** sekmesinde, **Dağıtım** grubunda **İçeriği Dağıt'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-199">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>

5. <span data-ttu-id="0ce0f-200">**İçeriği Dağıt sihirbazının** **Genel** sekmesinde, **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-200">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>

6. <span data-ttu-id="0ce0f-201">Sihirbazın **İçerik Hedef** sayfasında **Ekle'yi**ve ardından Dağıtım **Noktası'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-201">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>

7. <span data-ttu-id="0ce0f-202">Dağıtım **Noktaları Ekle** iletişim kutusunda, paketi ve programı barındıracak dağıtım noktası(lar)'ı seçin ve ardından **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-202">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>

8. <span data-ttu-id="0ce0f-203">Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-203">Complete the wizard.</span></span>

<span data-ttu-id="0ce0f-204">Paket şimdi, .NET Framework 4.5'i sessizce dağıtmak gereksinim duyduğunuz tüm bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-204">The package now contains all the information you need to silently deploy the .NET Framework 4.5.</span></span> <span data-ttu-id="0ce0f-205">Paketi ve programı dağıtmadan önce, dağıtım noktasına yüklenmiş olduğundan doğrulayın; Configuration Manager Documentation Library'de [Configuration Manager ile dağıttığınız Monitor içeriğinin](https://docs.microsoft.com/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) "İçerik durumu izleme" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-205">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Content status monitoring" section of [Monitor content you distribute with Configuration Manager](https://docs.microsoft.com/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) in the Configuration Manager Documentation Library.</span></span>

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a><span data-ttu-id="0ce0f-206">Paketi dağıtma</span><span class="sxs-lookup"><span data-stu-id="0ce0f-206">Deploy the package</span></span>

<span data-ttu-id="0ce0f-207">.NET Framework 4.5 paketini ve programını dağıtmak için:</span><span class="sxs-lookup"><span data-stu-id="0ce0f-207">To deploy the .NET Framework 4.5 package and program:</span></span>

1. <span data-ttu-id="0ce0f-208">Configuration Manager konsolunda **Yazılım Kitaplığı'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-208">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="0ce0f-209">Yazılım **Kitaplığı** çalışma alanında, **Uygulama Yönetimi'ni**genişletin ve ardından **Paketleri**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-209">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="0ce0f-210">Paket listesinden **,.NET Framework 4.5**adlı paketi seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-210">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>

4. <span data-ttu-id="0ce0f-211">**Giriş** sekmesinde, **Dağıtım** grubunda **Dağıt'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-211">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>

5. <span data-ttu-id="0ce0f-212">**Yazılım Dağıt**sihirbazının **Genel** sayfasında **Gözat'ı**seçin ve daha önce oluşturduğunuz koleksiyonu seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-212">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="0ce0f-213">**İleri**’yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-213">Choose **Next**.</span></span>

6. <span data-ttu-id="0ce0f-214">Sihirbazın **İçerik** sayfasında, yazılımı dağıtmak istediğiniz noktanın görüntülendiğini doğrulayın ve **sonra İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-214">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>

7. <span data-ttu-id="0ce0f-215">Sihirbazın **Dağıtım Ayarları** sayfasında, **Eylemin** **Yükleme**olarak ayarlı olduğunu ve **Amaç'ın Gerekli**olarak ayarlı olduğunu onaylayın. **Purpose**</span><span class="sxs-lookup"><span data-stu-id="0ce0f-215">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="0ce0f-216">Bu, yazılım paketinin hedeflenen bilgisayarlarda zorunlu bir yükleme olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-216">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="0ce0f-217">**İleri**’yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-217">Choose **Next**.</span></span>

8. <span data-ttu-id="0ce0f-218">Sihirbazın **Zamanlama** sayfasında ,.NET Çerçevesi'nin ne zaman yüklenmesini istediğinizi belirtin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-218">On the **Scheduling** page of the wizard, specify when you want the .NET Framework to be installed.</span></span> <span data-ttu-id="0ce0f-219">Yükleme zamanı atamak için **Yeni'yi** seçebilir veya kullanıcı oturum açıp kapattığında veya mümkün olan en kısa sürede yazılımı yüklemesini emredebilir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-219">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="0ce0f-220">**İleri**’yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-220">Choose **Next**.</span></span>

9. <span data-ttu-id="0ce0f-221">Sihirbazın **Kullanıcı Deneyimi** sayfasında varsayılan değerleri kullanın ve **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-221">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>

    > [!WARNING]
    > <span data-ttu-id="0ce0f-222">Üretim ortamınızın, dağıtım çizelgesi için farklı seçimler olmasını gerektiren ilkeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-222">Your production environment might have policies that require different selections for the deployment schedule.</span></span> <span data-ttu-id="0ce0f-223">Bu seçenekler hakkında bilgi [için, Bkz. Reklam Adı Özellikleri: Zamanlama Sekmesi](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).</span><span class="sxs-lookup"><span data-stu-id="0ce0f-223">For information about these options, see [Advertisement Name Properties: Schedule Tab](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).</span></span>

10. <span data-ttu-id="0ce0f-224">Sihirbazın **Dağıtım Noktaları** sayfasında varsayılan değerleri kullanın ve **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-224">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>

11. <span data-ttu-id="0ce0f-225">Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-225">Complete the wizard.</span></span> <span data-ttu-id="0ce0f-226">**İzleme** çalışma alanının **Dağıtımlar** düğümünde dağıtımın ilerlemesini izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-226">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>

<span data-ttu-id="0ce0f-227">Şimdi paket hedeflenen koleksiyona dağıtılır ve .NET Framework 4.5'in sessiz yüklemesi başlar.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-227">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="0ce0f-228">.NET Framework 4.5 yükleme hata kodları hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerinde [İade Kodları](#return_codes) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-228">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>

<a name="resources"></a>

## <a name="resources"></a><span data-ttu-id="0ce0f-229">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0ce0f-229">Resources</span></span>

<span data-ttu-id="0ce0f-230">.NET Framework 4.5 yeniden dağıtılabilir paketinin dağıtımını sınayabilir altyapı hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-230">For more information about the infrastructure for testing the deployment of the .NET Framework 4.5 redistributable package, see the following resources.</span></span>

<span data-ttu-id="0ce0f-231">**Etkin Dizin, DNS, DHCP:**</span><span class="sxs-lookup"><span data-stu-id="0ce0f-231">**Active Directory, DNS, DHCP:**</span></span>

- [<span data-ttu-id="0ce0f-232">Active Directory Domain Services</span><span class="sxs-lookup"><span data-stu-id="0ce0f-232">Active Directory Domain Services</span></span>](/windows/desktop/ad/active-directory-domain-services)

- [<span data-ttu-id="0ce0f-233">Etki Alanı Adı Sistemi (DNS)</span><span class="sxs-lookup"><span data-stu-id="0ce0f-233">Domain Name System (DNS)</span></span>](/windows-server/networking/dns/dns-top)

- [<span data-ttu-id="0ce0f-234">Dinamik Ana Bilgisayar Yapılandırma Protokolü (DHCP)</span><span class="sxs-lookup"><span data-stu-id="0ce0f-234">Dynamic Host Configuration Protocol (DHCP)</span></span>](/windows-server/networking/technologies/dhcp/dhcp-top)

<span data-ttu-id="0ce0f-235">**SQL Server 2008:**</span><span class="sxs-lookup"><span data-stu-id="0ce0f-235">**SQL Server 2008:**</span></span>

- <span data-ttu-id="0ce0f-236">[SQL Server 2008 Kurulumu (SQL Server Video)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="0ce0f-236">[Installing SQL Server 2008 (SQL Server Video)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span></span>

- [<span data-ttu-id="0ce0f-237">SQL Server 2008 Veritabanı Yöneticileri için Güvenlik Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ce0f-237">SQL Server 2008 Security Overview for Database Administrators</span></span>](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

<span data-ttu-id="0ce0f-238">**Sistem Merkezi 2012 Konfigürasyon Yöneticisi (Yönetim Noktası, Dağıtım Noktası):**</span><span class="sxs-lookup"><span data-stu-id="0ce0f-238">**System Center 2012 Configuration Manager (Management Point, Distribution Point):**</span></span>

- [<span data-ttu-id="0ce0f-239">System Center 2012 Configuration Manager için Site Yönetimi</span><span class="sxs-lookup"><span data-stu-id="0ce0f-239">Site Administration for System Center 2012 Configuration Manager</span></span>](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)

- [<span data-ttu-id="0ce0f-240">Configuration Manager Tek Site Planlama ve Dağıtım</span><span class="sxs-lookup"><span data-stu-id="0ce0f-240">Configuration Manager Single Site Planning and Deployment</span></span>](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)

<span data-ttu-id="0ce0f-241">**Windows bilgisayarlar için System Center 2012 Configuration Manager istemcisi:**</span><span class="sxs-lookup"><span data-stu-id="0ce0f-241">**System Center 2012 Configuration Manager client for Windows computers:**</span></span>

- [<span data-ttu-id="0ce0f-242">System Center 2012 Configuration Manager için İstemci Dağıtma</span><span class="sxs-lookup"><span data-stu-id="0ce0f-242">Deploying Clients for System Center 2012 Configuration Manager</span></span>](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a><span data-ttu-id="0ce0f-243">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="0ce0f-243">Troubleshooting</span></span>

### <a name="log-file-locations"></a><span data-ttu-id="0ce0f-244">Günlük dosyası konumları</span><span class="sxs-lookup"><span data-stu-id="0ce0f-244">Log file locations</span></span>

<span data-ttu-id="0ce0f-245">.NET Framework kurulumu sırasında aşağıdaki günlük dosyaları oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="0ce0f-245">The following log files are generated during .NET Framework setup:</span></span>

- <span data-ttu-id="0ce0f-246">%temp%\Microsoft .NET Framework *sürümü*\*.txt</span><span class="sxs-lookup"><span data-stu-id="0ce0f-246">%temp%\Microsoft .NET Framework *version*\*.txt</span></span>
- <span data-ttu-id="0ce0f-247">%temp%\Microsoft .NET Framework *sürümü*\*.html</span><span class="sxs-lookup"><span data-stu-id="0ce0f-247">%temp%\Microsoft .NET Framework *version*\*.html</span></span>

<span data-ttu-id="0ce0f-248">*sürüm,* 4.5 veya 4.7.2 gibi .NET Framework'ün yüklediğiniz sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-248">where *version* is the version of the .NET Framework that you're installing, such as 4.5 or 4.7.2.</span></span>

<span data-ttu-id="0ce0f-249">.NET Framework yükleme komutundaki `/log` komut satırı seçeneğini kullanarak günlük dosyalarının yazıldığı dizini de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-249">You can also specify the directory to which log files are written by using the `/log` command-line option in the .NET Framework installation command.</span></span> <span data-ttu-id="0ce0f-250">Daha fazla bilgi için [geliştiriciler için .NET Framework dağıtım kılavuzuna](deployment-guide-for-developers.md#command-line-options)bakın.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-250">For more information, see [.NET Framework deployment guide for developers](deployment-guide-for-developers.md#command-line-options).</span></span>

<span data-ttu-id="0ce0f-251">.NET Framework günlük dosyalarını toplamak ve dosyaların boyutunu küçülten sıkıştırılmış bir dolap (.cab) dosyası oluşturmak için [günlük toplama aracını](https://www.microsoft.com/download/details.aspx?id=12493) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-251">You can use the [log collection tool](https://www.microsoft.com/download/details.aspx?id=12493) to collect the .NET Framework log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>

<a name="return_codes"></a>

### <a name="return-codes"></a><span data-ttu-id="0ce0f-252">Dönüş kodları</span><span class="sxs-lookup"><span data-stu-id="0ce0f-252">Return codes</span></span>

<span data-ttu-id="0ce0f-253">Aşağıdaki tabloda .NET Framework 4.5 yeniden dağıtılabilir yükleme programındaki en yaygın iade kodları listelenilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-253">The following table lists the most common return codes from the .NET Framework 4.5 redistributable installation program.</span></span> <span data-ttu-id="0ce0f-254">Dönüş kodları yükleyicinin tüm sürümleri için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-254">The return codes are the same for all versions of the installer.</span></span>

<span data-ttu-id="0ce0f-255">Ayrıntılı bilgi için bağlantılar için, sonraki bölüme bakın, [Hata kodları indirin.](#additional_error_codes)</span><span class="sxs-lookup"><span data-stu-id="0ce0f-255">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>

|<span data-ttu-id="0ce0f-256">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="0ce0f-256">Return code</span></span>|<span data-ttu-id="0ce0f-257">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ce0f-257">Description</span></span>|
|-----------------|-----------------|
|<span data-ttu-id="0ce0f-258">0</span><span class="sxs-lookup"><span data-stu-id="0ce0f-258">0</span></span>|<span data-ttu-id="0ce0f-259">Yükleme başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-259">Installation completed successfully.</span></span>|
|<span data-ttu-id="0ce0f-260">1602</span><span class="sxs-lookup"><span data-stu-id="0ce0f-260">1602</span></span>|<span data-ttu-id="0ce0f-261">Kullanıcı yüklemeyi iptal etti.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-261">The user canceled installation.</span></span>|
|<span data-ttu-id="0ce0f-262">1603</span><span class="sxs-lookup"><span data-stu-id="0ce0f-262">1603</span></span>|<span data-ttu-id="0ce0f-263">Yükleme sırasında ciddi bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-263">A fatal error occurred during installation.</span></span>|
|<span data-ttu-id="0ce0f-264">1641</span><span class="sxs-lookup"><span data-stu-id="0ce0f-264">1641</span></span>|<span data-ttu-id="0ce0f-265">Yüklemenin tamamlanması için yeniden başlatma gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-265">A restart is required to complete the installation.</span></span> <span data-ttu-id="0ce0f-266">Bu ileti başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-266">This message indicates success.</span></span>|
|<span data-ttu-id="0ce0f-267">3010</span><span class="sxs-lookup"><span data-stu-id="0ce0f-267">3010</span></span>|<span data-ttu-id="0ce0f-268">Yüklemenin tamamlanması için yeniden başlatma gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-268">A restart is required to complete the installation.</span></span> <span data-ttu-id="0ce0f-269">Bu ileti başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-269">This message indicates success.</span></span>|
|<span data-ttu-id="0ce0f-270">5100</span><span class="sxs-lookup"><span data-stu-id="0ce0f-270">5100</span></span>|<span data-ttu-id="0ce0f-271">Kullanıcının bilgisayarı sistem gereksinimlerini karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-271">The user's computer does not meet system requirements.</span></span>|

<a name="additional_error_codes"></a>

### <a name="download-error-codes"></a><span data-ttu-id="0ce0f-272">İndirme hatası kodları</span><span class="sxs-lookup"><span data-stu-id="0ce0f-272">Download error codes</span></span>

- [<span data-ttu-id="0ce0f-273">Arka Plan Akıllı Aktarım Hizmeti (BITS) hata kodları</span><span class="sxs-lookup"><span data-stu-id="0ce0f-273">Background Intelligent Transfer Service (BITS) error codes</span></span>](/windows/desktop/Bits/bits-return-values)

- [<span data-ttu-id="0ce0f-274">URL takma hata kodları</span><span class="sxs-lookup"><span data-stu-id="0ce0f-274">URL moniker error codes</span></span>](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)

- [<span data-ttu-id="0ce0f-275">WinHttp hata kodları</span><span class="sxs-lookup"><span data-stu-id="0ce0f-275">WinHttp error codes</span></span>](/windows/desktop/WinHttp/error-messages)

<span data-ttu-id="0ce0f-276">Diğer hata kodları:</span><span class="sxs-lookup"><span data-stu-id="0ce0f-276">Other error codes:</span></span>

- [<span data-ttu-id="0ce0f-277">Windows Installer hata kodları</span><span class="sxs-lookup"><span data-stu-id="0ce0f-277">Windows Installer error codes</span></span>](/windows/desktop/msi/error-codes)

- <span data-ttu-id="0ce0f-278">[Windows Update Aracısı sonuç kodları](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="0ce0f-278">[Windows Update Agent result codes](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="0ce0f-279">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-279">See also</span></span>

- [<span data-ttu-id="0ce0f-280">Geliştiriciler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0ce0f-280">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="0ce0f-281">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="0ce0f-281">System Requirements</span></span>](../get-started/system-requirements.md)
