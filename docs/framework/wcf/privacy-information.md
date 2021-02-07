---
description: 'Hakkında daha fazla bilgi edinin: Windows Communication Foundation gizlilik bilgileri'
title: Windows Communication Foundation Gizlilik Bilgileri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: 4f942e84a072d15a12b6db7cc2c310d629a59f6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726695"
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="4ca43-103">Windows Communication Foundation Gizlilik Bilgileri</span><span class="sxs-lookup"><span data-stu-id="4ca43-103">Windows Communication Foundation Privacy Information</span></span>

<span data-ttu-id="4ca43-104">Microsoft, son kullanıcı gizliliğini korumayı taahhüt etmektedir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-104">Microsoft is committed to protecting end user privacy.</span></span> <span data-ttu-id="4ca43-105">Windows Communication Foundation (WCF), sürüm 3,0 kullanarak bir uygulama oluşturduğunuzda, uygulamanız son kullanıcılarınızın gizliliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-105">When you build an application using Windows Communication Foundation (WCF), version 3.0, your application may impact your end users' privacy.</span></span> <span data-ttu-id="4ca43-106">Örneğin, uygulamanız kullanıcı iletişim bilgilerini açıkça toplayabilir veya Internet üzerinden Web sitenize bilgi talep edebilir veya gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-106">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="4ca43-107">Uygulamanıza Microsoft teknolojisi eklerseniz, bu teknolojinin gizliliği etkileyebilecek kendi davranışı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-107">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> <span data-ttu-id="4ca43-108">WCF, siz veya Son Kullanıcı bunu bize göndermediğiniz müddetçe Microsoft 'a herhangi bir bilgi göndermez.</span><span class="sxs-lookup"><span data-stu-id="4ca43-108">WCF does not send any information to Microsoft from your application unless you or the end user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="4ca43-109">WCF kısaca</span><span class="sxs-lookup"><span data-stu-id="4ca43-109">WCF in Brief</span></span>  

 <span data-ttu-id="4ca43-110">WCF, geliştiricilerin dağıtılmış uygulamalar oluşturmalarına olanak tanıyan Microsoft .NET çerçevesini kullanan dağıtılmış bir mesajlaşma çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-110">WCF is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="4ca43-111">İki uygulama arasında iletilen iletiler, üst bilgi ve gövde bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-111">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="4ca43-112">Üst bilgiler, uygulama tarafından kullanılan hizmetlere bağlı olarak ileti yönlendirme, güvenlik bilgileri, işlemler ve daha fazlasını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-112">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="4ca43-113">İletiler genellikle varsayılan olarak şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-113">Messages are typically encrypted by default.</span></span> <span data-ttu-id="4ca43-114">Tek istisna, `BasicHttpBinding` güvenli olmayan, eski Web Hizmetleri ile kullanılmak üzere tasarlanmış olan öğesini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-114">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="4ca43-115">Uygulama Tasarımcısı olarak son tasarımdan siz sorumlusunuz.</span><span class="sxs-lookup"><span data-stu-id="4ca43-115">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="4ca43-116">SOAP gövdesindeki iletiler uygulamaya özgü verileri içerir; Ancak, uygulama tanımlı kişisel bilgiler gibi bu veriler, WCF şifreleme veya gizlilik özellikleri kullanılarak güvenliği sağlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-116">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using WCF encryption or confidentiality features.</span></span> <span data-ttu-id="4ca43-117">Aşağıdaki bölümlerde gizliliği potansiyel olarak etkileyebilecek özellikler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-117">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="4ca43-118">Mesajlaşma</span><span class="sxs-lookup"><span data-stu-id="4ca43-118">Messaging</span></span>  

 <span data-ttu-id="4ca43-119">Her WCF iletisinde, ileti hedefini belirten ve yanıtın gitmesi gereken bir adres üst bilgisi vardır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-119">Each WCF message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="4ca43-120">Bir uç nokta adresinin adres bileşeni, uç noktasını tanımlayan bir Tekdüzen kaynak tanımlayıcısıdır (URI).</span><span class="sxs-lookup"><span data-stu-id="4ca43-120">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="4ca43-121">Adres bir ağ adresi veya mantıksal adres olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-121">The address can be a network address or a logical address.</span></span> <span data-ttu-id="4ca43-122">Adres, makine adı (ana bilgisayar adı, tam etki alanı adı) ve bir IP adresi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-122">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="4ca43-123">Uç nokta adresi bir genel benzersiz tanımlayıcı (GUID) veya her bir adresi ayırt etmek için kullanılan geçici adresleme için GUID 'lerin bir koleksiyonunu da içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-123">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="4ca43-124">Her ileti, GUID olan bir ileti KIMLIĞI içerir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-124">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="4ca43-125">Bu özellik WS-Addressing Reference standardını izler.</span><span class="sxs-lookup"><span data-stu-id="4ca43-125">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="4ca43-126">WCF mesajlaşma katmanı, yerel makineye herhangi bir kişisel bilgi yazmaz.</span><span class="sxs-lookup"><span data-stu-id="4ca43-126">The WCF messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="4ca43-127">Bununla birlikte, bir hizmet geliştiricisi bu bilgileri açığa çıkaran bir hizmet (örneğin, bir uç nokta adında bir kişinin adını kullanarak ya da uç noktanın Web Hizmetleri Açıklama dilinde kişisel bilgiler dahil, ancak istemcilerin WSDL 'ye erişmek için HTTPS kullanmasını gerektirmeksizin), kişisel bilgileri ağ düzeyinde yayabilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-127">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="4ca43-128">Ayrıca bir geliştirici, kişisel bilgiler sunan bir uç noktaya karşı [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) aracını çalıştırıyorsa, aracın çıktısı bu bilgileri içerebilir ve çıkış dosyası yerel sabit diske yazılır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-128">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="4ca43-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="4ca43-129">Hosting</span></span>  

 <span data-ttu-id="4ca43-130">WCF 'deki barındırma özelliği, uygulamaların isteğe bağlı olarak başlamasını veya birden çok uygulama arasında bağlantı noktası paylaşımını etkinleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-130">The hosting feature in WCF allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="4ca43-131">WCF uygulaması, ASP.NET benzeri Internet Information Services (IIS) içinde barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-131">A WCF application can be hosted in Internet Information Services (IIS), similar to ASP.NET.</span></span>  
  
 <span data-ttu-id="4ca43-132">Barındırma, ağ üzerinde belirli bilgileri açığa çıkarır ve makinede veri bulundurmaz.</span><span class="sxs-lookup"><span data-stu-id="4ca43-132">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="4ca43-133">İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4ca43-133">Message Security</span></span>  

 <span data-ttu-id="4ca43-134">WCF güvenliği, Mesajlaşma uygulamalarına yönelik güvenlik özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-134">WCF security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="4ca43-135">Belirtilen güvenlik işlevleri kimlik doğrulaması ve yetkilendirme içerir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-135">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="4ca43-136">Kimlik doğrulaması, istemciler ve hizmetler arasında kimlik bilgileri geçirerek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-136">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="4ca43-137">Kimlik doğrulaması, aktarım düzeyi güvenlik aracılığıyla veya SOAP ileti düzeyi güvenliği aracılığıyla aşağıdaki gibi olabilir:</span><span class="sxs-lookup"><span data-stu-id="4ca43-137">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
