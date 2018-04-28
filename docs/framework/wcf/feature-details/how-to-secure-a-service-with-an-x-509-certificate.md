---
title: 'Nasıl Yapılır: X.509 Sertifikası ile Bir Hizmeti Güvenli Hale Getirme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
caps.latest.revision: 8
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 31028b6fe2cc34a9ae5cabe410bef0d753fd9436
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a>Nasıl Yapılır: X.509 Sertifikası ile Bir Hizmeti Güvenli Hale Getirme
Bir hizmeti bir X.509 sertifikası ile güvenli hale getirme olan bir temel teknik, çoğu bağlama [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kullanın. Bu konuda bir X.509 sertifikası ile kendini barındıran hizmet yapılandırma adımları açıklanmaktadır.  
  
 Sunucu kimliğini doğrulamak için kullanılan geçerli bir sertifika önkoşuldur. Sertifika sunucuya bir güvenilen sertifika yetkilisi tarafından verilmiş olması gerekir. Sertifika geçerli değilse, hizmet kullanmayı deneyen herhangi bir istemci hizmeti güven değil ve bağlantı yapılan sonuç. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] sertifikaları kullanma Bkz [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a>Kod kullanarak bir sertifika ile bir hizmeti yapılandırmak için  
  
1.  Hizmet sözleşmesi ve uygulanan hizmeti oluşturun. Daha fazla bilgi için bkz: [Hizmetleri Tasarlama ve uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
2.  Bir örneğini oluşturmak <xref:System.ServiceModel.WSHttpBinding> sınıfı ve kendi güvenlik modunu ayarlama <xref:System.ServiceModel.SecurityMode.Message>aşağıdaki kodda gösterildiği gibi.  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3.  İki oluşturmak <xref:System.Type> değişkenleri, her biri için anlaşma türü ve aşağıdaki kodda gösterildiği gibi uygulanan sözleşme.  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4.  Bir örneğini oluşturmak <xref:System.Uri> hizmetin taban adresi için sınıf. Çünkü `WSHttpBinding` HTTP taşıma Tekdüzen Kaynak Tanımlayıcısı (URI), o şema ile başlamalıdır kullanır veya [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet açıldığında bir özel durum oluşturur.  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5.  Yeni bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> uygulanan sözleşme türü değişkeni ve URI ile sınıfı.  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6.  Ekleme bir <xref:System.ServiceModel.Description.ServiceEndpoint> kullanarak hizmet <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi. Sözleşmeyi, bağlamayı ve bir uç nokta adresi oluşturucuya aşağıdaki kodda gösterildiği gibi geçirin.  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7.  İsteğe bağlı. Hizmetinden meta verilerini almak için yeni bir oluşturma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nesne ve ayarlama <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğine `true`.  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8.  Kullanım <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> hizmete geçerli sertifika eklemek için sınıfı. Yöntemi, bir sertifikayı bulmak için birkaç yöntemden birini kullanabilirsiniz. Bu örnekte <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> numaralandırması. Numaralandırma, sağlanan değer sertifikanın verildiği varlık adı olduğunu belirtir.  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. Çağrı <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> dinleme hizmeti başlatmak için yöntem. Bir konsol uygulaması oluşturuyorsanız, çağrı <xref:System.Console.ReadLine%2A> hizmet dinleme durumda tutmak için yöntem.  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> yöntemi bir X.509 sertifikası ile bir hizmeti yapılandırmak için.  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Şu ad alanlarından Kodu derlemek için gereklidir:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.Web.Services.Description>  
  
-   <xref:System.Security.Cryptography.X509Certificates>  
  
-   <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
