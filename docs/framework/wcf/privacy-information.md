---
title: Windows Communication Foundation Gizlilik Bilgileri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: e278b28e5c0015eeab549b04d3870dfa247a57ed
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808877"
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="3c030-102">Windows Communication Foundation Gizlilik Bilgileri</span><span class="sxs-lookup"><span data-stu-id="3c030-102">Windows Communication Foundation Privacy Information</span></span>
<span data-ttu-id="3c030-103">Microsoft, son kullanıcılar gizliliğinizi korumayı taahhüt eder.</span><span class="sxs-lookup"><span data-stu-id="3c030-103">Microsoft is committed to protecting end-users' privacy.</span></span> <span data-ttu-id="3c030-104">Sürüm 3.0, Windows Communication Foundation (WCF) kullanarak bir uygulama oluşturduğunuzda, uygulama, son kullanıcılarınızın gizlilik etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-104">When you build an application using Windows Communication Foundation (WCF), version 3.0, your application may impact your end-users' privacy.</span></span> <span data-ttu-id="3c030-105">Örneğin, uygulamanızın açıkça kullanıcı bilgilerini toplayabilir veya istek veya Web sitenize Internet üzerinden bilgi gönderme olabilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-105">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="3c030-106">Bu teknoloji, uygulamanızda Microsoft teknolojisi katıştırılmış içerirse, gizlilik etkileyebilecek kendi davranışa sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-106">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> <span data-ttu-id="3c030-107">Siz veya son kullanıcı seçmediğiniz sürece, bize göndermek WCF hiçbir bilgi Microsoft'a uygulamanızdan göndermez.</span><span class="sxs-lookup"><span data-stu-id="3c030-107">WCF does not send any information to Microsoft from your application unless you or the end-user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="3c030-108">Kısa WCF'de</span><span class="sxs-lookup"><span data-stu-id="3c030-108">WCF in Brief</span></span>  
 <span data-ttu-id="3c030-109">WCF, geliştiricilerin dağıtılmış uygulamalar oluşturmanıza olanak tanır Microsoft .NET Framework kullanılarak dağıtılmış bir Mesajlaşma çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="3c030-109">WCF is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="3c030-110">İki uygulama iletileri üstbilgi ve gövde bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3c030-110">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="3c030-111">Üstbilgiler, ileti yönlendirme, güvenlik bilgileri, işlemleri ve uygulama tarafından kullanılan hizmetler bağlı olarak daha fazla bilgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-111">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="3c030-112">İletiler genellikle varsayılan olarak şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="3c030-112">Messages are typically encrypted by default.</span></span> <span data-ttu-id="3c030-113">Kullanıldığında bir özel durum `BasicHttpBinding`, güvenli olmayan, eski Web Hizmetleri ile kullanılmak üzere tasarlanmış.</span><span class="sxs-lookup"><span data-stu-id="3c030-113">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="3c030-114">Uygulama Tasarımcısı, nihai tasarımı için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="3c030-114">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="3c030-115">SOAP gövdesi iletilerinde uygulamaya özgü verileri içerir; Ancak, bu veriler, uygulama tanımlı kişisel bilgiler gibi WCF şifreleme veya gizlilik özellikleri kullanarak güvenli hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-115">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using WCF encryption or confidentiality features.</span></span> <span data-ttu-id="3c030-116">Aşağıdaki bölümlerde olası gizliliği etkileyen özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3c030-116">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="3c030-117">İleti</span><span class="sxs-lookup"><span data-stu-id="3c030-117">Messaging</span></span>  
 <span data-ttu-id="3c030-118">İleti hedef belirten adres üstbilgisi her WCF ileti sahiptir ve yanıt nereye.</span><span class="sxs-lookup"><span data-stu-id="3c030-118">Each WCF message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="3c030-119">Uç nokta tanımlayan bir Tekdüzen Kaynak Tanımlayıcısı (URI) bir uç nokta adresi adresi bileşendir.</span><span class="sxs-lookup"><span data-stu-id="3c030-119">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="3c030-120">Adresine bir ağ adresi veya bir mantıksal adresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-120">The address can be a network address or a logical address.</span></span> <span data-ttu-id="3c030-121">Adres, makine adı (ana bilgisayar adı, tam etki alanı adı) ve bir IP adresi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-121">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="3c030-122">Geçici adresleme GUID'ler koleksiyonu her adresi keşfedilir için kullanılan veya uç nokta adresi, bir genel benzersiz tanımlayıcı (GUID) içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-122">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="3c030-123">Her ileti bir GUID olan bir ileti kimliği içeriyor.</span><span class="sxs-lookup"><span data-stu-id="3c030-123">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="3c030-124">Bu özellik WS adresleme başvuru standart izler.</span><span class="sxs-lookup"><span data-stu-id="3c030-124">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="3c030-125">WCF ileti katmanı, yerel makinede herhangi bir kişisel bilgi yazmaz.</span><span class="sxs-lookup"><span data-stu-id="3c030-125">The WCF messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="3c030-126">Bir hizmet geliştirici (örneğin, bir kişinin adını bir uç nokta adı kullanarak veya yaparak uç noktanın Web kişisel bilgiler dahil olmak üzere gibi bilgileri sunan bir hizmet oluşturduysanız ancak onu kişisel bilgileri ağ düzeyinde yay Açıklama Dili ancak WSDL erişmek için https kullanmak üzere istemcileri gerektirmeyen Hizmetleri).</span><span class="sxs-lookup"><span data-stu-id="3c030-126">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="3c030-127">Ayrıca, bir geliştirici çalıştırıyorsa [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kişisel bilgiler, aracın çıkış kullanıma sunan bir uç nokta karşı aracı, bu bilgileri içerebilir ve çıktı dosyasına yazılır yerel sabit disk.</span><span class="sxs-lookup"><span data-stu-id="3c030-127">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="3c030-128">Barındırma</span><span class="sxs-lookup"><span data-stu-id="3c030-128">Hosting</span></span>  
 <span data-ttu-id="3c030-129">WCF'de barındırma özelliği isteğe bağlı olarak başlatmak için veya birden çok uygulama arasında bağlantı noktası paylaşımı etkinleştirmek için uygulamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c030-129">The hosting feature in WCF allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="3c030-130">WCF uygulaması, Internet Information Services (IIS), benzer şekilde barındırılabilir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c030-130">An WCF application can be hosted in Internet Information Services (IIS), similar to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="3c030-131">Barındırma ağdaki belirli bir bilgi kullanıma sunmuyor ve veri makinede korumaz.</span><span class="sxs-lookup"><span data-stu-id="3c030-131">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="3c030-132">İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="3c030-132">Message Security</span></span>  
 <span data-ttu-id="3c030-133">WCF güvenlik Mesajlaşma uygulamalar için güvenlik özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c030-133">WCF security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="3c030-134">Kimlik doğrulama ve yetkilendirme sağlanan güvenlik işlevlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3c030-134">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="3c030-135">Kimlik doğrulaması istemcileri ve hizmetleri arasında kimlik bilgilerini geçirerek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-135">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="3c030-136">Kimlik doğrulama aktarım düzeyinde güvenlik yoluyla bulunabilir veya SOAP ileti güvenliği gibi düzeyi:</span><span class="sxs-lookup"><span data-stu-id="3c030-136">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
