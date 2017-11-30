---
title: "Barındırma Hizmetleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
caps.latest.revision: "31"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0d3cd2f53b81ae6114baa3c7eedd899126ed579
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="hosting-services"></a>Barındırma Hizmetleri
Etkin hale gelmesi bir hizmet oluşturduğu ve yaşam süresi ve bağlam denetleyen bir çalışma zamanı ortamında barındırılması gerekir. [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]Hizmetleri destekleyen yönetilen kodu herhangi bir Windows işlemin çalışmak üzere tasarlanmıştır.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Hizmet odaklı uygulamalar oluşturmak için birleşik bir programlama modeli sağlar. Bu programlama modeli, tutarlı kalır ve hizmetin dağıtıldığı çalışma zamanı ortamını bağımsızdır. Uygulamada, bu kod hizmetleriniz için aynı ne olursa olsun barındırma seçeneği benzer olduğunu anlamına gelir.  
  
 Bunlar gibi bir Windows hizmeti çalışan bir çalışan işlemi içinde Internet Information Services (IIS) tarafından ya da Windows İşlem Etkinleştirme Hizmeti (WAS) tarafından yönetilen çalışmasını sunucu ortamları için bir konsol uygulaması içinde seçenekleri aralığı barındırma. Geliştiriciler hizmetin dağıtım gereksinimlerini karşılayan barındırma ortamı seçin. Bu gereksinimleri hangi uygulamanın dağıtıldığını, platform üzerinde onu gerekir iletileri almasına ve göndermesine, taşıma veya işlem geri dönüştürme ve yeterli kullanılabilirliğini sağlamak için gereken diğer işlem yönetimi türüne veya bazı türetilen diğer yönetim veya Güvenilirlik gereksinimleri. Sonraki bölümde, seçenekleri barındırma hakkında bilgi ve yönergeler sağlar.  
  
## <a name="hosting-options"></a>Barındırma seçenekleri  
  
#### <a name="self-hosting-in-a-managed-application"></a>Kendi kendine yönetilen bir uygulamada barındırma  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Hizmetleri yönetilen bir uygulamada barındırılabilir. Dağıtmak için en az altyapısı gerektiğinden bu en esnek bir seçenektir. Yönetilen uygulama kod içinde hizmet için kod ekleme ve oluşturma ve bir örneği açın <xref:System.ServiceModel.ServiceHost> servisi kullanılabilir duruma getirmek için. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Nasıl yapılır: yönetilen bir uygulamada bir WCF Hizmeti barındırma](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Bu seçenek iki yaygın senaryolara olanak sağlar: [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] konsol uygulamaları ve olanlar gibi zengin istemci uygulamaları içinde çalışan hizmetler temel alarak [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] ya da Windows Forms (WinForms). Barındırma bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti bir konsol uygulaması içinde yararlıdır genellikle uygulamanın geliştirme aşamasında. Bu onları kolay hata ayıklamak, uygulama içinde neler olduğunu çıkışı bulmak için izleme bilgilerini almak kolay ve yeni konumlara kopyalayarak hareket etmek kolay hale getirir. Barındırma bu seçenek ayrıca zengin istemci uygulamaları gibi kolaylaştırır [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] ve dış dünyayla iletişim kurmak için WinForms uygulamalar. Örneğin, kullanan eşler arası işbirliği istemci [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] kendi kullanıcı arabirimi ve ayrıca ana bilgisayarlar için bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bağlanmak ve bilgi paylaşmak diğer istemciler sağlayan hizmet.  
  
