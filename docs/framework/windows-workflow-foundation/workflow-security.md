---
title: "İş akışı güvenlik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dbb1d1efc0758410f12f2c669cca85b9f0e38406
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-security"></a>İş akışı güvenlik
[!INCLUDE[wf](../../../includes/wf-md.md)]Microsoft SQL Server gibi birçok farklı teknolojiler ile tümleşiktir ve [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]. Bu teknolojiler ile etkileşim yanlış yapıldığında iş akışınıza güvenlik sorunlar çıkarabilir.  
  
## <a name="persistence-security-concerns"></a>Kalıcı güvenlik sorunları  
  
1.  Kullanan iş akışları bir <xref:System.Activities.Statements.Delay> etkinliği ve kalıcı bir hizmeti tarafından yeniden etkinleştirilmesi gerekir. Windows AppFabric, iş akışları ile süresi dolan zamanlayıcılar yeniden etkinleştirmek için iş akışı yönetimi hizmeti (WMS) kullanır. WMS oluşturur bir <xref:System.ServiceModel.WorkflowServiceHost> yeniden etkinleştirilen iş akışı barındırmak için. WMS hizmeti durdurulursa, kendi zamanlayıcılar sona erdiğinde kalıcı iş akışlarını yeniden değil.  
  
2.  Uygulama etki alanına dış kötü amaçlı varlıklar karşı dayanıklı depolamasına erişim korunmalıdır. Ayrıca, geliştiricilerin kötü amaçlı kod dayanıklı örneklemesini kodu aynı uygulama etki alanında yürütülemez emin olmalısınız.  
  
3.  Dayanıklı örnek oluşturma, yükseltilmiş (Yönetici) izinlerle çalıştırılmamalıdır.  
  
4.  Uygulama etki alanı işlenmekte olan veriler korunmalıdır.  
  
5.  Güvenlik yalıtımı gerektiren uygulamalar şema soyutlama aynı örneği paylaşmamalıdır. Bu tür uygulamalar farklı deposu sağlayıcıları kullanın veya farklı deposu örneklemesi kullanmak üzere yapılandırılmış sağlayıcıları depolamak gerekir.  
  
## <a name="sql-server-security-concerns"></a>SQL Server güvenlik sorunları  
  
-   Çok sayıda alt etkinlikler, konumları, yer işaretleri, ana bilgisayar uzantıları veya kapsamları kullanıldığında veya yer işaretleri çok büyük yükleri ile kullanıldığında belleği tükendi veya veritabanı alanı aşırı miktarda sırasında Kalıcılık ayrılabilir. Bu nesne ve veritabanı düzeyi güvenlik kullanılarak azaltılabilir.  
  
-   Kullanırken <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, örnek deposuna güvenli hale getirilmelidir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][SQL Server en iyi uygulamalar](http://go.microsoft.com/fwlink/?LinkId=164972).  
  
-   Örnek deposuna gizli verileri şifrelenmelidir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][SQL güvenlik şifreleme](http://go.microsoft.com/fwlink/?LinkId=164976).  
  
-   Yapılandırma dosyasında (Web.Config genellikle) güvenlidir ve dahil oturum açma ve parola bilgilerini olmadığından emin olmak için veritabanı bağlantı dizesi genellikle bir yapılandırma dosyasına dahil olduğundan, windows düzeyi güvenlik (ACL) kullanılmalıdır bağlantı dizesi. Windows kimlik doğrulaması veritabanı ve web sunucusu arasında yerine kullanılmalıdır.  
  
## <a name="considerations-for-workflowservicehost"></a>WorkflowServiceHost için ilgili önemli noktalar  
  
-   [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]iş akışlarında kullanılan uç noktalarını güvenli hale getirilmelidir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF güvenliğine genel bakış](http://go.microsoft.com/fwlink/?LinkID=164975).  
  
-   Ana bilgisayar düzeyinde yetkilendirme kullanarak uygulanabilir <xref:System.ServiceModel.ServiceAuthorizationManager>. Bkz: [nasıl yapılır: Özel Yetkilendirme Yöneticisi için bir hizmet oluşturma](http://go.microsoft.com/fwlink/?LinkId=192228) Ayrıntılar için. Bu ayrıca aşağıdaki örnekte gösterilmiştir: [güvenli hale getirme iş akışı Hizmetleri](../../../docs/framework/windows-workflow-foundation/samples/securing-workflow-services.md).  
  
-   Gelen ileti ServiceSecurityContext de OperationContext erişerek iş akışı içinde kullanılabilir.  Bkz: [bir iş akışı hizmetinden OperationContext erişimi](../../../docs/framework/wcf/feature-details/accessing-operationcontext-from-a-workflow-service.md) Ayrıntılar için.  
  
## <a name="wf-security-pack-ctp"></a>WF güvenlik paketi CTP  
 İlk topluluk teknoloji Önizleme (CTP) sürümü etkinlikleri ve göre kendi uygulama kümesini Microsoft WF güvenlik paketi CTP 1. [Windows Workflow Foundation](http://msdn.microsoft.com/netframework/aa663328.aspx)içinde [.NET Framework 4](http://msdn.microsoft.com/netframework/default.aspx) (WF 4) ve [Windows Identity Foundation (WIF)](http://msdn.microsoft.com/security/aa570351.aspx).  Microsoft WF güvenlik paketi CTP 1 etkinlikleri ve kolayca iş akışını kullanarak güvenlikle ilgili çeşitli senaryoları etkinleştirmek nasıl çalışılacağını kendi tasarımcılar içerir dahil olmak üzere:  
  
1.  Bir istemci kimliği iş akışında kimliğine bürünme  
  
2.  PrincipalPermission ve talep doğrulama gibi iş akışı içinde yetkilendirme  
  
3.  İleti kimliği doğrulanmış kullanıcı adı/parola veya bir belirteç gibi iş akışında belirtilen ClientCredentials kullanarak bir güvenlik belirteci hizmeti (STS) öğesinden alınan  
  
4.  Bir istemci güvenlik belirteci WS-Trust ActAs kullanarak bir arka uç hizmetine (talep tabanlı temsilci) akan  
  
Daha fazla bilgi ve WF güvenlik paketi CTP karşıdan yüklemek için bkz: [WF güvenlik paketi CTP](http://wf.codeplex.com/releases/view/48114)