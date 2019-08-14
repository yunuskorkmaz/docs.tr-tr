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
ms.openlocfilehash: 6bd81bd24d28f0a9e318d60a3b7fb4aa059f9a49
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971987"
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="a6664-102">Nasıl yapılır: Güvenlik Modunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="a6664-102">How to: Set the Security Mode</span></span>

<span data-ttu-id="a6664-103">Windows Communication Foundation (WCF) güvenliği, en önceden tanımlı bağlamalarda bulunan üç ortak güvenlik moduna sahiptir: Transport, Message ve "ileti kimlik bilgileri ile taşıma."</span><span class="sxs-lookup"><span data-stu-id="a6664-103">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="a6664-104">İki bağlama özgü iki ek mod vardır: üzerinde <xref:System.ServiceModel.BasicHttpBinding>bulunan "Transport-Credential Only" modu ve <xref:System.ServiceModel.NetMsmqBinding>üzerinde bulunan "both" modu.</span><span class="sxs-lookup"><span data-stu-id="a6664-104">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="a6664-105">Ancak, bu konu üç ortak güvenlik modu üzerinde yoğunlaşır: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>ve <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="a6664-105">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>

<span data-ttu-id="a6664-106">Önceden tanımlanmış her bağlamanın bu modların tümünü desteklediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a6664-106">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="a6664-107">Bu konu, <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.NetTcpBinding> sınıfları ile modunu ayarlar ve modu hem programlı olarak hem de yapılandırma aracılığıyla ayarlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6664-107">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>

