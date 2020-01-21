---
title: Windows Communication Foundation Gizlilik Bilgileri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: 7bd56d44eeb6af70b94cdde77d48e917ef8afb9a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347790"
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="c5e80-102">Windows Communication Foundation Gizlilik Bilgileri</span><span class="sxs-lookup"><span data-stu-id="c5e80-102">Windows Communication Foundation Privacy Information</span></span>
<span data-ttu-id="c5e80-103">Microsoft, son kullanıcıların gizliliğini korumayı taahhüt etmektedir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-103">Microsoft is committed to protecting end-users' privacy.</span></span> <span data-ttu-id="c5e80-104">Windows Communication Foundation (WCF), sürüm 3,0 kullanarak bir uygulama oluşturduğunuzda, uygulamanız son kullanıcılarınızın gizliliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-104">When you build an application using Windows Communication Foundation (WCF), version 3.0, your application may impact your end-users' privacy.</span></span> <span data-ttu-id="c5e80-105">Örneğin, uygulamanız kullanıcı iletişim bilgilerini açıkça toplayabilir veya Internet üzerinden Web sitenize bilgi talep edebilir veya gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-105">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="c5e80-106">Uygulamanıza Microsoft teknolojisi eklerseniz, bu teknolojinin gizliliği etkileyebilecek kendi davranışı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-106">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> <span data-ttu-id="c5e80-107">WCF, siz veya son kullanıcı tarafından bize göndermek için seçim yapmadıkça Microsoft 'a herhangi bir bilgi göndermez.</span><span class="sxs-lookup"><span data-stu-id="c5e80-107">WCF does not send any information to Microsoft from your application unless you or the end-user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="c5e80-108">WCF kısaca</span><span class="sxs-lookup"><span data-stu-id="c5e80-108">WCF in Brief</span></span>  
 <span data-ttu-id="c5e80-109">WCF, geliştiricilerin dağıtılmış uygulamalar oluşturmalarına olanak tanıyan Microsoft .NET çerçevesini kullanan dağıtılmış bir mesajlaşma çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-109">WCF is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="c5e80-110">İki uygulama arasında iletilen iletiler, üst bilgi ve gövde bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-110">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="c5e80-111">Üst bilgiler, uygulama tarafından kullanılan hizmetlere bağlı olarak ileti yönlendirme, güvenlik bilgileri, işlemler ve daha fazlasını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-111">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="c5e80-112">İletiler genellikle varsayılan olarak şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-112">Messages are typically encrypted by default.</span></span> <span data-ttu-id="c5e80-113">Tek istisna, güvenli olmayan, eski Web hizmetleriyle kullanılmak üzere tasarlanan `BasicHttpBinding`kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-113">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="c5e80-114">Uygulama Tasarımcısı olarak son tasarımdan siz sorumlusunuz.</span><span class="sxs-lookup"><span data-stu-id="c5e80-114">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="c5e80-115">SOAP gövdesindeki iletiler uygulamaya özgü verileri içerir; Ancak, uygulama tanımlı kişisel bilgiler gibi bu veriler, WCF şifreleme veya gizlilik özellikleri kullanılarak güvenliği sağlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-115">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using WCF encryption or confidentiality features.</span></span> <span data-ttu-id="c5e80-116">Aşağıdaki bölümlerde gizliliği potansiyel olarak etkileyebilecek özellikler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-116">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="c5e80-117">İleti</span><span class="sxs-lookup"><span data-stu-id="c5e80-117">Messaging</span></span>  
 <span data-ttu-id="c5e80-118">Her WCF iletisinde, ileti hedefini belirten ve yanıtın gitmesi gereken bir adres üst bilgisi vardır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-118">Each WCF message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="c5e80-119">Bir uç nokta adresinin adres bileşeni, uç noktasını tanımlayan bir Tekdüzen kaynak tanımlayıcısıdır (URI).</span><span class="sxs-lookup"><span data-stu-id="c5e80-119">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="c5e80-120">Adres bir ağ adresi veya mantıksal adres olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-120">The address can be a network address or a logical address.</span></span> <span data-ttu-id="c5e80-121">Adres, makine adı (ana bilgisayar adı, tam etki alanı adı) ve bir IP adresi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-121">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="c5e80-122">Uç nokta adresi bir genel benzersiz tanımlayıcı (GUID) veya her bir adresi ayırt etmek için kullanılan geçici adresleme için GUID 'lerin bir koleksiyonunu da içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-122">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="c5e80-123">Her ileti, GUID olan bir ileti KIMLIĞI içerir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-123">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="c5e80-124">Bu özellik, WS-Addressing başvuru standardını izler.</span><span class="sxs-lookup"><span data-stu-id="c5e80-124">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="c5e80-125">WCF mesajlaşma katmanı, yerel makineye herhangi bir kişisel bilgi yazmaz.</span><span class="sxs-lookup"><span data-stu-id="c5e80-125">The WCF messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="c5e80-126">Ancak, bir hizmet geliştiricisi bu bilgileri açığa çıkaran bir hizmet (örneğin, bir uç nokta adında bir kişinin adını kullanarak ya da uç noktanın Web 'e kişisel bilgiler dahil) bir hizmet oluşturarsa, kişisel bilgileri ağ düzeyinde yayabilir. Hizmetler açıklaması dili, ancak istemcilerin WSDL 'ye erişmek için HTTPS kullanmasını gerektirmemelidir).</span><span class="sxs-lookup"><span data-stu-id="c5e80-126">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="c5e80-127">Ayrıca bir geliştirici, kişisel bilgiler sunan bir uç noktaya karşı [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) aracını çalıştırıyorsa, aracın çıktısı bu bilgileri içerebilir ve çıkış dosyası yerel sabit diske yazılır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-127">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="c5e80-128">Barındırma</span><span class="sxs-lookup"><span data-stu-id="c5e80-128">Hosting</span></span>  
 <span data-ttu-id="c5e80-129">WCF 'deki barındırma özelliği, uygulamaların isteğe bağlı olarak başlamasını veya birden çok uygulama arasında bağlantı noktası paylaşımını etkinleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-129">The hosting feature in WCF allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="c5e80-130">WCF uygulaması, ASP.NET benzeri Internet Information Services (IIS) içinde barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-130">An WCF application can be hosted in Internet Information Services (IIS), similar to ASP.NET.</span></span>  
  
 <span data-ttu-id="c5e80-131">Barındırma, ağ üzerinde belirli bilgileri açığa çıkarır ve makinede veri bulundurmaz.</span><span class="sxs-lookup"><span data-stu-id="c5e80-131">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="c5e80-132">İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c5e80-132">Message Security</span></span>  
 <span data-ttu-id="c5e80-133">WCF güvenliği, Mesajlaşma uygulamalarına yönelik güvenlik özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-133">WCF security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="c5e80-134">Belirtilen güvenlik işlevleri kimlik doğrulaması ve yetkilendirme içerir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-134">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="c5e80-135">Kimlik doğrulaması, istemciler ve hizmetler arasında kimlik bilgileri geçirerek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-135">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="c5e80-136">Kimlik doğrulaması, aktarım düzeyi güvenlik aracılığıyla veya SOAP ileti düzeyi güvenliği aracılığıyla aşağıdaki gibi olabilir:</span><span class="sxs-lookup"><span data-stu-id="c5e80-136">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
