---
title: İş Akışı Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: d2d8556b1ed2ac0a2b030a88d6bfc0ad48ed6f5c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557521"
---
# <a name="workflow-security"></a>İş Akışı Güvenliği
Windows Workflow Foundation (WF), Microsoft SQL Server ve Windows Communication Foundation (WCF) gibi birkaç farklı teknolojiyle tümleşiktir. Bu teknolojilerle etkileşim kurmak, doğru şekilde yapıldıysa iş akışınıza güvenlik sorunları ortaya çıkarabilir.

## <a name="persistence-security-concerns"></a>Kalıcı güvenlik sorunları

1. <xref:System.Activities.Statements.Delay>Etkinlik ve kalıcılık kullanan iş akışlarının bir hizmet tarafından yeniden etkinleştirilmesi gerekir. Windows AppFabric, zaman aşımına uğradı zamanlayıcıları olan iş akışlarını yeniden etkinleştirmek için Iş akışı yönetim hizmeti 'ni (WMS WMS, yeniden <xref:System.ServiceModel.WorkflowServiceHost> etkinleştirilen iş akışını barındırmak için bir oluşturur. WMS hizmeti durdurulmuşsa, zamanlayıcılar süreleri dolduğunda kalıcı iş akışları yeniden etkinleştirilmeyecektir.

2. Dayanıklı örnek oluşturma erişimi, uygulama etki alanına harici olan kötü amaçlı varlıklara karşı korunmalıdır. Ayrıca, geliştiriciler kötü amaçlı kodun dayanıklı örnek oluşturma kodu ile aynı uygulama etki alanında yürütülemeyecek şekilde emin olmalıdır.

3. Dayanıklı örnek oluşturma yükseltilmiş (yönetici) izinlerle çalıştırılmamalıdır.

4. Uygulama etki alanı dışında işlenen verilerin korunması gerekir.

5. Güvenlik yalıtımı gerektiren uygulamalar, şema soyutlama örneğini paylaşmamalıdır. Bu tür uygulamalar farklı depo örneklemeleri kullanmak üzere yapılandırılmış farklı mağaza sağlayıcıları veya mağaza sağlayıcıları kullanmalıdır.

## <a name="sql-server-security-concerns"></a>SQL Server güvenlik sorunları

- Çok sayıda alt etkinlik, konum, yer işareti, konak uzantısı ya da kapsam kullanıldığında ya da çok büyük yükleri olan yer işaretleri kullanıldığında, bellek tükenebilir veya süreklilik sırasında yetersiz miktarda veritabanı alanı ayrılabilir. Bu, nesne düzeyi ve veritabanı düzeyinde güvenlik kullanılarak azaltılabilir.

- Kullanırken <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , örnek deposu güvenli olmalıdır.

- Örnek deposundaki hassas veriler şifrelenmelidir. Daha fazla bilgi için bkz. [SQL Server şifreleme](/sql/relational-databases/security/encryption/sql-server-encryption).

- Veritabanı bağlantı dizesi genellikle bir yapılandırma dosyasına eklendiğinden, yapılandırma dosyasının (genellikle Web.Config) güvende olduğundan ve oturum açma ve parola bilgilerinin bağlantı dizesinde bulunmadığından emin olmak için Windows düzeyinde güvenlik (ACL) kullanılmalıdır. Bunun yerine, veritabanı ile Web sunucusu arasında Windows kimlik doğrulaması kullanılmalıdır.

## <a name="considerations-for-workflowservicehost"></a>WorkflowServiceHost ile ilgili konular

- İş akışlarında kullanılan Windows Communication Foundation (WCF) uç noktaları güvenli olmalıdır. Daha fazla bilgi için bkz. [WCF güvenliğine genel bakış](../wcf/feature-details/security-overview.md).

- Konak düzeyinde yetkilendirme, kullanılarak uygulanabilir <xref:System.ServiceModel.ServiceAuthorizationManager> . Ayrıntılar için bkz. [nasıl yapılır: bir hizmet Için özel Yetkilendirme Yöneticisi oluşturma](../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md) .

- Gelen ileti için ServiceSecurityContext, OperationContext öğesine erişerek iş akışı içinden de kullanılabilir.

## <a name="wf-security-pack-ctp"></a>WF Güvenlik Paketi CTP
 Microsoft WF güvenlik paketi Community Technology Preview (CTP) 1, [.NET Framework 4](/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (WF 4) ve [Windows Identity Foundation (WIF)](/previous-versions/dotnet/framework/security/index)içindeki [Windows Workflow Foundation](index.md) temel alan bir dizi etkinliklerdir. Microsoft WF Güvenlik Paketi CTP 1 hem etkinlikleri hem de bu iş akışını kullanarak güvenlikle ilgili çeşitli senaryoları nasıl kolayca etkinleştirebileceğinizi gösteren tasarımcılarını içerir:

1. İş akışındaki istemci kimliğini taklit etme

2. PrincipalPermission ve talepler doğrulaması gibi iş akışı yetkilendirmesi

3. Kullanıcı adı/parola veya bir güvenlik belirteci hizmetinden (STS) alınan bir belirteç gibi, iş akışında belirtilen ClientCredentials kullanılarak kimliği doğrulanmış mesajlaşma

4. WS-Trust ActAs kullanarak bir arka uç hizmetine istemci güvenlik belirteci akışı (talepler tabanlı temsili)

Daha fazla bilgi edinmek ve WF Güvenlik Paketi CTP 'yi indirmek için, bkz. [WF Güvenlik PAKETI CTP](https://archive.codeplex.com/?p=wf)
