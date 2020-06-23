---
title: 'Nasıl yapılır: Güvenlik Modunu Ayarlama'
description: 'En önceden tanımlı bağlamalarda üç ortak WCF güvenlik modunu ayarlamayı öğrenin: Transport, Message ve TransportWithMessageCredential.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 2f834e1930b7676592f6cbc29a577424d75ebc01
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244549"
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="e06f9-103">Nasıl yapılır: Güvenlik Modunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="e06f9-103">How to: Set the Security Mode</span></span>

<span data-ttu-id="e06f9-104">Windows Communication Foundation (WCF) güvenliği, en önceden tanımlı bağlamalarda bulunan üç ortak güvenlik moduna sahiptir: Transport, Message ve "ileti kimlik bilgileri ile taşıma."</span><span class="sxs-lookup"><span data-stu-id="e06f9-104">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="e06f9-105">İki bağlama özgü iki ek mod vardır: üzerinde bulunan "Transport-Credential Only" modu <xref:System.ServiceModel.BasicHttpBinding> ve üzerinde bulunan "both" modu <xref:System.ServiceModel.NetMsmqBinding> .</span><span class="sxs-lookup"><span data-stu-id="e06f9-105">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="e06f9-106">Ancak, bu konu üç ortak güvenlik modu üzerinde yoğunlaşır: <xref:System.ServiceModel.SecurityMode.Transport> , <xref:System.ServiceModel.SecurityMode.Message> ve <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="e06f9-106">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>

<span data-ttu-id="e06f9-107">Önceden tanımlanmış her bağlamanın bu modların tümünü desteklediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e06f9-107">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="e06f9-108">Bu konu, ve sınıfları ile modunu <xref:System.ServiceModel.WSHttpBinding> Ayarlar <xref:System.ServiceModel.NetTcpBinding> ve modu hem programlı olarak hem de yapılandırma aracılığıyla ayarlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e06f9-108">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>

