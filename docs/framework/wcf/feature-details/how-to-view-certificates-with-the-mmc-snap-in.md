---
title: 'Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme'
description: Güvenli bir WCF istemcisi veya hizmeti bir sertifikayı kimlik bilgisi olarak kullanabilir. MMC eklentisini kullanarak inceleyebileceğiniz sertifika depolarının türleri hakkında bilgi edinin.
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: e63034e48ae836f67f89b454829f7196c94610cd
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246681"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="21fd7-104">Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme</span><span class="sxs-lookup"><span data-stu-id="21fd7-104">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="21fd7-105">Güvenli bir istemci veya hizmet oluşturduğunuzda kimlik bilgisi olarak bir [sertifika](working-with-certificates.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21fd7-105">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="21fd7-106">Örneğin, ortak bir kimlik bilgisi türü, yöntemiyle oluşturduğunuz X. 509.952 sertifikasıdır <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="21fd7-106">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="21fd7-107">Windows sistemlerinde Microsoft Yönetim Konsolu (MMC) ile inceleyebileceğiniz üç farklı türde sertifika deposu vardır:</span><span class="sxs-lookup"><span data-stu-id="21fd7-107">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="21fd7-108">Yerel bilgisayar: mağaza cihaz için yereldir ve cihazdaki tüm kullanıcılar için geneldir.</span><span class="sxs-lookup"><span data-stu-id="21fd7-108">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="21fd7-109">Geçerli Kullanıcı: mağaza, cihazdaki geçerli kullanıcı hesabına yereldir.</span><span class="sxs-lookup"><span data-stu-id="21fd7-109">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="21fd7-110">Hizmet hesabı: mağaza, cihazdaki belirli bir hizmette yereldir.</span><span class="sxs-lookup"><span data-stu-id="21fd7-110">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="21fd7-111">MMC ek bileşenindeki sertifikaları görüntüleme</span><span class="sxs-lookup"><span data-stu-id="21fd7-111">View certificates in the MMC snap-in</span></span>

<span data-ttu-id="21fd7-112">Aşağıdaki yordam, uygun bir sertifikayı bulmak için yerel cihazınızdaki mağazaların nasıl inceleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="21fd7-112">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span>
  
1. <span data-ttu-id="21fd7-113">**Başlat** menüsünden **Çalıştır** ' ı seçin ve ardından *MMC*' yi girin.</span><span class="sxs-lookup"><span data-stu-id="21fd7-113">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span>

    <span data-ttu-id="21fd7-114">MMC görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21fd7-114">The MMC appears.</span></span>
  
2. <span data-ttu-id="21fd7-115">**Dosya** menüsünde, **ek bileşen Ekle/Kaldır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="21fd7-115">From the **File** menu, select **Add/Remove Snap In**.</span></span>

    <span data-ttu-id="21fd7-116">**Ek bileşenleri Ekle veya Kaldır** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21fd7-116">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="21fd7-117">**Kullanılabilir ek bileşenler** listesinden **Sertifikalar**' ı seçin ve **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="21fd7-117">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Sertifika ek bileşeni ekleme](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="21fd7-119">**Sertifikalar ek bileşeni** penceresinde **bilgisayar hesabı**' nı seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="21fd7-119">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span>
  
    <span data-ttu-id="21fd7-120">İsteğe bağlı olarak, belirli bir hizmet için geçerli kullanıcı veya **hizmet hesabı** için **Kullanıcı hesabımı** seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21fd7-120">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="21fd7-121">Cihazınız için yönetici değilseniz yalnızca Kullanıcı hesabınız için sertifikaları yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21fd7-121">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="21fd7-122">**Bilgisayar Seç** penceresinde, **Yerel bilgisayar** seçili bırakın ve **son**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="21fd7-122">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="21fd7-123">**Ek bileşen Ekle veya Kaldır** penceresinde **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="21fd7-123">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Sertifika ek bileşeni ekleme](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="21fd7-125">İsteğe bağlı: **Dosya** menüsünde, daha sonra kullanmak üzere MMC konsol dosyasını kaydetmek için **Kaydet** veya **farklı kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="21fd7-125">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="21fd7-126">MMC ek bileşeninde sertifikalarınızı görüntülemek için sol bölmedeki **konsol kökü** ' nü seçin ve ardından **Sertifikalar (yerel bilgisayar)**' ı genişletin.</span><span class="sxs-lookup"><span data-stu-id="21fd7-126">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="21fd7-127">Her sertifika türü için dizinlerin listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21fd7-127">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="21fd7-128">Her bir sertifika dizininden sertifikalarını görüntüleyebilir, dışarı aktarabilir, içeri aktarabilir ve silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21fd7-128">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="21fd7-129">Sertifika Yöneticisi aracı ile sertifikaları görüntüleme</span><span class="sxs-lookup"><span data-stu-id="21fd7-129">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="21fd7-130">Sertifikaları, Sertifika Yöneticisi aracını kullanarak da görüntüleyebilir, dışarı aktarabilir, içeri aktarabilir ve silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21fd7-130">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="21fd7-131">Yerel cihaz için sertifikaları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="21fd7-131">To view certificates for the local device</span></span>

1. <span data-ttu-id="21fd7-132">**Başlat** menüsünden **Çalıştır** ' ı seçin ve ardından *Certlm. msc*yazın.</span><span class="sxs-lookup"><span data-stu-id="21fd7-132">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span>

    <span data-ttu-id="21fd7-133">Yerel cihaz için Sertifika Yöneticisi aracı görünür.</span><span class="sxs-lookup"><span data-stu-id="21fd7-133">The Certificate Manager tool for the local device appears.</span></span>
  
2. <span data-ttu-id="21fd7-134">Sertifikalarınızı görüntülemek için, sol bölmedeki **Sertifikalar-Yerel bilgisayar** altında, görüntülemek istediğiniz sertifika türü için dizini genişletin.</span><span class="sxs-lookup"><span data-stu-id="21fd7-134">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="21fd7-135">Geçerli kullanıcının sertifikalarını görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="21fd7-135">To view certificates for the current user</span></span>

1. <span data-ttu-id="21fd7-136">**Başlat** menüsünden **Çalıştır** ' ı seçin ve ardından *certmgr. msc*yazın.</span><span class="sxs-lookup"><span data-stu-id="21fd7-136">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span>

    <span data-ttu-id="21fd7-137">Geçerli Kullanıcı için Sertifika Yöneticisi aracı görünür.</span><span class="sxs-lookup"><span data-stu-id="21fd7-137">The Certificate Manager tool for the current user appears.</span></span>
  
2. <span data-ttu-id="21fd7-138">Sertifikalarınızı görüntülemek için Sertifikalar ' ın altında, sol bölmedeki **Geçerli Kullanıcı** ' nın altında, görüntülemek istediğiniz sertifika türü için dizini genişletin.</span><span class="sxs-lookup"><span data-stu-id="21fd7-138">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="21fd7-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21fd7-139">See also</span></span>

- [<span data-ttu-id="21fd7-140">Sertifikalarla çalışma</span><span class="sxs-lookup"><span data-stu-id="21fd7-140">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="21fd7-141">Nasıl yapılır: geliştirme sırasında kullanılmak üzere geçici sertifikalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="21fd7-141">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="21fd7-142">Nasıl yapılır: bir sertifikanın parmak izini alma</span><span class="sxs-lookup"><span data-stu-id="21fd7-142">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