- <span data-ttu-id="c5e80-137">SOAP iletisi güvenliği 'nde kimlik doğrulaması, Kullanıcı adı/parolalar, X. 509.440 sertifikaları, Kerberos biletleri ve SAML belirteçleri gibi kimlik bilgileri aracılığıyla yapılır; bu, verenlere bağlı olarak kişisel bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-137">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
- <span data-ttu-id="c5e80-138">Aktarım güvenliğini kullanarak, kimlik doğrulaması HTTP kimlik doğrulama şemaları (temel, Özet, anlaşma, tümleşik Windows yetkilendirmesi, NTLM, hiçbiri ve anonim) ve form kimlik doğrulaması gibi geleneksel aktarım kimlik doğrulama mekanizmaları aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-138">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="c5e80-139">Kimlik doğrulama, iletişim noktaları arasında kurulan güvenli bir oturumun oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-139">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="c5e80-140">Oturum, güvenlik oturumunun ömrünü sürdüeden bir GUID ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-140">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="c5e80-141">Aşağıdaki tabloda neler olduğu ve nerede tutulduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-141">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="c5e80-142">Veri</span><span class="sxs-lookup"><span data-stu-id="c5e80-142">Data</span></span>|<span data-ttu-id="c5e80-143">Depolama</span><span class="sxs-lookup"><span data-stu-id="c5e80-143">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="c5e80-144">Kullanıcı adı, X. 509.440 sertifikaları, Kerberos belirteçleri ve kimlik bilgilerine yapılan başvurular gibi sunum kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="c5e80-144">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="c5e80-145">Windows sertifika deposu gibi standart Windows kimlik bilgisi yönetim mekanizmaları.</span><span class="sxs-lookup"><span data-stu-id="c5e80-145">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="c5e80-146">Kullanıcı üyeliği bilgileri, örneğin Kullanıcı adları ve parolalar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-146">User membership information, such as usernames and passwords.</span></span>|<span data-ttu-id="c5e80-147">ASP.NET üyelik sağlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="c5e80-147">ASP.NET membership providers.</span></span>|  
|<span data-ttu-id="c5e80-148">Hizmetin istemcilere kimliğini doğrulamak için kullanılan hizmet hakkındaki kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="c5e80-148">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="c5e80-149">Hizmetin uç nokta adresi.</span><span class="sxs-lookup"><span data-stu-id="c5e80-149">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="c5e80-150">Çağıran bilgileri.</span><span class="sxs-lookup"><span data-stu-id="c5e80-150">Caller information.</span></span>|<span data-ttu-id="c5e80-151">Denetim günlükleri.</span><span class="sxs-lookup"><span data-stu-id="c5e80-151">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="c5e80-152">Denetim</span><span class="sxs-lookup"><span data-stu-id="c5e80-152">Auditing</span></span>  
 <span data-ttu-id="c5e80-153">Denetim, kimlik doğrulama ve yetkilendirme olaylarının başarısını ve başarısızlığını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c5e80-153">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="c5e80-154">Denetim kayıtları şu verileri içerir: hizmet URI 'SI, eylem URI 'SI ve arayanın kimliği.</span><span class="sxs-lookup"><span data-stu-id="c5e80-154">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="c5e80-155">Ayrıca Denetim, yönetici ileti günlüğe kaydetme yapılandırmasını değiştirdiğinde (açık veya kapalı), ileti günlüğü, uygulamaya özgü verileri üst bilgilerde ve gövdelerde günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c5e80-155">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="c5e80-156">[!INCLUDE[wxp](../../../includes/wxp-md.md)]için, uygulama olay günlüğüne bir kayıt kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-156">For [!INCLUDE[wxp](../../../includes/wxp-md.md)], a record is logged in the application event log.</span></span> <span data-ttu-id="c5e80-157">Windows Vista ve Windows Server 2003 için güvenlik olay günlüğüne bir kayıt kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-157">For Windows Vista and Windows Server 2003, a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="c5e80-158">İşlemler</span><span class="sxs-lookup"><span data-stu-id="c5e80-158">Transactions</span></span>  
 <span data-ttu-id="c5e80-159">İşlemler özelliği bir WCF uygulamasına işlem hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-159">The transactions feature provides transactional services to a WCF application.</span></span>  
  
 <span data-ttu-id="c5e80-160">İşlem yayma işleminde kullanılan işlem üstbilgileri, GUID 'Leri olan Işlem kimliklerini veya kayıt kimliklerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-160">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="c5e80-161">Işlemler özelliği, işlem durumunu yönetmek için Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) Işlem yöneticisi 'Ni (bir Windows bileşeni) kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-161">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="c5e80-162">Varsayılan olarak, Işlem yöneticileri arasındaki iletişimler şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-162">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="c5e80-163">İşlem yöneticileri, sürekli durumunun bir parçası olarak uç nokta başvurularını, Işlem kimliklerini ve kayıt kimliklerini günlüğe kaydetmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-163">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="c5e80-164">Bu durumun ömrü, Işlem yöneticisinin günlük dosyasının ömrü ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-164">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="c5e80-165">MSDTC hizmeti, bu günlüğün sahibi ve bakımını yapar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-165">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="c5e80-166">Işlemler özelliği, WS-koordinasyon ve WS Atomik Işlem standartları uygular.</span><span class="sxs-lookup"><span data-stu-id="c5e80-166">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="c5e80-167">Güvenilir oturumlar</span><span class="sxs-lookup"><span data-stu-id="c5e80-167">Reliable Sessions</span></span>  
 <span data-ttu-id="c5e80-168">WCF 'de güvenilir oturumlar, aktarım veya aracı arızalarının oluşması durumunda iletilerin aktarılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-168">Reliable sessions in WCF provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="c5e80-169">Bu kişiler, temeldeki taşımanın bağlantısı kesildiğinde (örneğin, kablosuz ağ üzerinde bir TCP bağlantısı) veya bir iletiyi kaybettiğinde (bir HTTP proxy 'si giden veya gelen bir iletiyi bırakırken) iletilerin tam olarak bir kez aktarılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-169">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="c5e80-170">Güvenilir oturumlar Ayrıca iletilerin gönderilme sırasını koruyarak ileti yeniden sıralamasını (çok yollu yönlendirme durumunda olabileceği gibi) de kurtarır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-170">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="c5e80-171">Güvenilir Oturumlar, WS-ReliableMessaging (WS-RM) protokolü kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-171">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="c5e80-172">Bunlar, belirli bir güvenilir oturumla ilişkili tüm iletileri tanımlamak için kullanılan oturum bilgilerini içeren WS-RM üst bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="c5e80-172">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="c5e80-173">Her WS-RM oturumunun bir GUID olan bir tanımlayıcısı vardır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-173">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="c5e80-174">Son kullanıcının makinesinde kişisel bilgi korunmaz.</span><span class="sxs-lookup"><span data-stu-id="c5e80-174">No personal information is retained on the end-user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="c5e80-175">Sıraya alınan kanallar</span><span class="sxs-lookup"><span data-stu-id="c5e80-175">Queued Channels</span></span>  
 <span data-ttu-id="c5e80-176">Kuyruklar iletileri alıcı uygulama adına gönderen uygulamadan depolar ve daha sonra bu iletileri alıcı uygulamasına iletir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-176">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="c5e80-177">Bu kişiler, örneğin, alıcı uygulama geçici olduğunda, uygulamaları almaya yönelik uygulamalar gönderen iletiler aktarımının sağlanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c5e80-177">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> <span data-ttu-id="c5e80-178">WCF, taşıma olarak Microsoft Message Queuing (MSMQ) kullanarak sıraya alma desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-178">WCF provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="c5e80-179">Sıraya alınan kanallar özelliği bir iletiye üst bilgi eklemez.</span><span class="sxs-lookup"><span data-stu-id="c5e80-179">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="c5e80-180">Bunun yerine, uygun Message Queuing ileti özellikleri ayarlanmış Message Queuing bir ileti oluşturur ve iletiyi Message Queuing kuyruğuna koymak için Message Queuing yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-180">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="c5e80-181">Message Queuing, Windows ile birlikte gelen isteğe bağlı bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-181">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="c5e80-182">Kuyruğa alma altyapısı olarak Message Queuing kullandığından, son kullanıcının makinesinde sıraya alınan kanallar özelliği korunmaz.</span><span class="sxs-lookup"><span data-stu-id="c5e80-182">No information is retained on the end-user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="c5e80-183">COM+ Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="c5e80-183">COM+ Integration</span></span>  
 <span data-ttu-id="c5e80-184">Bu özellik, WCF hizmetleriyle uyumlu hizmetler oluşturmak için mevcut COM ve COM+ işlevlerini sarmalanmış.</span><span class="sxs-lookup"><span data-stu-id="c5e80-184">This feature wraps existing COM and COM+ functionality to create services that are compatible with WCF services.</span></span> <span data-ttu-id="c5e80-185">Bu özellik belirli üst bilgileri kullanmaz ve son kullanıcının makinesinde verileri korumaz.</span><span class="sxs-lookup"><span data-stu-id="c5e80-185">This feature does not use specific headers and it does not retain data on the end-user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="c5e80-186">COM hizmeti bilinen adı</span><span class="sxs-lookup"><span data-stu-id="c5e80-186">COM Service Moniker</span></span>  
 <span data-ttu-id="c5e80-187">Bu, standart bir WCF istemcisine yönetilmeyen bir sarmalayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-187">This provides an unmanaged wrapper to a standard WCF client.</span></span> <span data-ttu-id="c5e80-188">Bu özellik, hat üzerinde belirli üst bilgilere sahip değildir ve makinede verileri kalıcı hale getiremez.</span><span class="sxs-lookup"><span data-stu-id="c5e80-188">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="c5e80-189">Eş Kanal</span><span class="sxs-lookup"><span data-stu-id="c5e80-189">Peer Channel</span></span>  
 <span data-ttu-id="c5e80-190">Eş kanal, WCF kullanarak çok taraflı uygulamaların geliştirilmesini mümkün.</span><span class="sxs-lookup"><span data-stu-id="c5e80-190">A peer channel enables development of multiparty applications using WCF.</span></span> <span data-ttu-id="c5e80-191">Çok taraflı mesajlaşma, bir ağ bağlamında meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-191">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="c5e80-192">Kafesler, düğümlerin katılabilme adı tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-192">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="c5e80-193">Eş kanaldaki her düğüm, Kullanıcı tarafından belirtilen bağlantı noktasında bir TCP dinleyicisi oluşturur ve esneklik sağlamak için kafesteki diğer düğümlerle bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-193">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="c5e80-194">Kafesteki diğer düğümlere bağlanmak için, düğümler aynı zamanda dinleyici adresi ve makinenin IP adresleri de dahil olmak üzere, ağ üzerindeki diğer düğümlerle birlikte bazı verileri de değiş tokuş eder.</span><span class="sxs-lookup"><span data-stu-id="c5e80-194">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="c5e80-195">Ağ üzerinden gönderilen iletiler, ileti sızdırma ve izinsiz değişiklik yapılmasını engellemek için gönderiyle ilgili güvenlik bilgilerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-195">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="c5e80-196">Son kullanıcının makinesinde kişisel bilgi depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="c5e80-196">No personal information is stored on the end-user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="c5e80-197">BT uzmanı deneyimi</span><span class="sxs-lookup"><span data-stu-id="c5e80-197">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="c5e80-198">İzleme</span><span class="sxs-lookup"><span data-stu-id="c5e80-198">Tracing</span></span>  
 <span data-ttu-id="c5e80-199">WCF altyapısının tanılama özelliği, aktarım ve hizmet modeli katmanlarından geçen iletileri ve bu iletilerle ilişkili etkinlikleri ve olayları günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c5e80-199">The diagnostics feature of the WCF infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="c5e80-200">Bu özellik varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-200">This feature is turned off by default.</span></span> <span data-ttu-id="c5e80-201">Uygulamanın yapılandırma dosyası kullanılarak etkinleştirilir ve izleme davranışı, çalışma zamanında WCF WMI sağlayıcısı kullanılarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-201">It is enabled using the application’s configuration file and the tracing behavior may be modified using the WCF WMI provider at run time.</span></span> <span data-ttu-id="c5e80-202">Etkinleştirildiğinde, izleme altyapısı, yapılandırılan dinleyicilerine ileti, etkinlik ve işleme olaylarını içeren bir tanılama izlemesi yayar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-202">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="c5e80-203">Çıktının biçimi ve konumu yöneticinin dinleyici yapılandırma seçeneklerine göre belirlenir, ancak genellikle XML biçimli bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-203">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="c5e80-204">Yönetici, izleme dosyalarındaki erişim denetim listesini (ACL) ayarlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="c5e80-204">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="c5e80-205">Özellikle, Windows etkinleştirme sistemi (WAS) tarafından barındırıldığında, yönetici, bu istenmiyorsa, dosyaların ortak sanal kök dizinden sunulmadığından emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-205">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="c5e80-206">İki tür izleme vardır: Ileti günlüğü ve hizmet modeli Tanılama izleme, aşağıdaki bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-206">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="c5e80-207">Her tür kendi izleme kaynağı aracılığıyla yapılandırılır: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> ve <xref:System.ServiceModel>.</span><span class="sxs-lookup"><span data-stu-id="c5e80-207">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="c5e80-208">Bu günlüğe kaydetme izleme kaynaklarından her ikisi de, uygulamada yerel olan verileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-208">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="c5e80-209">İleti Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="c5e80-209">Message Logging</span></span>  
 <span data-ttu-id="c5e80-210">İleti günlüğü izleme kaynağı (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>), yöneticinin sistem üzerinden akan iletileri günlüğe kaydetmeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-210">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="c5e80-211">Yapılandırma sayesinde, Kullanıcı yalnızca tüm iletileri veya ileti üstbilgilerini günlüğe kaydetmek, aktarım ve/veya hizmet modeli katmanlarında günlüğe kaydedilip edilmeyeceğini ve hatalı biçimlendirilmiş iletilerin eklenip eklenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-211">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="c5e80-212">Ayrıca Kullanıcı, hangi iletilerin günlüğe kaydedileceğini kısıtlamak için filtrelemeyi yapılandırabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-212">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="c5e80-213">Varsayılan olarak, ileti günlüğe kaydetme devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-213">By default, message logging is disabled.</span></span> <span data-ttu-id="c5e80-214">Yerel Makine Yöneticisi, uygulama düzeyinde yöneticinin ileti oturumunu açmasını önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-214">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="c5e80-215">Şifrelenmiş ve şifresi çözülmüş Ileti günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="c5e80-215">Encrypted and Decrypted Message Logging</span></span>  
 <span data-ttu-id="c5e80-216">Aşağıdaki koşullarda açıklandığı gibi iletiler günlüğe kaydedilir, şifrelenir veya çözülür.</span><span class="sxs-lookup"><span data-stu-id="c5e80-216">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="c5e80-217">Aktarım günlüğü</span><span class="sxs-lookup"><span data-stu-id="c5e80-217">Transport Logging</span></span>  
 <span data-ttu-id="c5e80-218">Aktarım düzeyinde alınan ve gönderilen iletileri günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c5e80-218">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="c5e80-219">Bu iletiler tüm üst bilgileri içerir ve bu, hatta gönderilirken ve alındığında şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-219">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="c5e80-220">İletiler, Tel gönderilmeden ve alındıkları sırada şifrelenirse, bunlar da şifreli olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-220">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="c5e80-221">Bir güvenlik protokolünün kullanıldığı bir özel durum (https): daha sonra, bu dosyalar, kablo üzerinde şifrelenseler bile gönderilmeden ve alındıktan sonra günlüğe çözülür.</span><span class="sxs-lookup"><span data-stu-id="c5e80-221">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="c5e80-222">Hizmet günlüğü</span><span class="sxs-lookup"><span data-stu-id="c5e80-222">Service Logging</span></span>  
 <span data-ttu-id="c5e80-223">İleti üst bilgisi işleme gerçekleştirildikten sonra, Kullanıcı kodu girildikten hemen önce ve sonra, hizmet modeli düzeyinde alınan veya gönderilen iletileri günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c5e80-223">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="c5e80-224">Bu düzeyde günlüğe kaydedilen iletiler, güvenli olsalar ve kabloda şifrelendiğinden bile çözülür.</span><span class="sxs-lookup"><span data-stu-id="c5e80-224">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="c5e80-225">Hatalı biçimlendirilmiş Ileti günlüğü</span><span class="sxs-lookup"><span data-stu-id="c5e80-225">Malformed Message Logging</span></span>  
 <span data-ttu-id="c5e80-226">WCF altyapısının anlayabileceği veya işleyebileceğini iletileri günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c5e80-226">Logs messages that the WCF infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="c5e80-227">İletiler olduğu gibi kaydedilir, yani şifrelenir veya değildir</span><span class="sxs-lookup"><span data-stu-id="c5e80-227">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="c5e80-228">İletiler, şifresi çözülmüş veya şifrelenmemiş biçimde günlüğe kaydedildiğinde, varsayılan olarak WCF güvenlik anahtarlarını ve bilgileri günlüğe kaydedilmeden önce iletilerden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-228">When messages are logged in decrypted or unencrypted form, by default WCF removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="c5e80-229">Sonraki bölümlerde hangi bilgilerin kaldırıldığı ve ne zaman olduğu açıklanır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-229">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="c5e80-230">Makine Yöneticisi ve uygulama dağıtıcısı, varsayılan davranışı günlük anahtarlarına ve potansiyel olarak kişisel bilgilere değiştirecek şekilde, her ikisi de belirli yapılandırma eylemlerini almalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-230">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="c5e80-231">Şifresi çözülmüş/şifrelenmemiş Iletileri günlüğe kaydederken Ileti başlıklarından kaldırılan bilgiler</span><span class="sxs-lookup"><span data-stu-id="c5e80-231">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="c5e80-232">İletiler, şifresi çözülmüş/şifrelenmemiş biçiminde günlüğe kaydedildiğinde, güvenlik anahtarları ve potansiyel olarak kişisel bilgiler, günlüğe kaydedilmeden önce ileti başlıklarından ve ileti gövdelerinde varsayılan olarak kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-232">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="c5e80-233">Aşağıdaki listede, anahtarların ve potansiyel olarak kişisel bilgilerin hangi WCF tarafından kabul olduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-233">The following list shows what WCF considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="c5e80-234">Kaldırılan anahtarlar:</span><span class="sxs-lookup"><span data-stu-id="c5e80-234">Keys that are removed:</span></span>  
  
 <span data-ttu-id="c5e80-235">xmlns: WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" ve xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" Için \-</span><span class="sxs-lookup"><span data-stu-id="c5e80-235">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="c5e80-236">wst:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="c5e80-236">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="c5e80-237">Wst: entropi</span><span class="sxs-lookup"><span data-stu-id="c5e80-237">wst:Entropy</span></span>  
  
 <span data-ttu-id="c5e80-238">xmlns Için \-: ws& = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" ve xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="c5e80-238">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="c5e80-239">WSS: parola</span><span class="sxs-lookup"><span data-stu-id="c5e80-239">wsse:Password</span></span>  
  
 <span data-ttu-id="c5e80-240">WSS: nonce</span><span class="sxs-lookup"><span data-stu-id="c5e80-240">wsse:Nonce</span></span>  
  
 <span data-ttu-id="c5e80-241">Kaldırılan potansiyel kişisel bilgiler:</span><span class="sxs-lookup"><span data-stu-id="c5e80-241">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="c5e80-242">xmlns Için \-: ws& = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" ve xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="c5e80-242">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="c5e80-243">WSS: Kullanıcı adı</span><span class="sxs-lookup"><span data-stu-id="c5e80-243">wsse:Username</span></span>  
  
 <span data-ttu-id="c5e80-244">WSS: BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="c5e80-244">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="c5e80-245">\- For the items in bold (below) are removed:</span><span class="sxs-lookup"><span data-stu-id="c5e80-245">\- For the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="c5e80-246">\<onaylama</span><span class="sxs-lookup"><span data-stu-id="c5e80-246">\<Assertion</span></span>  
  
 <span data-ttu-id="c5e80-247">MajorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="c5e80-247">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="c5e80-248">MinorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="c5e80-248">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="c5e80-249">AssertionId 'si = "[KIMLIK]"</span><span class="sxs-lookup"><span data-stu-id="c5e80-249">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="c5e80-250">Issuer = "[dize]"</span><span class="sxs-lookup"><span data-stu-id="c5e80-250">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="c5e80-251">IssueInstant = "[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="c5e80-251">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="c5e80-252">\<koşullar NotBefore = "[TarihSaat]" NotOnOrAfter = "[dateTime]" ></span><span class="sxs-lookup"><span data-stu-id="c5e80-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span></span>  
  
 <span data-ttu-id="c5e80-253">\<AudienceRestrictionCondition ></span><span class="sxs-lookup"><span data-stu-id="c5e80-253">\<AudienceRestrictionCondition></span></span>  
  
 <span data-ttu-id="c5e80-254">\<hedef kitle > [Uri]\</Audience > +</span><span class="sxs-lookup"><span data-stu-id="c5e80-254">\<Audience>[uri]\</Audience>+</span></span>  
  
 <span data-ttu-id="c5e80-255">\</AudienceRestrictionCondition > \*</span><span class="sxs-lookup"><span data-stu-id="c5e80-255">\</AudienceRestrictionCondition>\*</span></span>  
  
 <span data-ttu-id="c5e80-256">\<DoNotCacheCondition/> \*</span><span class="sxs-lookup"><span data-stu-id="c5e80-256">\<DoNotCacheCondition />\*</span></span>  
  
 <span data-ttu-id="c5e80-257"><\!--soyut temel tür</span><span class="sxs-lookup"><span data-stu-id="c5e80-257"><\!-- abstract base type</span></span>  
  
 <span data-ttu-id="c5e80-258">\<koşulu/> \*</span><span class="sxs-lookup"><span data-stu-id="c5e80-258">\<Condition />\*</span></span>  
  
 -->  
  
 <span data-ttu-id="c5e80-259">\</Conditions >?</span><span class="sxs-lookup"><span data-stu-id="c5e80-259">\</Conditions>?</span></span>  
  
 <span data-ttu-id="c5e80-260">\<önerileri ></span><span class="sxs-lookup"><span data-stu-id="c5e80-260">\<Advice></span></span>  
  
 <span data-ttu-id="c5e80-261">\<AssertionIDReference > [KIMLIK]\</AssertionIDReference > \*</span><span class="sxs-lookup"><span data-stu-id="c5e80-261">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="c5e80-262">\<onaylama > [onaylama]\</assertion > \*</span><span class="sxs-lookup"><span data-stu-id="c5e80-262">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="c5e80-263">[any] \*</span><span class="sxs-lookup"><span data-stu-id="c5e80-263">[any]\*</span></span>  
  
 <span data-ttu-id="c5e80-264">\</tavsiyeler >?</span><span class="sxs-lookup"><span data-stu-id="c5e80-264">\</Advice>?</span></span>  
  
 <span data-ttu-id="c5e80-265"><\!--soyut temel türler</span><span class="sxs-lookup"><span data-stu-id="c5e80-265"><\!-- Abstract base types</span></span>  
  
 <span data-ttu-id="c5e80-266">\<deyimin/> \*</span><span class="sxs-lookup"><span data-stu-id="c5e80-266">\<Statement />\*</span></span>  
  
 <span data-ttu-id="c5e80-267">\<Subjectdeyimin ></span><span class="sxs-lookup"><span data-stu-id="c5e80-267">\<SubjectStatement></span></span>  
  
 <span data-ttu-id="c5e80-268">\<konu ></span><span class="sxs-lookup"><span data-stu-id="c5e80-268">\<Subject></span></span>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 <span data-ttu-id="c5e80-269">\<SubjectConfirmation ></span><span class="sxs-lookup"><span data-stu-id="c5e80-269">\<SubjectConfirmation></span></span>  
  
 <span data-ttu-id="c5e80-270">\<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +</span><span class="sxs-lookup"><span data-stu-id="c5e80-270">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="c5e80-271">\<SubjectConfirmationData > [any]\</SubjectConfirmationData >?</span><span class="sxs-lookup"><span data-stu-id="c5e80-271">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="c5e80-272">\<DS: KeyInfo >...\</DS: KeyInfo >?</span><span class="sxs-lookup"><span data-stu-id="c5e80-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="c5e80-273">\</SubjectConfirmation >?</span><span class="sxs-lookup"><span data-stu-id="c5e80-273">\</SubjectConfirmation>?</span></span>  
  
 <span data-ttu-id="c5e80-274">\</Subject ></span><span class="sxs-lookup"><span data-stu-id="c5e80-274">\</Subject></span></span>  
  
 <span data-ttu-id="c5e80-275">\</Subjectdeyimin > \*</span><span class="sxs-lookup"><span data-stu-id="c5e80-275">\</SubjectStatement>\*</span></span>  
  
 -->  
  
 <span data-ttu-id="c5e80-276">\<Authenticationdeyimin</span><span class="sxs-lookup"><span data-stu-id="c5e80-276">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="c5e80-277">AuthenticationMethod = "[Uri]"</span><span class="sxs-lookup"><span data-stu-id="c5e80-277">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="c5e80-278">AuthenticationInstant = "[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="c5e80-278">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="c5e80-279">Konusuna</span><span class="sxs-lookup"><span data-stu-id="c5e80-279">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="c5e80-280">< AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="c5e80-280"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="c5e80-281">AuthorityKind = "[QName]"</span><span class="sxs-lookup"><span data-stu-id="c5e80-281">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="c5e80-282">Konum = "[Uri]"</span><span class="sxs-lookup"><span data-stu-id="c5e80-282">Location="[uri]"</span></span>  
  
 <span data-ttu-id="c5e80-283">Binding="[uri]"</span><span class="sxs-lookup"><span data-stu-id="c5e80-283">Binding="[uri]"</span></span>  
  
 />*  
  
 <span data-ttu-id="c5e80-284">\</Authenticationdeyimin > \*</span><span class="sxs-lookup"><span data-stu-id="c5e80-284">\</AuthenticationStatement>\*</span></span>  
  
 <span data-ttu-id="c5e80-285">\<Attributedeyimin ></span><span class="sxs-lookup"><span data-stu-id="c5e80-285">\<AttributeStatement></span></span>  
  
 <span data-ttu-id="c5e80-286">Konusuna</span><span class="sxs-lookup"><span data-stu-id="c5e80-286">[Subject]</span></span>  
  
 <span data-ttu-id="c5e80-287">\<özniteliği</span><span class="sxs-lookup"><span data-stu-id="c5e80-287">\<Attribute</span></span>  
  
 <span data-ttu-id="c5e80-288">AttributeName = "[dize]"</span><span class="sxs-lookup"><span data-stu-id="c5e80-288">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="c5e80-289">AttributeNamespace = "[Uri]"</span><span class="sxs-lookup"><span data-stu-id="c5e80-289">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 <span data-ttu-id="c5e80-290">\</Attribute > +</span><span class="sxs-lookup"><span data-stu-id="c5e80-290">\</Attribute>+</span></span>  
  
 <span data-ttu-id="c5e80-291">\</Attributedeyimin > \*</span><span class="sxs-lookup"><span data-stu-id="c5e80-291">\</AttributeStatement>\*</span></span>  
  
 <span data-ttu-id="c5e80-292">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="c5e80-292">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="c5e80-293">Resource = "[Uri]"</span><span class="sxs-lookup"><span data-stu-id="c5e80-293">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="c5e80-294">Karar = "[reddetme&#124;&#124;belirsiz izin ver]"</span><span class="sxs-lookup"><span data-stu-id="c5e80-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="c5e80-295">Konusuna</span><span class="sxs-lookup"><span data-stu-id="c5e80-295">[Subject]</span></span>  
  
 <span data-ttu-id="c5e80-296">\<Action namespace = "[Uri]" > [dize]\</Action > +</span><span class="sxs-lookup"><span data-stu-id="c5e80-296">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 <span data-ttu-id="c5e80-297">\<bulgu ></span><span class="sxs-lookup"><span data-stu-id="c5e80-297">\<Evidence></span></span>  
  
 <span data-ttu-id="c5e80-298">\<AssertionIDReference > [KIMLIK]\</AssertionIDReference > +</span><span class="sxs-lookup"><span data-stu-id="c5e80-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="c5e80-299">\<onaylama > [onaylama]\</assertion > +</span><span class="sxs-lookup"><span data-stu-id="c5e80-299">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="c5e80-300">/Kanıt > \<?</span><span class="sxs-lookup"><span data-stu-id="c5e80-300">\</Evidence>?</span></span>  
  
 <span data-ttu-id="c5e80-301">\</AuthorizationDecisionStatement > \*</span><span class="sxs-lookup"><span data-stu-id="c5e80-301">\</AuthorizationDecisionStatement>\*</span></span>  
  
 <span data-ttu-id="c5e80-302">\</assertion ></span><span class="sxs-lookup"><span data-stu-id="c5e80-302">\</Assertion></span></span>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="c5e80-303">Şifresi çözülmüş/şifrelenmemiş Iletileri günlüğe kaydederken Ileti gövdelerinde kaldırılan bilgiler</span><span class="sxs-lookup"><span data-stu-id="c5e80-303">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="c5e80-304">Daha önce açıklandığı gibi, WCF anahtarları ve bilinen potansiyel olarak kişisel bilgileri, günlüğe kaydedilen ve şifrelenmemiş iletiler için ileti başlıklarından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-304">As previously described, WCF removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="c5e80-305">Ayrıca, WCF anahtarlar ve bilinen potansiyel kişisel bilgileri, anahtar değişimine dahil olan güvenlik iletilerini açıklayan aşağıdaki listede bulunan gövde öğeleri ve eylemler için ileti gövdesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-305">In addition, WCF removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="c5e80-306">Aşağıdaki ad alanları için:</span><span class="sxs-lookup"><span data-stu-id="c5e80-306">For the following namespaces:</span></span>  
  
 <span data-ttu-id="c5e80-307">xmlns: WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" ve xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (örneğin, kullanılabilir bir eylem yoksa)</span><span class="sxs-lookup"><span data-stu-id="c5e80-307">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="c5e80-308">Bu gövde öğeleri için, anahtar değişimini içeren bilgiler kaldırılır:</span><span class="sxs-lookup"><span data-stu-id="c5e80-308">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="c5e80-309">wst:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="c5e80-309">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="c5e80-310">wst:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="c5e80-310">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="c5e80-311">wst:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="c5e80-311">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="c5e80-312">Bilgiler aşağıdaki eylemlerin her biri için de kaldırılır:</span><span class="sxs-lookup"><span data-stu-id="c5e80-312">Information is also removed for each of the following Actions:</span></span>  
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend`
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="c5e80-313">Uygulamaya özgü üst bilgilerden ve gövde verilerinden hiçbir bilgi kaldırılmadı</span><span class="sxs-lookup"><span data-stu-id="c5e80-313">No Information Is Removed from Application-specific Headers and Body Data</span></span>  
 <span data-ttu-id="c5e80-314">WCF, uygulamaya özgü üst bilgilerde (örneğin, sorgu dizeleri) veya gövde verilerinde (örneğin, kredi kartı numarası) kişisel bilgileri izlemez.</span><span class="sxs-lookup"><span data-stu-id="c5e80-314">WCF does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="c5e80-315">İleti günlüğe kaydetme açık olduğunda, uygulamaya özgü üst bilgiler ve gövde bilgilerindeki kişisel bilgilere günlüklerde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-315">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="c5e80-316">Daha sonra, yapılandırma ve günlük dosyalarındaki ACL 'Leri ayarlamaktan uygulama dağıtıcı sorumludur.</span><span class="sxs-lookup"><span data-stu-id="c5e80-316">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="c5e80-317">Ayrıca, bu bilgilerin görünür olmasını istemediyse günlüğe kaydetmeyi kapatabilir veya günlüğe kaydedildikten sonra bu bilgileri günlük dosyalarından filtreleyebiliriz.</span><span class="sxs-lookup"><span data-stu-id="c5e80-317">He also can turn off logging if he does not want this information to be visible, or he may filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="c5e80-318">Hizmet modeli Izleme</span><span class="sxs-lookup"><span data-stu-id="c5e80-318">Service Model Tracing</span></span>  
 <span data-ttu-id="c5e80-319">Hizmet modeli izleme kaynağı (<xref:System.ServiceModel>), ileti işlemeyle ilgili etkinliklerin ve olayların izlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-319">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="c5e80-320">Bu özellik <xref:System.Diagnostics>.NET Framework tanılama işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-320">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="c5e80-321"><xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> özelliğinde olduğu gibi, konum ve ACL 'SI, .NET Framework uygulama yapılandırma dosyaları kullanılarak Kullanıcı tarafından yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-321">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="c5e80-322">İleti günlüğe kaydetme sırasında, yönetici izlemeyi etkinleştirse de dosya konumu her zaman yapılandırılır; Bu nedenle, yönetici ACL 'yi denetler.</span><span class="sxs-lookup"><span data-stu-id="c5e80-322">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="c5e80-323">İzlemeler, bir ileti kapsamda olduğunda ileti üst bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-323">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="c5e80-324">Önceki bölümde bulunan ileti üstbilgilerinde kişisel bilgilerini gizlemek için de aynı kurallar geçerlidir: daha önce tanımlanan kişisel bilgiler, izlemelerin üst bilgilerinden varsayılan olarak kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-324">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="c5e80-325">Makine Yöneticisi ve uygulama dağıtıcısı, olası kişisel bilgileri günlüğe kaydetmek için yapılandırmayı değiştirmeli.</span><span class="sxs-lookup"><span data-stu-id="c5e80-325">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="c5e80-326">Bununla birlikte, uygulamaya özgü üst bilgilerde yer alan kişisel bilgilere izlemeler de kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-326">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="c5e80-327">Uygulama dağıtıcı, yapılandırma ve izleme dosyalarındaki ACL 'Leri ayarlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="c5e80-327">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="c5e80-328">Ayrıca, bu bilgilerin görünür olmasını istememesi durumunda izlemeyi kapatabilir veya günlüğe kaydedildikten sonra bu bilgileri izleme dosyalarından filtreleyebilirler.</span><span class="sxs-lookup"><span data-stu-id="c5e80-328">He also can turn off tracing if he does not want this information to be visible, or he can filter out this information from the trace files after it is logged.</span></span>  
  
 <span data-ttu-id="c5e80-329">ServiceModel Izlemenin bir parçası olarak, benzersiz kimlikler (etkinlik kimlikleri olarak adlandırılır ve tipik olarak bir GUID), altyapının farklı bölümleriyle bir ileti akışı olarak farklı etkinlikleri birbirine bağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-329">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="c5e80-330">Özel Izleme dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="c5e80-330">Custom Trace Listeners</span></span>  
 <span data-ttu-id="c5e80-331">İleti günlüğe kaydetme ve izleme için, bir özel izleme dinleyicisi yapılandırılabilir ve bu da, hatta (örneğin, uzak bir veritabanına) izlemeleri ve iletileri gönderebilirler.</span><span class="sxs-lookup"><span data-stu-id="c5e80-331">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="c5e80-332">Uygulama dağıtıcı, özel dinleyicileri yapılandırmadan veya kullanıcıların bunu yapabilmesini sağlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="c5e80-332">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="c5e80-333">Ayrıca, uzak konumda sunulan kişisel bilgilerden da sorumludur ve ACL 'Leri bu konuma doğru şekilde uygulamak için de sorumludur.</span><span class="sxs-lookup"><span data-stu-id="c5e80-333">He is also responsible for any personal information exposed at the remote location, and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="c5e80-334">BT uzmanlarına yönelik diğer özellikler</span><span class="sxs-lookup"><span data-stu-id="c5e80-334">Other features for IT Professionals</span></span>  
 <span data-ttu-id="c5e80-335">WCF, WMI aracılığıyla WCF altyapı yapılandırma bilgilerini kullanıma sunan bir WMI sağlayıcısına sahiptir (Windows ile gönderilir).</span><span class="sxs-lookup"><span data-stu-id="c5e80-335">WCF has a WMI provider that exposes the WCF infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="c5e80-336">Varsayılan olarak, WMI arabirimi Yöneticiler tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-336">By default, the WMI interface is available to administrators.</span></span>  
  
 <span data-ttu-id="c5e80-337">WCF yapılandırması .NET Framework yapılandırma mekanizmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-337">WCF configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="c5e80-338">Yapılandırma dosyaları makinede depolanır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-338">The configuration files are stored on the machine.</span></span> <span data-ttu-id="c5e80-339">Uygulama geliştiricisi ve Yöneticisi, uygulama gereksinimlerinin her biri için yapılandırma dosyalarını ve ACL 'yi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c5e80-339">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="c5e80-340">Yapılandırma dosyası, uç nokta adreslerini ve sertifika deposundaki sertifikalara bağlantıları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-340">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="c5e80-341">Sertifikalar, uygulama tarafından kullanılan özelliklerin çeşitli özelliklerini yapılandırmak için uygulama verileri sağlamak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-341">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="c5e80-342">WCF Ayrıca, <xref:System.Environment.FailFast%2A> yöntemini çağırarak .NET Framework işlem dökümü işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-342">WCF also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="c5e80-343">BT uzmanı araçları</span><span class="sxs-lookup"><span data-stu-id="c5e80-343">IT Pro Tools</span></span>  
 <span data-ttu-id="c5e80-344">WCF Ayrıca, Windows SDK teslim eden aşağıdaki BT uzmanı araçlarını da sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e80-344">WCF also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="c5e80-345">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="c5e80-345">SvcTraceViewer.exe</span></span>  
 <span data-ttu-id="c5e80-346">Görüntüleyici, WCF izleme dosyalarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c5e80-346">The viewer displays WCF trace files.</span></span> <span data-ttu-id="c5e80-347">Görüntüleyici, izlemelerde hangi bilgilerin yer aldığı bilgisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-347">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="c5e80-348">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="c5e80-348">SvcConfigEditor.exe</span></span>  
 <span data-ttu-id="c5e80-349">Düzenleyici, kullanıcının WCF yapılandırma dosyalarını oluşturmasına ve düzenlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-349">The editor allows the user to create and edit WCF configuration files.</span></span> <span data-ttu-id="c5e80-350">Düzenleyici, yapılandırma dosyalarında hangi bilgilerin yer aldığı bilgisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-350">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="c5e80-351">Aynı görev bir metin Düzenleyicisi ile gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-351">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodel_reg"></a><span data-ttu-id="c5e80-352">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="c5e80-352">ServiceModel_Reg</span></span>  
 <span data-ttu-id="c5e80-353">Bu araç, kullanıcının bir makinedeki ServiceModel yüklemelerini yönetmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-353">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="c5e80-354">Araç, çalışırken bir konsol penceresinde durum iletilerini görüntüler ve süreçte, WCF yüklemesinin yapılandırmasıyla ilgili bilgileri görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-354">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the WCF installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="c5e80-355">WSATConfig. exe ve WSATUı. dll</span><span class="sxs-lookup"><span data-stu-id="c5e80-355">WSATConfig.exe and WSATUI.dll</span></span>  
 <span data-ttu-id="c5e80-356">Bu araçlar, BT uzmanlarının WCF 'de birlikte çalışabilen WS-AtomicTransaction ağ desteğini yapılandırmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-356">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in WCF.</span></span> <span data-ttu-id="c5e80-357">Araçlar, kullanıcının kayıt defterinde depolanan en sık kullanılan WS-AtomicTransaction ayarlarının değerlerini değiştirmesine ve değiştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-357">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="c5e80-358">Çapraz kesme özellikleri</span><span class="sxs-lookup"><span data-stu-id="c5e80-358">Cross-cutting Features</span></span>  
 <span data-ttu-id="c5e80-359">Aşağıdaki özellikler çapraz kesme.</span><span class="sxs-lookup"><span data-stu-id="c5e80-359">The following features are cross-cutting.</span></span> <span data-ttu-id="c5e80-360">Diğer bir deyişle, önceki özelliklerden herhangi biri ile birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-360">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="c5e80-361">Hizmet Çerçevesi</span><span class="sxs-lookup"><span data-stu-id="c5e80-361">Service Framework</span></span>  
 <span data-ttu-id="c5e80-362">Üst bilgiler bir CLR sınıfının örneğiyle bir iletiyi ilişkilendiren GUID olan bir örnek KIMLIĞI içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-362">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="c5e80-363">Web Hizmetleri Açıklama Dili (WSDL), bağlantı noktasının tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-363">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="c5e80-364">Her bağlantı noktasının bir uç nokta adresi ve uygulama tarafından kullanılan hizmetleri temsil eden bir bağlaması vardır.</span><span class="sxs-lookup"><span data-stu-id="c5e80-364">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="c5e80-365">WSDL 'nin kullanıma sunulmasına yapılandırma kullanılarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e80-365">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="c5e80-366">Makinede bilgi korunmaz.</span><span class="sxs-lookup"><span data-stu-id="c5e80-366">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5e80-367">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5e80-367">See also</span></span>

- [<span data-ttu-id="c5e80-368">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c5e80-368">Windows Communication Foundation</span></span>](index.md)
- [<span data-ttu-id="c5e80-369">Security</span><span class="sxs-lookup"><span data-stu-id="c5e80-369">Security</span></span>](./feature-details/security.md)
