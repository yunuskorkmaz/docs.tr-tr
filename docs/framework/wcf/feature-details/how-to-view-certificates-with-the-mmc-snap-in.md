---
title: 'Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 72fd6a1be2f33e1bfeb08fd43f3436627ee842e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521588"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="66e32-102">Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme</span><span class="sxs-lookup"><span data-stu-id="66e32-102">How to: View Certificates with the MMC Snap-in</span></span>
<span data-ttu-id="66e32-103">Ortak bir kimlik bilgisi türünü X.509 sertifikasıdır.</span><span class="sxs-lookup"><span data-stu-id="66e32-103">A common type of credential is the X.509 certificate.</span></span> <span data-ttu-id="66e32-104">Güvenli Hizmetleri veya istemciler oluştururken, bir sertifika yöntemleri kullanarak istemci veya hizmet kimlik bilgisi olarak kullanılabilir belirtebilirsiniz <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="66e32-104">When creating secure services or clients, you can specify a certificate be used as the client or service credential by using methods such as the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="66e32-105">Yöntemi, sertifikanın depolandığı deponun ve sertifikasını ararken kullanmak için bir değer gibi çeşitli parametreler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="66e32-105">The method requires various parameters, such as the store where the certificate is stored and a value to use when searching for the certificate.</span></span> <span data-ttu-id="66e32-106">Aşağıdaki yordam bir bilgisayarda uygun bir sertifika bulmak için depoları incelemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="66e32-106">The following procedure demonstrates how to examine the stores on a computer to find an appropriate certificate.</span></span> <span data-ttu-id="66e32-107">Sertifika parmak izi bulma örneği için bkz: [nasıl yapılır: Bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="66e32-107">For an example of finding the certificate thumbprint, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="66e32-108">Sertifikalar MMC ek bileşeninde görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="66e32-108">To view certificates in the MMC snap-in</span></span>  
  
1.  <span data-ttu-id="66e32-109">Bir komut istemi penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="66e32-109">Open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="66e32-110">Tür `mmc` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="66e32-110">Type `mmc` and press the ENTER key.</span></span> <span data-ttu-id="66e32-111">Yerel makine deposuna sertifikaları görüntülemek için yönetici rolünde olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="66e32-111">Note that to view certificates in the local machine store, you must be in the Administrator role.</span></span>  
  
3.  <span data-ttu-id="66e32-112">Üzerinde **dosya** menüsünde tıklatın **Ekle/Kaldır ek bileşen içinde**.</span><span class="sxs-lookup"><span data-stu-id="66e32-112">On the **File** menu, click **Add/Remove Snap In**.</span></span>  
  
4.  <span data-ttu-id="66e32-113">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="66e32-113">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="66e32-114">İçinde **tek başına ek eklentisi** iletişim kutusunda **sertifikaları**.</span><span class="sxs-lookup"><span data-stu-id="66e32-114">In the **Add Standalone Snap-in** dialog box, select **Certificates**.</span></span>  
  
6.  <span data-ttu-id="66e32-115">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="66e32-115">Click **Add**.</span></span>  
  
7.  <span data-ttu-id="66e32-116">İçinde **Sertifikalar ek bileşenini** iletişim kutusunda **bilgisayar hesabı** tıklatıp **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="66e32-116">In the **Certificates snap-in** dialog box, select **Computer account** and click **Next**.</span></span> <span data-ttu-id="66e32-117">İsteğe bağlı olarak seçebileceğiniz **My kullanıcı hesabı** veya **hizmet hesabı**.</span><span class="sxs-lookup"><span data-stu-id="66e32-117">Optionally, you can select **My User account** or **Service account**.</span></span> <span data-ttu-id="66e32-118">Bilgisayarın Yönetici değilseniz, yalnızca kullanıcı hesabınız için sertifikaları yönetebilir.</span><span class="sxs-lookup"><span data-stu-id="66e32-118">If you are not an administrator of the computer, you can manage certificates only for your user account.</span></span>  
  
8.  <span data-ttu-id="66e32-119">İçinde **Bilgisayar Seç** iletişim kutusu, tıklayın **son**.</span><span class="sxs-lookup"><span data-stu-id="66e32-119">In the **Select Computer** dialog box, click **Finish**.</span></span>  
  
9. <span data-ttu-id="66e32-120">İçinde **tek başına ek eklentisi** iletişim kutusu, tıklayın **Kapat**.</span><span class="sxs-lookup"><span data-stu-id="66e32-120">In the **Add Standalone Snap-in** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="66e32-121">Üzerinde **Ekle/Kaldır ek bileşenini** iletişim kutusu, tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="66e32-121">On the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="66e32-122">İçinde **konsol kökü** penceresinde tıklayın **sertifikalar (yerel bilgisayar)** sertifikayı görüntülemek için bilgisayar için depolar.</span><span class="sxs-lookup"><span data-stu-id="66e32-122">In the **Console Root** window, click **Certificates (Local Computer)** to view the certificate stores for the computer.</span></span>  
  
12. <span data-ttu-id="66e32-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="66e32-123">Optional.</span></span> <span data-ttu-id="66e32-124">Hesabınız için sertifikaları görüntülemek için 3-6 adımlarını yineleyin.</span><span class="sxs-lookup"><span data-stu-id="66e32-124">To view certificates for your account, repeat steps 3 to 6.</span></span> <span data-ttu-id="66e32-125">Yerne 7. adımda **bilgisayar hesabı**, tıklayın **My kullanıcı hesabı** 8-10 adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="66e32-125">In step 7, instead of selecting **Computer account**, click **My User account** and repeat steps 8 to 10.</span></span>  
  
13. <span data-ttu-id="66e32-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="66e32-126">Optional.</span></span> <span data-ttu-id="66e32-127">Üzerinde **dosya** menüsünde tıklatın **Kaydet** veya **Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="66e32-127">On the **File** menu, click **Save** or **Save As**.</span></span> <span data-ttu-id="66e32-128">Daha sonra yeniden kullanmak için konsol dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="66e32-128">Save the console file for later reuse.</span></span>  
  
## <a name="viewing-certificates-with-internet-explorer"></a><span data-ttu-id="66e32-129">Internet Explorer ile sertifikaları görüntüleme</span><span class="sxs-lookup"><span data-stu-id="66e32-129">Viewing Certificates with Internet Explorer</span></span>  
 <span data-ttu-id="66e32-130">Da görüntüleyebilir, dışarı aktarma almak ve Internet Explorer'ı kullanarak sertifikaları silin.</span><span class="sxs-lookup"><span data-stu-id="66e32-130">You can also view, export, import, and delete certificates by using Internet Explorer.</span></span>  
  
#### <a name="to-view-certificates-with-internet-explorer"></a><span data-ttu-id="66e32-131">Internet Explorer ile sertifikaları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="66e32-131">To view certificates with Internet Explorer</span></span>  
  
1.  <span data-ttu-id="66e32-132">Internet Explorer'ı tıklatın **Araçları**, ardından **Internet Seçenekleri** görüntülenecek **Internet Seçenekleri** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="66e32-132">In Internet Explorer, click **Tools**, then click **Internet Options** to display the **Internet Options** dialog box.</span></span>  
  
2.  <span data-ttu-id="66e32-133">Tıklayın **içerik** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="66e32-133">Click the **Content** tab.</span></span>  
  
3.  <span data-ttu-id="66e32-134">Altında **sertifikaları**, tıklayın **sertifikaları**.</span><span class="sxs-lookup"><span data-stu-id="66e32-134">Under **Certificates**, click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="66e32-135">Herhangi bir sertifika ayrıntılarını görüntülemek için sertifikayı seçin ve tıklayın **görünümü**.</span><span class="sxs-lookup"><span data-stu-id="66e32-135">To view details of any certificate, select the certificate and click **View**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e32-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66e32-136">See also</span></span>
- [<span data-ttu-id="66e32-137">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="66e32-137">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="66e32-138">Nasıl yapılır: Geliştirme sırasında kullanmak için geçici sertifikalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="66e32-138">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="66e32-139">Nasıl yapılır: Bir sertifikanın parmak izini alma</span><span class="sxs-lookup"><span data-stu-id="66e32-139">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