- <span data-ttu-id="4ca43-138">SOAP iletisi güvenliği 'nde kimlik doğrulaması, Kullanıcı adı/parolalar, X. 509.440 sertifikaları, Kerberos biletleri ve SAML belirteçleri gibi kimlik bilgileri aracılığıyla yapılır; bu, verenlere bağlı olarak kişisel bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-138">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
- <span data-ttu-id="4ca43-139">Aktarım güvenliğini kullanarak, kimlik doğrulaması HTTP kimlik doğrulama şemaları (temel, Özet, anlaşma, tümleşik Windows yetkilendirmesi, NTLM, hiçbiri ve anonim) ve form kimlik doğrulaması gibi geleneksel aktarım kimlik doğrulama mekanizmaları aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-139">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="4ca43-140">Kimlik doğrulama, iletişim noktaları arasında kurulan güvenli bir oturumun oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-140">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="4ca43-141">Oturum, güvenlik oturumunun ömrünü sürdüeden bir GUID ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-141">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="4ca43-142">Aşağıdaki tabloda neler olduğu ve nerede tutulduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-142">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="4ca43-143">Veriler</span><span class="sxs-lookup"><span data-stu-id="4ca43-143">Data</span></span>|<span data-ttu-id="4ca43-144">Depolama</span><span class="sxs-lookup"><span data-stu-id="4ca43-144">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="4ca43-145">Kullanıcı adı, X. 509.440 sertifikaları, Kerberos belirteçleri ve kimlik bilgilerine yapılan başvurular gibi sunum kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="4ca43-145">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="4ca43-146">Windows sertifika deposu gibi standart Windows kimlik bilgisi yönetim mekanizmaları.</span><span class="sxs-lookup"><span data-stu-id="4ca43-146">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="4ca43-147">Kullanıcı üyeliği bilgileri, örneğin Kullanıcı adları ve parolalar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-147">User membership information, such as usernames and passwords.</span></span>|<span data-ttu-id="4ca43-148">ASP.NET üyelik sağlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="4ca43-148">ASP.NET membership providers.</span></span>|  
|<span data-ttu-id="4ca43-149">Hizmetin istemcilere kimliğini doğrulamak için kullanılan hizmet hakkındaki kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="4ca43-149">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="4ca43-150">Hizmetin uç nokta adresi.</span><span class="sxs-lookup"><span data-stu-id="4ca43-150">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="4ca43-151">Çağıran bilgileri.</span><span class="sxs-lookup"><span data-stu-id="4ca43-151">Caller information.</span></span>|<span data-ttu-id="4ca43-152">Denetim günlükleri.</span><span class="sxs-lookup"><span data-stu-id="4ca43-152">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="4ca43-153">Denetim</span><span class="sxs-lookup"><span data-stu-id="4ca43-153">Auditing</span></span>  

 <span data-ttu-id="4ca43-154">Denetim, kimlik doğrulama ve yetkilendirme olaylarının başarısını ve başarısızlığını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4ca43-154">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="4ca43-155">Denetim kayıtları şu verileri içerir: hizmet URI 'SI, eylem URI 'SI ve arayanın kimliği.</span><span class="sxs-lookup"><span data-stu-id="4ca43-155">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="4ca43-156">Ayrıca Denetim, yönetici ileti günlüğe kaydetme yapılandırmasını değiştirdiğinde (açık veya kapalı), ileti günlüğü, uygulamaya özgü verileri üst bilgilerde ve gövdelerde günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4ca43-156">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="4ca43-157">Windows XP 'de, uygulama olay günlüğüne bir kayıt kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-157">For Windows XP, a record is logged in the application event log.</span></span> <span data-ttu-id="4ca43-158">Windows Vista ve Windows Server 2003 için güvenlik olay günlüğüne bir kayıt kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-158">For Windows Vista and Windows Server 2003, a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="4ca43-159">İşlemler</span><span class="sxs-lookup"><span data-stu-id="4ca43-159">Transactions</span></span>  

 <span data-ttu-id="4ca43-160">İşlemler özelliği bir WCF uygulamasına işlem hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-160">The transactions feature provides transactional services to a WCF application.</span></span>  
  
 <span data-ttu-id="4ca43-161">İşlem yayma işleminde kullanılan işlem üstbilgileri, GUID 'Leri olan Işlem kimliklerini veya kayıt kimliklerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-161">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="4ca43-162">Işlemler özelliği, işlem durumunu yönetmek için Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) Işlem yöneticisi 'Ni (bir Windows bileşeni) kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-162">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="4ca43-163">Varsayılan olarak, Işlem yöneticileri arasındaki iletişimler şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-163">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="4ca43-164">İşlem yöneticileri, sürekli durumunun bir parçası olarak uç nokta başvurularını, Işlem kimliklerini ve kayıt kimliklerini günlüğe kaydetmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-164">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="4ca43-165">Bu durumun ömrü, Işlem yöneticisinin günlük dosyasının ömrü ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-165">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="4ca43-166">MSDTC hizmeti, bu günlüğün sahibi ve bakımını yapar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-166">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="4ca43-167">Işlemler özelliği WS-Coordination ve WS-Atomic Işlem standartlarını uygular.</span><span class="sxs-lookup"><span data-stu-id="4ca43-167">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="4ca43-168">Güvenilir oturumlar</span><span class="sxs-lookup"><span data-stu-id="4ca43-168">Reliable Sessions</span></span>  

 <span data-ttu-id="4ca43-169">WCF 'de güvenilir oturumlar, aktarım veya aracı arızalarının oluşması durumunda iletilerin aktarılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-169">Reliable sessions in WCF provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="4ca43-170">Bu kişiler, temeldeki taşımanın bağlantısı kesildiğinde (örneğin, kablosuz ağ üzerinde bir TCP bağlantısı) veya bir iletiyi kaybettiğinde (bir HTTP proxy 'si giden veya gelen bir iletiyi bırakırken) iletilerin tam olarak bir kez aktarılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-170">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="4ca43-171">Güvenilir oturumlar Ayrıca iletilerin gönderilme sırasını koruyarak ileti yeniden sıralamasını (çok yollu yönlendirme durumunda olabileceği gibi) de kurtarır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-171">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="4ca43-172">Güvenilir oturumlar WS-ReliableMessaging (WS-RM) protokolü kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-172">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="4ca43-173">Bunlar, belirli bir güvenilir oturumla ilişkili tüm iletileri tanımlamak için kullanılan oturum bilgilerini içeren WS-RM üst bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="4ca43-173">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="4ca43-174">Her WS-RM oturumunun bir GUID olan bir tanımlayıcısı vardır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-174">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="4ca43-175">Son kullanıcının makinesinde kişisel bilgi korunmaz.</span><span class="sxs-lookup"><span data-stu-id="4ca43-175">No personal information is retained on the end user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="4ca43-176">Sıraya alınan kanallar</span><span class="sxs-lookup"><span data-stu-id="4ca43-176">Queued Channels</span></span>  

 <span data-ttu-id="4ca43-177">Kuyruklar iletileri alıcı uygulama adına gönderen uygulamadan depolar ve daha sonra bu iletileri alıcı uygulamasına iletir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-177">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="4ca43-178">Bu kişiler, örneğin, alıcı uygulama geçici olduğunda, uygulamaları almaya yönelik uygulamalar gönderen iletiler aktarımının sağlanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="4ca43-178">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> <span data-ttu-id="4ca43-179">WCF, taşıma olarak Microsoft Message Queuing (MSMQ) kullanarak sıraya alma desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-179">WCF provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="4ca43-180">Sıraya alınan kanallar özelliği bir iletiye üst bilgi eklemez.</span><span class="sxs-lookup"><span data-stu-id="4ca43-180">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="4ca43-181">Bunun yerine, uygun Message Queuing ileti özellikleri ayarlanmış Message Queuing bir ileti oluşturur ve iletiyi Message Queuing kuyruğuna koymak için Message Queuing yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-181">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="4ca43-182">Message Queuing, Windows ile birlikte gelen isteğe bağlı bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-182">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="4ca43-183">Kuyruğa alma altyapısı olarak Message Queuing kullandığından, son kullanıcının makinesinde sıraya alınan kanallar özelliği korunmaz.</span><span class="sxs-lookup"><span data-stu-id="4ca43-183">No information is retained on the end user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="4ca43-184">COM+ Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="4ca43-184">COM+ Integration</span></span>  

 <span data-ttu-id="4ca43-185">Bu özellik, WCF hizmetleriyle uyumlu hizmetler oluşturmak için mevcut COM ve COM+ işlevlerini sarmalanmış.</span><span class="sxs-lookup"><span data-stu-id="4ca43-185">This feature wraps existing COM and COM+ functionality to create services that are compatible with WCF services.</span></span> <span data-ttu-id="4ca43-186">Bu özellik belirli üst bilgileri kullanmaz ve son kullanıcının makinesinde verileri korumaz.</span><span class="sxs-lookup"><span data-stu-id="4ca43-186">This feature does not use specific headers and it does not retain data on the end user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="4ca43-187">COM hizmeti bilinen adı</span><span class="sxs-lookup"><span data-stu-id="4ca43-187">COM Service Moniker</span></span>  

 <span data-ttu-id="4ca43-188">Bu, standart bir WCF istemcisine yönetilmeyen bir sarmalayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-188">This provides an unmanaged wrapper to a standard WCF client.</span></span> <span data-ttu-id="4ca43-189">Bu özellik, hat üzerinde belirli üst bilgilere sahip değildir ve makinede verileri kalıcı hale getiremez.</span><span class="sxs-lookup"><span data-stu-id="4ca43-189">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="4ca43-190">Eş Kanal</span><span class="sxs-lookup"><span data-stu-id="4ca43-190">Peer Channel</span></span>  

 <span data-ttu-id="4ca43-191">Eş kanal, WCF kullanarak çok taraflı uygulamaların geliştirilmesini mümkün.</span><span class="sxs-lookup"><span data-stu-id="4ca43-191">A peer channel enables development of multiparty applications using WCF.</span></span> <span data-ttu-id="4ca43-192">Çok taraflı mesajlaşma, bir ağ bağlamında meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-192">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="4ca43-193">Kafesler, düğümlerin katılabilme adı tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-193">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="4ca43-194">Eş kanaldaki her düğüm, Kullanıcı tarafından belirtilen bağlantı noktasında bir TCP dinleyicisi oluşturur ve esneklik sağlamak için kafesteki diğer düğümlerle bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-194">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="4ca43-195">Kafesteki diğer düğümlere bağlanmak için, düğümler aynı zamanda dinleyici adresi ve makinenin IP adresleri de dahil olmak üzere, ağ üzerindeki diğer düğümlerle birlikte bazı verileri de değiş tokuş eder.</span><span class="sxs-lookup"><span data-stu-id="4ca43-195">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="4ca43-196">Ağ üzerinden gönderilen iletiler, ileti sızdırma ve izinsiz değişiklik yapılmasını engellemek için gönderiyle ilgili güvenlik bilgilerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-196">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="4ca43-197">Son kullanıcının makinesinde kişisel bilgi depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="4ca43-197">No personal information is stored on the end user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="4ca43-198">BT uzmanı deneyimi</span><span class="sxs-lookup"><span data-stu-id="4ca43-198">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="4ca43-199">İzleme</span><span class="sxs-lookup"><span data-stu-id="4ca43-199">Tracing</span></span>  

 <span data-ttu-id="4ca43-200">WCF altyapısının tanılama özelliği, aktarım ve hizmet modeli katmanlarından geçen iletileri ve bu iletilerle ilişkili etkinlikleri ve olayları günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4ca43-200">The diagnostics feature of the WCF infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="4ca43-201">Bu özellik varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-201">This feature is turned off by default.</span></span> <span data-ttu-id="4ca43-202">Uygulamanın yapılandırma dosyası kullanılarak etkinleştirilir ve izleme davranışı, çalışma zamanında WCF WMI sağlayıcısı kullanılarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-202">It is enabled using the application’s configuration file and the tracing behavior may be modified using the WCF WMI provider at run time.</span></span> <span data-ttu-id="4ca43-203">Etkinleştirildiğinde, izleme altyapısı, yapılandırılan dinleyicilerine ileti, etkinlik ve işleme olaylarını içeren bir tanılama izlemesi yayar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-203">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="4ca43-204">Çıktının biçimi ve konumu yöneticinin dinleyici yapılandırma seçeneklerine göre belirlenir, ancak genellikle XML biçimli bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-204">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="4ca43-205">Yönetici, izleme dosyalarındaki erişim denetim listesini (ACL) ayarlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="4ca43-205">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="4ca43-206">Özellikle, Windows etkinleştirme sistemi (WAS) tarafından barındırıldığında, yönetici, bu istenmiyorsa, dosyaların ortak sanal kök dizinden sunulmadığından emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-206">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="4ca43-207">İki tür izleme vardır: Ileti günlüğü ve hizmet modeli Tanılama izleme, aşağıdaki bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-207">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="4ca43-208">Her tür kendi izleme kaynağı aracılığıyla yapılandırılır: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> ve <xref:System.ServiceModel> .</span><span class="sxs-lookup"><span data-stu-id="4ca43-208">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="4ca43-209">Bu günlüğe kaydetme izleme kaynaklarından her ikisi de, uygulamada yerel olan verileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-209">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="4ca43-210">İleti Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="4ca43-210">Message Logging</span></span>  

 <span data-ttu-id="4ca43-211">İleti günlüğe kaydetme izleme kaynağı ( <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> ), yöneticinin sistem üzerinden akan iletileri günlüğe kaydetmeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-211">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="4ca43-212">Yapılandırma sayesinde, Kullanıcı yalnızca tüm iletileri veya ileti üstbilgilerini günlüğe kaydetmek, aktarım ve/veya hizmet modeli katmanlarında günlüğe kaydedilip edilmeyeceğini ve hatalı biçimlendirilmiş iletilerin eklenip eklenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-212">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="4ca43-213">Ayrıca Kullanıcı, hangi iletilerin günlüğe kaydedileceğini kısıtlamak için filtrelemeyi yapılandırabilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-213">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="4ca43-214">Varsayılan olarak, ileti günlüğe kaydetme devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-214">By default, message logging is disabled.</span></span> <span data-ttu-id="4ca43-215">Yerel Makine Yöneticisi, uygulama düzeyinde yöneticinin ileti oturumunu açmasını önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-215">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="4ca43-216">Şifrelenmiş ve şifresi çözülmüş Ileti günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="4ca43-216">Encrypted and Decrypted Message Logging</span></span>  

 <span data-ttu-id="4ca43-217">Aşağıdaki koşullarda açıklandığı gibi iletiler günlüğe kaydedilir, şifrelenir veya çözülür.</span><span class="sxs-lookup"><span data-stu-id="4ca43-217">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="4ca43-218">Aktarım günlüğü</span><span class="sxs-lookup"><span data-stu-id="4ca43-218">Transport Logging</span></span>  
 <span data-ttu-id="4ca43-219">Aktarım düzeyinde alınan ve gönderilen iletileri günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4ca43-219">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="4ca43-220">Bu iletiler tüm üst bilgileri içerir ve bu, hatta gönderilirken ve alındığında şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-220">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="4ca43-221">İletiler, Tel gönderilmeden ve alındıkları sırada şifrelenirse, bunlar da şifreli olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-221">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="4ca43-222">Bir güvenlik protokolünün kullanıldığı bir özel durum (https): daha sonra, bu dosyalar, kablo üzerinde şifrelenseler bile gönderilmeden ve alındıktan sonra günlüğe çözülür.</span><span class="sxs-lookup"><span data-stu-id="4ca43-222">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="4ca43-223">Hizmet günlüğü</span><span class="sxs-lookup"><span data-stu-id="4ca43-223">Service Logging</span></span>  
 <span data-ttu-id="4ca43-224">İleti üst bilgisi işleme gerçekleştirildikten sonra, Kullanıcı kodu girildikten hemen önce ve sonra, hizmet modeli düzeyinde alınan veya gönderilen iletileri günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4ca43-224">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="4ca43-225">Bu düzeyde günlüğe kaydedilen iletiler, güvenli olsalar ve kabloda şifrelendiğinden bile çözülür.</span><span class="sxs-lookup"><span data-stu-id="4ca43-225">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="4ca43-226">Hatalı biçimlendirilmiş Ileti günlüğü</span><span class="sxs-lookup"><span data-stu-id="4ca43-226">Malformed Message Logging</span></span>  
 <span data-ttu-id="4ca43-227">WCF altyapısının anlayabileceği veya işleyebileceğini iletileri günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4ca43-227">Logs messages that the WCF infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="4ca43-228">İletiler olduğu gibi kaydedilir, yani şifrelenir veya değildir</span><span class="sxs-lookup"><span data-stu-id="4ca43-228">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="4ca43-229">İletiler, şifresi çözülmüş veya şifrelenmemiş biçimde günlüğe kaydedildiğinde, varsayılan olarak WCF güvenlik anahtarlarını ve bilgileri günlüğe kaydedilmeden önce iletilerden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-229">When messages are logged in decrypted or unencrypted form, by default WCF removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="4ca43-230">Sonraki bölümlerde hangi bilgilerin kaldırıldığı ve ne zaman olduğu açıklanır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-230">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="4ca43-231">Makine Yöneticisi ve uygulama dağıtıcısı, varsayılan davranışı günlük anahtarlarına ve potansiyel olarak kişisel bilgilere değiştirecek şekilde, her ikisi de belirli yapılandırma eylemlerini almalıdır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-231">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="4ca43-232">Şifresi çözülmüş/şifrelenmemiş Iletileri günlüğe kaydederken Ileti başlıklarından kaldırılan bilgiler</span><span class="sxs-lookup"><span data-stu-id="4ca43-232">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  

 <span data-ttu-id="4ca43-233">İletiler, şifresi çözülmüş/şifrelenmemiş biçiminde günlüğe kaydedildiğinde, güvenlik anahtarları ve potansiyel olarak kişisel bilgiler, günlüğe kaydedilmeden önce ileti başlıklarından ve ileti gövdelerinde varsayılan olarak kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-233">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="4ca43-234">Aşağıdaki listede, anahtarların ve potansiyel olarak kişisel bilgilerin hangi WCF tarafından kabul olduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-234">The following list shows what WCF considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="4ca43-235">Kaldırılan anahtarlar:</span><span class="sxs-lookup"><span data-stu-id="4ca43-235">Keys that are removed:</span></span>  
  
 <span data-ttu-id="4ca43-236">\- Xmlns: WST = " http://schemas.xmlsoap.org/ws/2004/04/trust " ve xmlns: WST = " http://schemas.xmlsoap.org/ws/2005/02/trust " için</span><span class="sxs-lookup"><span data-stu-id="4ca43-236">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="4ca43-237">Wst: BinarySecret</span><span class="sxs-lookup"><span data-stu-id="4ca43-237">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="4ca43-238">Wst: entropi</span><span class="sxs-lookup"><span data-stu-id="4ca43-238">wst:Entropy</span></span>  
  
 <span data-ttu-id="4ca43-239">\- Xmlns: WSO = " http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd " ve xmlns: WSO = " http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd " için</span><span class="sxs-lookup"><span data-stu-id="4ca43-239">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="4ca43-240">WSS: parola</span><span class="sxs-lookup"><span data-stu-id="4ca43-240">wsse:Password</span></span>  
  
 <span data-ttu-id="4ca43-241">WSS: nonce</span><span class="sxs-lookup"><span data-stu-id="4ca43-241">wsse:Nonce</span></span>  
  
 <span data-ttu-id="4ca43-242">Kaldırılan potansiyel kişisel bilgiler:</span><span class="sxs-lookup"><span data-stu-id="4ca43-242">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="4ca43-243">\- Xmlns: WSO = " http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd " ve xmlns: WSO = " http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd " için</span><span class="sxs-lookup"><span data-stu-id="4ca43-243">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="4ca43-244">WSS: Kullanıcı adı</span><span class="sxs-lookup"><span data-stu-id="4ca43-244">wsse:Username</span></span>  
  
 <span data-ttu-id="4ca43-245">WSS: BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="4ca43-245">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="4ca43-246">\- Xmlns: SAML = "urn: oassıs: names: TC: SAML: 1.0: assertion" kalın (aşağıda) öğeleri kaldırılır:</span><span class="sxs-lookup"><span data-stu-id="4ca43-246">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="4ca43-247">\<Onaylama işlemi</span><span class="sxs-lookup"><span data-stu-id="4ca43-247">\<Assertion</span></span>  
  
 <span data-ttu-id="4ca43-248">MajorVersion = "1"</span><span class="sxs-lookup"><span data-stu-id="4ca43-248">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="4ca43-249">MinorVersion = "1"</span><span class="sxs-lookup"><span data-stu-id="4ca43-249">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="4ca43-250">AssertionId 'si = "[KIMLIK]"</span><span class="sxs-lookup"><span data-stu-id="4ca43-250">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="4ca43-251">Issuer = "[dize]"</span><span class="sxs-lookup"><span data-stu-id="4ca43-251">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="4ca43-252">IssueInstant = "[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="4ca43-252">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 \<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]">  
  
 \<AudienceRestrictionCondition>  
  
 <span data-ttu-id="4ca43-253">\<Audience>kullanılmamışsa\</Audience>+</span><span class="sxs-lookup"><span data-stu-id="4ca43-253">\<Audience>[uri]\</Audience>+</span></span>  
  
 \</AudienceRestrictionCondition>*  
  
 \<DoNotCacheCondition />*  
  
 <span data-ttu-id="4ca43-254"><\!--soyut temel tür</span><span class="sxs-lookup"><span data-stu-id="4ca43-254"><\!-- abstract base type</span></span>  
  
 \<Condition />*  
  
 -->  
  
 <span data-ttu-id="4ca43-255">\</Conditions>?</span><span class="sxs-lookup"><span data-stu-id="4ca43-255">\</Conditions>?</span></span>  
  
 \<Advice>  
  
 <span data-ttu-id="4ca43-256">\<AssertionIDReference>NUMARASıNı\</AssertionIDReference>\*</span><span class="sxs-lookup"><span data-stu-id="4ca43-256">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="4ca43-257">\<Assertion>onay\</Assertion>\*</span><span class="sxs-lookup"><span data-stu-id="4ca43-257">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="4ca43-258">[any] \*</span><span class="sxs-lookup"><span data-stu-id="4ca43-258">[any]\*</span></span>  
  
 <span data-ttu-id="4ca43-259">\</Advice>?</span><span class="sxs-lookup"><span data-stu-id="4ca43-259">\</Advice>?</span></span>  
  
 <span data-ttu-id="4ca43-260"><\!--Soyut temel türler</span><span class="sxs-lookup"><span data-stu-id="4ca43-260"><\!-- Abstract base types</span></span>  
  
 \<Statement />*  
  
 \<SubjectStatement>  
  
 \<Subject>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 \<SubjectConfirmation>  
  
 <span data-ttu-id="4ca43-261">\<ConfirmationMethod>anyURI\</ConfirmationMethod>+</span><span class="sxs-lookup"><span data-stu-id="4ca43-261">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="4ca43-262">\<SubjectConfirmationData>[any] \</SubjectConfirmationData> ?</span><span class="sxs-lookup"><span data-stu-id="4ca43-262">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="4ca43-263">\<ds:KeyInfo>...\</ds:KeyInfo>?</span><span class="sxs-lookup"><span data-stu-id="4ca43-263">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="4ca43-264">\</SubjectConfirmation>?</span><span class="sxs-lookup"><span data-stu-id="4ca43-264">\</SubjectConfirmation>?</span></span>  
  
 \</Subject>  
  
 \</SubjectStatement>*  
  
 -->  
  
 <span data-ttu-id="4ca43-265">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="4ca43-265">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="4ca43-266">AuthenticationMethod = "[Uri]"</span><span class="sxs-lookup"><span data-stu-id="4ca43-266">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="4ca43-267">AuthenticationInstant = "[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="4ca43-267">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="4ca43-268">Konusuna</span><span class="sxs-lookup"><span data-stu-id="4ca43-268">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="4ca43-269"><AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="4ca43-269"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="4ca43-270">AuthorityKind = "[QName]"</span><span class="sxs-lookup"><span data-stu-id="4ca43-270">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="4ca43-271">Konum = "[Uri]"</span><span class="sxs-lookup"><span data-stu-id="4ca43-271">Location="[uri]"</span></span>  
  
 <span data-ttu-id="4ca43-272">Binding = "[Uri]"</span><span class="sxs-lookup"><span data-stu-id="4ca43-272">Binding="[uri]"</span></span>  
  
 />*  
  
 \</AuthenticationStatement>*  
  
 \<AttributeStatement>  
  
 <span data-ttu-id="4ca43-273">Konusuna</span><span class="sxs-lookup"><span data-stu-id="4ca43-273">[Subject]</span></span>  
  
 <span data-ttu-id="4ca43-274">\<Özniteliğe</span><span class="sxs-lookup"><span data-stu-id="4ca43-274">\<Attribute</span></span>  
  
 <span data-ttu-id="4ca43-275">AttributeName = "[dize]"</span><span class="sxs-lookup"><span data-stu-id="4ca43-275">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="4ca43-276">AttributeNamespace = "[Uri]"</span><span class="sxs-lookup"><span data-stu-id="4ca43-276">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 \</Attribute>+  
  
 \</AttributeStatement>*  
  
 <span data-ttu-id="4ca43-277">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="4ca43-277">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="4ca43-278">Resource = "[Uri]"</span><span class="sxs-lookup"><span data-stu-id="4ca43-278">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="4ca43-279">Karar = "[Izin&#124;reddetme&#124;belirsiz]"</span><span class="sxs-lookup"><span data-stu-id="4ca43-279">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="4ca43-280">Konusuna</span><span class="sxs-lookup"><span data-stu-id="4ca43-280">[Subject]</span></span>  
  
 <span data-ttu-id="4ca43-281">\<Action Namespace="[uri]">dizisinde\</Action>+</span><span class="sxs-lookup"><span data-stu-id="4ca43-281">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 \<Evidence>  
  
 <span data-ttu-id="4ca43-282">\<AssertionIDReference>NUMARASıNı\</AssertionIDReference>+</span><span class="sxs-lookup"><span data-stu-id="4ca43-282">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="4ca43-283">\<Assertion>onay\</Assertion>+</span><span class="sxs-lookup"><span data-stu-id="4ca43-283">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="4ca43-284">\</Evidence>?</span><span class="sxs-lookup"><span data-stu-id="4ca43-284">\</Evidence>?</span></span>  
  
 \</AuthorizationDecisionStatement>*  
  
 \</Assertion>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="4ca43-285">Şifresi çözülmüş/şifrelenmemiş Iletileri günlüğe kaydederken Ileti gövdelerinde kaldırılan bilgiler</span><span class="sxs-lookup"><span data-stu-id="4ca43-285">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  

 <span data-ttu-id="4ca43-286">Daha önce açıklandığı gibi, WCF anahtarları ve bilinen potansiyel olarak kişisel bilgileri, günlüğe kaydedilen ve şifrelenmemiş iletiler için ileti başlıklarından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-286">As previously described, WCF removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="4ca43-287">Ayrıca, WCF anahtarlar ve bilinen potansiyel kişisel bilgileri, anahtar değişimine dahil olan güvenlik iletilerini açıklayan aşağıdaki listede bulunan gövde öğeleri ve eylemler için ileti gövdesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-287">In addition, WCF removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="4ca43-288">Aşağıdaki ad alanları için:</span><span class="sxs-lookup"><span data-stu-id="4ca43-288">For the following namespaces:</span></span>  
  
 <span data-ttu-id="4ca43-289">xmlns: WST = " http://schemas.xmlsoap.org/ws/2004/04/trust " ve xmlns: WST = " http://schemas.xmlsoap.org/ws/2005/02/trust " (örneğin, kullanılabilir bir eylem yoksa)</span><span class="sxs-lookup"><span data-stu-id="4ca43-289">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="4ca43-290">Bu gövde öğeleri için, anahtar değişimini içeren bilgiler kaldırılır:</span><span class="sxs-lookup"><span data-stu-id="4ca43-290">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="4ca43-291">Wst: RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="4ca43-291">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="4ca43-292">Wst: RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="4ca43-292">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="4ca43-293">Wst: RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="4ca43-293">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="4ca43-294">Bilgiler aşağıdaki eylemlerin her biri için de kaldırılır:</span><span class="sxs-lookup"><span data-stu-id="4ca43-294">Information is also removed for each of the following Actions:</span></span>  
  
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
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="4ca43-295">Uygulamaya özgü üst bilgilerden ve gövde verilerinden hiçbir bilgi kaldırılmadı</span><span class="sxs-lookup"><span data-stu-id="4ca43-295">No Information Is Removed from Application-specific Headers and Body Data</span></span>  

 <span data-ttu-id="4ca43-296">WCF, uygulamaya özgü üst bilgilerde (örneğin, sorgu dizeleri) veya gövde verilerinde (örneğin, kredi kartı numarası) kişisel bilgileri izlemez.</span><span class="sxs-lookup"><span data-stu-id="4ca43-296">WCF does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="4ca43-297">İleti günlüğe kaydetme açık olduğunda, uygulamaya özgü üst bilgiler ve gövde bilgilerindeki kişisel bilgilere günlüklerde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-297">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="4ca43-298">Daha sonra, yapılandırma ve günlük dosyalarındaki ACL 'Leri ayarlamaktan uygulama dağıtıcı sorumludur.</span><span class="sxs-lookup"><span data-stu-id="4ca43-298">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="4ca43-299">Ayrıca, bu bilgilerin görünür olmasını istemediklerinde günlüğe kaydetmeyi kapatabilir veya günlüğe kaydedildikten sonra bu bilgileri günlük dosyalarından filtreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ca43-299">They also can turn off logging if they don't want this information to be visible, or filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="4ca43-300">Hizmet modeli Izleme</span><span class="sxs-lookup"><span data-stu-id="4ca43-300">Service Model Tracing</span></span>  

 <span data-ttu-id="4ca43-301">Hizmet modeli izleme kaynağı ( <xref:System.ServiceModel> ), ileti işlemeyle ilgili etkinliklerin ve olayların izlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-301">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="4ca43-302">Bu özellik ' den .NET Framework tanılama işlevini kullanır <xref:System.Diagnostics> .</span><span class="sxs-lookup"><span data-stu-id="4ca43-302">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="4ca43-303">Özelliği ile olduğu gibi <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> , konum ve ACL 'si, .NET Framework uygulama yapılandırma dosyaları kullanılarak Kullanıcı tarafından yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-303">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="4ca43-304">İleti günlüğe kaydetme sırasında, yönetici izlemeyi etkinleştirse de dosya konumu her zaman yapılandırılır; Bu nedenle, yönetici ACL 'yi denetler.</span><span class="sxs-lookup"><span data-stu-id="4ca43-304">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="4ca43-305">İzlemeler, bir ileti kapsamda olduğunda ileti üst bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-305">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="4ca43-306">Önceki bölümde bulunan ileti üstbilgilerinde kişisel bilgilerini gizlemek için de aynı kurallar geçerlidir: daha önce tanımlanan kişisel bilgiler, izlemelerin üst bilgilerinden varsayılan olarak kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-306">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="4ca43-307">Makine Yöneticisi ve uygulama dağıtıcısı, olası kişisel bilgileri günlüğe kaydetmek için yapılandırmayı değiştirmeli.</span><span class="sxs-lookup"><span data-stu-id="4ca43-307">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="4ca43-308">Bununla birlikte, uygulamaya özgü üst bilgilerde yer alan kişisel bilgilere izlemeler de kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-308">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="4ca43-309">Uygulama dağıtıcı, yapılandırma ve izleme dosyalarındaki ACL 'Leri ayarlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="4ca43-309">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="4ca43-310">Ayrıca, bu bilgileri gizlemek veya günlüğe kaydedildikten sonra bu bilgileri izleme dosyalarından filtrelemek için izlemeyi kapatabilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-310">They can also turn off tracing to hide this information or filter out this information from the trace files after it's logged.</span></span>  
  
 <span data-ttu-id="4ca43-311">ServiceModel Izlemenin bir parçası olarak, benzersiz kimlikler (etkinlik kimlikleri olarak adlandırılır ve tipik olarak bir GUID), altyapının farklı bölümleriyle bir ileti akışı olarak farklı etkinlikleri birbirine bağlar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-311">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="4ca43-312">Özel Izleme dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="4ca43-312">Custom Trace Listeners</span></span>  

 <span data-ttu-id="4ca43-313">İleti günlüğe kaydetme ve izleme için, bir özel izleme dinleyicisi yapılandırılabilir ve bu da, hatta (örneğin, uzak bir veritabanına) izlemeleri ve iletileri gönderebilirler.</span><span class="sxs-lookup"><span data-stu-id="4ca43-313">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="4ca43-314">Uygulama dağıtıcı, özel dinleyicileri yapılandırmadan veya kullanıcıların bunu yapabilmesini sağlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="4ca43-314">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="4ca43-315">Bunlar ayrıca uzak konumda sunulan kişisel bilgilerden sorumludur ve ACL 'Leri bu konuma doğru şekilde uygulamak için de sorumludur.</span><span class="sxs-lookup"><span data-stu-id="4ca43-315">They are also responsible for any personal information exposed at the remote location and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="4ca43-316">BT uzmanlarına yönelik diğer özellikler</span><span class="sxs-lookup"><span data-stu-id="4ca43-316">Other features for IT Professionals</span></span>  

 <span data-ttu-id="4ca43-317">WCF, WMI aracılığıyla WCF altyapı yapılandırma bilgilerini kullanıma sunan bir WMI sağlayıcısına sahiptir (Windows ile gönderilir).</span><span class="sxs-lookup"><span data-stu-id="4ca43-317">WCF has a WMI provider that exposes the WCF infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="4ca43-318">Varsayılan olarak, WMI arabirimi Yöneticiler tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-318">By default, the WMI interface is available to administrators.</span></span>  
  
 <span data-ttu-id="4ca43-319">WCF yapılandırması .NET Framework yapılandırma mekanizmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-319">WCF configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="4ca43-320">Yapılandırma dosyaları makinede depolanır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-320">The configuration files are stored on the machine.</span></span> <span data-ttu-id="4ca43-321">Uygulama geliştiricisi ve Yöneticisi, uygulama gereksinimlerinin her biri için yapılandırma dosyalarını ve ACL 'yi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4ca43-321">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="4ca43-322">Yapılandırma dosyası, uç nokta adreslerini ve sertifika deposundaki sertifikalara bağlantıları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-322">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="4ca43-323">Sertifikalar, uygulama tarafından kullanılan özelliklerin çeşitli özelliklerini yapılandırmak için uygulama verileri sağlamak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-323">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="4ca43-324">WCF Ayrıca yöntemini çağırarak .NET Framework işlem dökümü işlevini kullanır <xref:System.Environment.FailFast%2A> .</span><span class="sxs-lookup"><span data-stu-id="4ca43-324">WCF also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="4ca43-325">BT uzmanı araçları</span><span class="sxs-lookup"><span data-stu-id="4ca43-325">IT Pro Tools</span></span>  

 <span data-ttu-id="4ca43-326">WCF Ayrıca, Windows SDK teslim eden aşağıdaki BT uzmanı araçlarını da sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ca43-326">WCF also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="4ca43-327">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="4ca43-327">SvcTraceViewer.exe</span></span>  

 <span data-ttu-id="4ca43-328">Görüntüleyici, WCF izleme dosyalarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4ca43-328">The viewer displays WCF trace files.</span></span> <span data-ttu-id="4ca43-329">Görüntüleyici, izlemelerde hangi bilgilerin yer aldığı bilgisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-329">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="4ca43-330">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="4ca43-330">SvcConfigEditor.exe</span></span>  

 <span data-ttu-id="4ca43-331">Düzenleyici, kullanıcının WCF yapılandırma dosyalarını oluşturmasına ve düzenlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-331">The editor allows the user to create and edit WCF configuration files.</span></span> <span data-ttu-id="4ca43-332">Düzenleyici, yapılandırma dosyalarında hangi bilgilerin yer aldığı bilgisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-332">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="4ca43-333">Aynı görev bir metin Düzenleyicisi ile gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-333">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodel_reg"></a><span data-ttu-id="4ca43-334">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="4ca43-334">ServiceModel_Reg</span></span>  

 <span data-ttu-id="4ca43-335">Bu araç, kullanıcının bir makinedeki ServiceModel yüklemelerini yönetmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-335">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="4ca43-336">Araç, çalışırken bir konsol penceresinde durum iletilerini görüntüler ve süreçte, WCF yüklemesinin yapılandırmasıyla ilgili bilgileri görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-336">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the WCF installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="4ca43-337">WSATConfig.exe ve WSATUI.dll</span><span class="sxs-lookup"><span data-stu-id="4ca43-337">WSATConfig.exe and WSATUI.dll</span></span>  

 <span data-ttu-id="4ca43-338">Bu araçlar, BT uzmanlarının WCF 'de birlikte çalışabilen WS-AtomicTransaction ağ desteğini yapılandırmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-338">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in WCF.</span></span> <span data-ttu-id="4ca43-339">Araçlar, kullanıcının kayıt defterinde depolanan en yaygın olarak kullanılan WS-AtomicTransaction ayarlarının değerlerini değiştirmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-339">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="4ca43-340">Çapraz kesme özellikleri</span><span class="sxs-lookup"><span data-stu-id="4ca43-340">Cross-cutting Features</span></span>  

 <span data-ttu-id="4ca43-341">Aşağıdaki özellikler çapraz kesme.</span><span class="sxs-lookup"><span data-stu-id="4ca43-341">The following features are cross-cutting.</span></span> <span data-ttu-id="4ca43-342">Diğer bir deyişle, önceki özelliklerden herhangi biri ile birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-342">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="4ca43-343">Hizmet Çerçevesi</span><span class="sxs-lookup"><span data-stu-id="4ca43-343">Service Framework</span></span>  

 <span data-ttu-id="4ca43-344">Üst bilgiler bir CLR sınıfının örneğiyle bir iletiyi ilişkilendiren GUID olan bir örnek KIMLIĞI içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-344">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="4ca43-345">Web Hizmetleri Açıklama Dili (WSDL), bağlantı noktasının tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-345">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="4ca43-346">Her bağlantı noktasının bir uç nokta adresi ve uygulama tarafından kullanılan hizmetleri temsil eden bir bağlaması vardır.</span><span class="sxs-lookup"><span data-stu-id="4ca43-346">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="4ca43-347">WSDL 'nin kullanıma sunulmasına yapılandırma kullanılarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ca43-347">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="4ca43-348">Makinede bilgi korunmaz.</span><span class="sxs-lookup"><span data-stu-id="4ca43-348">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ca43-349">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ca43-349">See also</span></span>

- [<span data-ttu-id="4ca43-350">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4ca43-350">Windows Communication Foundation</span></span>](index.md)
- [<span data-ttu-id="4ca43-351">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="4ca43-351">Security</span></span>](./feature-details/security.md)
