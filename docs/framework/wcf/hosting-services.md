---
title: Barındırma Hizmetleri
description: Bir WCF hizmeti için barındırma seçenekleri hakkında bilgi edinin. Bir hizmet, kendisini oluşturan bir çalışma zamanı ortamında barındırılmalıdır ve bağlamını ve ömrünü denetler.
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
ms.openlocfilehash: 86ce392bb76b22e2b6a65fa1d005ed8e9589af15
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246395"
---
# <a name="hosting-services"></a>Barındırma hizmetleri

Etkin hale gelmesi için bir hizmetin kendisini oluşturan bir çalışma zamanı ortamı içinde barındırılması ve bağlamını ve ömrünü denetmasıdır. Windows Communication Foundation (WCF) Hizmetleri, yönetilen kodu destekleyen herhangi bir Windows işleminde çalışmak üzere tasarlanmıştır.

WCF, hizmet yönelimli uygulamalar oluşturmaya yönelik Birleşik bir programlama modeli sağlar. Bu programlama modeli tutarlı kalır ve Hizmetin dağıtıldığı çalışma zamanı ortamından bağımsızdır. Pratikte bu, hizmetlerinize yönelik kodun barındırma seçeneği ne olursa olsun çok daha fazla göründüğünü gösterir.

Bu barındırma seçenekleri bir konsol uygulamasının içinde, Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti (WAS) tarafından yönetilen bir çalışan işlemi içinde çalışan bir Windows hizmeti gibi sunucu ortamlarında çalışır. Geliştiriciler, hizmetin dağıtım gereksinimlerini karşılayan barındırma ortamını seçer. Bu gereksinimler, uygulamanın dağıtıldığı platformdan, ileti göndermek ve almak zorunda olduğu taşıma işleminin, yeterli kullanılabilirliği sağlamak için gereken işlem geri dönüştürme ve diğer işlem yönetimi türü ya da başka bir yönetim ya da güvenilirlik gereksinimlerinden türetilebilir. Sonraki bölümde, barındırma seçenekleri hakkında bilgi ve yönergeler sağlanmaktadır.

## <a name="hosting-options"></a>Barındırma seçenekleri

### <a name="self-host-in-a-managed-application"></a>Yönetilen bir uygulamada Self-Host
 WCF Hizmetleri, yönetilen herhangi bir uygulamada barındırılabilir. Dağıtım için en az altyapıyı gerektirdiğinden bu en esnek seçenektir. Hizmetin kodunu yönetilen uygulama kodunun içine ekleyin ve sonra <xref:System.ServiceModel.ServiceHost> hizmeti kullanılabilir hale getirmek için bir örneğini oluşturup açın. Daha fazla bilgi için bkz. [nasıl yapılır: yönetilen bir uygulamada BIR WCF hizmeti barındırma](how-to-host-a-wcf-service-in-a-managed-application.md).

 Bu seçenek, iki yaygın senaryoyu mümkün bir şekilde sunar: konsol uygulamalarında çalışan WCF Hizmetleri ve Windows Presentation Foundation (WPF) veya Windows Forms (WinForms) tabanlı olanlar gibi zengin istemci uygulamaları. Bir WCF hizmetini bir konsol uygulaması içinde barındırmak, genellikle uygulamanın geliştirme aşamasında yararlıdır. Bu, uygulamanın içinde neler olduğunu öğrenmek ve yeni konumlara kopyalayarak kolayca geçiş yapmak için, ' den izleme bilgilerinin oluşmasını kolay bir şekilde oluşturmanızı kolaylaştırır. Bu barındırma seçeneği Ayrıca, WPF ve WinForms uygulamaları gibi zengin istemci uygulamalarının dış dünya ile iletişim kurmasını kolaylaştırır. Örneğin, Kullanıcı arabirimi için WPF kullanan eşler arası işbirliği istemcisi ve ayrıca diğer istemcilerin bu sunucuya bağlanmasına ve bilgi paylaşmasına izin veren bir WCF hizmeti barındırır.

### <a name="managed-windows-services"></a>Yönetilen Windows Hizmetleri

