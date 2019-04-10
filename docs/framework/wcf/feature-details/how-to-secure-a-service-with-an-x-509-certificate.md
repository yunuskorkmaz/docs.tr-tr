---
title: 'Nasıl yapılır: X.509 Sertifikası ile Bir Hizmeti Güvenli Hale Getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
ms.openlocfilehash: 75c7a0e50301ce80d51b9b2a10ed650a1600ec79
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300092"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a>Nasıl yapılır: X.509 Sertifikası ile Bir Hizmeti Güvenli Hale Getirme
X.509 sertifikası ile bir hizmeti güvenli hale getirme çoğu bağlamaları Windows Communication Foundation (WCF) kullanan temel bir tekniktir. Bu konuda bir X.509 sertifikası ile şirket içinde barındırılan bir hizmet yapılandırma adımlarını açıklar.  
  
 Sunucunun kimliğini doğrulamak için kullanılan geçerli bir sertifika önkoşuldur. Sertifika sunucusu için bir güvenilen sertifika yetkilisi tarafından verilmiş olması gerekir. Sertifika geçerli değilse, hizmeti kullanmaya çalışırken herhangi bir istemci hizmeti güvenmeyecek ve bağlantı sonuç olarak yapılacaktır. Sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a>Kod kullanarak bir sertifika ile bir hizmeti yapılandırmak için  
  
1. Hizmet sözleşmesi ve uygulanan hizmeti oluşturun. Daha fazla bilgi için [Hizmetleri Tasarlama ve uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
2. Bir örneğini oluşturmak <xref:System.ServiceModel.WSHttpBinding> sınıfı ve kendi güvenlik modunu ayarlama <xref:System.ServiceModel.SecurityMode.Message>aşağıdaki kodda gösterildiği gibi.  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3. İki <xref:System.Type> değişkenler, her biri için anlaşma türü ve aşağıdaki kodda gösterildiği uygulanan sözleşme.  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4. Bir örneğini oluşturmak <xref:System.Uri> hizmetin taban adresine sınıfı. Çünkü `WSHttpBinding` kullanan HTTP aktarımı Tekdüzen Kaynak Tanımlayıcısı (URI) bu şemasıyla başlamalı ve Windows Communication Foundation (WCF) hizmet açıldığında bir özel durum oluşturur.  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5. Yeni bir örneğini oluşturma <xref:System.ServiceModel.ServiceHost> uygulanan sözleşme türü değişkeni ve URI ile sınıfı.  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6. Ekleme bir <xref:System.ServiceModel.Description.ServiceEndpoint> kullanarak hizmet <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi. Sözleşmeyi, bağlamayı ve uç nokta adresi oluşturucuya, aşağıdaki kodda gösterildiği şekilde geçirin.  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7. İsteğe bağlı. Yeni bir oluşturma hizmeti meta verilerini almak için <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ayarlayın ve nesne <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğini `true`.  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8. Kullanım <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> hizmetine geçerli sertifika eklemek için sınıfı. Yöntemi, bir sertifika bulmak için birkaç yöntemden birini kullanabilirsiniz. Bu örnekte <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> sabit listesi. Sabit sağlanan değer sertifikanın verildiği kişi varlığı adını belirtir.  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. Çağrı <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> dinleme hizmeti başlatmak için yöntemi. Bir konsol uygulaması oluşturuyorsanız, çağrı <xref:System.Console.ReadLine%2A> hizmet dinleme durumda tutmak için yöntemi.  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> bir X.509 sertifikası ile bir hizmeti yapılandırmak için yöntemi.  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Aşağıdaki ad alanlarını, kodu derlemek için gereklidir:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.Web.Services.Description>  
  
-   <xref:System.Security.Cryptography.X509Certificates>  
  
-   <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
