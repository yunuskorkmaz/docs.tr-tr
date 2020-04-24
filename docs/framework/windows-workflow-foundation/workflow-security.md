---
title: İş Akışı Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: 2a9b26f8da7616480f69a6c4580b8d351833c9ee
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646312"
---
# <a name="workflow-security"></a>İş Akışı Güvenliği
Windows İş Akışı Temeli (WF), Microsoft SQL Server ve Windows Communication Foundation (WCF) gibi birkaç farklı teknolojiyle tümleşiktir. Bu teknolojilerle etkileşim de yanlış yapılırsa iş akışınıza güvenlik sorunlarına neden olabilir.

## <a name="persistence-security-concerns"></a>Kalıcılık Güvenlik Endişeleri

1. Etkinlik <xref:System.Activities.Statements.Delay> ve kalıcılık kullanan iş akışlarının bir hizmet tarafından yeniden etkinleştirilmesi gerekir. Windows AppFabric, süresi dolmuş zamanlayıcılarla iş akışlarını yeniden etkinleştirmek için İş Akışı Yönetimi Hizmeti'ni (WMS) kullanır. WMS yeniden <xref:System.ServiceModel.WorkflowServiceHost> etkinleştirilen iş akışını barındıracak bir oluşturur. WMS hizmeti durdurulursa, zamanlayıcılarının süresi dolduğunda kalıcı iş akışları yeniden etkinleştirilmez.

2. Dayanıklı instancing erişim uygulama etki alanı dışında kötü niyetli varlıklara karşı korunmalıdır. Ayrıca, geliştiriciler kötü amaçlı kodun dayanıklı instancing koduyla aynı uygulama etki alanında yürütülememesini sağlamalıdır.

3. Dayanıklı instancing yükseltilmiş (Yönetici) izinleri ile çalıştırılmamalıdır.

4. Uygulama etki alanı dışında işlenen veriler korunmalıdır.

5. Güvenlik yalıtımı gerektiren uygulamalar şema soyutlama aynı örneği paylaşmamalıdır. Bu tür uygulamalar farklı mağaza sağlayıcıları veya farklı mağaza anlık kullanımları kullanmak üzere yapılandırılmış mağaza sağlayıcıları kullanmalıdır.

## <a name="sql-server-security-concerns"></a>SQL Server Güvenlik Endişeleri

- Çok sayıda alt etkinlik, konum, yer imleri, ana bilgisayar uzantıları veya kapsamlar kullanıldığında veya çok büyük taşıma yüklerine sahip yer imleri kullanıldığında, bellek tükenebilir veya kalıcılık sırasında gereksiz miktarda veritabanı alanı ayrılabilir. Bu, nesne düzeyi ve veritabanı düzeyinde güvenlik kullanılarak azaltılabilir.

- Kullanırken, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>örnek deposu güvenli olmalıdır.

- Örnek depodaki hassas veriler şifrelenmelidir. Daha fazla bilgi için [SQL Server Encryption'ye](/sql/relational-databases/security/encryption/sql-server-encryption)bakın.

- Veritabanı bağlantı dizesi genellikle bir yapılandırma dosyasına dahil olduğundan, yapılandırma dosyasının (Web.Config genellikle) güvenli olduğundan ve giriş ve parola bilgilerinin bağlantı dizesine dahil edilmemesini sağlamak için windows düzeyinde güvenlik (ACL) kullanılmalıdır. Windows kimlik doğrulaması yerine veritabanı ve web sunucusu arasında kullanılmalıdır.

## <a name="considerations-for-workflowservicehost"></a>İş AkışıServiceHost için Dikkat Edilecek Noktalar

- İş akışlarında kullanılan Windows Communication Foundation (WCF) uç noktaları güvence altına alınmalıdır. Daha fazla bilgi için [WCF Security Genel Bakış'a](../wcf/feature-details/security-overview.md)bakın.

- Ana bilgisayar düzeyinde yetkilendirme kullanılarak <xref:System.ServiceModel.ServiceAuthorizationManager>uygulanabilir. [Bkz. Nasıl Olunan:](../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md) Ayrıntılar için Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturun.

- Gelen iletiiçin ServiceSecurityContext, OperationContext'a erişerek iş akışı içinden de kullanılabilir.

## <a name="wf-security-pack-ctp"></a>WF Güvenlik Paketi CTP
 Microsoft WF Security Pack topluluk teknolojisi önizlemesi (CTP) 1, [.NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (WF 4) ve [Windows Identity Foundation (WIF)](https://docs.microsoft.com/previous-versions/dotnet/framework/security/index)'deki [Windows İş Akışı Vakfı'na](index.md) dayalı bir dizi etkinlik ve bunların uygulanmasıdır. Microsoft WF Güvenlik Paketi CTP 1, iş akışını kullanarak güvenlikle ilgili çeşitli senaryoları nasıl kolayca etkinleştireceklerini gösteren hem etkinlikleri hem de tasarımcılarını içerir:

1. İş akışında istemci kimliğinin kimliğine bürünme

2. PrincipalPermission ve Taleplerin doğrulanması gibi iş akışı yetkilendirmesi

3. İş akışında belirtilen kullanıcı adı/parola veya Güvenlik Belirteci Hizmeti'nden (STS) alınan bir belirteç gibi Istemci Kimlik Bilgilerini kullanarak kimlik doğrulaması

4. WS-Trust ActAs'ı kullanarak istemci güvenlik belirteci bir arka uç hizmetine (talep tabanlı delegasyon) akması

Daha fazla bilgi ve WF Güvenlik Paketi CTP indirmek için bkz: [WF Güvenlik Paketi CTP](https://archive.codeplex.com/?p=wf)
