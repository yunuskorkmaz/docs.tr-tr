---
title: "Nasıl yapılır: MMC Ek Bileşeni ile Sertifikaları Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 43925a301d4f0d2ca1a852912255be49dd330ae5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="1bf0d-102">Nasıl yapılır: MMC Ek Bileşeni ile Sertifikaları Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1bf0d-102">How to: View Certificates with the MMC Snap-in</span></span>
<span data-ttu-id="1bf0d-103">Bir ortak kimlik bilgisi X.509 sertifikası türüdür.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-103">A common type of credential is the X.509 certificate.</span></span> <span data-ttu-id="1bf0d-104">Güvenli Hizmetleri veya istemcileri oluştururken, bir sertifika, istemci veya hizmet kimlik bilgisi olarak yöntemleri kullanarak kullanılabilir belirtebilirsiniz <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-104">When creating secure services or clients, you can specify a certificate be used as the client or service credential by using methods such as the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="1bf0d-105">Yöntemi, sertifikanın depolandığı deposu ve sertifika için ararken kullanmak için bir değer gibi çeşitli parametreleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-105">The method requires various parameters, such as the store where the certificate is stored and a value to use when searching for the certificate.</span></span> <span data-ttu-id="1bf0d-106">Aşağıdaki yordam, uygun bir sertifika bulmak için bir bilgisayarda depoları incelemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-106">The following procedure demonstrates how to examine the stores on a computer to find an appropriate certificate.</span></span> <span data-ttu-id="1bf0d-107">Sertifika parmak izini bulma örneği için bkz: [nasıl yapılır: bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="1bf0d-107">For an example of finding the certificate thumbprint, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="1bf0d-108">MMC ek bileşeninde sertifikaları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="1bf0d-108">To view certificates in the MMC snap-in</span></span>  
  
1.  <span data-ttu-id="1bf0d-109">Bir komut istemi penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-109">Open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="1bf0d-110">Tür `mmc` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-110">Type `mmc` and press the ENTER key.</span></span> <span data-ttu-id="1bf0d-111">Yerel makine deposunda sertifikaları görüntülemek için yönetici rolünde olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-111">Note that to view certificates in the local machine store, you must be in the Administrator role.</span></span>  
  
3.  <span data-ttu-id="1bf0d-112">Üzerinde **dosya** menüsünde tıklatın **Ekle/Kaldır ek bileşenini**.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-112">On the **File** menu, click **Add/Remove Snap In**.</span></span>  
  
4.  <span data-ttu-id="1bf0d-113">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-113">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="1bf0d-114">İçinde **tek başına ek bileşen Ekle alanında** iletişim kutusunda **Sertifikalar**.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-114">In the **Add Standalone Snap-in** dialog box, select **Certificates**.</span></span>  
  
6.  <span data-ttu-id="1bf0d-115">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-115">Click **Add**.</span></span>  
  
7.  <span data-ttu-id="1bf0d-116">İçinde **Sertifikalar ek bileşenini** iletişim kutusunda **bilgisayar hesabı** tıklatıp **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-116">In the **Certificates snap-in** dialog box, select **Computer account** and click **Next**.</span></span> <span data-ttu-id="1bf0d-117">İsteğe bağlı olarak seçebileceğiniz **My kullanıcı hesabı** veya **hizmet hesabı**.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-117">Optionally, you can select **My User account** or **Service account**.</span></span> <span data-ttu-id="1bf0d-118">Bilgisayarın yöneticisi değilse, yalnızca kullanıcı hesabınız için sertifikaları yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-118">If you are not an administrator of the computer, you can manage certificates only for your user account.</span></span>  
  
8.  <span data-ttu-id="1bf0d-119">İçinde **Bilgisayar Seç** iletişim kutusu, tıklatın **son**.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-119">In the **Select Computer** dialog box, click **Finish**.</span></span>  
  
9. <span data-ttu-id="1bf0d-120">İçinde **tek başına ek bileşen Ekle alanında** iletişim kutusu, tıklatın **Kapat**.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-120">In the **Add Standalone Snap-in** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="1bf0d-121">Üzerinde **Ekle/Kaldır ek bileşenini** iletişim kutusu, tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-121">On the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="1bf0d-122">İçinde **konsol kökü** penceresinde tıklatın **sertifikalar (yerel bilgisayar)** sertifikayı görüntülemek için bilgisayar için depolar.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-122">In the **Console Root** window, click **Certificates (Local Computer)** to view the certificate stores for the computer.</span></span>  
  
12. <span data-ttu-id="1bf0d-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-123">Optional.</span></span> <span data-ttu-id="1bf0d-124">Hesabınıza ilişkin sertifikaları görüntülemek için 3-6 adımlarını yineleyin.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-124">To view certificates for your account, repeat steps 3 to 6.</span></span> <span data-ttu-id="1bf0d-125">Seçmek yerine 7. adımda **bilgisayar hesabı**, tıklatın **My kullanıcı hesabı** ve 8-10 adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-125">In step 7, instead of selecting **Computer account**, click **My User account** and repeat steps 8 to 10.</span></span>  
  
13. <span data-ttu-id="1bf0d-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-126">Optional.</span></span> <span data-ttu-id="1bf0d-127">Üzerinde **dosya** menüsünde tıklatın **kaydetmek** veya **Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-127">On the **File** menu, click **Save** or **Save As**.</span></span> <span data-ttu-id="1bf0d-128">Daha sonra yeniden kullanmak için konsol dosyasına kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-128">Save the console file for later reuse.</span></span>  
  
## <a name="viewing-certificates-with-internet-explorer"></a><span data-ttu-id="1bf0d-129">Internet Explorer ile sertifikaları görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1bf0d-129">Viewing Certificates with Internet Explorer</span></span>  
 <span data-ttu-id="1bf0d-130">Da görüntüleyebilir, dışarı aktarmak ve Internet Explorer kullanarak sertifikaları silmek.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-130">You can also view, export, import, and delete certificates by using Internet Explorer.</span></span>  
  
#### <a name="to-view-certificates-with-internet-explorer"></a><span data-ttu-id="1bf0d-131">Internet Explorer ile sertifikaları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="1bf0d-131">To view certificates with Internet Explorer</span></span>  
  
1.  <span data-ttu-id="1bf0d-132">Internet Explorer'daki **Araçları**, ardından **Internet Seçenekleri** görüntülemek için **Internet Seçenekleri** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-132">In Internet Explorer, click **Tools**, then click **Internet Options** to display the **Internet Options** dialog box.</span></span>  
  
2.  <span data-ttu-id="1bf0d-133">Tıklatın **içerik** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-133">Click the **Content** tab.</span></span>  
  
3.  <span data-ttu-id="1bf0d-134">Altında **sertifikaları**, tıklatın **Sertifikalar**.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-134">Under **Certificates**, click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="1bf0d-135">Herhangi bir sertifika ayrıntılarını görüntüleyin, sertifikayı seçin ve ' **Görünüm**.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-135">To view details of any certificate, select the certificate and click **View**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf0d-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1bf0d-136">See Also</span></span>  
 [<span data-ttu-id="1bf0d-137">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="1bf0d-137">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="1bf0d-138">Nasıl yapılır: geliştirme sırasında kullanmak için geçici sertifikalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bf0d-138">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [<span data-ttu-id="1bf0d-139">Nasıl yapılır: bir sertifikanın parmak izini alma</span><span class="sxs-lookup"><span data-stu-id="1bf0d-139">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
