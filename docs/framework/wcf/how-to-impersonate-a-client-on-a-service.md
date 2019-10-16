---
title: 'Nasıl yapılır: Bir Hizmette İstemci Kimliğine Bürünme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
ms.openlocfilehash: 34650a2a6cc32e16581e692b55d24d2fe02b6884
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320961"
---
# <a name="how-to-impersonate-a-client-on-a-service"></a>Nasıl yapılır: Bir Hizmette İstemci Kimliğine Bürünme
Windows Communication Foundation (WCF) hizmeti üzerinde bir istemcinin kimliğine bürünme hizmeti, hizmetin istemci adına eylem gerçekleştirmesine olanak sağlar. Bir makinedeki dizinlere ve dosyalara erişim veya SQL Server veritabanına erişim gibi erişim denetim listesi (ACL) denetimlerine tabi olan eylemler için, ACL denetimi istemci kullanıcı hesabına göre yapılır. Bu konuda, bir Windows etki alanındaki bir istemcinin istemci kimliğe bürünme düzeyi ayarlaması için gereken temel adımlar gösterilmektedir. Bunun çalışan bir örneği için bkz. [Istemcinin kimliğine bürünme](./samples/impersonating-the-client.md). İstemci kimliğe bürünme hakkında daha fazla bilgi için bkz. [temsil ve kimliğe bürünme](./feature-details/delegation-and-impersonation-with-wcf.md).  
  
> [!NOTE]
> İstemci ve hizmet aynı bilgisayarda çalışırken ve istemci bir sistem hesabı altında (yani `Local System` veya `Network Service`) çalışıyorsa, durum bilgisi olan güvenlik bağlamı belirteçleriyle güvenli bir oturum oluşturulduğunda istemciye kimliğe bürünme yapılamaz. Bir WinForms veya konsol uygulaması genellikle şu anda oturum açmış olan hesap altında çalışır, bu sayede hesaba varsayılan olarak kimliğe bürünme yapılabilir. Ancak, istemci bir ASP.NET sayfası olduğunda ve Bu sayfa IIS 6,0 veya IIS 7,0 ' de barındırılıyorsa, istemci varsayılan olarak `Network Service` hesabı altında çalışır. Güvenli oturumları destekleyen sistem tarafından sağlanmış tüm bağlamalar, varsayılan olarak durum bilgisiz güvenlik bağlamı belirtecini kullanır. Ancak, istemci bir ASP.NET sayfasıdır ve durum bilgisi olan güvenlik bağlamı belirteçleri olan güvenli oturumlar kullanılırsa, istemciye kimliğe bürünme yapılamaz. Güvenli bir oturumda durum bilgisi olan güvenlik bağlamı belirteçleri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenli bir oturum Için güvenlik bağlamı belirteci oluşturma](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a>Bir hizmette önbelleğe alınmış bir Windows belirtecinden istemci kimliğine bürünme özelliğini etkinleştirmek için  
  
1. Hizmeti oluşturun. Bu temel yordamın bir öğreticisi için bkz. [Başlangıç Öğreticisi](getting-started-tutorial.md).  
  
2. Windows kimlik doğrulaması kullanan bir bağlama kullanın ve <xref:System.ServiceModel.NetTcpBinding> veya <xref:System.ServiceModel.WSHttpBinding> gibi bir oturum oluşturur.  
  
3. Hizmet arabiriminin uygulamasını oluştururken, <xref:System.ServiceModel.OperationBehaviorAttribute> sınıfını istemci kimliğe bürünme gerektiren yönteme uygulayın. @No__t-0 özelliğini <xref:System.ServiceModel.ImpersonationOption.Required> olarak ayarlayın.  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a>İstemcide izin verilen kimliğe bürünme düzeyini ayarlamak için  
  
1. [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)kullanarak hizmet istemci kodu oluşturun. Daha fazla bilgi için bkz. [WCF Istemcisi kullanarak hizmetlere erişme](accessing-services-using-a-wcf-client.md).  
  
2. WCF istemcisini oluşturduktan sonra, <xref:System.ServiceModel.Security.WindowsClientCredential> sınıfının <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliğini <xref:System.Security.Principal.TokenImpersonationLevel> sabit listesi değerlerinden birine ayarlayın.  
  
    > [!NOTE]
    > @No__t-0 ' ı kullanmak için, anlaşmalı Kerberos kimlik doğrulaması (bazen *çok aşamalı* veya *çok adımlı* Kerberos olarak adlandırılır) kullanılmalıdır. Bunun nasıl uygulanacağı hakkında bir açıklama için bkz. [güvenlik Için En Iyi uygulamalar](./feature-details/best-practices-for-security-in-wcf.md).  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.Security.Principal.TokenImpersonationLevel>
- [İstemci Kimliğine Bürünme](./samples/impersonating-the-client.md)
- [Temsilcilik ve Kimliğe Bürünme](./feature-details/delegation-and-impersonation-with-wcf.md)
