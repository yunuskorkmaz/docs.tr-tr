---
title: 'Nasıl yapilir: MMC snap-in ile sertifikaları görüntüleme'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 35048c24e838c513909fae8bedcba287001f5cef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184779"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="7acff-102">Nasıl yapilir: MMC snap-in ile sertifikaları görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7acff-102">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="7acff-103">Güvenli bir istemci veya hizmet oluşturduğunuzda, [sertifikayı](working-with-certificates.md) kimlik bilgisi olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7acff-103">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="7acff-104">Örneğin, yaygın bir kimlik bilgisi türü, <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> yöntemle oluşturduğunuz X.509 sertifikasıdır.</span><span class="sxs-lookup"><span data-stu-id="7acff-104">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="7acff-105">Windows sistemlerinde Microsoft Yönetim Konsolu (MMC) ile incelediğiniz üç farklı sertifika deposu türü vardır:</span><span class="sxs-lookup"><span data-stu-id="7acff-105">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="7acff-106">Yerel bilgisayar: Mağaza aygıtiçin yerel ve aygıttaki tüm kullanıcılar için geneldir.</span><span class="sxs-lookup"><span data-stu-id="7acff-106">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="7acff-107">Geçerli kullanıcı: Mağaza, aygıttaki geçerli kullanıcı hesabına yereldir.</span><span class="sxs-lookup"><span data-stu-id="7acff-107">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="7acff-108">Servis hesabı: Mağaza, aygıttaki belirli bir hizmetin yereldir.</span><span class="sxs-lookup"><span data-stu-id="7acff-108">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="7acff-109">MMC snap-in'deki sertifikaları görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7acff-109">View certificates in the MMC snap-in</span></span>

<span data-ttu-id="7acff-110">Aşağıdaki yordam, uygun bir sertifika bulmak için yerel cihazınızdaki mağazaların nasıl incelenir olduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="7acff-110">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span>
  
1. <span data-ttu-id="7acff-111">**Başlat** menüsünden **Çalıştır'ı** seçin ve ardından *mmc'yi*girin.</span><span class="sxs-lookup"><span data-stu-id="7acff-111">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span>

    <span data-ttu-id="7acff-112">MMC görünür.</span><span class="sxs-lookup"><span data-stu-id="7acff-112">The MMC appears.</span></span>
  
2. <span data-ttu-id="7acff-113">**Dosya** menüsünden **Ekle/Kaldır'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="7acff-113">From the **File** menu, select **Add/Remove Snap In**.</span></span>

    <span data-ttu-id="7acff-114">**Eklenti veya Kaldır Snap-ins** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7acff-114">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="7acff-115">Kullanılabilir **ekler** listesinden **Sertifikalar'ı**seçin ve ardından **Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="7acff-115">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Sertifika ekleme ekleme](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="7acff-117">**Sertifikalar'a giriş** penceresinde **Bilgisayar hesabı'nı**seçin ve sonra **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="7acff-117">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span>
  
    <span data-ttu-id="7acff-118">İsteğe bağlı olarak, belirli bir hizmet için geçerli kullanıcı veya **Hizmet hesabı** için kullanıcı **hesabımı** seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7acff-118">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7acff-119">Aygıtınızın yöneticisi değilseniz, sertifikaları yalnızca kullanıcı hesabınız için yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7acff-119">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="7acff-120">Bilgisayarı **Seç** penceresinde, **Yerel bilgisayarı** seçili bırakın ve ardından **Bitir'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="7acff-120">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="7acff-121">Ekle **veya Kaldır** penceresinde **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="7acff-121">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Sertifika ekleme ekleme](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="7acff-123">İsteğe bağlı: **Dosya** menüsünden, MMC konsol dosyasını daha sonra kullanmak üzere kaydetmek için **Kaydet** veya **Kaydet'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="7acff-123">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="7acff-124">Sertifikalarınızı MMC snap-in'de görüntülemek için sol bölmede **Konsol Kökü'nü** seçin ve **ardından Sertifikaları (Yerel Bilgisayar)** genişletin.</span><span class="sxs-lookup"><span data-stu-id="7acff-124">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="7acff-125">Her sertifika türü için dizin listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7acff-125">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="7acff-126">Her sertifika dizininden, sertifikalarını görüntüleyebilir, dışa aktarabilir, içe aktarabilir ve silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7acff-126">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="7acff-127">Sertifika Yöneticisi aracıyla sertifikaları görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7acff-127">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="7acff-128">Sertifika Yöneticisi aracını kullanarak sertifikaları görüntüleyebilir, dışa aktarabilir, içe aktarabilir ve silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7acff-128">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="7acff-129">Yerel aygıtın sertifikalarını görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="7acff-129">To view certificates for the local device</span></span>

1. <span data-ttu-id="7acff-130">**Başlat** menüsünden **Çalıştır'ı** seçin ve *ardından certlm.msc'yi*girin.</span><span class="sxs-lookup"><span data-stu-id="7acff-130">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span>

    <span data-ttu-id="7acff-131">Yerel aygıt için Sertifika Yöneticisi aracı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7acff-131">The Certificate Manager tool for the local device appears.</span></span>
  
2. <span data-ttu-id="7acff-132">Sertifikalarınızı görüntülemek için, sol bölmedeki **Sertifikalar - Yerel Bilgisayar** altında, görüntülemek istediğiniz sertifika türüiçin dizini genişletin.</span><span class="sxs-lookup"><span data-stu-id="7acff-132">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="7acff-133">Geçerli kullanıcının sertifikalarını görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="7acff-133">To view certificates for the current user</span></span>

1. <span data-ttu-id="7acff-134">**Başlat** menüsünden **Çalıştır'ı** seçin ve ardından *certmgr.msc'yi*girin.</span><span class="sxs-lookup"><span data-stu-id="7acff-134">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span>

    <span data-ttu-id="7acff-135">Geçerli kullanıcı için Sertifika Yöneticisi aracı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7acff-135">The Certificate Manager tool for the current user appears.</span></span>
  
2. <span data-ttu-id="7acff-136">Sertifikalarınızı görüntülemek **için, Sertifikalar altında - Sol** bölmedeki Geçerli Kullanıcı, görüntülemek istediğiniz sertifika türüiçin dizini genişletin.</span><span class="sxs-lookup"><span data-stu-id="7acff-136">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="7acff-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7acff-137">See also</span></span>

- [<span data-ttu-id="7acff-138">Sertifikalarla çalışma</span><span class="sxs-lookup"><span data-stu-id="7acff-138">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="7acff-139">Nasıl kullanılır: Geliştirme sırasında kullanılmak üzere geçici sertifikalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="7acff-139">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="7acff-140">Nasıl yapılır: Sertifikanın parmak izini alma</span><span class="sxs-lookup"><span data-stu-id="7acff-140">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
