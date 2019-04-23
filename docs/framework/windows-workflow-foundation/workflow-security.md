---
title: İş Akışı Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: a5a8d4d0d41efb7a255080994c8e18302d302447
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773226"
---
# <a name="workflow-security"></a>İş Akışı Güvenliği
Windows Workflow Foundation (WF), Microsoft SQL Server ve Windows Communication Foundation (WCF) gibi birçok farklı teknoloji ile tümleşiktir. Bu teknolojiler ile etkileşim güvenlik sorunları yanlış yapıldığında, iş akışınıza neden olabilir.

## <a name="persistence-security-concerns"></a>Kalıcılık güvenlik konuları

1. İş akışı bir <xref:System.Activities.Statements.Delay> etkinliği ve kalıcı bir hizmet tarafından etkinleştirilmesi gerekir. Windows AppFabric, süresi dolmuş zamanlayıcılar ile iş akışlarını yeniden etkinleştirmek için iş akışı yönetimi hizmeti (WMS) kullanır. WMS oluşturur bir <xref:System.ServiceModel.WorkflowServiceHost> yeniden etkinleştirilen iş akışı barındırma için. WMS hizmeti durdurulursa, zamanlayıcılar sona erdiğinde kalıcı iş akışlarını yeniden etkinleştirilmedi.

2. Dayanıklı örnek oluşturma erişimi, kötü amaçlı varlıkları dış uygulama etki alanına karşı korunmalıdır. Ayrıca, geliştiriciler kötü amaçlı kod dayanıklı örneklemesini kod aynı uygulama etki alanında çalıştırılamayacağından emin olmalısınız.

3. Dayanıklı örnek oluşturma, yükseltilmiş (Yönetici) izinlerle çalıştırılmamalıdır.

4. Uygulama etki alanı işlenmekte olan verinin korunmalıdır.

5. Güvenlik yalıtımı gerektiren uygulamalar için şema Özeti'nın aynı örneğine paylaşmamalıdır. Bu tür uygulamalar farklı depolama sağlayıcıları kullanın veya farklı depolama örneklemeleri kullanacak şekilde yapılandırılmış sağlayıcıları depolamak gerekir.

## <a name="sql-server-security-concerns"></a>SQL Server güvenlik konuları

-   Çok sayıda alt etkinlikleri, konumları, yer işaretleri, konak uzantıları veya kapsamları kullanıldığında veya çok büyük yükleri yer işaretleriyle kullanıldığında, bellek tükendi veya Kalıcılık sırasında veritabanı boş alanı aşırı miktarda ayrılabilir. Bu, nesne düzeyinde ve veritabanı düzeyinde güvenlik kullanarak azaltılabilir.

-   Kullanırken <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, örnek deposuna güvenli hale getirilmelidir. Daha fazla bilgi için [SQL Server en iyi uygulamaları](https://go.microsoft.com/fwlink/?LinkId=164972).

-   Örnek deposunda hassas verilerin şifrelenmesi. Daha fazla bilgi için [SQL güvenlik şifrelemesi](https://go.microsoft.com/fwlink/?LinkId=164976).

-   Yapılandırma dosyasında (Web.Config genellikle) güvenlidir ve bulunan oturum açma ve parola bilgisi olmadığından emin olmak için veritabanı bağlantı dizesi genellikle bir yapılandırma dosyasına dahil olduğundan, windows düzeyi güvenlik (ACL) kullanılmalıdır bağlantı dizesi. Windows kimlik doğrulaması web sunucusu ve veritabanı arasında yerine kullanılmalıdır.

## <a name="considerations-for-workflowservicehost"></a>WorkflowServiceHost dikkate alınacak noktalar

-   İş akışlarında kullanılan bir Windows Communication Foundation (WCF) uç noktalarını güvenli hale getirilmelidir. Daha fazla bilgi için [WCF güvenliğine genel bakış](https://go.microsoft.com/fwlink/?LinkID=164975).

-   Konak düzeyinde yetkilendirme kullanarak uygulanabilir <xref:System.ServiceModel.ServiceAuthorizationManager>. Bkz: [nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](https://go.microsoft.com/fwlink/?LinkId=192228) Ayrıntılar için.

-   Gelen iletinin ServiceSecurityContext ayrıca OperationContext erişimi tarafından iş akışı içinde kullanılabilir.

## <a name="wf-security-pack-ctp"></a>WF güvenlik paketi CTP
 İlk topluluk teknoloji Önizleme (CTP) sürümü bir dizi etkinlikleri ve kendi uygulama temel Microsoft WF güvenlik paketi CTP 1. [Windows Workflow Foundation](index.md) içinde [.NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (WF (4) ve [Windows Identity Foundation (WIF)](../security/index.md).  Microsoft WF güvenlik paketi CTP 1 etkinlikleri ve hangi kolayca iş akışı kullanarak güvenlikle ilgili çeşitli senaryoları etkinleştirmek nasıl çalışılacağını, tasarımcılar içerir dahil olmak üzere:

1. Bir istemci kimliği iş akışında kimliğine bürünme

2. PrincipalPermission ve talep doğrulama gibi iş akışı içinde yetkilendirme

3. Bir güvenlik belirteci hizmeti (STS) öğesinden alınan ileti kimliği doğrulanmış kullanıcı adı/parola veya belirteci gibi iş akışı içinde belirtilen ClientCredentials kullanma

4. WS-Trust ActAs kullanarak arka uç hizmeti (talep tabanlı temsilci) için bir istemci güvenlik belirteci akan

Daha fazla bilgi ve WF güvenlik paketi CTP indirmek için bkz: [WF güvenlik paketi CTP](https://archive.codeplex.com/?p=wf)