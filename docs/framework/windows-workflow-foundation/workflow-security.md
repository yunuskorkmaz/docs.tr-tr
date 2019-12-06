---
title: İş Akışı Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: 36d03a2fca8f143b98338050fc9da4490960bda9
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837525"
---
# <a name="workflow-security"></a>İş Akışı Güvenliği
Windows Workflow Foundation (WF), Microsoft SQL Server ve Windows Communication Foundation (WCF) gibi birkaç farklı teknolojiyle tümleşiktir. Bu teknolojilerle etkileşim kurmak, doğru şekilde yapıldıysa iş akışınıza güvenlik sorunları ortaya çıkarabilir.

## <a name="persistence-security-concerns"></a>Kalıcı güvenlik sorunları

1. Bir <xref:System.Activities.Statements.Delay> etkinlik ve kalıcılık kullanan iş akışlarının bir hizmet tarafından yeniden etkinleştirilmesi gerekir. Windows AppFabric, zaman aşımına uğradı zamanlayıcıları olan iş akışlarını yeniden etkinleştirmek için Iş akışı yönetim hizmeti 'ni (WMS WMS, yeniden etkinleştirilen iş akışını barındırmak için bir <xref:System.ServiceModel.WorkflowServiceHost> oluşturur. WMS hizmeti durdurulmuşsa, zamanlayıcılar süreleri dolduğunda kalıcı iş akışları yeniden etkinleştirilmeyecektir.

2. Dayanıklı örnek oluşturma erişimi, uygulama etki alanına harici olan kötü amaçlı varlıklara karşı korunmalıdır. Ayrıca, geliştiriciler kötü amaçlı kodun dayanıklı örnek oluşturma kodu ile aynı uygulama etki alanında yürütülemeyecek şekilde emin olmalıdır.

3. Dayanıklı örnek oluşturma yükseltilmiş (yönetici) izinlerle çalıştırılmamalıdır.

4. Uygulama etki alanı dışında işlenen verilerin korunması gerekir.

5. Güvenlik yalıtımı gerektiren uygulamalar, şema soyutlama örneğini paylaşmamalıdır. Bu tür uygulamalar farklı depo örneklemeleri kullanmak üzere yapılandırılmış farklı mağaza sağlayıcıları veya mağaza sağlayıcıları kullanmalıdır.

## <a name="sql-server-security-concerns"></a>SQL Server güvenlik sorunları

- Çok sayıda alt etkinlik, konum, yer işareti, konak uzantısı ya da kapsam kullanıldığında ya da çok büyük yükleri olan yer işaretleri kullanıldığında, bellek tükenebilir veya süreklilik sırasında yetersiz miktarda veritabanı alanı ayrılabilir. Bu, nesne düzeyi ve veritabanı düzeyinde güvenlik kullanılarak azaltılabilir.

- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>kullanırken, örnek deposu güvenli olmalıdır.

- Örnek deposundaki hassas veriler şifrelenmelidir. Daha fazla bilgi için bkz. [SQL Server şifreleme](/sql/relational-databases/security/encryption/sql-server-encryption).

- Veritabanı bağlantı dizesi genellikle bir yapılandırma dosyasına dahil edildiğinden, yapılandırma dosyasının (genellikle Web. config) güvenli olduğundan ve bu oturum açma ve parola bilgilerinin ' de yer aldığından emin olmak için Windows düzeyi güvenlik (ACL) kullanılmalıdır. bağlantı dizesi. Bunun yerine, veritabanı ile Web sunucusu arasında Windows kimlik doğrulaması kullanılmalıdır.

## <a name="considerations-for-workflowservicehost"></a>WorkflowServiceHost ile ilgili konular

- İş akışlarında kullanılan Windows Communication Foundation (WCF) uç noktaları güvenli olmalıdır. Daha fazla bilgi için bkz. [WCF güvenliğine genel bakış](../wcf/feature-details/security-overview.md).

- Ana bilgisayar düzeyinde yetkilendirme, <xref:System.ServiceModel.ServiceAuthorizationManager>kullanılarak uygulanabilir. Ayrıntılar için bkz. [nasıl yapılır: bir hizmet Için özel Yetkilendirme Yöneticisi oluşturma](../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md) .

- Gelen ileti için ServiceSecurityContext, OperationContext öğesine erişerek iş akışı içinden de kullanılabilir.

## <a name="wf-security-pack-ctp"></a>WF Güvenlik Paketi CTP
 Microsoft WF Güvenlik Paketi CTP 1, bir dizi etkinliğin ve bunların uygulamalarının, [.NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (WF 4) ve [Windows Identity Foundation (wıf)](../security/index.md) [Windows Workflow Foundation](index.md) temel ALıNARAK birinci topluluk teknoloji önizleme (CTP) sürümüdür.  Microsoft WF Güvenlik Paketi CTP 1 hem etkinlikleri hem de bu iş akışını kullanarak güvenlikle ilgili çeşitli senaryoları nasıl kolayca etkinleştirebileceğinizi gösteren tasarımcılarını içerir:

1. İş akışındaki istemci kimliğini taklit etme

2. PrincipalPermission ve talepler doğrulaması gibi iş akışı yetkilendirmesi

3. Kullanıcı adı/parola veya bir güvenlik belirteci hizmetinden (STS) alınan bir belirteç gibi, iş akışında belirtilen ClientCredentials kullanılarak kimliği doğrulanmış mesajlaşma

4. WS-Trust ActAs kullanarak bir arka uç hizmetine istemci güvenlik belirteci akışı (talepler tabanlı temsili)

Daha fazla bilgi edinmek ve WF Güvenlik Paketi CTP 'yi indirmek için, bkz. [WF Güvenlik PAKETI CTP](https://archive.codeplex.com/?p=wf)
