---
title: 'Nasıl yapılır: X.509 Sertifikası ile Bir Hizmeti Güvenli Hale Getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
ms.openlocfilehash: 6757d6375cbe1662b8bd7beb8a7562be166bc414
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181512"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a><span data-ttu-id="a48d1-102">Nasıl yapılır: X.509 Sertifikası ile Bir Hizmeti Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a48d1-102">How to: Secure a Service with an X.509 Certificate</span></span>
<span data-ttu-id="a48d1-103">X.509 sertifikası ile bir hizmeti güvenli hale getirme çoğu bağlamaları Windows Communication Foundation (WCF) kullanan temel bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="a48d1-103">Securing a service with an X.509 certificate is a basic technique that most bindings in Windows Communication Foundation (WCF) use.</span></span> <span data-ttu-id="a48d1-104">Bu konuda bir X.509 sertifikası ile şirket içinde barındırılan bir hizmet yapılandırma adımlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a48d1-104">This topic walks through the steps of configuring a self-hosted service with an X.509 certificate.</span></span>  
  
 <span data-ttu-id="a48d1-105">Sunucunun kimliğini doğrulamak için kullanılan geçerli bir sertifika önkoşuldur.</span><span class="sxs-lookup"><span data-stu-id="a48d1-105">A prerequisite is a valid certificate that can be used to authenticate the server.</span></span> <span data-ttu-id="a48d1-106">Sertifika sunucusu için bir güvenilen sertifika yetkilisi tarafından verilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a48d1-106">The certificate must be issued to the server by a trusted certificate authority.</span></span> <span data-ttu-id="a48d1-107">Sertifika geçerli değilse, hizmeti kullanmaya çalışırken herhangi bir istemci hizmeti güvenmeyecek ve bağlantı sonuç olarak yapılacaktır.</span><span class="sxs-lookup"><span data-stu-id="a48d1-107">If the certificate is not valid, any client trying to use the service will not trust the service, and consequently no connection will be made.</span></span> <span data-ttu-id="a48d1-108">Sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a48d1-108">For more information about using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a><span data-ttu-id="a48d1-109">Kod kullanarak bir sertifika ile bir hizmeti yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="a48d1-109">To configure a service with a certificate using code</span></span>  
  
1.  <span data-ttu-id="a48d1-110">Hizmet sözleşmesi ve uygulanan hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a48d1-110">Create the service contract and the implemented service.</span></span> <span data-ttu-id="a48d1-111">Daha fazla bilgi için [Hizmetleri Tasarlama ve uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="a48d1-111">For more information, see [Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
2.  <span data-ttu-id="a48d1-112">Bir örneğini oluşturmak <xref:System.ServiceModel.WSHttpBinding> sınıfı ve kendi güvenlik modunu ayarlama <xref:System.ServiceModel.SecurityMode.Message>aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="a48d1-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3.  <span data-ttu-id="a48d1-113">İki <xref:System.Type> değişkenler, her biri için anlaşma türü ve aşağıdaki kodda gösterildiği uygulanan sözleşme.</span><span class="sxs-lookup"><span data-stu-id="a48d1-113">Create two <xref:System.Type> variables, one each for the contract type and the implemented contract, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4.  <span data-ttu-id="a48d1-114">Bir örneğini oluşturmak <xref:System.Uri> hizmetin taban adresine sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a48d1-114">Create an instance of the <xref:System.Uri> class for the base address of the service.</span></span> <span data-ttu-id="a48d1-115">Çünkü `WSHttpBinding` kullanan HTTP aktarımı Tekdüzen Kaynak Tanımlayıcısı (URI) bu şemasıyla başlamalı ve Windows Communication Foundation (WCF) hizmet açıldığında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a48d1-115">Because the `WSHttpBinding` uses the HTTP transport, the Uniform Resource Identifier (URI) must begin with that schema, or Windows Communication Foundation (WCF) will throw an exception when the service is opened.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5.  <span data-ttu-id="a48d1-116">Yeni bir örneğini oluşturma <xref:System.ServiceModel.ServiceHost> uygulanan sözleşme türü değişkeni ve URI ile sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a48d1-116">Create a new instance of the <xref:System.ServiceModel.ServiceHost> class with the implemented contract type variable and the URI.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6.  <span data-ttu-id="a48d1-117">Ekleme bir <xref:System.ServiceModel.Description.ServiceEndpoint> kullanarak hizmet <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a48d1-117">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> to the service using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span> <span data-ttu-id="a48d1-118">Sözleşmeyi, bağlamayı ve uç nokta adresi oluşturucuya, aşağıdaki kodda gösterildiği şekilde geçirin.</span><span class="sxs-lookup"><span data-stu-id="a48d1-118">Pass the contract, binding, and an endpoint address to the constructor, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7.  <span data-ttu-id="a48d1-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a48d1-119">Optional.</span></span> <span data-ttu-id="a48d1-120">Yeni bir oluşturma hizmeti meta verilerini almak için <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ayarlayın ve nesne <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="a48d1-120">To retrieve metadata from the service, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> object and set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8.  <span data-ttu-id="a48d1-121">Kullanım <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> hizmetine geçerli sertifika eklemek için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a48d1-121">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to add the valid certificate to the service.</span></span> <span data-ttu-id="a48d1-122">Yöntemi, bir sertifika bulmak için birkaç yöntemden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a48d1-122">The method can use one of several methods to find a certificate.</span></span> <span data-ttu-id="a48d1-123">Bu örnekte <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="a48d1-123">This example uses the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> enumeration.</span></span> <span data-ttu-id="a48d1-124">Sabit sağlanan değer sertifikanın verildiği kişi varlığı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a48d1-124">The enumeration specifies that the supplied value is the name of the entity that the certificate was issued to.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. <span data-ttu-id="a48d1-125">Çağrı <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> dinleme hizmeti başlatmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a48d1-125">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service listening.</span></span> <span data-ttu-id="a48d1-126">Bir konsol uygulaması oluşturuyorsanız, çağrı <xref:System.Console.ReadLine%2A> hizmet dinleme durumda tutmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a48d1-126">If you are creating a console application, call the <xref:System.Console.ReadLine%2A> method to keep the service in the listening state.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="a48d1-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="a48d1-127">Example</span></span>  
 <span data-ttu-id="a48d1-128">Aşağıdaki örnekte <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> bir X.509 sertifikası ile bir hizmeti yapılandırmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a48d1-128">The following example uses the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method to configure a service with an X.509 certificate.</span></span>  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a48d1-129">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a48d1-129">Compiling the Code</span></span>  
 <span data-ttu-id="a48d1-130">Aşağıdaki ad alanlarını, kodu derlemek için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="a48d1-130">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.Web.Services.Description>  
  
-   <xref:System.Security.Cryptography.X509Certificates>  
  
-   <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a><span data-ttu-id="a48d1-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a48d1-131">See also</span></span>

- [<span data-ttu-id="a48d1-132">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="a48d1-132">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
