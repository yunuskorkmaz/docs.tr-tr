---
title: "Nasıl yapılır: Bir Hizmette İstemci Kimliğine Bürünme"
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
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c868e2b31fa15d0f0c9228828beba03666d5591
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-impersonate-a-client-on-a-service"></a>Nasıl yapılır: Bir Hizmette İstemci Kimliğine Bürünme
Üzerinde bir istemci kimliğine bürünme bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hizmeti, istemci adına eylemleri gerçekleştirmek hizmet sağlar. Eylemler tabi erişim denetim listesi (ACL), dizinleri ve dosyaları bir makinede erişim veya bir SQL Server veritabanına erişimi gibi ACL onay istemci kullanıcı hesabıdır karşı denetler. Bu konu, bir istemcinin kimliğe bürünme düzeyi ayarlamak bir istemci bir Windows etki alanında etkinleştirmek için gereken temel adımlarda gösterir. Bu çalışma örnek için bkz: [istemci kimliğine bürünme](../../../docs/framework/wcf/samples/impersonating-the-client.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]İstemcinin kimliğe bürünme bkz [temsilcilik ve kimliğe bürünme](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
> [!NOTE]
>  Ne zaman istemci hem de hizmet aynı bilgisayarda çalışan ve istemci bir sistem hesabı altında çalışan (diğer bir deyişle, `Local System` veya `Network Service`), güvenli oturum durum bilgisi olan güvenlik bağlamı belirteçleriyle kurulduğunda istemci bürünülemez. Böylece hesap varsayılan olarak taklit edilebileceğini bir WinForms ya da konsol uygulaması genellikle şu anda oturum açmış hesabı altında çalışır. Ancak, istemci olduğunda bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sayfa ve bu sayfa barındırılan [!INCLUDE[iis601](../../../includes/iis601-md.md)] veya IIS 7.0 sonra istemci altında Çalıştır `Network Service` varsayılan hesabı. Güvenli oturumlar destek sistem tarafından sağlanan bağlamalar tümünün durumsuz bir güvenlik bağlamı belirteci varsayılan olarak kullanın. Ancak, istemci ise bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sayfası ve durum bilgisi olan güvenlik bağlamı belirteçleri ile güvenli oturumlar kullanılıyorsa, istemci bürünülemez. [!INCLUDE[crabout](../../../includes/crabout-md.md)]durum bilgisi olan güvenlik bağlamı belirteçleri kullanarak güvenli bir oturumda bkz [nasıl yapılır: güvenli oturum açmak için bir güvenlik bağlamı belirteci oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a>Bir hizmet önbelleğe alınmış Windows belirteç istemciden kimliğine bürünme etkinleştirmek için  
  
1.  Hizmeti oluşturun. Bu temel yordamı öğretici için bkz [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
2.  Windows kimlik doğrulamasını kullanır ve bir oturum gibi oluşturan bir bağlama kullanmak <xref:System.ServiceModel.NetTcpBinding> veya <xref:System.ServiceModel.WSHttpBinding>.  
  
3.  Hizmetin arabirimini uygulaması oluştururken, uygulama <xref:System.ServiceModel.OperationBehaviorAttribute> istemci kimliğe bürünme gerektiren yöntemi sınıfı. Ayarlama <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliğine <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a>İstemci üzerinde izin verilen kimliğe bürünme düzeyi ayarlamak için  
  
1.  Kullanarak hizmeti istemci kodunu oluşturmak [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Bir WCF istemcisi kullanarak hizmetlere erişme](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).  
  
2.  Oluşturduktan sonra [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci, kümesi <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği <xref:System.ServiceModel.Security.WindowsClientCredential> birine sınıfı <xref:System.Security.Principal.TokenImpersonationLevel> numaralandırma değerleri.  
  
    > [!NOTE]
    >  Kullanmak için <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, üzerinde anlaşılan Kerberos kimlik doğrulaması (bazen adlı *çok leg* veya *çok adımlı* Kerberos) kullanılması gerekir. Bu uygulama açıklaması için bkz: [en iyi güvenlik uygulamaları](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 [İstemci Kimliğine Bürünme](../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [Temsilcilik ve Kimliğe Bürünme](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
