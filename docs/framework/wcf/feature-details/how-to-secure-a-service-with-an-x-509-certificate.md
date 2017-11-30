---
title: "Nasıl Yapılır: X.509 Sertifikası ile Bir Hizmeti Güvenli Hale Getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: ec2800d2b6a910f75366e323b7580afe08de2acb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a><span data-ttu-id="41150-102">Nasıl Yapılır: X.509 Sertifikası ile Bir Hizmeti Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="41150-102">How to: Secure a Service with an X.509 Certificate</span></span>
<span data-ttu-id="41150-103">Bir hizmeti bir X.509 sertifikası ile güvenli hale getirme olan bir temel teknik, çoğu bağlama [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kullanın.</span><span class="sxs-lookup"><span data-stu-id="41150-103">Securing a service with an X.509 certificate is a basic technique that most bindings in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] use.</span></span> <span data-ttu-id="41150-104">Bu konuda bir X.509 sertifikası ile kendini barındıran hizmet yapılandırma adımları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="41150-104">This topic walks through the steps of configuring a self-hosted service with an X.509 certificate.</span></span>  
  
 <span data-ttu-id="41150-105">Sunucu kimliğini doğrulamak için kullanılan geçerli bir sertifika önkoşuldur.</span><span class="sxs-lookup"><span data-stu-id="41150-105">A prerequisite is a valid certificate that can be used to authenticate the server.</span></span> <span data-ttu-id="41150-106">Sertifika sunucuya bir güvenilen sertifika yetkilisi tarafından verilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="41150-106">The certificate must be issued to the server by a trusted certificate authority.</span></span> <span data-ttu-id="41150-107">Sertifika geçerli değilse, hizmet kullanmayı deneyen herhangi bir istemci hizmeti güven değil ve bağlantı yapılan sonuç.</span><span class="sxs-lookup"><span data-stu-id="41150-107">If the certificate is not valid, any client trying to use the service will not trust the service, and consequently no connection will be made.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="41150-108">sertifikaları kullanma Bkz [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="41150-108"> using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a><span data-ttu-id="41150-109">Kod kullanarak bir sertifika ile bir hizmeti yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="41150-109">To configure a service with a certificate using code</span></span>  
  
1.  <span data-ttu-id="41150-110">Hizmet sözleşmesi ve uygulanan hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="41150-110">Create the service contract and the implemented service.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="41150-111">[Hizmetleri Tasarlama ve uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="41150-111"> [Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
2.  <span data-ttu-id="41150-112">Bir örneğini oluşturmak <xref:System.ServiceModel.WSHttpBinding> sınıfı ve kendi güvenlik modunu ayarlama <xref:System.ServiceModel.SecurityMode.Message>aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="41150-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3.  <span data-ttu-id="41150-113">İki oluşturmak <xref:System.Type> değişkenleri, her biri için anlaşma türü ve aşağıdaki kodda gösterildiği gibi uygulanan sözleşme.</span><span class="sxs-lookup"><span data-stu-id="41150-113">Create two <xref:System.Type> variables, one each for the contract type and the implemented contract, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4.  <span data-ttu-id="41150-114">Bir örneğini oluşturmak <xref:System.Uri> hizmetin taban adresi için sınıf.</span><span class="sxs-lookup"><span data-stu-id="41150-114">Create an instance of the <xref:System.Uri> class for the base address of the service.</span></span> <span data-ttu-id="41150-115">Çünkü `WSHttpBinding` HTTP taşıma Tekdüzen Kaynak Tanımlayıcısı (URI), o şema ile başlamalıdır kullanır veya [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet açıldığında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41150-115">Because the `WSHttpBinding` uses the HTTP transport, the Uniform Resource Identifier (URI) must begin with that schema, or [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] will throw an exception when the service is opened.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5.  <span data-ttu-id="41150-116">Yeni bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> uygulanan sözleşme türü değişkeni ve URI ile sınıfı.</span><span class="sxs-lookup"><span data-stu-id="41150-116">Create a new instance of the <xref:System.ServiceModel.ServiceHost> class with the implemented contract type variable and the URI.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6.  <span data-ttu-id="41150-117">Ekleme bir <xref:System.ServiceModel.Description.ServiceEndpoint> kullanarak hizmet <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="41150-117">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> to the service using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span> <span data-ttu-id="41150-118">Sözleşmeyi, bağlamayı ve bir uç nokta adresi oluşturucuya aşağıdaki kodda gösterildiği gibi geçirin.</span><span class="sxs-lookup"><span data-stu-id="41150-118">Pass the contract, binding, and an endpoint address to the constructor, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7.  <span data-ttu-id="41150-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="41150-119">Optional.</span></span> <span data-ttu-id="41150-120">Hizmetinden meta verilerini almak için yeni bir oluşturma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nesne ve ayarlama <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="41150-120">To retrieve metadata from the service, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> object and set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8.  <span data-ttu-id="41150-121">Kullanım <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> hizmete geçerli sertifika eklemek için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="41150-121">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to add the valid certificate to the service.</span></span> <span data-ttu-id="41150-122">Yöntemi, bir sertifikayı bulmak için birkaç yöntemden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41150-122">The method can use one of several methods to find a certificate.</span></span> <span data-ttu-id="41150-123">Bu örnekte <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="41150-123">This example uses the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> enumeration.</span></span> <span data-ttu-id="41150-124">Numaralandırma, sağlanan değer sertifikanın verildiği varlık adı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="41150-124">The enumeration specifies that the supplied value is the name of the entity that the certificate was issued to.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. <span data-ttu-id="41150-125">Çağrı <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> dinleme hizmeti başlatmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="41150-125">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service listening.</span></span> <span data-ttu-id="41150-126">Bir konsol uygulaması oluşturuyorsanız, çağrı <xref:System.Console.ReadLine%2A> hizmet dinleme durumda tutmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="41150-126">If you are creating a console application, call the <xref:System.Console.ReadLine%2A> method to keep the service in the listening state.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="41150-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="41150-127">Example</span></span>  
 <span data-ttu-id="41150-128">Aşağıdaki örnek kullanır <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> yöntemi bir X.509 sertifikası ile bir hizmeti yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="41150-128">The following example uses the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method to configure a service with an X.509 certificate.</span></span>  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="41150-129">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="41150-129">Compiling the Code</span></span>  
 <span data-ttu-id="41150-130">Şu ad alanlarından Kodu derlemek için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="41150-130">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.Web.Services.Description>  
  
-   <xref:System.Security.Cryptography.X509Certificates>  
  
-   <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a><span data-ttu-id="41150-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41150-131">See Also</span></span>  
 [<span data-ttu-id="41150-132">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="41150-132">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