<span data-ttu-id="a6664-108">Daha fazla bilgi için bkz. WCF güvenliği, [güvenlik genel bakış](../../../docs/framework/wcf/feature-details/security-overview.md), [hizmetleri güvenli hale](../../../docs/framework/wcf/securing-services.md)getirme ve [Hizmetleri ve istemcileri güvenli hale getirme](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="a6664-108">For more information, see WCF security, see [Security Overview](../../../docs/framework/wcf/feature-details/security-overview.md), [Securing Services](../../../docs/framework/wcf/securing-services.md), and [Securing Services and Clients](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="a6664-109">Aktarım modu ve ileti hakkında daha fazla bilgi için bkz. [Aktarım güvenliği](../../../docs/framework/wcf/feature-details/transport-security.md) ve [ileti güvenliği](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="a6664-109">For more information about transport mode and message, see [Transport Security](../../../docs/framework/wcf/feature-details/transport-security.md) and [Message Security](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>

## <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="a6664-110">Koddaki güvenlik modunu ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a6664-110">To set the security mode in code</span></span>

1. <span data-ttu-id="a6664-111">Kullandığınız bağlama sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a6664-111">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="a6664-112">Önceden tanımlanmış bağlamaların listesi için bkz. [sistem tarafından sunulan bağlamalar](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="a6664-112">For a list of predefined bindings, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="a6664-113">Bu örnek, <xref:System.ServiceModel.WSHttpBinding> sınıfının bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a6664-113">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

2. <span data-ttu-id="a6664-114">Özelliği tarafından döndürülen nesnesinin `Mode` `Security` özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a6664-114">Set the `Mode` property of the object returned by the `Security` property.</span></span>

     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]

     <span data-ttu-id="a6664-115">Alternatif olarak, aşağıdaki kodda gösterildiği gibi modunu ileti olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a6664-115">Alternatively, set the mode to message, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]

     <span data-ttu-id="a6664-116">Ya da aşağıdaki kodda gösterildiği gibi modu ileti kimlik bilgileriyle taşıma olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a6664-116">Or set the mode to transport with message credentials, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]

3. <span data-ttu-id="a6664-117">Ayrıca, aşağıdaki kodda gösterildiği gibi, bağlama oluşturucusunda modu da ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6664-117">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]

## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="a6664-118">ClientCredentialType özelliği ayarlanıyor</span><span class="sxs-lookup"><span data-stu-id="a6664-118">Setting the ClientCredentialType Property</span></span>

<span data-ttu-id="a6664-119">Modunun üç değerden birine ayarlanması, `ClientCredentialType` özelliği nasıl ayarlayabileceğinizi belirler.</span><span class="sxs-lookup"><span data-stu-id="a6664-119">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="a6664-120">Örneğin, <xref:System.ServiceModel.WSHttpBinding> sınıfını kullanarak modunu olarak `Transport` ayarlamak, <xref:System.ServiceModel.HttpTransportSecurity> sınıfının <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> özelliğini uygun bir değere ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6664-120">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="a6664-121">Taşıma modu için ClientCredentialType özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a6664-121">To set the ClientCredentialType property for Transport mode</span></span>

1. <span data-ttu-id="a6664-122">Bağlamanın bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a6664-122">Create an instance of the binding.</span></span>

2. <span data-ttu-id="a6664-123">Ayarlama `Mode` özelliğini `Transport`.</span><span class="sxs-lookup"><span data-stu-id="a6664-123">Set the `Mode` property to `Transport`.</span></span>

3. <span data-ttu-id="a6664-124">`ClientCredential` Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a6664-124">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="a6664-125">Aşağıdaki kod özelliği olarak `Windows`ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a6664-125">The following code sets the property to `Windows`.</span></span>

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="a6664-126">Ileti modu için ClientCredentialType özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a6664-126">To set the ClientCredentialType property for Message mode</span></span>

1. <span data-ttu-id="a6664-127">Bağlamanın bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a6664-127">Create an instance of the binding.</span></span>

2. <span data-ttu-id="a6664-128">Ayarlama `Mode` özelliğini `Message`.</span><span class="sxs-lookup"><span data-stu-id="a6664-128">Set the `Mode` property to `Message`.</span></span>

3. <span data-ttu-id="a6664-129">`ClientCredential` Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a6664-129">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="a6664-130">Aşağıdaki kod özelliği olarak `Certificate`ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a6664-130">The following code sets the property to `Certificate`.</span></span>

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="a6664-131">Yapılandırmada Mode ve ClientCredentialType özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a6664-131">To set the Mode and ClientCredentialType property in configuration</span></span>

1. <span data-ttu-id="a6664-132">Yapılandırma dosyasının [ \<Bindings >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesine uygun bir bağlama öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a6664-132">Add an appropriate binding element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="a6664-133">Aşağıdaki örnek bir [ \<WSHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="a6664-133">The following example adds a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

2. <span data-ttu-id="a6664-134">Bir `<binding>` öğesi ekleyin ve `name` özniteliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a6664-134">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="a6664-135">`<security>` Bir öğesi ekleyin ve `mode` özniteliği `Message`, `Transport`veya olarakayarlayın.`TransportWithMessageCredential`</span><span class="sxs-lookup"><span data-stu-id="a6664-135">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

4. <span data-ttu-id="a6664-136">Mod olarak `Transport`ayarlandıysa, bir `<transport>` öğesi ekleyin ve `clientCredential` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a6664-136">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>

     <span data-ttu-id="a6664-137">Aşağıdaki örnek,`Transport"`modunu "olarak ayarlar ve sonra `<transport>` öğesinin `clientCredentialType` özniteliğini"`Windows"`olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a6664-137">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="a6664-138">Alternatif olarak, `security mode` `<"message">` öğesini ve ardından`Message"`öğesini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a6664-138">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="a6664-139">Bu örnek, `clientCredentialType` "`Certificate"`olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a6664-139">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="a6664-140"><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> Değeri kullanmak özel bir durumdur ve aşağıda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a6664-140">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>

### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="a6664-141">TransportWithMessageCredential kullanma</span><span class="sxs-lookup"><span data-stu-id="a6664-141">Using TransportWithMessageCredential</span></span>

<span data-ttu-id="a6664-142">Güvenlik modu olarak `TransportWithMessageCredential`ayarlandığında, taşıma, aktarım düzeyi güvenliği sağlayan gerçek mekanizmayı belirler.</span><span class="sxs-lookup"><span data-stu-id="a6664-142">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="a6664-143">Örneğin, HTTP Protokolü HTTP (HTTPS) üzerinden Güvenli Yuva Katmanı (SSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="a6664-143">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="a6664-144">Bu nedenle, herhangi `ClientCredentialType` bir aktarım güvenliği nesnesinin ( <xref:System.ServiceModel.HttpTransportSecurity>gibi) özelliğinin ayarlanması yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="a6664-144">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="a6664-145">Diğer `ClientCredentialType` bir deyişle, yalnızca ileti güvenliği nesnesinin ( `WSHttpBinding` bağlama, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> nesne) kümesini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6664-145">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>

<span data-ttu-id="a6664-146">Daha fazla bilgi için [nasıl yapılır: Taşıma güvenliği ve Ileti kimlik bilgilerini](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="a6664-146">For more information, see [How to: Use Transport Security and Message Credentials](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6664-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6664-147">See also</span></span>

- [<span data-ttu-id="a6664-148">Nasıl yapılır: SSL sertifikası ile bir bağlantı noktası yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a6664-148">How to: Configure a Port with an SSL Certificate</span></span>](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="a6664-149">Nasıl yapılır: Taşıma güvenliği ve Ileti kimlik bilgilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="a6664-149">How to: Use Transport Security and Message Credentials</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)
- [<span data-ttu-id="a6664-150">Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="a6664-150">Transport Security</span></span>](../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="a6664-151">İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="a6664-151">Message Security</span></span>](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="a6664-152">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6664-152">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="a6664-153">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a6664-153">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="a6664-154">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a6664-154">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [<span data-ttu-id="a6664-155">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a6664-155">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [<span data-ttu-id="a6664-156">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a6664-156">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
