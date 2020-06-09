---
title: 'Nasıl Yapılır: X.509 Sertifikası ile Bir Hizmeti Güvenli Hale Getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
ms.openlocfilehash: 10d6db63368ee55040f85f922b9483982e8ff264
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596974"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a>Nasıl Yapılır: X.509 Sertifikası ile Bir Hizmeti Güvenli Hale Getirme
Bir hizmetin bir X. 509.440 sertifikası ile güvenliğini sağlamak, Windows Communication Foundation (WCF) ' deki bağlamaların çoğu tarafından kullanılan temel bir tekniktir. Bu konu, bir X. 509.952 sertifikasıyla şirket içinde barındırılan bir hizmeti yapılandırma adımlarında size yol gösterir.  
  
 Önkoşul, sunucunun kimliğini doğrulamak için kullanılabilecek geçerli bir sertifikadır. Sertifika, güvenilen bir sertifika yetkilisi tarafından sunucuya verilmelidir. Sertifika geçerli değilse, hizmeti kullanmaya çalışan tüm istemciler hizmete güvenmez ve bu nedenle hiçbir bağlantı yapılmaz. Sertifikaları kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md).  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a>Kodu kullanarak bir hizmeti sertifikayla yapılandırmak için  
  
1. Hizmet sözleşmesini ve uygulanan hizmeti oluşturun. Daha fazla bilgi için bkz. [Hizmetleri tasarlama ve uygulama](../designing-and-implementing-services.md).  
  
2. <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.SecurityMode.Message> Aşağıdaki kodda gösterildiği gibi, sınıfının bir örneğini oluşturun ve güvenlik modunu olarak ayarlayın.  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3. <xref:System.Type>Aşağıdaki kodda gösterildiği gibi, her biri anlaşma türü ve uygulanan sözleşme için olmak üzere iki değişken oluşturun.  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4. <xref:System.Uri>Hizmetin temel adresi için sınıfının bir örneğini oluşturun. , `WSHttpBinding` Http taşımasını kullandığından, Tekdüzen Kaynak tanımlayıcısı (URI) bu şemayla başlamalıdır veya Windows Communication Foundation (WCF) hizmet açıldığında bir özel durum oluşturur.  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5. <xref:System.ServiceModel.ServiceHost>Uygulanan anlaşma türü değişkeni ve URI ile sınıfın yeni bir örneğini oluşturun.  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6. <xref:System.ServiceModel.Description.ServiceEndpoint>Yöntemini kullanarak hizmetine bir ekleyin <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> . Aşağıdaki kodda gösterildiği gibi, sözleşmeyi, bağlamayı ve bir uç nokta adresini oluşturucuya geçirin.  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7. İsteğe bağlı. Hizmetten meta verileri almak için yeni bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nesne oluşturun ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğini olarak ayarlayın `true` .  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8. <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> Geçerli sertifikayı hizmete eklemek için sınıfının yöntemini kullanın. Yöntemi, bir sertifikayı bulmak için birkaç yöntemden birini kullanabilir. Bu örnek, <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> sabit listesini kullanır. Sabit listesi, sağlanan değerin sertifikanın verildiği varlığın adı olduğunu belirtir.  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>Hizmeti dinlemeye başlamak için yöntemini çağırın. Konsol uygulaması oluşturuyorsanız, <xref:System.Console.ReadLine%2A> hizmeti dinleme durumunda tutmak için yöntemini çağırın.  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> X. 509.440 sertifikasıyla bir hizmeti yapılandırmak için yöntemini kullanır.  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu derlemek için aşağıdaki ad alanları gereklidir:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.Web.Services.Description>  
  
- <xref:System.Security.Cryptography.X509Certificates>  
  
- <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sertifikalarla Çalışma](working-with-certificates.md)
