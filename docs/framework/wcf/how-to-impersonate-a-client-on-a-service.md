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
ms.openlocfilehash: d58f25f279bf2baa1caa7744cea94b909f48866f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310583"
---
# <a name="how-to-impersonate-a-client-on-a-service"></a>Nasıl yapılır: Bir Hizmette İstemci Kimliğine Bürünme
Bir Windows Communication Foundation (WCF) hizmette istemci kimliğine bürünme istemci adına eylem gerçekleştirmek hizmet sağlar. Erişim tabi eylemleri için Denetim listesi (ACL), dizinleri ve dosyaları bir makinede erişim veya bir SQL Server veritabanına erişimi gibi ACL onay istemci kullanıcı hesabıdır karşı denetler. Bu konuda, bir istemcinin kimliğe bürünme düzeyi ayarlamak bir istemci bir Windows etki alanında etkinleştirmek için gerekli temel adımlar gösterilmektedir. Bu çalışma örneği için bkz [istemci kimliğine bürünme](../../../docs/framework/wcf/samples/impersonating-the-client.md). İstemci kimliğine bürünme hakkında daha fazla bilgi için bkz: [temsilcilik ve kimliğe bürünme](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
> [!NOTE]
>  Ne zaman aynı bilgisayarda çalışan istemci ve hizmet ve istemci bir sistem hesabı altında çalışıyor (diğer bir deyişle, `Local System` veya `Network Service`), durum bilgisi olan güvenlik bağlamı belirteçleri ile güvenli bir oturum kurulduktan sonra istemci veritabanının özellikleri alınamaz. Böylece hesap varsayılan olarak taklit edilebileceğini bir WinForms ya da konsol uygulamasının genellikle şu anda oturum açmış hesap altında çalışır. Ancak, istemci olduğunda bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sayfası ve bu sayfayı barındırılan [!INCLUDE[iis601](../../../includes/iis601-md.md)] veya IIS 7.0 ve ardından istemci altında çalıştırmak `Network Service` varsayılan hesabı. Tüm güvenli oturumlar destekleyen sistem tarafından sağlanan bağlamaları, varsayılan olarak durum bilgisi olmayan bir güvenlik bağlamı belirteci kullanın. Ancak, istemci bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sayfası ve durum bilgisi olan güvenlik bağlamı belirteçleriyle güvenli oturumlar kullanılıyorsa, istemci veritabanının özellikleri alınamaz. Durum bilgisi olan güvenlik bağlamı belirteçleri güvenli bir oturumda kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bir güvenlik bağlamı oluşturmak için güvenli bir oturum belirteci](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a>Kimliğe bürünme, bir istemcinin bir hizmette önbelleğe alınmış bir Windows belirteçten etkinleştirmek için  
  
1. Hizmeti oluşturun. Bu temel yordamı ile ilgili öğretici için bkz. [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
2. Windows kimlik doğrulamasını kullanır ve bir oturumu, gibi oluşturan bir bağlamayı kullanan <xref:System.ServiceModel.NetTcpBinding> veya <xref:System.ServiceModel.WSHttpBinding>.  
  
3. Hizmetin arabirimi uygulaması oluştururken, uygulama <xref:System.ServiceModel.OperationBehaviorAttribute> istemci kimliğine bürünme gerektiren yöntemine sınıfı. Ayarlama <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliğini <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a>İstemcide izin verilen kimliğe bürünme düzeyini ayarlamak için  
  
1. Kullanarak hizmeti istemci kodunu oluşturmak [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Daha fazla bilgi için [WCF istemci kullanarak hizmetlere erişme](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).  
  
2. WCF istemcisini oluşturduktan sonra ayarlamak <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği <xref:System.ServiceModel.Security.WindowsClientCredential> sınıfı birine <xref:System.Security.Principal.TokenImpersonationLevel> sabit listesi değerleri.  
  
    > [!NOTE]
    >  Kullanılacak <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, üzerinde anlaşılan Kerberos kimlik doğrulaması (olarak da adlandırılır *çok oluşturan* veya *çok adımlı* Kerberos) kullanılmalıdır. Bu uygulama bir açıklaması için bkz: [en iyi güvenlik uygulamaları](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.Security.Principal.TokenImpersonationLevel>
- [İstemci Kimliğine Bürünme](../../../docs/framework/wcf/samples/impersonating-the-client.md)
- [Temsilcilik ve Kimliğe Bürünme](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
