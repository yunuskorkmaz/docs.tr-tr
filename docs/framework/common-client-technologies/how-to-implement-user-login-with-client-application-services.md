---
title: "Nasıl Yapılır: İstemci Uygulama Hizmetleri ile Kullanıcı Oturum Açma Adını Uygulama"
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
helpviewer_keywords:
- validating users [client application services]
- validation [.NET Framework], client application services
- client application services, authenticate users
ms.assetid: 5431a671-eb02-4e18-a651-24764fccec9a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 909fbaa4e7dc1d384b5085d71cec346bde44cf14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-user-login-with-client-application-services"></a>Nasıl Yapılır: İstemci Uygulama Hizmetleri ile Kullanıcı Oturum Açma Adını Uygulama
İstemci uygulama hizmetleri varolan aracılığıyla kullanıcıları doğrulamak için kullanabileceğiniz [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profil hizmeti. Nasıl ayarlandığı hakkında bilgi için [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profil hizmet için bkz: [Microsoft Ajax ile form kimlik doğrulaması kullanarak](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e).  
  
 Aşağıdaki yordamlar, uygulamanızın istemci kimlik doğrulama hizmeti sağlayıcıları birini kullanmak için yapılandırıldığında, kimlik doğrulama hizmeti aracılığıyla kullanıcıları doğrulamak açıklar. Daha fazla bilgi için bkz: [nasıl yapılır: istemci uygulama hizmetleri yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
 Genellikle aracılığıyla tüm doğrulama işlemini gerçekleştirecek `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi. Bu yöntem kimlik doğrulama hizmeti yapılandırılmış kimlik doğrulama sağlayıcısı aracılığıyla etkileşim yönetir. Daha fazla bilgi için bkz: [istemci uygulama hizmetlerine genel bakış](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
 Forms kimlik doğrulaması yordamları çalışan bir erişim gerektiren [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] kimlik doğrulama hizmeti. İstemci uygulamasının uçtan uca test konusunda yönergeler özellikleri Hizmetleri için bkz: [izlenecek yol: istemci uygulama hizmetleri kullanarak](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
### <a name="to-authenticate-a-user-with-forms-authentication-using-a-membership-credentials-provider"></a>Bir kullanıcının bir üyelik kullanarak form kimlik doğrulaması ile kimlik doğrulaması için kimlik bilgileri sağlayıcısı  
  
1.  Uygulama <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> arabirimi. Aşağıdaki örnekte gösterildiği kod bir <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> uygulama oturum açma iletişim kutusu sınıfı için türetilen <xref:System.Windows.Forms.Form?displayProperty=nameWithType>. Bu iletişim kutusunda metin kutuları kullanıcı adı ve parolasını ve bir "Beni anımsa" onay kutusu vardır. İstemci kimlik doğrulama sağlayıcısı çağırdığında <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> yöntemi, formun görüntülenir. Kullanıcı oturum açma iletişim kutusunda bilgileri doldurur ve Tamam tıkladığında belirtilen değerlerle yeni bir döndürülür <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> nesnesi.  
  
     [!code-csharp[ClientApplicationServices#210](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#210)]
     [!code-vb[ClientApplicationServices#210](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#210)]  
  
2.  Çağrı `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi ve boş dize parametre değerleri olarak geçirin. Boş dizeler belirttiğinizde, bu yöntem dahili olarak çağırır <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> yöntemi, uygulamanız için yapılandırılan kimlik bilgileri sağlayıcısı. Aşağıdaki kod örneği, tüm Windows Forms uygulamaya erişimi kısıtlamak için bu yöntemi çağırır. Bu kod ekleyebilirsiniz bir <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> işleyicisi.  
  
     [!code-csharp[ClientApplicationServices#317](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#317)]
     [!code-vb[ClientApplicationServices#317](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#317)]  
  
### <a name="to-authenticate-a-user-with-forms-authentication-without-using-a-membership-credentials-provider"></a>Üyelik kimlik bilgileri sağlayıcısı kullanmadan form kimlik doğrulaması ile bir kullanıcının kimliğini doğrulamak için  
  
-   Çağrı `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi ve kullanıcı adı ve parola değerlerini geçişinde kullanıcıdan alınır.  
  
     [!code-csharp[ClientApplicationServices#318](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#318)]
     [!code-vb[ClientApplicationServices#318](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#318)]  
  
### <a name="to-authenticate-a-user-with-windows-authentication"></a>Windows kimlik doğrulamasıyla kullanıcının kimliğini doğrulamak için  
  
-   Çağrı `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi ve geçişi dizeleri parametre boş. Bu yöntem çağrısı her zaman döndürülecek `true` Windows kimliğini içeren kullanıcının tanımlama bilgisi önbelleği için bir tanımlama bilgisi ekler.  
  
     [!code-csharp[ClientApplicationServices#319](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#319)]
     [!code-vb[ClientApplicationServices#319](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#319)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu konudaki örnek kod, bir Windows istemci uygulamasında kimlik doğrulamasının en basit kullanımları gösterir. Çağırdığınızda `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi ile istemci uygulama hizmetleri ve forms kimlik doğrulaması, kodunuzu atabilirsiniz ancak, bir <xref:System.Net.WebException>. Bu kimlik doğrulama hizmeti kullanılamaz olduğunu gösterir. Bu özel durumun nasıl ele alınacağını örneği için bkz: [izlenecek yol: istemci uygulama hizmetleri kullanarak](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemci uygulama hizmetleri](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [İstemci uygulama hizmetlerine genel bakış](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Nasıl yapılır: istemci uygulama hizmetlerini yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [İzlenecek yol: İstemci uygulama hizmetleri kullanma](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [Microsoft Ajax ile form kimlik doğrulaması kullanma](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)