<span data-ttu-id="e06f9-109">Daha fazla bilgi için bkz. WCF güvenliği, [güvenlik genel bakış](./feature-details/security-overview.md), [hizmetleri güvenli hale](securing-services.md)getirme ve [Hizmetleri ve istemcileri güvenli hale getirme](./feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="e06f9-109">For more information, see WCF security, see [Security Overview](./feature-details/security-overview.md), [Securing Services](securing-services.md), and [Securing Services and Clients](./feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="e06f9-110">Aktarım modu ve ileti hakkında daha fazla bilgi için bkz. [Aktarım güvenliği](./feature-details/transport-security.md) ve [ileti güvenliği](./feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="e06f9-110">For more information about transport mode and message, see [Transport Security](./feature-details/transport-security.md) and [Message Security](./feature-details/message-security-in-wcf.md).</span></span>

## <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="e06f9-111">Koddaki güvenlik modunu ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e06f9-111">To set the security mode in code</span></span>

1. <span data-ttu-id="e06f9-112">Kullandığınız bağlama sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e06f9-112">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="e06f9-113">Önceden tanımlanmış bağlamaların listesi için bkz. [sistem tarafından sunulan bağlamalar](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="e06f9-113">For a list of predefined bindings, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="e06f9-114">Bu örnek, sınıfının bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="e06f9-114">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

2. <span data-ttu-id="e06f9-115">`Mode`Özelliği tarafından döndürülen nesnesinin özelliğini ayarlayın `Security` .</span><span class="sxs-lookup"><span data-stu-id="e06f9-115">Set the `Mode` property of the object returned by the `Security` property.</span></span>

     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]

     <span data-ttu-id="e06f9-116">Alternatif olarak, aşağıdaki kodda gösterildiği gibi modunu ileti olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e06f9-116">Alternatively, set the mode to message, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]

     <span data-ttu-id="e06f9-117">Ya da aşağıdaki kodda gösterildiği gibi modu ileti kimlik bilgileriyle taşıma olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e06f9-117">Or set the mode to transport with message credentials, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]

3. <span data-ttu-id="e06f9-118">Ayrıca, aşağıdaki kodda gösterildiği gibi, bağlama oluşturucusunda modu da ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e06f9-118">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]

## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="e06f9-119">ClientCredentialType özelliği ayarlanıyor</span><span class="sxs-lookup"><span data-stu-id="e06f9-119">Setting the ClientCredentialType Property</span></span>

<span data-ttu-id="e06f9-120">Modunun üç değerden birine ayarlanması, özelliği nasıl ayarlayabileceğinizi belirler `ClientCredentialType` .</span><span class="sxs-lookup"><span data-stu-id="e06f9-120">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="e06f9-121">Örneğin, <xref:System.ServiceModel.WSHttpBinding> sınıfını kullanarak modunu olarak ayarlamak, `Transport` <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> <xref:System.ServiceModel.HttpTransportSecurity> sınıfının özelliğini uygun bir değere ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e06f9-121">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="e06f9-122">Taşıma modu için ClientCredentialType özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e06f9-122">To set the ClientCredentialType property for Transport mode</span></span>

1. <span data-ttu-id="e06f9-123">Bağlamanın bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e06f9-123">Create an instance of the binding.</span></span>

2. <span data-ttu-id="e06f9-124">`Mode`Özelliğini olarak ayarlayın `Transport` .</span><span class="sxs-lookup"><span data-stu-id="e06f9-124">Set the `Mode` property to `Transport`.</span></span>

3. <span data-ttu-id="e06f9-125">`ClientCredential`Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e06f9-125">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="e06f9-126">Aşağıdaki kod özelliği olarak ayarlar `Windows` .</span><span class="sxs-lookup"><span data-stu-id="e06f9-126">The following code sets the property to `Windows`.</span></span>

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="e06f9-127">Ileti modu için ClientCredentialType özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e06f9-127">To set the ClientCredentialType property for Message mode</span></span>

1. <span data-ttu-id="e06f9-128">Bağlamanın bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e06f9-128">Create an instance of the binding.</span></span>

2. <span data-ttu-id="e06f9-129">`Mode`Özelliğini olarak ayarlayın `Message` .</span><span class="sxs-lookup"><span data-stu-id="e06f9-129">Set the `Mode` property to `Message`.</span></span>

3. <span data-ttu-id="e06f9-130">`ClientCredential`Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e06f9-130">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="e06f9-131">Aşağıdaki kod özelliği olarak ayarlar `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="e06f9-131">The following code sets the property to `Certificate`.</span></span>

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="e06f9-132">Yapılandırmada Mode ve ClientCredentialType özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e06f9-132">To set the Mode and ClientCredentialType property in configuration</span></span>

1. <span data-ttu-id="e06f9-133">Yapılandırma dosyasının öğesine uygun bir bağlama öğesi ekleyin [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="e06f9-133">Add an appropriate binding element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="e06f9-134">Aşağıdaki örnek bir öğesi ekler [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e06f9-134">The following example adds a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

2. <span data-ttu-id="e06f9-135">Bir `<binding>` öğesi ekleyin ve `name` özniteliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e06f9-135">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="e06f9-136">Bir `<security>` öğesi ekleyin ve `mode` özniteliği `Message` , veya olarak ayarlayın `Transport` `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="e06f9-136">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

4. <span data-ttu-id="e06f9-137">Mod olarak ayarlandıysa `Transport` , bir `<transport>` öğesi ekleyin ve `clientCredential` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e06f9-137">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>

     <span data-ttu-id="e06f9-138">Aşağıdaki örnek, modunu " `Transport"` olarak ayarlar ve sonra `clientCredentialType` `<transport>` öğesinin özniteliğini" olarak ayarlar `Windows"` .</span><span class="sxs-lookup"><span data-stu-id="e06f9-138">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="e06f9-139">Alternatif olarak, `security mode` `Message"` öğesini ve ardından öğesini olarak ayarlayın `<"message">` .</span><span class="sxs-lookup"><span data-stu-id="e06f9-139">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="e06f9-140">Bu örnek, `clientCredentialType` "olarak ayarlar `Certificate"` .</span><span class="sxs-lookup"><span data-stu-id="e06f9-140">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="e06f9-141">Değeri kullanmak <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> özel bir durumdur ve aşağıda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e06f9-141">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>

### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="e06f9-142">TransportWithMessageCredential kullanma</span><span class="sxs-lookup"><span data-stu-id="e06f9-142">Using TransportWithMessageCredential</span></span>

<span data-ttu-id="e06f9-143">Güvenlik modu olarak ayarlandığında `TransportWithMessageCredential` , taşıma, aktarım düzeyi güvenliği sağlayan gerçek mekanizmayı belirler.</span><span class="sxs-lookup"><span data-stu-id="e06f9-143">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="e06f9-144">Örneğin, HTTP Protokolü HTTP (HTTPS) üzerinden Güvenli Yuva Katmanı (SSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="e06f9-144">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="e06f9-145">Bu nedenle, `ClientCredentialType` herhangi bir aktarım güvenliği nesnesinin (gibi) özelliğinin ayarlanması <xref:System.ServiceModel.HttpTransportSecurity> yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="e06f9-145">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="e06f9-146">Diğer bir deyişle, yalnızca `ClientCredentialType` ileti güvenliği nesnesinin ( `WSHttpBinding` bağlama, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> nesne) kümesini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e06f9-146">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>

<span data-ttu-id="e06f9-147">Daha fazla bilgi için bkz. [nasıl yapılır: taşıma güvenlik ve Ileti kimlik bilgilerini kullanma](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="e06f9-147">For more information, see [How to: Use Transport Security and Message Credentials](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e06f9-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e06f9-148">See also</span></span>

- [<span data-ttu-id="e06f9-149">Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e06f9-149">How to: Configure a Port with an SSL Certificate</span></span>](./feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="e06f9-150">Nasıl yapılır: Taşıma Güveniği ve İleti Kimlik Bilgilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="e06f9-150">How to: Use Transport Security and Message Credentials</span></span>](./feature-details/how-to-use-transport-security-and-message-credentials.md)
- [<span data-ttu-id="e06f9-151">Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e06f9-151">Transport Security</span></span>](./feature-details/transport-security.md)
- [<span data-ttu-id="e06f9-152">İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e06f9-152">Message Security</span></span>](./feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="e06f9-153">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="e06f9-153">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="e06f9-154">Sistem tarafından sağlanmış bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e06f9-154">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
