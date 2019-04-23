---
title: COM+ Uygulamaları ile Tümleştirme Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: e481e48f-7096-40eb-9f20-7f0098412941
ms.openlocfilehash: b5294080d0cc76fdb98bc0908f4273dbb011f982
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328731"
---
# <a name="integrating-with-com-applications-overview"></a>COM+ Uygulamaları ile Tümleştirme Genel Bakış
Windows Communication Foundation (WCF) dağıtılmış uygulamalar oluşturmak için zengin bir ortam sağlar. COM +'da barındırılan bir bileşen tabanlı uygulama mantığı zaten kullanıyorsanız, WCF, yeniden yazmak zorunda kalmadan yerine mevcut mantığınızı genişletmek için de kullanabilirsiniz. Mevcut COM + veya Enterprise Hizmetleri iş mantığı Web Hizmetleri aracılığıyla kullanıma sunmak istediğiniz, ortak bir senaryodur.  
  
 Bir arabirim bir COM + bileşeni üzerinde bir Web hizmeti olarak sunulduğunda belirtimi ve bu hizmetlerin sözleşmesi uygulama başlatma zamanında gerçekleştirilir otomatik bir eşlemesi tarafından belirlenir. Aşağıdaki liste, bu eşleme için kavramsal model gösterir:  
  
-   Bir hizmetin her kullanıma sunulan bir COM sınıfı için tanımlanır.  
  
-   Hizmet sözleşmesini doğrudan yapılandırmasında tanımlı yöntemi dışlama olasılığını ile seçilen bileşenin arabirim tanımı türetilir.  
  
-   Bu sözleşme işlemlerinde doğrudan bileşenin arabirim tanımı yöntemlerde türetilmiştir.  
  
-   Bu işlemler için parametreleri doğrudan bileşenin yöntemi parametrelerine karşılık gelen COM birlikte çalışabilirlik türden türetilir.  
  
 Varsayılan adresleri ve aktarım bağlama hizmeti, bir hizmet yapılandırma dosyasında sağlanır, ancak bunlar olarak yapılandırılabilen için gereklidir.  
  
> [!NOTE]
>  COM arabirimleri ve yapılandırma değişmediği sürece sözleşmeler sunulan Web Hizmetleri için de sabit kalır. Birkaç arabirimi için bir değişiklik, kullanılabilir hizmetlerin otomatik olarak güncelleştirmez ve COM + hizmet modeli Yapılandırma Aracı (ComSvcConfig.exe) yeniden çalıştırmayı gerektirir.  
  
 COM + uygulama ve bileşenlerinin kimlik doğrulaması ve yetkilendirme gereksinimlerine bir Web hizmeti olarak kullanıldığında zorlanmaya devam edin.  
  
 Çağıran bir Web hizmeti işlemi başlatırsa, işlem tabanlı olarak işaretlenmiş bileşenleri bu işlem kapsamında kaydettirin.  
  
 Aşağıdaki adımlar, bir COM + bileşenin arabirimi bileşen değiştirmeden, bir Web hizmeti olarak kullanıma sunmak için gereklidir:  
  
1. COM + bileşenin arabirimi bir Web hizmeti olarak kullanıma sunulabilecek olup olmadığını belirler.  
  
2. Uygun bir barındırma modunu seçin.  
  
3. COM + hizmet modeli Yapılandırma Aracı (ComSvcConfig.exe) arabirimi için bir Web hizmeti eklemek için kullanın. ComSvcConfig.exe kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: COM + hizmet modeli yapılandırma aracı kullanın](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
4. Uygulama yapılandırma dosyasında herhangi bir ek hizmet ayarı yapılandırın. Bir bileşen yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: COM + hizmet ayarlarını yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md).  
  
## <a name="supported-interfaces"></a>Desteklenen arabirimi  
 Bir Web hizmeti olarak kullanıma sunulabilir arabirimleri türüyle ilgili bazı kısıtlamalar vardır. Aşağıdaki türde arabirimler desteklenmez:  
  
-   Nesne başvuruları - parametreler olarak geçen arabirimleri aşağıdaki sınırlı nesne başvuru yaklaşımı sınırlı nesne başvurusu desteği bölümünde açıklanan.  
  
-   Geçiş türleri arabirimleri ile uyumlu olmayan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] COM birlikte çalışabilirlik dönüştürme.  
  
-   Uygulama havuzu oluşturma COM + tarafından barındırıldığında özelliği etkin olan uygulamalar için arabirim.  
  
-   Uygulamaya özel olarak işaretlenmiş bileşenlerin arabirimleri.  
  
-   COM + altyapı arabirimleri.  
  
-   Sistem uygulaması arabirimleri.  
  
-   Genel derleme önbelleğine eklenmemiş olan Enterprise Hizmetleri bileşenlerin arabirimleri.  
  
