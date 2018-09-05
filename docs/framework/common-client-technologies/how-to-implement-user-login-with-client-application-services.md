---
title: 'Nasıl Yapılır: İstemci Uygulama Hizmetleri ile Kullanıcı Oturum Açma Adını Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating users [client application services]
- validation [.NET Framework], client application services
- client application services, authenticate users
ms.assetid: 5431a671-eb02-4e18-a651-24764fccec9a
ms.openlocfilehash: a878b12620faf9a6e9fecbd2e76644aea3d80611
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504802"
---
# <a name="how-to-implement-user-login-with-client-application-services"></a>Nasıl Yapılır: İstemci Uygulama Hizmetleri ile Kullanıcı Oturum Açma Adını Uygulama
İstemci uygulama hizmetleri var olan bir aracılığıyla kullanıcıları doğrulamak için kullanabileceğiniz [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profil hizmeti. Nasıl ayarlandığı hakkında daha fazla bilgi için [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profil hizmeti için bkz: [kullanarak form kimlik doğrulaması ile Microsoft Ajax](https://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e).  
  
 Aşağıdaki yordamlarda, uygulamanızın istemci kimlik doğrulama hizmeti sağlayıcıları birini kullanmak için yapılandırıldığında, kimlik doğrulama hizmeti aracılığıyla kullanıcıları doğrulamak açıklanır. Daha fazla bilgi için [nasıl yapılır: istemci uygulama servislerini yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
 Genellikle tüm doğrulama aracılığıyla gerçekleştireceğiniz `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi. Bu yöntem, yapılandırılmış kimlik doğrulama sağlayıcısı aracılığıyla kimlik doğrulaması hizmetiyle etkileşimi yönetir. Daha fazla bilgi için [istemci uygulama servislerine genel bakış](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
 Forms kimlik doğrulaması yordamları çalışan bir erişmesi [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] kimlik doğrulama hizmeti. İstemci uygulamasının uçtan uca test Kılavuzu services özellikleri için bkz: [izlenecek yol: istemci uygulama hizmetleri kullanarak](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
### <a name="to-authenticate-a-user-with-forms-authentication-using-a-membership-credentials-provider"></a>Bir kullanıcının bir üyelik kimlik sağlayıcısı kullanarak form kimlik doğrulaması ile kimliğini doğrulamak için  
  
1.  Uygulama <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> arabirimi. Aşağıdaki kod örnekte gösterildiği bir <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> uygulama oturum açma iletişim kutusu sınıfı için türetilen <xref:System.Windows.Forms.Form?displayProperty=nameWithType>. Bu iletişim kutusunda, metin kutuları için kullanıcı adı ve parola ve "Beni Hatırla" onay kutusu vardır. İstemci kimlik doğrulama sağlayıcısı çağırdığında <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> yöntemi, formu görüntülenir. Kullanıcı oturum açma iletişim kutusundaki bilgileri doldurur ve Tamam'ı tıklattığında, belirtilen değerlerle yeni bir döndürülür <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> nesne.  
  
     [!code-csharp[ClientApplicationServices#210](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#210)]
     [!code-vb[ClientApplicationServices#210](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#210)]  
  
2.  Çağrı `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi ve boş dize olarak parametre değerlerini geçirin. Boş dizeler belirttiğinizde, bu yöntem çağrısı <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> uygulamanız için yapılandırılmış kimlik sağlayıcısı için yöntemi. Aşağıdaki kod örneği, tüm Windows Formları uygulamaya erişimi sınırlamak için bu yöntemi çağırır. Bu kodu ekleyebileceğiniz bir <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> işleyici.  
  
     [!code-csharp[ClientApplicationServices#317](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#317)]
     [!code-vb[ClientApplicationServices#317](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#317)]  
  
### <a name="to-authenticate-a-user-with-forms-authentication-without-using-a-membership-credentials-provider"></a>Forms kimlik doğrulaması ile bir kullanıcının bir üyelik kullanmadan kimlik doğrulaması için kimlik bilgileri sağlayıcısı  
  
-   Çağrı `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> kullanıcıdan alınan yöntemi ve kullanıcı adı ve parola değerlerini geçirin.  
  
     [!code-csharp[ClientApplicationServices#318](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#318)]
     [!code-vb[ClientApplicationServices#318](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#318)]  
  
### <a name="to-authenticate-a-user-with-windows-authentication"></a>Windows kimlik doğrulaması ile bir kullanıcının kimliğini doğrulamak için  
  
-   Çağrı `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi ve pass boş dizeler için parametreleri. Bu yöntem çağrısının her zaman döndürür `true` ve Windows kimlik içeren kullanıcının tanımlama bilgisi önbelleği için bir tanımlama bilgisi ekler.  
  
     [!code-csharp[ClientApplicationServices#319](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#319)]
     [!code-vb[ClientApplicationServices#319](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#319)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu konudaki örnek kod, bir Windows istemci uygulamasında kimlik doğrulamasının en basit kullanımları gösterir. Çağırdığınızda `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi ile istemci uygulama hizmetleri ve forms kimlik doğrulaması, kodunuzu ancak oluşturabilecek bir <xref:System.Net.WebException>. Bu kimlik doğrulama hizmeti kullanılamaz olduğunu gösterir. Bu özel durumu işlemek nasıl bir örnek için bkz [izlenecek yol: istemci uygulama hizmetleri kullanarak](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemci Uygulama Servisleri](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [İstemci Uygulama Servislerine Genel Bakış](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [İzlenecek Yol: İstemci Uygulama Servislerini Kullanma](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [Microsoft Ajax ile Forms kimlik doğrulaması kullanma](https://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)
