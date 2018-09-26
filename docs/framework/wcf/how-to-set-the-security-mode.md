---
title: 'Nasıl yapılır: Güvenlik Modunu Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
author: BrucePerlerMS
ms.openlocfilehash: 32fd1ebede841488d1bfabd2f92bd3fb1ffb55e8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087349"
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="39aa7-102">Nasıl yapılır: Güvenlik Modunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="39aa7-102">How to: Set the Security Mode</span></span>
<span data-ttu-id="39aa7-103">Windows Communication Foundation (WCF) güvenlik üzerinde en önceden tanımlanmış bağlamaları bulunan üç yaygın güvenlik modu vardır: aktarım iletisi ve "ileti kimlik bilgileri ile aktarma."</span><span class="sxs-lookup"><span data-stu-id="39aa7-103">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="39aa7-104">İki ek modları için iki bağlamaları belirli: "yalnızca Aktarım-credential" modu sonucuna <xref:System.ServiceModel.BasicHttpBinding>ve bulunan "Hem" modu <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="39aa7-104">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="39aa7-105">Ancak, bu konuda üç yaygın güvenlik modlarını yoğunlaşır: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, ve <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="39aa7-105">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
 <span data-ttu-id="39aa7-106">Önceden tanımlanmış her bağlama tüm bu modlardan desteklediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="39aa7-106">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="39aa7-107">Bu konuda moduyla ayarlar <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.NetTcpBinding> sınıfları ve programlı ve yapılandırma yoluyla modunu ayarlama işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="39aa7-107">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>  
  
 <span data-ttu-id="39aa7-108">Daha fazla bilgi için bkz, WCF güvenlik bkz [güvenliğine genel bakış](../../../docs/framework/wcf/feature-details/security-overview.md), [Hizmetleri güvenli hale getirme](../../../docs/framework/wcf/securing-services.md), ve [Hizmetleri güvenli hale getirme ve istemciler](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="39aa7-108">For more information, see WCF security, see [Security Overview](../../../docs/framework/wcf/feature-details/security-overview.md), [Securing Services](../../../docs/framework/wcf/securing-services.md), and [Securing Services and Clients](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="39aa7-109">Aktarım modu ve ileti hakkında daha fazla bilgi için bkz. [aktarım güvenliği](../../../docs/framework/wcf/feature-details/transport-security.md) ve [ileti güvenliği](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="39aa7-109">For more information about transport mode and message, see [Transport Security](../../../docs/framework/wcf/feature-details/transport-security.md) and [Message Security](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
### <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="39aa7-110">Kod içinde güvenlik modunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="39aa7-110">To set the security mode in code</span></span>  
  
1.  <span data-ttu-id="39aa7-111">Kullanmakta olduğunuz bağlama sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="39aa7-111">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="39aa7-112">Önceden tanımlanmış bağlamaları bir listesi için bkz. [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="39aa7-112">For a list of predefined bindings, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="39aa7-113">Bu örnek, bir örneğini oluşturur. <xref:System.ServiceModel.WSHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="39aa7-113">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>  
  
2.  <span data-ttu-id="39aa7-114">Ayarlama `Mode` özelliği tarafından döndürülen nesne `Security` özelliği.</span><span class="sxs-lookup"><span data-stu-id="39aa7-114">Set the `Mode` property of the object returned by the `Security` property.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     <span data-ttu-id="39aa7-115">Alternatif olarak, aşağıdaki kodda gösterildiği gibi modu iletisine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="39aa7-115">Alternatively, set the mode to message, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     <span data-ttu-id="39aa7-116">Veya aşağıdaki kodda gösterildiği gibi ileti kimlik bilgileri ile aktarma için moduna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="39aa7-116">Or set the mode to transport with message credentials, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3.  <span data-ttu-id="39aa7-117">Bağlama oluşturucusunun içinde aşağıdaki kodda gösterildiği gibi modunu ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39aa7-117">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="39aa7-118">ClientCredentialType özelliğini ayarlama</span><span class="sxs-lookup"><span data-stu-id="39aa7-118">Setting the ClientCredentialType Property</span></span>  
 <span data-ttu-id="39aa7-119">Üç değerden birini modunu ayarlama belirler nasıl ayarlanacağını `ClientCredentialType` özelliği.</span><span class="sxs-lookup"><span data-stu-id="39aa7-119">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="39aa7-120">Örnek olarak, <xref:System.ServiceModel.WSHttpBinding> modu ayarını sınıfı `Transport` ayarlamalısınız anlamına gelir <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> özelliği <xref:System.ServiceModel.HttpTransportSecurity> sınıfı uygun değeri.</span><span class="sxs-lookup"><span data-stu-id="39aa7-120">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="39aa7-121">Aktarım modu için ClientCredentialType özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="39aa7-121">To set the ClientCredentialType property for Transport mode</span></span>  
  
1.  <span data-ttu-id="39aa7-122">Bağlama örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="39aa7-122">Create an instance of the binding.</span></span>  
  
2.  <span data-ttu-id="39aa7-123">Ayarlama `Mode` özelliğini `Transport`.</span><span class="sxs-lookup"><span data-stu-id="39aa7-123">Set the `Mode` property to `Transport`.</span></span>  
  
3.  <span data-ttu-id="39aa7-124">Ayarlama `ClientCredential` özelliğini uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="39aa7-124">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="39aa7-125">Aşağıdaki kod özelliği ayarlar `Windows`.</span><span class="sxs-lookup"><span data-stu-id="39aa7-125">The following code sets the property to `Windows`.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="39aa7-126">İleti modu ClientCredentialType özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="39aa7-126">To set the ClientCredentialType property for Message mode</span></span>  
  
1.  <span data-ttu-id="39aa7-127">Bağlama örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="39aa7-127">Create an instance of the binding.</span></span>  
  
2.  <span data-ttu-id="39aa7-128">Ayarlama `Mode` özelliğini `Message`.</span><span class="sxs-lookup"><span data-stu-id="39aa7-128">Set the `Mode` property to `Message`.</span></span>  
  
3.  <span data-ttu-id="39aa7-129">Ayarlama `ClientCredential` özelliğini uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="39aa7-129">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="39aa7-130">Aşağıdaki kod özelliği ayarlar `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="39aa7-130">The following code sets the property to `Certificate`.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="39aa7-131">Yapılandırma modu ve ClientCredentialType özelliği ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="39aa7-131">To set the Mode and ClientCredentialType property in configuration</span></span>  
  
1.  <span data-ttu-id="39aa7-132">Uygun bağlama öğeye ekleme [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyasının öğesi.</span><span class="sxs-lookup"><span data-stu-id="39aa7-132">Add an appropriate binding element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="39aa7-133">Aşağıdaki örnek ekler bir [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="39aa7-133">The following example adds a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
2.  <span data-ttu-id="39aa7-134">Ekleme bir `<binding>` öğesi ve kümesi kendi `name` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="39aa7-134">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="39aa7-135">Ekleme bir `<security>` öğesi ve kümesi `mode` özniteliğini `Message`, `Transport`, veya `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="39aa7-135">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>  
  
4.  <span data-ttu-id="39aa7-136">Modu ayarlanırsa `Transport`, ekleme bir `<transport>` öğesi ve kümesi `clientCredential` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="39aa7-136">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>  
  
     <span data-ttu-id="39aa7-137">Aşağıdaki örnekte modu ayarlar "`Transport"`ve ardından ayarlar `clientCredentialType` özniteliği `<transport>` öğesine"`Windows"`.</span><span class="sxs-lookup"><span data-stu-id="39aa7-137">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" />  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     <span data-ttu-id="39aa7-138">Alternatif olarak, kümesinin `security mode` için "`Message"`ve ardından bir `<"message">` öğesi.</span><span class="sxs-lookup"><span data-stu-id="39aa7-138">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="39aa7-139">Bu örnekte ayarlar `clientCredentialType` için "`Certificate"`.</span><span class="sxs-lookup"><span data-stu-id="39aa7-139">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" />  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     <span data-ttu-id="39aa7-140">Kullanarak <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> değeri özel bir durumdur ve aşağıda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="39aa7-140">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>  
  
### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="39aa7-141">TransportWithMessageCredential kullanma</span><span class="sxs-lookup"><span data-stu-id="39aa7-141">Using TransportWithMessageCredential</span></span>  
 <span data-ttu-id="39aa7-142">Güvenlik modunu ayarlama zaman `TransportWithMessageCredential`, aktarım düzeyi güvenlik sağlayan gerçek mekanizması taşıma belirler.</span><span class="sxs-lookup"><span data-stu-id="39aa7-142">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="39aa7-143">Örneğin, HTTP protokolü, HTTP (HTTPS) üzerinden Güvenli Yuva Katmanı (SSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="39aa7-143">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="39aa7-144">Bu nedenle, ayarı `ClientCredentialType` herhangi bir aktarım güvenliği nesnenin özellik (gibi <xref:System.ServiceModel.HttpTransportSecurity>) göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="39aa7-144">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="39aa7-145">Diğer bir deyişle, yalnızca ayarlayabilirsiniz `ClientCredentialType` ileti güvenlik nesnesi (için `WSHttpBinding` bağlamayı <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> nesne).</span><span class="sxs-lookup"><span data-stu-id="39aa7-145">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>  
  
 <span data-ttu-id="39aa7-146">Daha fazla bilgi için [nasıl yapılır: kullanım taşıma Güveniği ve ileti kimlik bilgilerini](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="39aa7-146">For more information, see [How to: Use Transport Security and Message Credentials](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39aa7-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="39aa7-147">See Also</span></span>  
 [<span data-ttu-id="39aa7-148">Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="39aa7-148">How to: Configure a Port with an SSL Certificate</span></span>](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="39aa7-149">Nasıl yapılır: Aktarım Güvenliği ve İleti Kimlik Bilgilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="39aa7-149">How to: Use Transport Security and Message Credentials</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [<span data-ttu-id="39aa7-150">Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="39aa7-150">Transport Security</span></span>](../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="39aa7-151">İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="39aa7-151">Message Security</span></span>](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [<span data-ttu-id="39aa7-152">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="39aa7-152">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="39aa7-153">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="39aa7-153">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="39aa7-154">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="39aa7-154">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)  
 [<span data-ttu-id="39aa7-155">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="39aa7-155">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)  
 [<span data-ttu-id="39aa7-156">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="39aa7-156">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