### <a name="limited-object-reference-support"></a>Sınırlı nesne başvurusu desteği  
 Bir dizi Dağıtılmış COM + bileşenleri nesneleri tarafından başvuru parametreleri, ADO kayıt kümesini nesneyi döndürme gibi kullandığından COM + tümleştirme nesne başvuru parametreleri için sınırlı destek içerir. Uygulayan nesneler için destek sınırlıdır `IPersistStream` COM arabirimi. Bu ADO kayıt kümesini nesneleri içerir ve uygulama özel COM nesneleri için uygulanabilir.  
  
 Bu desteğini etkinleştirmek için ComSvcConfig.exe araç sağlar. **allowreferences** normal yöntem imzası parametresi devre dışı bırakır ve nesne başvuru parametreleri kullanılmayan emin olmak için aracın çalıştığı denetler anahtarı . Ayrıca, parametre olarak geçirmeniz nesne türlerini gerekir adlandırılacağını ve içinde tanımlanan <`persistableTypes`> alt yapılandırma öğesi <`comContract`> öğesi.  
  
 Bu özellik kullanıldığında, COM + tümleştirme hizmet kullanan `IPersistStream` serileştirmek veya seri durumdan nesne örneği için arabirim. Nesne örneği desteklemiyorsa `IPersistStream`, bir özel durum oluşturulur.  
  
 Bir istemci uygulamasından yöntemlerde <xref:System.ServiceModel.ComIntegration.PersistStreamTypeWrapper> nesnesi, bir nesneyi bir hizmete geçirebilir ve benzer şekilde bir nesne almak için kullanılabilir.  
  
> [!NOTE]
>  Serileştirme yaklaşımın özel ve platforma özgü yapısı nedeniyle, bu WCF istemcileri ve WCF hizmetleri arasında kullanım için idealdir.  
  
## <a name="selecting-the-hosting-mode"></a>Barındırma modu seçme  
 COM + Web hizmetlerini barındırma şu modlardan birinde kullanıma sunar:  
  
-   COM +-barındırılan  
  
     Web hizmeti, uygulamanın adanmış COM + sunucusu işlem içinde (Dllhost.exe) barındırılır. Bu modda uygulama Web hizmeti istekleri almak için önce açıkça başlatılması gerekir. COM + Seçenekleri "Çalıştırma olarak bir NT hizmeti" veya "boştayken bırakabilirsiniz" uygulama ve hizmetlerinin boşta kapatma önlemek için kullanılabilir. Bu mod, hem Web hizmeti hem de sunucu uygulaması için DCOM erişim sağlar.  
  
-   Web barındırılan  
  
     Web hizmeti Web sunucusu çalışan işlemi içinde barındırılır. Bu mod, ilk istek alındığında etkin olmasını COM + gerektirmez. Bu istek alındığında uygulamanın etkin değilse, istek işleme önce otomatik olarak etkinleştirilir. Bu mod ayrıca hem Web hizmeti hem de sunucu uygulaması için DCOM erişim sağlar, ancak Web hizmeti istekleri için bir işlem atlama neden olur. Bu genellikle, kimliğe bürünme özelliğini etkinleştirmek istemci gerektirir. WCF'de, bu ile yapılabilir <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği <xref:System.ServiceModel.Security.WindowsClientCredential> özelliği genel olarak erişilebilen sınıfı <xref:System.ServiceModel.ChannelFactory%601> sınıfı, hem de <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> numaralandırma değeri.  
  
-   Web barındırılan işlem içi  
  
     Web hizmeti ve COM + uygulama mantığı Web sunucusu çalışan işlemi içinde barındırılır. Bu, Web hizmeti istekleri için bir işlem atlama neden olmadan Web barındırılan modunun Otomatik etkinleştirme sağlar. Olumsuz yönüyse, sunucu uygulaması DCOM üzerinden erişilemez ' dir.  
  
### <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Diğer WCF hizmetlerinde olduğu gibi kullanıma sunulan hizmet için güvenlik ayarlarını yapılandırma ayarları için WCF kanalı üzerinden yönetilir. DCOM makineye özel izin ayarları gibi geleneksel DCOM güvenlik ayarlarını zorlanmaz. COM + uygulama rolleri zorlamak için "bileşen düzeyinde erişim denetimleri" yetkilendirme bileşen için etkinleştirilmesi gerekir.  
  
 Güvenli olmayan bir bağlama kullanımını iletişim değiştirilmesine veya bilgileri açığa açık bırakabilirsiniz. Bunu önlemek için güvenli bir bağlama kullanmanız önerilir.  
  
 COM +-barındırılan ve Web barındırılan modda istemci uygulamaları gerekir izin istemci kullanıcının kimliğine bürünmek için sunucu işlemi. WCF istemcileri bu yapılabilir kimliğe bürünme düzeyini ayarlayarak <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.  
  
 Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) HTTP aktarımı kullanarak ile Httpcfg.exe araç, aktarım uç nokta adresi ayırmak için kullanılabilir. Diğer yapılandırmalar hedeflenen hizmet olarak davranan dolandırıcı Hizmetleri karşı korumak önemlidir. Bir rogue hizmet istenen uç noktada başlatılmasını önlemek için yasal hizmeti bir NT hizmeti olarak çalıştırmak için yapılandırılabilir. Bu uç nokta adresi yanlış hizmetlerin önce talep etmek üzere yasal hizmet sağlar.  
  
 Bir COM + uygulaması ile yapılandırılan COM + rolleri Web barındırılan bir hizmet olarak kullanıma sunma, uygulamanın rollerden biri için "Launch IIS işlem hesabı" eklenmelidir. Bu hesap, genellikle kullandıktan sonra temiz kapatma nesnelerin etkinleştirmek için adıyla IWAM_machinename eklenmelidir. Hesabın herhangi bir ek izin verilmemelidir.  
  
 COM + işlem özellikleri geri dönüştürme tümleşik uygulamaları kullanılamaz. Uygulamanın işlem geri dönüştürme kullanmak üzere yapılandırılmış ve bileşenlerin bir COM + barındırılan işlemde çalıştığından, hizmeti başlatılamıyor. Bu gereksinim, işlem geri dönüştürme ayarları uygulanmamış olduğundan Web barındırılan işlem modu kullanarak Hizmetleri içermez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM Uygulamaları ile Tümleştirme Genel Bakış](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