Bu barındırma seçeneği, bir WCF hizmetini yönetilen bir Windows hizmeti (eski adıyla NT hizmeti) olarak barındıran uygulama etki alanını (AppDomain) kaydettirerek hizmetin işlem yaşam süresinin Windows Hizmetleri için Hizmet Denetim Yöneticisi (SCM) tarafından denetlenmesine yöneliktir. Kendi kendine barındırma seçeneği gibi, bu tür bir barındırma ortamı, bazı barındırma kodunun uygulamanın bir parçası olarak yazılmasını gerektirir. Hizmet, bir <xref:System.ServiceProcess.ServiceBase> WCF hizmet sözleşmesi arabiriminden ve sınıfından kalıtımla almasına neden olarak hem bir Windows hizmeti hem de BIR WCF hizmeti olarak uygulanır. <xref:System.ServiceModel.ServiceHost>Daha sonra, geçersiz kılınan bir yöntem içinde oluşturulup açılır <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> ve geçersiz kılınan bir yöntem içinde kapatılır <xref:System.ServiceProcess.ServiceBase.OnStop> . İçinden devralan bir yükleyici sınıfı <xref:System.Configuration.Install.Installer> , programın Installutil.exe aracı tarafından bir Windows hizmeti olarak yüklenmesine izin vermek için de uygulanmalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: yönetilen bir Windows hizmetinde BIR WCF hizmeti barındırma](./feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md). Yönetilen Windows hizmeti barındırma seçeneği tarafından etkinleştirilen senaryo, ileti etkin olmayan güvenli bir ortamda IIS dışında barındırılan uzun süre çalışan bir WCF hizmetidir. Hizmetin kullanım ömrü, işletim sistemi tarafından bunun yerine denetlenir. Bu barındırma seçeneği Windows 'un tüm sürümlerinde kullanılabilir.

### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)

IIS barındırma seçeneği, ASP.NET ile tümleşiktir ve işlem geri dönüşümü, boşta kalma, işlem sistem durumu izleme ve ileti tabanlı etkinleştirme gibi bu teknolojilerin sunduğu özellikleri kullanır. Windows XP ve Windows Server 2003 işletim sistemlerinde bu, yüksek oranda kullanılabilir ve yüksek oranda ölçeklenebilir olması gereken Web hizmeti uygulamalarını barındırmak için tercih edilen çözümdür. IIS Ayrıca, müşterilerin bir kurumsal sınıf sunucu ürününden beklediği tümleşik yönetilebilirlik sağlar. Bu barındırma seçeneği IIS 'nin düzgün şekilde yapılandırılmasını gerektirir, ancak herhangi bir barındırma kodunun uygulamanın bir parçası olarak yazılmasını gerektirmez. WCF hizmeti için IIS barındırmanın nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: IIS 'de WCF hizmeti barındırma](./feature-details/how-to-host-a-wcf-service-in-iis.md).

 IIS tarafından barındırılan hizmetler yalnızca HTTP taşımasını kullanabilir. IIS 5,1 ' de uygulanması Windows XP 'de bazı sınırlamalar sunmuştur. Windows XP 'de IIS 5,1 tarafından bir WCF hizmeti için sunulan ileti tabanlı etkinleştirme, aynı bilgisayardaki diğer şirket içinde barındırılan WCF hizmetinin iletişim kurmak için 80 bağlantı noktasını kullanmasını engeller. WCF Hizmetleri, Windows Server 2003 üzerinde IIS 6,0 ile barındırılan diğer uygulamalarla aynı AppDomain/uygulama havuzunda/çalışan Işleminde çalıştırılabilir. Ancak, WCF ve IIS 6,0 her ikisi de çekirdek modu HTTP yığınını (HTTP.sys) kullandığından, IIS 6,0, bağlantı noktası 80 ' nı aynı makinede çalışan diğer şirket içinde barındırılan WCF hizmetleriyle paylaşabilir ve IIS 5,1 ' den farklı olabilir.

### <a name="windows-process-activation-service-was"></a>Windows Işlem etkinleştirme hizmeti (WAS)

Windows Işlem etkinleştirme hizmeti (WAS), Windows Server 2008 için Windows Vista 'da da kullanılabilir olan yeni işlem etkinleştirme mekanizmasıdır. Tanıdık IIS 6,0 işlem modelini (uygulama havuzları ve ileti tabanlı işlem etkinleştirme) ve barındırma özelliklerini (hızlı hata koruması, sistem durumu izleme ve geri dönüşüm gibi) korur, ancak etkinleştirme mimarisinden HTTP bağımlılığını kaldırır. IIS 7,0, HTTP üzerinden ileti tabanlı etkinleştirme gerçekleştirmeyi başarmıştı. Ek WCF bileşenleri Ayrıca, WCF tarafından desteklenen TCP, MSMQ ve adlandırılmış kanallar gibi diğer protokoller üzerinde ileti tabanlı etkinleştirme sağlamaktır. Bu, iletişim protokolleri kullanan uygulamaların işlem geri dönüştürme, hızlı hata koruması ve yalnızca HTTP tabanlı uygulamalarda kullanılabilen ortak yapılandırma sistemi gibi IIS özelliklerini kullanmasına olanak sağlar.

 Bu barındırma seçeneği, doğru şekilde yapılandırılmasını gerektirir, ancak uygulamanın bir parçası olarak herhangi bir barındırma kodu yazmanızı gerektirmez. WAS barındırmanın nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: BIR WCF hizmetini BARıNDıRMA was](./feature-details/how-to-host-a-wcf-service-in-was.md).

