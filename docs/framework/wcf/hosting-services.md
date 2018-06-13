---
title: Barındırma Hizmetleri
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
ms.openlocfilehash: d4fb974cdfec87606f13b5cbd83be2c86f2a1ae5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807859"
---
# <a name="hosting-services"></a>Barındırma Hizmetleri
Etkin hale gelmesi bir hizmet oluşturduğu ve yaşam süresi ve bağlam denetleyen bir çalışma zamanı ortamında barındırılması gerekir. Windows Communication Foundation (WCF) hizmetlerini destekleyen yönetilen kodu herhangi bir Windows işlemin çalışmak üzere tasarlanmıştır.  
  
 WCF hizmet odaklı uygulamalar oluşturmak için birleşik bir programlama modeli sağlar. Bu programlama modeli, tutarlı kalır ve hizmetin dağıtıldığı çalışma zamanı ortamını bağımsızdır. Uygulamada, bu kod hizmetleriniz için aynı ne olursa olsun barındırma seçeneği benzer olduğunu anlamına gelir.  
  
 Bunlar gibi bir Windows hizmeti çalışan bir çalışan işlemi içinde Internet Information Services (IIS) tarafından ya da Windows İşlem Etkinleştirme Hizmeti (WAS) tarafından yönetilen çalışmasını sunucu ortamları için bir konsol uygulaması içinde seçenekleri aralığı barındırma. Geliştiriciler hizmetin dağıtım gereksinimlerini karşılayan barındırma ortamı seçin. Bu gereksinimleri hangi uygulamanın dağıtıldığını, platform üzerinde onu gerekir iletileri almasına ve göndermesine, taşıma veya işlem geri dönüştürme ve yeterli kullanılabilirliğini sağlamak için gereken diğer işlem yönetimi türüne veya bazı türetilen diğer yönetim veya Güvenilirlik gereksinimleri. Sonraki bölümde, seçenekleri barındırma hakkında bilgi ve yönergeler sağlar.  
  
## <a name="hosting-options"></a>Barındırma seçenekleri  
  
