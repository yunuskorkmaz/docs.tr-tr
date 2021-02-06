---
description: 'Daha fazla bilgi edinin: nasıl yapılır: bir hizmetin X. 509.440 sertifikasıyla güvenliğini sağlama'
title: 'Nasıl yapılır: X.509 Sertifikası ile Bir Hizmeti Güvenli Hale Getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
ms.openlocfilehash: 57c8e78777c620fd3078651dbafbbf010fbd3768
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643390"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a><span data-ttu-id="644d5-103">Nasıl yapılır: X.509 Sertifikası ile Bir Hizmeti Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="644d5-103">How to: Secure a Service with an X.509 Certificate</span></span>

<span data-ttu-id="644d5-104">Bir hizmetin bir X. 509.440 sertifikası ile güvenliğini sağlamak, Windows Communication Foundation (WCF) ' deki bağlamaların çoğu tarafından kullanılan temel bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="644d5-104">Securing a service with an X.509 certificate is a basic technique that most bindings in Windows Communication Foundation (WCF) use.</span></span> <span data-ttu-id="644d5-105">Bu konu, bir X. 509.952 sertifikasıyla şirket içinde barındırılan bir hizmeti yapılandırma adımlarında size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="644d5-105">This topic walks through the steps of configuring a self-hosted service with an X.509 certificate.</span></span>  
  
 <span data-ttu-id="644d5-106">Önkoşul, sunucunun kimliğini doğrulamak için kullanılabilecek geçerli bir sertifikadır.</span><span class="sxs-lookup"><span data-stu-id="644d5-106">A prerequisite is a valid certificate that can be used to authenticate the server.</span></span> <span data-ttu-id="644d5-107">Sertifika, güvenilen bir sertifika yetkilisi tarafından sunucuya verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="644d5-107">The certificate must be issued to the server by a trusted certificate authority.</span></span> <span data-ttu-id="644d5-108">Sertifika geçerli değilse, hizmeti kullanmaya çalışan tüm istemciler hizmete güvenmez ve bu nedenle hiçbir bağlantı yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="644d5-108">If the certificate is not valid, any client trying to use the service will not trust the service, and consequently no connection will be made.</span></span> <span data-ttu-id="644d5-109">Sertifikaları kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="644d5-109">For more information about using certificates, see [Working with Certificates](working-with-certificates.md).</span></span>  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a><span data-ttu-id="644d5-110">Kodu kullanarak bir hizmeti sertifikayla yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="644d5-110">To configure a service with a certificate using code</span></span>  
  
1. <span data-ttu-id="644d5-111">Hizmet sözleşmesini ve uygulanan hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="644d5-111">Create the service contract and the implemented service.</span></span> <span data-ttu-id="644d5-112">Daha fazla bilgi için bkz. [Hizmetleri tasarlama ve uygulama](../designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="644d5-112">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md).</span></span>  
  
2. <span data-ttu-id="644d5-113"><xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.SecurityMode.Message> Aşağıdaki kodda gösterildiği gibi, sınıfının bir örneğini oluşturun ve güvenlik modunu olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="644d5-113">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3. <span data-ttu-id="644d5-114"><xref:System.Type>Aşağıdaki kodda gösterildiği gibi, her biri anlaşma türü ve uygulanan sözleşme için olmak üzere iki değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="644d5-114">Create two <xref:System.Type> variables, one each for the contract type and the implemented contract, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4. <span data-ttu-id="644d5-115"><xref:System.Uri>Hizmetin temel adresi için sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="644d5-115">Create an instance of the <xref:System.Uri> class for the base address of the service.</span></span> <span data-ttu-id="644d5-116">, `WSHttpBinding` Http taşımasını kullandığından, Tekdüzen Kaynak tanımlayıcısı (URI) bu şemayla başlamalıdır veya Windows Communication Foundation (WCF) hizmet açıldığında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="644d5-116">Because the `WSHttpBinding` uses the HTTP transport, the Uniform Resource Identifier (URI) must begin with that schema, or Windows Communication Foundation (WCF) will throw an exception when the service is opened.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5. <span data-ttu-id="644d5-117"><xref:System.ServiceModel.ServiceHost>Uygulanan anlaşma türü değişkeni ve URI ile sınıfın yeni bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="644d5-117">Create a new instance of the <xref:System.ServiceModel.ServiceHost> class with the implemented contract type variable and the URI.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6. <span data-ttu-id="644d5-118"><xref:System.ServiceModel.Description.ServiceEndpoint>Yöntemini kullanarak hizmetine bir ekleyin <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> .</span><span class="sxs-lookup"><span data-stu-id="644d5-118">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> to the service using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span> <span data-ttu-id="644d5-119">Aşağıdaki kodda gösterildiği gibi, sözleşmeyi, bağlamayı ve bir uç nokta adresini oluşturucuya geçirin.</span><span class="sxs-lookup"><span data-stu-id="644d5-119">Pass the contract, binding, and an endpoint address to the constructor, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7. <span data-ttu-id="644d5-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="644d5-120">Optional.</span></span> <span data-ttu-id="644d5-121">Hizmetten meta verileri almak için yeni bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nesne oluşturun ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="644d5-121">To retrieve metadata from the service, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> object and set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8. <span data-ttu-id="644d5-122"><xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> Geçerli sertifikayı hizmete eklemek için sınıfının yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="644d5-122">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to add the valid certificate to the service.</span></span> <span data-ttu-id="644d5-123">Yöntemi, bir sertifikayı bulmak için birkaç yöntemden birini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="644d5-123">The method can use one of several methods to find a certificate.</span></span> <span data-ttu-id="644d5-124">Bu örnek, <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> sabit listesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="644d5-124">This example uses the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> enumeration.</span></span> <span data-ttu-id="644d5-125">Sabit listesi, sağlanan değerin sertifikanın verildiği varlığın adı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="644d5-125">The enumeration specifies that the supplied value is the name of the entity that the certificate was issued to.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. <span data-ttu-id="644d5-126"><xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>Hizmeti dinlemeye başlamak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="644d5-126">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service listening.</span></span> <span data-ttu-id="644d5-127">Konsol uygulaması oluşturuyorsanız, <xref:System.Console.ReadLine%2A> hizmeti dinleme durumunda tutmak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="644d5-127">If you are creating a console application, call the <xref:System.Console.ReadLine%2A> method to keep the service in the listening state.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="644d5-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="644d5-128">Example</span></span>  

 <span data-ttu-id="644d5-129">Aşağıdaki örnek, <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> X. 509.440 sertifikasıyla bir hizmeti yapılandırmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="644d5-129">The following example uses the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method to configure a service with an X.509 certificate.</span></span>  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="644d5-130">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="644d5-130">Compiling the Code</span></span>  

 <span data-ttu-id="644d5-131">Kodu derlemek için aşağıdaki ad alanları gereklidir:</span><span class="sxs-lookup"><span data-stu-id="644d5-131">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.Web.Services.Description>  
  
- <xref:System.Security.Cryptography.X509Certificates>  
  
- <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a><span data-ttu-id="644d5-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="644d5-132">See also</span></span>

- [<span data-ttu-id="644d5-133">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="644d5-133">Working with Certificates</span></span>](working-with-certificates.md)