## <a name="choose-a-hosting-environment"></a>Barındırma ortamı seçin
 Aşağıdaki tabloda, barındırma seçeneklerinin her biriyle ilişkili bazı önemli avantajlar ve senaryolar özetlenmektedir.

|Barındırma ortamı|Genel Senaryolar|Önemli avantajlar ve sınırlamalar|
|-------------------------|----------------------|----------------------------------|
|Yönetilen uygulama ("kendiliğinden konak")|-Geliştirme sırasında kullanılan konsol uygulamaları.<br />-Hizmetlere erişen zengin WinForm ve WPF istemci uygulamaları.|Esnek.<br />-Kolay dağıtım.<br />-Hizmetler için kurumsal bir çözüm değildir.|
|Windows Hizmetleri (eski adıyla NT Hizmetleri olarak biliniyordu)|-IIS dışında barındırılan uzun süredir çalışan bir WCF hizmeti.|-Hizmet işlem ömrü, ileti etkin değil işletim sistemi tarafından denetlenir.<br />-Tüm Windows sürümleri tarafından desteklenir.<br />-Güvenli ortam.|
|IıS 5,1, ııS 6,0|-HTTP protokolünü kullanarak Internet üzerinde ASP.NET içeriğiyle bir WCF hizmetini yan yana çalıştırın.|-İşlem geri dönüşümü.<br />-Idle kapanıyor.<br />-İşlem durumu izleme.<br />-İleti tabanlı etkinleştirme.<br />-Yalnızca HTTP.|
|Windows Işlem etkinleştirme hizmeti (WAS)|-Çeşitli aktarım protokollerini kullanarak Internet 'e IIS yüklemeden bir WCF hizmeti çalıştırma.|-IIS gerekli değildir.<br />-İşlem geri dönüşümü.<br />-Idle kapanıyor.<br />-İşlem durumu izleme.<br />-İleti tabanlı etkinleştirme.<br />-HTTP, TCP, adlandırılmış kanallar ve MSMQ ile kullanılır.|
|IIS 7.0|-ASP.NET içeriğiyle bir WCF hizmeti çalıştırın.<br />-Çeşitli aktarım protokollerini kullanarak Internet üzerinde bir WCF hizmeti çalıştırın.|-Avantajlandı.<br />-ASP.NET ve IIS içeriğiyle tümleşiktir.|

 Bir barındırma ortamının seçimi, dağıtıldığı Windows sürümüne, ileti göndermek için gereken aktarımları ve işlem ve uygulama etki alanı geri dönüşüm türünü gerektirir. Aşağıdaki tabloda, bu gereksinimlerle ilgili veriler özetlenmektedir.

|Barındırma ortamı|Platform kullanılabilirliği|Desteklenen aktarımlar|İşlem ve AppDomain geri dönüştürme|
|-------------------------|---------------------------|--------------------------|-------------------------------------|
|Yönetilen uygulamalar ("kendiliğinden konak")|Windows XP, Windows Server 2003, Windows Vista,<br /><br /> Windows Server 2008|HTTP<br /><br /> net. TCP,<br /><br /> net. pipe,<br /><br /> net. MSMQ|No|
|Windows Hizmetleri (eski adıyla NT Hizmetleri olarak biliniyordu)|Windows XP, Windows Server 2003, Windows Vista,<br /><br /> Windows Server 2008|HTTP<br /><br /> net. TCP,<br /><br /> net. pipe,<br /><br /> net. MSMQ|No|
|IıS 5,1|Windows XP|HTTP|Yes|
|IIS 6.0|Windows Server 2003|HTTP|Yes|
|Windows Işlem etkinleştirme hizmeti (WAS)|Windows Vista, Windows Server 2008|HTTP<br /><br /> net. TCP,<br /><br /> net. pipe,<br /><br /> net. MSMQ|Yes|

 Güvenilir olmayan ana bilgisayar güvenlik güvenliği 'nden bir hizmet veya herhangi bir uzantıyı çalıştırmanın gerektiğini unutmayın. Ayrıca, bir uygulama, ' <xref:System.ServiceModel.ServiceHost> ın bir kimliğe bürünme özelliğini açarken kullanıcının oturumu kapatmadığından (örneğin, kullanıcının önbelleğe alınmasını) emin olmalıdır <xref:System.Security.Principal.WindowsIdentity> .

## <a name="see-also"></a>Ayrıca bkz.

- [Temel Programlama Yaşam Döngüsü](basic-programming-lifecycle.md)
- [Hizmet Sözleşmelerini Uygulama](implementing-service-contracts.md)
- [Nasıl yapılır: IIS'de WCF Hizmeti Barındırma](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma](./feature-details/how-to-host-a-wcf-service-in-was.md)
- [Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma](./feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma](how-to-host-a-wcf-service-in-a-managed-application.md)