-   <span data-ttu-id="3c030-137">SOAP iletisi güvenlik kimlik doğrulama kullanıcı adı/parola, X.509 sertifikaları, Kerberos biletleri ve bunların tümü veren bağlı olarak kişisel bilgiler içerebilir, SAML belirteçleri gibi kimlik bilgileri üzerinden gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-137">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
-   <span data-ttu-id="3c030-138">Taşıma güvenliği kullanarak, kimlik doğrulaması yoluyla HTTP kimlik doğrulama şemasını gibi geleneksel aktarım kimlik doğrulama mekanizmaları yapılır (temel, Özet, anlaşma, tümleşik Windows kimlik doğrulaması, NTLM, None ve anonim) ve form kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="3c030-138">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="3c030-139">Kimlik doğrulama iletişim kuran uç noktaları arasında kurulan güvenli bir oturum neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-139">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="3c030-140">Oturumun güvenlik oturumu yaşam süresi bir GUID ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3c030-140">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="3c030-141">Aşağıdaki tabloda ne tutulur gösterir ve nerede.</span><span class="sxs-lookup"><span data-stu-id="3c030-141">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="3c030-142">Veri</span><span class="sxs-lookup"><span data-stu-id="3c030-142">Data</span></span>|<span data-ttu-id="3c030-143">Depolama</span><span class="sxs-lookup"><span data-stu-id="3c030-143">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="3c030-144">Kullanıcı adı, X.509 sertifikaları, Kerberos belirteçleri ve kimlik bilgilerini başvurular gibi sunu kimlik.</span><span class="sxs-lookup"><span data-stu-id="3c030-144">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="3c030-145">Windows kimlik bilgileri yönetim mekanizmalarını Windows sertifika deposunda gibi.</span><span class="sxs-lookup"><span data-stu-id="3c030-145">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="3c030-146">Kullanıcı adları ve parolalar gibi kullanıcı üyelik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="3c030-146">User membership information, such as usernames and passwords.</span></span>|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]<span data-ttu-id="3c030-147"> Üyelik sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="3c030-147"> membership providers.</span></span>|  
|<span data-ttu-id="3c030-148">İstemci hizmetinin kimliğini doğrulamak için kullanılan hizmet kimlik bilgilerini.</span><span class="sxs-lookup"><span data-stu-id="3c030-148">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="3c030-149">Hizmet uç noktası adresi.</span><span class="sxs-lookup"><span data-stu-id="3c030-149">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="3c030-150">Arayan bilgileri.</span><span class="sxs-lookup"><span data-stu-id="3c030-150">Caller information.</span></span>|<span data-ttu-id="3c030-151">Denetim günlükleri.</span><span class="sxs-lookup"><span data-stu-id="3c030-151">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="3c030-152">Denetim</span><span class="sxs-lookup"><span data-stu-id="3c030-152">Auditing</span></span>  
 <span data-ttu-id="3c030-153">Denetim başarılı ve başarısız kimlik doğrulama ve yetkilendirme olayların kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3c030-153">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="3c030-154">Denetim kayıtlarını içeren aşağıdaki veriler: URI, eylem URI'si ve arayanın kimliği hizmet.</span><span class="sxs-lookup"><span data-stu-id="3c030-154">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="3c030-155">İleti günlüğe kaydetme, üstbilgiler ve gövdeleri uygulamaya özgü verileri günlüğe çünkü ayrıca Denetim zaman yönetici ileti günlüğe kaydetme, (Bu açma veya kapatma) yapılandırmasını değiştirir kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3c030-155">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="3c030-156">İçin [!INCLUDE[wxp](../../../includes/wxp-md.md)], bir kayıt uygulama olay günlüğüne kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-156">For [!INCLUDE[wxp](../../../includes/wxp-md.md)], a record is logged in the application event log.</span></span> <span data-ttu-id="3c030-157">İçin [!INCLUDE[wv](../../../includes/wv-md.md)] ve [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], bir kayıt güvenlik olay günlüğüne kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-157">For [!INCLUDE[wv](../../../includes/wv-md.md)] and [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="3c030-158">İşlemler</span><span class="sxs-lookup"><span data-stu-id="3c030-158">Transactions</span></span>  
 <span data-ttu-id="3c030-159">WCF uygulaması işlem hizmetleri işlemleri özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c030-159">The transactions feature provides transactional services to a WCF application.</span></span>  
  
 <span data-ttu-id="3c030-160">İşlem yayma işleminde kullanılan işlem üstbilgileri işlem kimlikleri veya guıd'lerdir kaydı kimlikleri içeriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-160">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="3c030-161">İşlemler özelliği, işlem durumu yönetmek için Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) işlem Yöneticisi'ni (Windows bileşeni) kullanır.</span><span class="sxs-lookup"><span data-stu-id="3c030-161">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="3c030-162">Varsayılan olarak, işlem yöneticileri arasındaki iletişimler şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="3c030-162">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="3c030-163">İşlem yöneticileri uç nokta başvurular, işlem kimlikleri ve kaydı kimlikleri dayanıklı durumlarına bir parçası olarak oturum açabilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-163">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="3c030-164">Bu durum ömrü İşlem Yöneticisi'nin günlük dosyası ömrü tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="3c030-164">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="3c030-165">MSDTC hizmeti sahibi ve bu günlük dosyası tutar.</span><span class="sxs-lookup"><span data-stu-id="3c030-165">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="3c030-166">İşlemler özelliği Web Hizmetleri koordinasyonu ve WS-Atomic işlem standartlarını uygular.</span><span class="sxs-lookup"><span data-stu-id="3c030-166">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="3c030-167">Güvenilir oturumlar</span><span class="sxs-lookup"><span data-stu-id="3c030-167">Reliable Sessions</span></span>  
 <span data-ttu-id="3c030-168">Taşıma veya Ara hatalar oluştuğunda güvenilir oturumlar wcf'de ileti aktarımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c030-168">Reliable sessions in WCF provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="3c030-169">Sağladıkları bir tam olarak-temel Aktarımı'nın (örneğin, TCP bağlantısı bir kablosuz ağ üzerinde) bağlantısını keser veya bir ileti (bir HTTP proxy giden veya gelen ileti siliniyor) kaybeder olsa bile bir kez ileti aktarılması.</span><span class="sxs-lookup"><span data-stu-id="3c030-169">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="3c030-170">Güvenilir oturumlar da iletisi (çok yollu yönlendirme söz konusu olduğunda olabilir gibi), hangi iletileri gönderilen sipariş koruma yeniden sıralama kurtarın.</span><span class="sxs-lookup"><span data-stu-id="3c030-170">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="3c030-171">Güvenilir oturumlar WS-ReliableMessaging (WS-RM) protokolü kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3c030-171">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="3c030-172">Bunlar, belirli bir güvenilir oturum ile ilişkili tüm iletileri tanımlamak için kullanılan oturum bilgilerini içeren WS-RM üstbilgileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3c030-172">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="3c030-173">Her bir WS-RM oturumu bir GUID olan bir tanımlayıcı vardır.</span><span class="sxs-lookup"><span data-stu-id="3c030-173">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="3c030-174">Herhangi bir kişisel bilgi son kullanıcının makinede korunur.</span><span class="sxs-lookup"><span data-stu-id="3c030-174">No personal information is retained on the end-user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="3c030-175">Sıraya alınan kanalları</span><span class="sxs-lookup"><span data-stu-id="3c030-175">Queued Channels</span></span>  
 <span data-ttu-id="3c030-176">Kuyruklar alıcı uygulamanın adına gönderen bir uygulamadan gelen iletileri depolamak ve daha sonra alıcı uygulamaya bu iletileri iletebilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-176">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="3c030-177">Bunlar, örneğin, alıcı uygulamanın geçici olduğunda, ileti aktarımını alıcı uygulamalar için Gönderen uygulamalardan sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="3c030-177">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> <span data-ttu-id="3c030-178">WCF bir taşıma olarak Microsoft Message Queuing (MSMQ) kullanarak queuing için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c030-178">WCF provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="3c030-179">Sıraya alınan kanalları özellik üstbilgi iletiye eklemez.</span><span class="sxs-lookup"><span data-stu-id="3c030-179">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="3c030-180">Bunun yerine, uygun Message Queuing iletisi özellikler kümesi ile Message Queuing iletisi oluşturur ve ileti Message Queuing sırasına koymak için Message Queuing yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="3c030-180">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="3c030-181">Message Queuing, Windows ile birlikte gelen bir isteğe bağlı bir bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="3c030-181">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="3c030-182">Hiçbir bilgi olarak queuing altyapı Message Queuing kullandığından son kullanıcının makinede sıraya alınan kanalları özelliği tarafından korunur.</span><span class="sxs-lookup"><span data-stu-id="3c030-182">No information is retained on the end-user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="3c030-183">COM+ Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="3c030-183">COM+ Integration</span></span>  
 <span data-ttu-id="3c030-184">Bu özellik, WCF hizmetleri ile uyumlu olan hizmetleri oluşturmak için varolan COM ve COM + işlevi sarmalar.</span><span class="sxs-lookup"><span data-stu-id="3c030-184">This feature wraps existing COM and COM+ functionality to create services that are compatible with WCF services.</span></span> <span data-ttu-id="3c030-185">Bu özellik belirli üstbilgileri kullanmaz ve son kullanıcının makinedeki verileri korumaz.</span><span class="sxs-lookup"><span data-stu-id="3c030-185">This feature does not use specific headers and it does not retain data on the end-user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="3c030-186">COM hizmet bilinen adı</span><span class="sxs-lookup"><span data-stu-id="3c030-186">COM Service Moniker</span></span>  
 <span data-ttu-id="3c030-187">Bu, standart bir WCF istemcisi yönetilmeyen bir sarmalayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c030-187">This provides an unmanaged wrapper to a standard WCF client.</span></span> <span data-ttu-id="3c030-188">Bu özellik belirli üstbilgileri kablo yok veya makinedeki verileri devam etmez.</span><span class="sxs-lookup"><span data-stu-id="3c030-188">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="3c030-189">Eş Kanal</span><span class="sxs-lookup"><span data-stu-id="3c030-189">Peer Channel</span></span>  
 <span data-ttu-id="3c030-190">Eş kanal WCF kullanılarak taraflı uygulamaların geliştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c030-190">A peer channel enables development of multiparty applications using WCF.</span></span> <span data-ttu-id="3c030-191">Çok taraflı Mesajlaşma kafes bağlamında oluşur.</span><span class="sxs-lookup"><span data-stu-id="3c030-191">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="3c030-192">Kafesleri düğümleri katılabilirsiniz bir ad tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3c030-192">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="3c030-193">Eş kanal içindeki her bir düğümün kullanıcı tanımlı bir bağlantı noktası TCP dinleyiciyi oluşturur ve dayanıklılık sağlamak için kafes içindeki diğer düğümlere bağlantılarla oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3c030-193">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="3c030-194">Kafes içindeki diğer düğümlere bağlanmak için düğümleri de dinleyici adresi ve kafes içindeki diğer düğümlere de makinenin IP adresleriyle gibi bazı veriler, exchange.</span><span class="sxs-lookup"><span data-stu-id="3c030-194">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="3c030-195">Geçici kafes gönderilen iletileri ileti yanıltma ve üzerinde oynanmasını önlemek için gönderene ilgili güvenlik bilgileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-195">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="3c030-196">Herhangi bir kişisel bilgi son kullanıcının makinede depolanır.</span><span class="sxs-lookup"><span data-stu-id="3c030-196">No personal information is stored on the end-user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="3c030-197">BT Uzmanı deneyimi</span><span class="sxs-lookup"><span data-stu-id="3c030-197">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="3c030-198">İzleme</span><span class="sxs-lookup"><span data-stu-id="3c030-198">Tracing</span></span>  
 <span data-ttu-id="3c030-199">WCF altyapısının Tanılama özelliğini taşıma ve hizmet modeli katmanları ve etkinlikleri ve bu iletileriyle ilişkili olayları geçirir iletilerini günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3c030-199">The diagnostics feature of the WCF infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="3c030-200">Bu özellik varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="3c030-200">This feature is turned off by default.</span></span> <span data-ttu-id="3c030-201">Uygulama yapılandırma dosyası kullanarak etkindir ve izleme davranışı çalışma zamanında WCF WMI sağlayıcısı kullanılarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-201">It is enabled using the application’s configuration file and the tracing behavior may be modified using the WCF WMI provider at run time.</span></span> <span data-ttu-id="3c030-202">Etkinleştirildiğinde, izleme altyapısına iletileri, etkinlikler ve yapılandırılmış dinleyicileri için olayları işlemeyi içeren bir tanı izleme yayar.</span><span class="sxs-lookup"><span data-stu-id="3c030-202">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="3c030-203">Çıktı konumunu ve biçim yöneticinin dinleyicisi yapılandırma seçeneklerine göre belirlenir, ancak genellikle bir XML biçimli dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="3c030-203">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="3c030-204">Yönetici, izleme dosyaları üzerinde erişim denetimi listesi (ACL) ayarlanmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="3c030-204">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="3c030-205">Özellikle, Windows etkinleştirme sistem (WAS) tarafından barındırıldığında, yönetici dosya ortak sanal kök dizininden sunulan, bu değil istenirse değil emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c030-205">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="3c030-206">İzleme iki tür vardır: ileti günlüğe kaydetme ve tanılama hizmet modeli aşağıdaki bölümde açıklanan izleme,.</span><span class="sxs-lookup"><span data-stu-id="3c030-206">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="3c030-207">Her tür kendi izleme kaynağı yapılandırılır: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> ve <xref:System.ServiceModel>.</span><span class="sxs-lookup"><span data-stu-id="3c030-207">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="3c030-208">Bu günlük izleme kaynaklarının ikisinin uygulamayı yerel olarak veri yakalayın.</span><span class="sxs-lookup"><span data-stu-id="3c030-208">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="3c030-209">İleti Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="3c030-209">Message Logging</span></span>  
 <span data-ttu-id="3c030-210">İleti izleme kaynağı günlüğe kaydetme (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) iletilerini günlüğe kaydetmek için bir yönetici sistemi aracılığıyla akan sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c030-210">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="3c030-211">Yapılandırma yoluyla, iletilerin tamamını veya yalnızca ileti üstbilgilerini, taşıma ve/veya hizmet modeli katmanına günlüğe ve hatalı biçimlendirilmiş iletileri dahil edilip edilmeyeceğini oturum kullanıcı karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c030-211">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="3c030-212">Ayrıca, kullanıcının hangi iletileri günlüğe kısıtlamak için filtreleme yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c030-212">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="3c030-213">Varsayılan olarak, ileti günlüğe kaydetme devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="3c030-213">By default, message logging is disabled.</span></span> <span data-ttu-id="3c030-214">Yerel Makine Yöneticisi oturum açma ileti uygulama düzeyinde yönetici önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-214">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="3c030-215">Şifrelenmiş ve şifresi ileti günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="3c030-215">Encrypted and Decrypted Message Logging</span></span>  
 <span data-ttu-id="3c030-216">İletileri günlüğe, şifrelenmiş veya şifresi, aşağıdaki koşulları'nda açıklanan şekilde.</span><span class="sxs-lookup"><span data-stu-id="3c030-216">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="3c030-217">Günlük aktarma</span><span class="sxs-lookup"><span data-stu-id="3c030-217">Transport Logging</span></span>  
 <span data-ttu-id="3c030-218">Alınan ve aktarım düzeyinde gönderilen iletileri günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3c030-218">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="3c030-219">Bu iletiler tüm başlıkları içerir ve kablo ve alınma zaman gönderilmeden önce şifrelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="3c030-219">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="3c030-220">İletileri kablo gönderilmeden önce şifrelenir ve alındığında, günlüğe kaydedildikten de şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="3c030-220">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="3c030-221">Bir güvenlik protokolü kullanılan (https) bir özel durum olduğunda: Bunlar gönderilmeden önce ve kablo şifrelenmiş olsa bile alınma sonra şifresi sonra kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-221">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="3c030-222">Hizmet günlüğü</span><span class="sxs-lookup"><span data-stu-id="3c030-222">Service Logging</span></span>  
 <span data-ttu-id="3c030-223">Alınan veya hizmet modeli düzeyinde hemen önce ve kullanıcı kodu girdikten sonra kanal üstbilgi işlemeyi gerçekleştikten sonra gönderilen iletileri günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3c030-223">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="3c030-224">Güvenli ve kablo şifrelenmiş olsa bile bu düzeyde günlüğe kaydedilen iletileri şifresi çözülür.</span><span class="sxs-lookup"><span data-stu-id="3c030-224">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="3c030-225">Hatalı biçimlendirilmiş bir ileti günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="3c030-225">Malformed Message Logging</span></span>  
 <span data-ttu-id="3c030-226">WCF altyapı anlamak veya işleyemiyor iletileri günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3c030-226">Logs messages that the WCF infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="3c030-227">İletileri olarak kaydediliyor-diğer bir deyişle, veya şifrelenir</span><span class="sxs-lookup"><span data-stu-id="3c030-227">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="3c030-228">İletileri oturum açtığında şifresi çözülmüş veya şifrelenmemiş formunu WCF varsayılan güvenlik anahtarlarını ve potansiyel olarak kişisel bilgi gelen iletileri açmadan önce kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3c030-228">When messages are logged in decrypted or unencrypted form, by default WCF removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="3c030-229">Hangi bilgilerin kaldırılır, sonraki bölümlerde açıklanmıştır ve ne zaman.</span><span class="sxs-lookup"><span data-stu-id="3c030-229">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="3c030-230">Makine Yöneticisi ve uygulama dağıtıcı hem gerçekleştirmeniz gereken anahtarları ve büyük olasılıkla kişisel bilgileri günlüğe kaydetmek için varsayılan davranışı değiştirmek için belirli yapılandırma eylemleri.</span><span class="sxs-lookup"><span data-stu-id="3c030-230">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="3c030-231">Bilgi iletisi üstbilgileri şifresi çözülür ve şifrelenmemiş iletileri oturum açarken kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="3c030-231">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="3c030-232">Ne zaman iletileri şifresi çözülür ve şifrelenmemiş formunda, güvenlik anahtarları günlüğe kaydedilir ve potansiyel olarak kişisel bilgiler kaldırılır ileti üstbilgilerini ve İleti gövdeleri varsayılan olarak günlüğe kaydedilen önce.</span><span class="sxs-lookup"><span data-stu-id="3c030-232">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="3c030-233">Aşağıdaki liste, WCF anahtarları ve potansiyel olarak kişisel bilgi dikkate gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c030-233">The following list shows what WCF considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="3c030-234">Kaldırılan anahtarları:</span><span class="sxs-lookup"><span data-stu-id="3c030-234">Keys that are removed:</span></span>  
  
 <span data-ttu-id="3c030-235">\- İçin xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" ve xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"</span><span class="sxs-lookup"><span data-stu-id="3c030-235">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="3c030-236">wst:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="3c030-236">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="3c030-237">WST:Entropy</span><span class="sxs-lookup"><span data-stu-id="3c030-237">wst:Entropy</span></span>  
  
 <span data-ttu-id="3c030-238">\- İçin xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" ve xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="3c030-238">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="3c030-239">wsse:Password</span><span class="sxs-lookup"><span data-stu-id="3c030-239">wsse:Password</span></span>  
  
 <span data-ttu-id="3c030-240">wsse:nonce</span><span class="sxs-lookup"><span data-stu-id="3c030-240">wsse:Nonce</span></span>  
  
 <span data-ttu-id="3c030-241">Kaldırılır potansiyel olarak kişisel bilgi:</span><span class="sxs-lookup"><span data-stu-id="3c030-241">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="3c030-242">\- İçin xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" ve xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="3c030-242">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="3c030-243">wsse:username</span><span class="sxs-lookup"><span data-stu-id="3c030-243">wsse:Username</span></span>  
  
 <span data-ttu-id="3c030-244">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="3c030-244">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="3c030-245">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span><span class="sxs-lookup"><span data-stu-id="3c030-245">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="3c030-246">\<onaylama işlemi</span><span class="sxs-lookup"><span data-stu-id="3c030-246">\<Assertion</span></span>  
  
 <span data-ttu-id="3c030-247">MajorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="3c030-247">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="3c030-248">MinorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="3c030-248">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="3c030-249">Onaylama kimliği = "[ID]"</span><span class="sxs-lookup"><span data-stu-id="3c030-249">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="3c030-250">Veren = "[dize]"</span><span class="sxs-lookup"><span data-stu-id="3c030-250">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="3c030-251">IssueInstant = "[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="3c030-251">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="3c030-252">\<NotBefore koşulları "[dateTime]" NotOnOrAfter = "[dateTime]" = ></span><span class="sxs-lookup"><span data-stu-id="3c030-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span></span>  
  
 <span data-ttu-id="3c030-253">\<AudienceRestrictionCondition ></span><span class="sxs-lookup"><span data-stu-id="3c030-253">\<AudienceRestrictionCondition></span></span>  
  
 <span data-ttu-id="3c030-254">\<Hedef kitle > [URI]\</Audience > +</span><span class="sxs-lookup"><span data-stu-id="3c030-254">\<Audience>[uri]\</Audience>+</span></span>  
  
 <span data-ttu-id="3c030-255">\</ AudienceRestrictionCondition > \*</span><span class="sxs-lookup"><span data-stu-id="3c030-255">\</AudienceRestrictionCondition>\*</span></span>  
  
 <span data-ttu-id="3c030-256">\<DoNotCacheCondition / > \*</span><span class="sxs-lookup"><span data-stu-id="3c030-256">\<DoNotCacheCondition />\*</span></span>  
  
 <span data-ttu-id="3c030-257"><\!--soyut taban türü</span><span class="sxs-lookup"><span data-stu-id="3c030-257"><\!-- abstract base type</span></span>  
  
 <span data-ttu-id="3c030-258">\<Koşul / > \*</span><span class="sxs-lookup"><span data-stu-id="3c030-258">\<Condition />\*</span></span>  
  
 -->  
  
 <span data-ttu-id="3c030-259">\</ Koşulları >?</span><span class="sxs-lookup"><span data-stu-id="3c030-259">\</Conditions>?</span></span>  
  
 <span data-ttu-id="3c030-260">\<Öneri ></span><span class="sxs-lookup"><span data-stu-id="3c030-260">\<Advice></span></span>  
  
 <span data-ttu-id="3c030-261">\<AssertionIDReference > [kimlik]\</AssertionIDReference > \*</span><span class="sxs-lookup"><span data-stu-id="3c030-261">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="3c030-262">\<Onaylama işlemi > [onaylama]\</Assertion > \*</span><span class="sxs-lookup"><span data-stu-id="3c030-262">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="3c030-263">[herhangi bir] \*</span><span class="sxs-lookup"><span data-stu-id="3c030-263">[any]\*</span></span>  
  
 <span data-ttu-id="3c030-264">\</ Öneriler >?</span><span class="sxs-lookup"><span data-stu-id="3c030-264">\</Advice>?</span></span>  
  
 <span data-ttu-id="3c030-265"><\!--Soyut taban türleri</span><span class="sxs-lookup"><span data-stu-id="3c030-265"><\!-- Abstract base types</span></span>  
  
 <span data-ttu-id="3c030-266">\<Deyimi / > \*</span><span class="sxs-lookup"><span data-stu-id="3c030-266">\<Statement />\*</span></span>  
  
 <span data-ttu-id="3c030-267">\<SubjectStatement ></span><span class="sxs-lookup"><span data-stu-id="3c030-267">\<SubjectStatement></span></span>  
  
 <span data-ttu-id="3c030-268">\<Konu ></span><span class="sxs-lookup"><span data-stu-id="3c030-268">\<Subject></span></span>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 <span data-ttu-id="3c030-269">\<SubjectConfirmation ></span><span class="sxs-lookup"><span data-stu-id="3c030-269">\<SubjectConfirmation></span></span>  
  
 <span data-ttu-id="3c030-270">\<ConfirmationMethod > [anyURI]\</ConfirmationMethod > +</span><span class="sxs-lookup"><span data-stu-id="3c030-270">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="3c030-271">\<SubjectConfirmationData > [herhangi bir]\</SubjectConfirmationData >?</span><span class="sxs-lookup"><span data-stu-id="3c030-271">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="3c030-272">\<DS:KeyInfo >... \</ds:KeyInfo >?</span><span class="sxs-lookup"><span data-stu-id="3c030-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="3c030-273">\</ SubjectConfirmation >?</span><span class="sxs-lookup"><span data-stu-id="3c030-273">\</SubjectConfirmation>?</span></span>  
  
 <span data-ttu-id="3c030-274">\</ Konu ></span><span class="sxs-lookup"><span data-stu-id="3c030-274">\</Subject></span></span>  
  
 <span data-ttu-id="3c030-275">\</ SubjectStatement > \*</span><span class="sxs-lookup"><span data-stu-id="3c030-275">\</SubjectStatement>\*</span></span>  
  
 -->  
  
 <span data-ttu-id="3c030-276">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="3c030-276">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="3c030-277">AuthenticationMethod = "[URI]"</span><span class="sxs-lookup"><span data-stu-id="3c030-277">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="3c030-278">AuthenticationInstant = "[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="3c030-278">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="3c030-279">[Konu]</span><span class="sxs-lookup"><span data-stu-id="3c030-279">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="3c030-280">< AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="3c030-280"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="3c030-281">AuthorityKind = "[QName]"</span><span class="sxs-lookup"><span data-stu-id="3c030-281">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="3c030-282">Konumu = "[URI]"</span><span class="sxs-lookup"><span data-stu-id="3c030-282">Location="[uri]"</span></span>  
  
 <span data-ttu-id="3c030-283">Binding="[uri]"</span><span class="sxs-lookup"><span data-stu-id="3c030-283">Binding="[uri]"</span></span>  
  
 />*  
  
 <span data-ttu-id="3c030-284">\</ AuthenticationStatement > \*</span><span class="sxs-lookup"><span data-stu-id="3c030-284">\</AuthenticationStatement>\*</span></span>  
  
 <span data-ttu-id="3c030-285">\<AttributeStatement ></span><span class="sxs-lookup"><span data-stu-id="3c030-285">\<AttributeStatement></span></span>  
  
 <span data-ttu-id="3c030-286">[Konu]</span><span class="sxs-lookup"><span data-stu-id="3c030-286">[Subject]</span></span>  
  
 <span data-ttu-id="3c030-287">\<Özniteliği</span><span class="sxs-lookup"><span data-stu-id="3c030-287">\<Attribute</span></span>  
  
 <span data-ttu-id="3c030-288">AttributeName = "[dize]"</span><span class="sxs-lookup"><span data-stu-id="3c030-288">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="3c030-289">AttributeNamespace = "[URI]"</span><span class="sxs-lookup"><span data-stu-id="3c030-289">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 <span data-ttu-id="3c030-290">\</ Öznitelik > +</span><span class="sxs-lookup"><span data-stu-id="3c030-290">\</Attribute>+</span></span>  
  
 <span data-ttu-id="3c030-291">\</ AttributeStatement > \*</span><span class="sxs-lookup"><span data-stu-id="3c030-291">\</AttributeStatement>\*</span></span>  
  
 <span data-ttu-id="3c030-292">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="3c030-292">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="3c030-293">Kaynak = "[URI]"</span><span class="sxs-lookup"><span data-stu-id="3c030-293">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="3c030-294">Karar = "[izin&#124;Reddet&#124;belirsiz]"</span><span class="sxs-lookup"><span data-stu-id="3c030-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="3c030-295">[Konu]</span><span class="sxs-lookup"><span data-stu-id="3c030-295">[Subject]</span></span>  
  
 <span data-ttu-id="3c030-296">\<Eylem Namespace = "[URI]" > [dize] \< /eylem > +</span><span class="sxs-lookup"><span data-stu-id="3c030-296">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 <span data-ttu-id="3c030-297">\<Kanıt ></span><span class="sxs-lookup"><span data-stu-id="3c030-297">\<Evidence></span></span>  
  
 <span data-ttu-id="3c030-298">\<AssertionIDReference > [kimlik]\</AssertionIDReference > +</span><span class="sxs-lookup"><span data-stu-id="3c030-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="3c030-299">\<Onaylama işlemi > [onaylama]\</Assertion > +</span><span class="sxs-lookup"><span data-stu-id="3c030-299">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="3c030-300">\</ Kanıtlayan bilgiler >?</span><span class="sxs-lookup"><span data-stu-id="3c030-300">\</Evidence>?</span></span>  
  
 <span data-ttu-id="3c030-301">\</ AuthorizationDecisionStatement > \*</span><span class="sxs-lookup"><span data-stu-id="3c030-301">\</AuthorizationDecisionStatement>\*</span></span>  
  
 <span data-ttu-id="3c030-302">\</ Onaylama ></span><span class="sxs-lookup"><span data-stu-id="3c030-302">\</Assertion></span></span>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="3c030-303">İleti gövdeleri şifresi çözülür ve şifrelenmemiş iletileri günlüğe kaydetme bırakırken kaldırılan bilgileri</span><span class="sxs-lookup"><span data-stu-id="3c030-303">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="3c030-304">Daha önce açıklandığı gibi WCF kaldırır anahtarları ve şifresi çözülür ve şifrelenmemiş günlüğe kaydedilen iletilere ileti üstbilgilerini bilinen büyük olasılıkla kişisel bilgileri.</span><span class="sxs-lookup"><span data-stu-id="3c030-304">As previously described, WCF removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="3c030-305">Ayrıca, WCF anahtarları ve bilinen potansiyel olarak kişisel bilgi İleti gövdeleri gövde öğeleri ve anahtar değişimi içinde yer alan güvenlik iletileri tanımlayan eylemleri aşağıdaki listeden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3c030-305">In addition, WCF removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="3c030-306">Aşağıdaki ad alanları için:</span><span class="sxs-lookup"><span data-stu-id="3c030-306">For the following namespaces:</span></span>  
  
 <span data-ttu-id="3c030-307">xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" ve xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (örneğin, hiçbir eylem varsa kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="3c030-307">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="3c030-308">Bilgiler, anahtar değişimi içeren bu gövdesi öğelerini için kaldırılır:</span><span class="sxs-lookup"><span data-stu-id="3c030-308">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="3c030-309">wst:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="3c030-309">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="3c030-310">wst:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="3c030-310">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="3c030-311">wst:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="3c030-311">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="3c030-312">Bilgi de her aşağıdaki eylemlerden birini kaldırılır:</span><span class="sxs-lookup"><span data-stu-id="3c030-312">Information is also removed for each of the following Actions:</span></span>  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend  
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="3c030-313">Hiçbir bilgi uygulamaya özgü üstbilgi ve gövde verileri kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="3c030-313">No Information Is Removed from Application-specific Headers and Body Data</span></span>  
 <span data-ttu-id="3c030-314">WCF uygulamaya özgü üstbilgileri (örneğin, sorgu dizeleri) veya gövde verileri (örneğin, kredi kartı numarası) kişisel bilgilerin izlemez.</span><span class="sxs-lookup"><span data-stu-id="3c030-314">WCF does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="3c030-315">İleti günlüğe kaydetme açık olduğunda, uygulamaya özgü üstbilgilerindeki kişisel bilgileri ve gövde bilgileri günlüklerde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-315">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="3c030-316">Yeniden uygulama dağıtıcı ACL'leri yapılandırma ve günlük dosyalarını ayarlanmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="3c030-316">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="3c030-317">Kendisi ayrıca kendisinin görünür olması için bu bilgileri istemez veya günlüğe kaydedilir sonra ki bu günlük dosyalarındaki bilgileri filtrelemenize oturum kapatma etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c030-317">He also can turn off logging if he does not want this information to be visible, or he may filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="3c030-318">Hizmet modeli izleme</span><span class="sxs-lookup"><span data-stu-id="3c030-318">Service Model Tracing</span></span>  
 <span data-ttu-id="3c030-319">Hizmet modeli izleme kaynağı (<xref:System.ServiceModel>) ilgili ileti işleme etkinliklerini ve olayları izlemeyi etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="3c030-319">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="3c030-320">Bu özellik .NET Framework tanılama işlevlerini kullanır <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="3c030-320">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="3c030-321">İle <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> özelliği, konumu ve onun ACL kullanıcı-.NET Framework uygulama yapılandırma dosyaları kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-321">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="3c030-322">Yönetici izleme etkinleştirdiğinde ileti günlüğe kaydetme gibi dosya konumuna her zaman yapılandırılır; Bu nedenle, ACL yönetici denetler.</span><span class="sxs-lookup"><span data-stu-id="3c030-322">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="3c030-323">Bir ileti kapsamda olduğunda izlemeleri ileti üstbilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3c030-323">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="3c030-324">Önceki bölümde ileti üstbilgilerini potansiyel olarak kişisel bilgilerinizi gizlemek için aynı kurallar geçerlidir: daha önce tanımlanan kişisel bilgiler izlemeleri üstbilgilerinde varsayılan olarak kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="3c030-324">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="3c030-325">Makine Yöneticisi ve uygulama dağıtıcı yapılandırmanın büyük olasılıkla kişisel bilgileri günlüğe kaydetmek için değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c030-325">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="3c030-326">Ancak, uygulamaya özgü üstbilgilerinde bulunan kişisel bilgileri içindeki günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-326">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="3c030-327">Uygulama dağıtıcı, ACL'leri yapılandırma ve izleme dosyaları ayarlanmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="3c030-327">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="3c030-328">Kendisi ayrıca izlemeyi devre dışı kendisinin görünür olması için bu bilgileri istemediği ya da sonra günlüğe kaydedilir bu bilgileri izleme dosyalarından filtreleyebilirsiniz kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c030-328">He also can turn off tracing if he does not want this information to be visible, or he can filter out this information from the trace files after it is logged.</span></span>  
  
 <span data-ttu-id="3c030-329">Farklı etkinlikler benzersiz kimlikler (etkinlik kimlikleri ve genellikle bir GUID denir) kapsamında ServiceModel izleme, bir ileti olarak birbirine bağlamak altyapısının farklı bölümleri aracılığıyla akar.</span><span class="sxs-lookup"><span data-stu-id="3c030-329">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="3c030-330">Özel izleme dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="3c030-330">Custom Trace Listeners</span></span>  
 <span data-ttu-id="3c030-331">Günlüğe kaydetme ve izleme her iki ileti için özel İzleme dinleyicisi, hangi izlemeleri ve iletileri kablo (örneğin, bir uzak veritabanına) gönderebilir yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-331">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="3c030-332">Uygulama dağıtıcı özel dinleyicileri yapılandırma veya bunu yapmak kullanıcıları etkinleştirme için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="3c030-332">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="3c030-333">Kendisi Ayrıca uzak konumda kullanıma sunulan herhangi bir kişisel bilgi ve bu konuma ACL'ler düzgün bir şekilde uygulamak için sorumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="3c030-333">He is also responsible for any personal information exposed at the remote location, and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="3c030-334">BT uzmanları için diğer özellikleri</span><span class="sxs-lookup"><span data-stu-id="3c030-334">Other features for IT Professionals</span></span>  
 <span data-ttu-id="3c030-335">WCF WCF altyapı yapılandırma bilgileri (Windows ile birlikte gelen) WMI üzerinden kullanıma sunan bir WMI sağlayıcısı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3c030-335">WCF has a WMI provider that exposes the WCF infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="3c030-336">Varsayılan olarak, WMI arabirimi yöneticiler tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-336">By default, the WMI interface is available to administrators.</span></span>  
  
 <span data-ttu-id="3c030-337">WCF yapılandırması, .NET Framework yapılandırma mekanizması kullanır.</span><span class="sxs-lookup"><span data-stu-id="3c030-337">WCF configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="3c030-338">Yapılandırma dosyaları makinede depolanır.</span><span class="sxs-lookup"><span data-stu-id="3c030-338">The configuration files are stored on the machine.</span></span> <span data-ttu-id="3c030-339">Uygulama geliştiricisi ve yönetici yapılandırma dosyalarını ve ACL her uygulamanın gereksinimleri için oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3c030-339">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="3c030-340">Bir yapılandırma dosyası, uç nokta adresleri ve sertifika deposundaki sertifikalar bağlantılar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-340">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="3c030-341">Sertifikalar, uygulama tarafından kullanılan özellikler çeşitli özelliklerini yapılandırmak için uygulama verilerini sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-341">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="3c030-342">WCF de çağırarak .NET Framework işlem dökümü işlevselliğini kullanır <xref:System.Environment.FailFast%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3c030-342">WCF also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="3c030-343">BT Uzmanı araçlarını</span><span class="sxs-lookup"><span data-stu-id="3c030-343">IT Pro Tools</span></span>  
 <span data-ttu-id="3c030-344">WCF aynı zamanda Windows SDK'ın sevk aşağıdaki BT uzmanları araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c030-344">WCF also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="3c030-345">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="3c030-345">SvcTraceViewer.exe</span></span>  
 <span data-ttu-id="3c030-346">Görüntüleyici WCF izleme dosyaları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3c030-346">The viewer displays WCF trace files.</span></span> <span data-ttu-id="3c030-347">Görüntüleyici ne olursa olsun bilgileri izlemeleri bulunan gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c030-347">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="3c030-348">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="3c030-348">SvcConfigEditor.exe</span></span>  
 <span data-ttu-id="3c030-349">Düzenleyici WCF yapılandırma dosyalarını oluşturmak ve düzenlemek olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3c030-349">The editor allows the user to create and edit WCF configuration files.</span></span> <span data-ttu-id="3c030-350">Düzenleyici ne olursa olsun bilgileri yapılandırma dosyalarında bulunan gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c030-350">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="3c030-351">Aynı görevi bir metin düzenleyicisiyle gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-351">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodelreg"></a><span data-ttu-id="3c030-352">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="3c030-352">ServiceModel_Reg</span></span>  
 <span data-ttu-id="3c030-353">Bu aracı bir makinede ServiceModel yükler yönetmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3c030-353">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="3c030-354">Çalıştırır ve bu süreçte WCF yükleme yapılandırma hakkında bilgi görüntüleyebilir, aracı konsol penceresinde durum iletilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3c030-354">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the WCF installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="3c030-355">WSATConfig.exe ve WSATUI.dll</span><span class="sxs-lookup"><span data-stu-id="3c030-355">WSATConfig.exe and WSATUI.dll</span></span>  
 <span data-ttu-id="3c030-356">Bu araçlar, WCF birlikte çalışabilen WS-AtomicTransaction ağ desteğini yapılandırmak BT uzmanları olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c030-356">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in WCF.</span></span> <span data-ttu-id="3c030-357">Araçları görüntülemek ve kayıt defterinde depolanan en yaygın kullanılan WS-AtomicTransaction ayarlarının değerleri değiştirmek izin verin.</span><span class="sxs-lookup"><span data-stu-id="3c030-357">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="3c030-358">Çapraz kesme özellikleri</span><span class="sxs-lookup"><span data-stu-id="3c030-358">Cross-cutting Features</span></span>  
 <span data-ttu-id="3c030-359">Çapraz kesme özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="3c030-359">The following features are cross-cutting.</span></span> <span data-ttu-id="3c030-360">Diğer bir deyişle, bunlar herhangi bir önceki özellikleri ile oluşturulmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-360">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="3c030-361">Hizmet Çerçevesi</span><span class="sxs-lookup"><span data-stu-id="3c030-361">Service Framework</span></span>  
 <span data-ttu-id="3c030-362">Üstbilgiler, bir ileti CLR sınıfının bir örneği ile ilişkilendirir GUID'dir bir örnek kimliği içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-362">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="3c030-363">Web Hizmetleri Açıklama Dili (WSDL) bağlantı noktası bir tanım içeriyor.</span><span class="sxs-lookup"><span data-stu-id="3c030-363">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="3c030-364">Her bağlantı noktası bir uç nokta adresi ve uygulama tarafından kullanılan hizmetler temsil eden bir bağlaması var.</span><span class="sxs-lookup"><span data-stu-id="3c030-364">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="3c030-365">WSDL gösterme, yapılandırmayı kullanarak devre dışı açılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c030-365">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="3c030-366">Hiçbir bilgi makinede korunur.</span><span class="sxs-lookup"><span data-stu-id="3c030-366">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c030-367">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c030-367">See Also</span></span>  
 [<span data-ttu-id="3c030-368">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3c030-368">Windows Communication Foundation</span></span>](http://msdn.microsoft.com/library/fd327ade-0260-4c40-adbe-b74645ba3277)  
 [<span data-ttu-id="3c030-369">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="3c030-369">Security</span></span>](../../../docs/framework/wcf/feature-details/security.md)
