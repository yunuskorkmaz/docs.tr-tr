---
title: 'Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 69f79b64250ff46524e7b4720d13351774875a3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167511"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="a2d5c-102">Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a2d5c-102">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="a2d5c-103">Güvenli istemci veya hizmet oluştururken kullanabileceğiniz bir [sertifika](working-with-certificates.md) kimlik bilgisi olarak.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-103">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="a2d5c-104">Örneğin, ortak bir kimlik bilgisi türü ile oluşturduğunuz X.509 sertifikası olan <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-104">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span> 

<span data-ttu-id="a2d5c-105">Microsoft Yönetim Konsolu (MMC) ile Windows sistemlerinde inceleyebilirsiniz sertifika depolarını üç farklı türü vardır:</span><span class="sxs-lookup"><span data-stu-id="a2d5c-105">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="a2d5c-106">Yerel bilgisayar: Yerel cihaz ve cihazdaki tüm kullanıcılar için küresel deposudur.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-106">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="a2d5c-107">Geçerli kullanıcı: Cihazdaki geçerli kullanıcı hesabı için yerel deposudur.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-107">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="a2d5c-108">Hizmet hesabı: Belirli bir hizmete cihazdaki yerel deposudur.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-108">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="a2d5c-109">MMC ek bileşeninde sertifikaları görüntüle</span><span class="sxs-lookup"><span data-stu-id="a2d5c-109">View certificates in the MMC snap-in</span></span> 

<span data-ttu-id="a2d5c-110">Aşağıdaki yordam, uygun bir sertifika bulmak için yerel cihazınıza depoları incelemek nasıl göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="a2d5c-110">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span> 
  
1. <span data-ttu-id="a2d5c-111">Seçin **çalıştırma** gelen **Başlat** menüsünde ve enter *mmc*.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-111">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span> 

    <span data-ttu-id="a2d5c-112">MMC açılır.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-112">The MMC appears.</span></span> 
  
2. <span data-ttu-id="a2d5c-113">Gelen **dosya** menüsünde **Ekle/Kaldır ek bileşen içinde**.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-113">From the **File** menu, select **Add/Remove Snap In**.</span></span> 
    
    <span data-ttu-id="a2d5c-114">**Ek bileşenler Ekle / Kaldır** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-114">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="a2d5c-115">Gelen **kullanılabilir ek bileşenler** listesinde **sertifikaları**, ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-115">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Sertifika ek bileşenini Ekle](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="a2d5c-117">İçinde **Sertifikalar ek bileşenini** penceresinde **bilgisayar hesabı**ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-117">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span> 
  
    <span data-ttu-id="a2d5c-118">İsteğe bağlı olarak seçebileceğiniz **kullanıcı hesabım** geçerli kullanıcı için ya da **hizmet hesabı** belirli bir hizmet için.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-118">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="a2d5c-119">Bir yöneticinin Cihazınızda siz değilseniz, yalnızca kullanıcı hesabınız için sertifikaları yönetebilir.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-119">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="a2d5c-120">İçinde **Bilgisayar Seç** penceresinde bırakın **yerel bilgisayar** seçili ve ardından **son**.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-120">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="a2d5c-121">İçinde **Ekle veya Kaldır ek bileşenini** penceresinde **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-121">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Sertifika ek bileşenini Ekle](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="a2d5c-123">İsteğe bağlı: Gelen **dosya** menüsünde **Kaydet** veya **Kaydet** daha sonra kullanmak için MMC konsolu dosyasını kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-123">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="a2d5c-124">MMC ek bileşeninde, sertifikaları görüntülemek için seçin **konsol kökü** sol bölmede genişletin **sertifikalar (yerel bilgisayar)**.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-124">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="a2d5c-125">Her sertifika türünün dizinlerinin listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-125">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="a2d5c-126">Her sertifika dizinden görüntülemek, dışarı aktarma, alma ve sertifikalarını silin.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-126">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="a2d5c-127">Sertifika Yöneticisi Aracı ile sertifikaları görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a2d5c-127">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="a2d5c-128">Da görüntüleyebilir, dışarı aktarma almak ve Sertifika Yöneticisi aracı kullanarak sertifikaları silin.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-128">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="a2d5c-129">Yerel cihaz sertifikalarını görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="a2d5c-129">To view certificates for the local device</span></span>

1. <span data-ttu-id="a2d5c-130">Seçin **çalıştırma** gelen **Başlat** menüsünde ve enter *certlm.msc*.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-130">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span> 

    <span data-ttu-id="a2d5c-131">Sertifika Yöneticisi Aracı için yerel cihaz görünür.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-131">The Certificate Manager tool for the local device appears.</span></span> 
  
2. <span data-ttu-id="a2d5c-132">Sertifikalarınızı, altında görüntülemek için **sertifikalar - yerel bilgisayar** sol bölmede, görüntülemek istediğiniz sertifika türü için dizine genişletin.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-132">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="a2d5c-133">Geçerli kullanıcının sertifikalarını görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="a2d5c-133">To view certificates for the current user</span></span>

1. <span data-ttu-id="a2d5c-134">Seçin **çalıştırma** gelen **Başlat** menüsünde ve enter *certmgr.msc*.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-134">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span> 

    <span data-ttu-id="a2d5c-135">Geçerli kullanıcı için Sertifika Yöneticisi Aracı görünür.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-135">The Certificate Manager tool for the current user appears.</span></span> 
  
2. <span data-ttu-id="a2d5c-136">Sertifikalarınızı, altında görüntülemek için **Sertifikalar - Geçerli kullanıcı** sol bölmede, görüntülemek istediğiniz sertifika türü için dizine genişletin.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-136">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2d5c-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2d5c-137">See also</span></span>

- [<span data-ttu-id="a2d5c-138">Sertifikalarla çalışma</span><span class="sxs-lookup"><span data-stu-id="a2d5c-138">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="a2d5c-139">Nasıl yapılır: Geliştirme sırasında kullanmak için geçici sertifikalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="a2d5c-139">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="a2d5c-140">Nasıl yapılır: Bir sertifikanın parmak izini alma</span><span class="sxs-lookup"><span data-stu-id="a2d5c-140">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