#### <a name="managed-windows-services"></a>Yönetilen Windows Hizmetleri  
 Bu barındırma seçeneği barındıran uygulama etki alanı (AppDomain) kaydetme oluşan bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet (önceki adıyla NT hizmeti olarak da bilinir) yönetilen bir Windows hizmeti olarak böylece hizmeti işlem ömrü hizmet denetimi yöneticisi tarafından denetlenir (SCM) Windows Hizmetleri için. Kendi kendine barındırma seçeneği gibi bazı barındırma kodu uygulamanın bir parçası yazılmıştır bu tür barındırma ortamı gerektirir. Hizmet ve hem de bir Windows hizmeti olarak uygulanır bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] devralınmalıdır kendisine neden tarafından hizmet <xref:System.ServiceProcess.ServiceBase> de sınıfı olarak gelen bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet sözleşme arabirimi. <xref:System.ServiceModel.ServiceHost> Sonra oluşturulan ve bir geçersiz kılınan içinde açılan <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> yöntemi ve bir geçersiz kılınan içinde kapalı <xref:System.ServiceProcess.ServiceBase.OnStop> yöntemi. Öğesinden devralınan bir yükleyici sınıfı <xref:System.Configuration.Install.Installer> Installutil.exe aracı tarafından bir Windows hizmeti olarak yüklenecek program izin vermek için de uygulanmalıdır. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Nasıl yapılır: yönetilen bir Windows hizmetinde bir WCF Hizmeti barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md). Uzun süre çalışan bir yönetilen seçeneği barındıran Windows hizmeti tarafından etkin senaryo olan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] message-etkinleştirilmediğini güvenli bir ortamda IIS dışında barındırılan hizmeti. Hizmet ömrü, bunun yerine işletim sistemi tarafından denetlenir. Barındırma bu seçenek, tüm Windows sürümlerinde kullanılabilir.  
  
#### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)  
 Barındırma seçeneği IIS ile tümleşiktir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ve bu teknolojiler sunar, işlem geri dönüştürme, boşta kapatma, sistem durumu izleme işlemi ve ileti tabanlı etkinleştirme gibi özellikleri kullanır. Üzerinde [!INCLUDE[wxp](../../../includes/wxp-md.md)] ve [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] işletim sistemleri, bu olduğu yüksek oranda kullanılabilir ve ölçeklendirilebilir olmalıdır Web hizmeti uygulamalarını barındırmak için tercih edilen bir çözüm. IIS, aynı zamanda müşterilerin bir kurumsal sınıf server ürün beklediğiniz tümleşik yönetilebilirlik sağlar. Bu barındırma seçeneği IIS düzgün şekilde yapılandırılmasını gerektirir, ancak herhangi bir barındırma kod uygulamanın bir parçası yazılması gerektirmez. [!INCLUDE[crabout](../../../includes/crabout-md.md)]IIS için barındırma nasıl yapılandırıldığı bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet için bkz: [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
 IIS barındırılan hizmetleri yalnızca HTTP taşıma kullanabilirsiniz. IIS 5.1 kendi uygulamasında bazı sınırlamalar anlatılmıştır [!INCLUDE[wxp](../../../includes/wxp-md.md)]. İleti tabanlı etkinleştirme için sağlanan bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet tarafından IIS 5.1 [!INCLUDE[wxp](../../../includes/wxp-md.md)] herhangi diğer kendi kendini barındıran engeller [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] iletişim kurmak için 80 numaralı bağlantı noktasını kullanarak aynı bilgisayarda hizmet. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Hizmetleri aynı AppDomain/uygulama havuzu/çalışan işlem tarafından barındırılan diğer uygulamaları olarak çalıştırabilirsiniz [!INCLUDE[iis601](../../../includes/iis601-md.md)] üzerinde [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Ancak çünkü [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ve [!INCLUDE[iis601](../../../includes/iis601-md.md)] hem de çekirdek modu HTTP yığınını (HTTP.sys) kullanmak [!INCLUDE[iis601](../../../includes/iis601-md.md)] 80 numaralı bağlantı noktasını otomatik olarak barındırılan diğer paylaşabilirsiniz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] IIS 5.1 aksine aynı makine üzerinde çalışan hizmetleri.  
  
#### <a name="windows-process-activation-service-was"></a>Windows İşlem Etkinleştirme Hizmeti (WAS)  
 Windows İşlem Etkinleştirme Hizmeti (WAS) mekanizmasıdır yeni işlem etkinleştirme için [!INCLUDE[lserver](../../../includes/lserver-md.md)] olan de kullanılabilir [!INCLUDE[wv](../../../includes/wv-md.md)]. Bilinen korur [!INCLUDE[iis601](../../../includes/iis601-md.md)] işlem modelini (uygulama havuzları ve işlem ileti tabanlı etkinleştirme) ve barındırma özellikleri (örneğin, hızlı hata koruması, sistem durumu izleme ve geri dönüşüm), ancak bunu etkinleştirmeden HTTP üzerindeki bağımlılığı kaldırır Mimari. [!INCLUDE[iisver](../../../includes/iisver-md.md)]HTTP üzerinden ileti tabanlı etkinleştirme gerçekleştirmek için WAS kullanır. Ek [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bileşenleri de bağlama noktasına sahip diğer üzerinden ileti tabanlı etkinleştirme protokolleri sağlamak için WAS [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] , TCP, MSMQ ve adlandırılmış kanallar gibi destekler. Bu işlem geri dönüştürme gibi IIS özelliklerini hızlı kullanmaya iletişim protokolleri kullanan uygulamaları koruma ve yalnızca HTTP tabanlı uygulamalar için de kullanılabilir ortak yapılandırma sistemi başarısız sağlar.  
  
 Bu barındırma seçeneği gerektirir, olması düzgün şekilde yapılandırıldığından, ancak, uygulamanın bir parçası barındırma kod yazmaya gerektirmez. [!INCLUDE[crabout](../../../includes/crabout-md.md)]nasıl yapılandırılacağı barındırma için bkz: [nasıl yapılır: bir WCF Hizmeti barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="choosing-a-hosting-environment"></a>Bir barındırma ortamı seçme  
 Aşağıdaki tabloda bazı avantajları ve her barındırma seçenekleri ile ilgili senaryolar özetlenmiştir.  
  
|Barındırma ortamı|Yaygın senaryolar|Avantajları ve sınırlamaları|  
|-------------------------|----------------------|----------------------------------|  
|Yönetilen uygulama ("kendi kendini barındıran")|-Konsol uygulamaları geliştirme sırasında kullanılır.<br />-Zengin WinForm ve [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] istemci uygulamaları hizmetlerine erişme.|-Esnek.<br />-Kolay dağıtın.<br />-Olmayan bir kuruluş çözümü Hizmetleri için.|  
|Windows (önceki adıyla NT hizmeti olarak bilinir) Hizmetleri|-a uzun süre çalışan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] IIS dışında barındırılan hizmet.|-Hizmet işlemi ömrü ileti etkinleştirilmedi işletim sistemi tarafından denetlenen.<br />-Tüm Windows sürümlerinde desteklenir.<br />-Güvenli bir ortam.|  
|IIS 5.1,[!INCLUDE[iis601](../../../includes/iis601-md.md)]|-Çalışan bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet yana birimi ile [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Internet'te HTTP protokolünü kullanan içerik.|-İşlem geri dönüştürme.<br />-Boşta kapatma.<br />-Sistem durumu izleme işlemi.<br />-İleti tabanlı etkinleştirme.<br />-Yalnızca HTTP.|  
|Windows İşlem Etkinleştirme Hizmeti (WAS)|-Çalışan bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] çeşitli aktarım protokolünü kullanarak Internet'te IIS yüklemeden hizmet.|-IIS gerekli değildir.<br />-İşlem geri dönüştürme.<br />-Boşta kapatma.<br />-Sistem durumu izleme işlemi.<br />-İleti tabanlı etkinleştirme.<br />-HTTP, TCP, Adlandırılmış Kanallar ve MSMQ ile çalışır.|  
|IIS 7.0|-Çalışan bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti ile [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] içeriği.<br />-Çalışan bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Internet'te çeşitli aktarım protokolünü kullanan hizmet.|-Avantajları OLUŞTU.<br />-Tümleşik [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ve IIS içeriği.|  
  
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
 [Temel programlama yaşam döngüsü](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)  
 [Nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [Nasıl yapılır: bir WCF Hizmeti barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)  
 [Nasıl yapılır: yönetilen bir Windows hizmetinde bir WCF Hizmeti barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Nasıl yapılır: yönetilen bir uygulamada bir WCF Hizmeti barındırma](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