#### <a name="self-hosting-in-a-managed-application"></a>Kendi kendine yönetilen bir uygulamada barındırma  
 WCF hizmetleri yönetilen bir uygulamada barındırılabilir. Dağıtmak için en az altyapısı gerektiğinden bu en esnek bir seçenektir. Yönetilen uygulama kod içinde hizmet için kod ekleme ve oluşturma ve bir örneği açın <xref:System.ServiceModel.ServiceHost> servisi kullanılabilir duruma getirmek için. Daha fazla bilgi için bkz: [nasıl yapılır: yönetilen bir uygulamada bir WCF Hizmeti barındırma](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Bu seçenek iki yaygın senaryolara olanak sağlar: WCF Hizmetleri konsol uygulamaları ve olanlar gibi zengin istemci uygulamaları içinde çalıştıran tabanlı Windows Presentation Foundation (WPF) veya Windows Forms (WinForms). Bir konsol uygulaması içindeki bir WCF Hizmeti barındırma uygulama geliştirme aşamasında genellikle yararlıdır. Bu onları kolay hata ayıklamak, uygulama içinde neler olduğunu çıkışı bulmak için izleme bilgilerini almak kolay ve yeni konumlara kopyalayarak hareket etmek kolay hale getirir. Barındırma bu seçenek ayrıca zengin istemci uygulamaları gibi kolaylaştırır [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] ve dış dünyayla iletişim kurmak için WinForms uygulamalar. Örneğin, kullanan eşler arası işbirliği istemci [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] kendi kullanıcı arabirimi için ve ayrıca bağlanmak ve bilgi paylaşmak diğer istemcilerin bir WCF hizmetini barındırır.  
  
#### <a name="managed-windows-services"></a>Yönetilen Windows Hizmetleri  
 Böylece hizmetinin işlem yaşam süresi Hizmet Denetimi Yöneticisi (SCM) tarafından denetlenen bir WCF Hizmeti (önceki adıyla NT hizmeti olarak da bilinir) yönetilen bir Windows hizmeti olarak barındıran uygulama etki alanı (AppDomain) kaydolma bu barındırma seçeneği oluşur Windows Hizmetleri. Kendi kendine barındırma seçeneği gibi bazı barındırma kodu uygulamanın bir parçası yazılmıştır bu tür barındırma ortamı gerektirir. Hizmet hem de bir Windows hizmeti ve bir WCF hizmeti olarak devralınacak neden tarafından uygulanır <xref:System.ServiceProcess.ServiceBase> sınıf yanı sıra bir WCF Hizmeti sözleşmesi arabirimi. <xref:System.ServiceModel.ServiceHost> Sonra oluşturulan ve bir geçersiz kılınan içinde açılan <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> yöntemi ve bir geçersiz kılınan içinde kapalı <xref:System.ServiceProcess.ServiceBase.OnStop> yöntemi. Öğesinden devralınan bir yükleyici sınıfı <xref:System.Configuration.Install.Installer> Installutil.exe aracı tarafından bir Windows hizmeti olarak yüklenecek program izin vermek için de uygulanmalıdır. Daha fazla bilgi için bkz: [nasıl yapılır: yönetilen bir Windows hizmetinde bir WCF Hizmeti barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md). Yönetilen Windows seçeneği barındırma hizmeti tarafından etkin senaryo ileti-etkinleştirilmediğini güvenli bir ortamda IIS dışında barındırılan uzun süre çalışan WCF Hizmeti olmasıdır. Hizmet ömrü, bunun yerine işletim sistemi tarafından denetlenir. Barındırma bu seçenek, tüm Windows sürümlerinde kullanılabilir.  
  
#### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)  
 Barındırma seçeneği IIS ile tümleşiktir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ve bu teknolojiler sunar, işlem geri dönüştürme, boşta kapatma, sistem durumu izleme işlemi ve ileti tabanlı etkinleştirme gibi özellikleri kullanır. Üzerinde [!INCLUDE[wxp](../../../includes/wxp-md.md)] ve [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] işletim sistemleri, bu olduğu yüksek oranda kullanılabilir ve ölçeklendirilebilir olmalıdır Web hizmeti uygulamalarını barındırmak için tercih edilen bir çözüm. IIS, aynı zamanda müşterilerin bir kurumsal sınıf server ürün beklediğiniz tümleşik yönetilebilirlik sağlar. Bu barındırma seçeneği IIS düzgün şekilde yapılandırılmasını gerektirir, ancak herhangi bir barındırma kod uygulamanın bir parçası yazılması gerektirmez. Bir WCF hizmeti için barındırma IIS yapılandırma hakkında daha fazla bilgi için bkz [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
 IIS barındırılan hizmetleri yalnızca HTTP taşıma kullanabilirsiniz. IIS 5.1 kendi uygulamasında bazı sınırlamalar anlatılmıştır [!INCLUDE[wxp](../../../includes/wxp-md.md)]. Bir WCF hizmeti için IIS 5.1 tarafından sağlanan ileti tabanlı etkinleştirme [!INCLUDE[wxp](../../../includes/wxp-md.md)] herhangi diğer kendi kendini barındıran WCF Hizmeti iletişim kurmak için 80 numaralı bağlantı noktasını kullanarak aynı bilgisayarda engeller. WCF hizmetleri aynı AppDomain/uygulama havuzu/çalışan işlem tarafından barındırılan diğer uygulamaları olarak çalıştırabilirsiniz [!INCLUDE[iis601](../../../includes/iis601-md.md)] üzerinde [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Ancak çünkü WCF ve [!INCLUDE[iis601](../../../includes/iis601-md.md)] hem de çekirdek modu HTTP yığınını (HTTP.sys) kullanmak [!INCLUDE[iis601](../../../includes/iis601-md.md)] bağlantı noktası 80 IIS 5.1 aksine aynı makine üzerinde çalışan diğer kendi kendini barındıran WCF hizmetleri ile paylaşabilirsiniz.  
  
#### <a name="windows-process-activation-service-was"></a>Windows İşlem Etkinleştirme Hizmeti (WAS)  
 Windows İşlem Etkinleştirme Hizmeti (WAS) mekanizmasıdır yeni işlem etkinleştirme için [!INCLUDE[lserver](../../../includes/lserver-md.md)] olan de kullanılabilir [!INCLUDE[wv](../../../includes/wv-md.md)]. Bilinen korur [!INCLUDE[iis601](../../../includes/iis601-md.md)] işlem modelini (uygulama havuzları ve işlem ileti tabanlı etkinleştirme) ve barındırma özellikleri (örneğin, hızlı hata koruması, sistem durumu izleme ve geri dönüşüm), ancak bunu etkinleştirmeden HTTP üzerindeki bağımlılığı kaldırır Mimari. [!INCLUDE[iisver](../../../includes/iisver-md.md)] HTTP üzerinden ileti tabanlı etkinleştirme gerçekleştirmek için WAS kullanır. Ek WCF bileşenleri ileti tabanlı etkinleştirme, WCF destekleyen diğer protokoller üzerinden, TCP, MSMQ ve adlandırılmış kanallar gibi sağlamak üzere WAS ayrıca takın. Bu işlem geri dönüştürme gibi IIS özelliklerini hızlı kullanmaya iletişim protokolleri kullanan uygulamaları koruma ve yalnızca HTTP tabanlı uygulamalar için de kullanılabilir ortak yapılandırma sistemi başarısız sağlar.  
  
 Bu barındırma seçeneği gerektirir, olması düzgün şekilde yapılandırıldığından, ancak, uygulamanın bir parçası barındırma kod yazmaya gerektirmez. Nasıl yapılandırılacağı hakkında daha fazla bilgi barındırma için bkz: [nasıl yapılır: bir WCF Hizmeti barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="choosing-a-hosting-environment"></a>Bir barındırma ortamı seçme  
 Aşağıdaki tabloda bazı avantajları ve her barındırma seçenekleri ile ilgili senaryolar özetlenmiştir.  
  
|Barındırma ortamı|Yaygın senaryolar|Avantajları ve sınırlamaları|  
|-------------------------|----------------------|----------------------------------|  
|Yönetilen uygulama ("kendi kendini barındıran")|-Konsol uygulamaları geliştirme sırasında kullanılır.<br />-Zengin WinForm ve [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] istemci uygulamaları hizmetlerine erişme.|-Esnek.<br />-Kolay dağıtın.<br />-Olmayan bir kuruluş çözümü Hizmetleri için.|  
|Windows (önceki adıyla NT hizmeti olarak bilinir) Hizmetleri|-IIS dışında barındırılan uzun süre çalışan WCF hizmeti.|-Hizmet işlemi ömrü ileti etkinleştirilmedi işletim sistemi tarafından denetlenen.<br />-Tüm Windows sürümlerinde desteklenir.<br />-Güvenli bir ortam.|  
|IIS 5.1, [!INCLUDE[iis601](../../../includes/iis601-md.md)]|-Çalıştıran bir WCF Hizmeti yana birimi ile [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Internet'te HTTP protokolünü kullanan içerik.|-İşlem geri dönüştürme.<br />-Boşta kapatma.<br />-Sistem durumu izleme işlemi.<br />-İleti tabanlı etkinleştirme.<br />-Yalnızca HTTP.|  
|Windows İşlem Etkinleştirme Hizmeti (WAS)|-Çeşitli aktarım protokolünü kullanarak Internet'te IIS yüklemeden bir WCF hizmeti çalışıyor.|-IIS gerekli değildir.<br />-İşlem geri dönüştürme.<br />-Boşta kapatma.<br />-Sistem durumu izleme işlemi.<br />-İleti tabanlı etkinleştirme.<br />-HTTP, TCP, Adlandırılmış Kanallar ve MSMQ ile çalışır.|  
|IIS 7.0|-Çalıştıran bir WCF Hizmeti ile [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] içeriği.<br />-Çeşitli aktarım protokolünü kullanarak Internet üzerinde bir WCF hizmeti çalışıyor.|-Avantajları OLUŞTU.<br />-Tümleşik [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ve IIS içeriği.|  
  
 Bir barındırma ortamı seçimi üzerinde dağıtıldığı, Windows iletilerini ve işlem ve uygulama gerektiriyorsa, etki alanı geri dönüştürme türü gönderilmesini gerektiriyor taşımalar sürümüne bağlıdır. Aşağıdaki tabloda bu gereksinimleri için ilgili verileri özetler.  
  
|Barındırma ortamı|Platform kullanılabilirliği|Desteklenen aktarmalar|İşlem ve AppDomain geri dönüştürme|  
|-------------------------|---------------------------|--------------------------|-------------------------------------|  
|Yönetilen uygulamaların ("kendi kendini barındıran")|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> NET.MSMQ|Hayır|  
|Windows (önceki adıyla NT hizmeti olarak bilinir) Hizmetleri|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> NET.MSMQ|Hayır|  
|IIS 5.1|[!INCLUDE[wxp](../../../includes/wxp-md.md)]|HTTP|Evet|  
|[!INCLUDE[iis601](../../../includes/iis601-md.md)]|[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]|HTTP|Evet|  
|Windows İşlem Etkinleştirme Hizmeti (WAS)|[!INCLUDE[wv](../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> NET.MSMQ|Evet|  
  
 Bir hizmeti veya herhangi bir genişletme bir güvenilmeyen ana bilgisayar güvenlik ihlalleri güvenlikten çalıştıran dikkate almak önemlidir. Ayrıca, açarken unutmayın bir <xref:System.ServiceModel.ServiceHost> altında kimliğe bürünme, uygulamanın kullanıcı kapalı, örneğin önbelleğe alarak kaydedildiğini değil emin olmalısınız <xref:System.Security.Principal.WindowsIdentity> kullanıcının.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sistem Gereksinimleri](../../../docs/framework/wcf/wcf-system-requirements.md)  
 [Temel Programlama Yaşam Döngüsü](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Hizmet Anlaşmalarını Uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)  
 [Nasıl yapılır: IIS'de WCF Hizmeti Barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)  
 [Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
