---
title: COM+ Uygulamaları ile Tümleştirme Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: e481e48f-7096-40eb-9f20-7f0098412941
ms.openlocfilehash: 57a1537e1bde1efcd3586d032efee063561efcca
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586500"
---
# <a name="integrating-with-com-applications-overview"></a>COM+ Uygulamaları ile Tümleştirme Genel Bakış
Windows Communication Foundation (WCF) dağıtılmış uygulamalar oluşturmak için zengin bir ortam sağlar. Zaten COM+ içinde barındırılan bileşen tabanlı uygulama mantığını kullanıyorsanız, WCF kullanarak mevcut mantığınızı yeniden yazmak yerine genişletebilirsiniz. Yaygın bir senaryo, Web Hizmetleri aracılığıyla mevcut COM+ veya kurumsal hizmetler iş mantığını göstermek istediğinizde olur.  
  
 Bir COM+ bileşenindeki bir arabirim bir Web hizmeti olarak sunulduğunda, bu hizmetlerin belirtimi ve anlaşması, uygulama başlatma zamanında gerçekleştirilen bir otomatik eşleme tarafından belirlenir. Aşağıdaki listede, bu eşleme için kavramsal model gösterilmektedir:  
  
- Sunulan her bir COM sınıfı için bir hizmet tanımlanmıştır.  
  
- Hizmet sözleşmesi, yapılandırma içinde tanımlanan yöntem dışlama olasılığa sahip seçili bileşenin arabirim tanımından doğrudan türetilir.  
  
- Bu sözleşmede bulunan işlemler, doğrudan bileşenin arabirim tanımındaki metotlardan türetilir.  
  
- Bu işlemlere yönelik parametreler, doğrudan bileşen yöntemi parametrelerine karşılık gelen COM birlikte çalışabilirlik türünden türetilir.  
  
 Hizmet için varsayılan adresler ve aktarım bağlamaları bir hizmet yapılandırma dosyasında sağlanır, ancak bunlar gerektiği şekilde yeniden yapılandırılabilir.  
  
> [!NOTE]
> COM+ arabirimleri ve yapılandırması değişmeden kaldığı sürece, sunulan Web Hizmetleri sözleşmeleri sabit kalır. Birkaç arabirimde değişiklik, kullanılabilir hizmetleri otomatik olarak güncelleştirmez ve COM+ hizmet modeli yapılandırma aracı (ComSvcConfig. exe) için yeniden çalışıyor olmalıdır.  
  
 COM+ uygulamasının ve bileşenlerinin kimlik doğrulama ve yetkilendirme gereksinimleri, bir Web hizmeti olarak kullanıldığında zorlanmaya devam eder.  
  
 Çağıran bir Web hizmeti işlemi başlatırsa, bileşen bu işlem kapsamı içinde işlem listeleme olarak işaretlenir.  
  
 Bileşeni değiştirmeden bir COM+ bileşeninin arabirimini Web hizmeti olarak göstermek için aşağıdaki adımlar gereklidir:  
  
1. COM+ bileşeni arabiriminin bir Web hizmeti olarak sunulup sunulamayacağını belirleme.  
  
2. Uygun bir barındırma modu seçin.  
  
3. Arabirim için bir Web hizmeti eklemek için COM+ hizmet modeli yapılandırma aracı 'nı (ComSvcConfig. exe) kullanın. ComSvcConfig. exe ' nin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: com+ hizmet modeli yapılandırma aracını kullanma](how-to-use-the-com-service-model-configuration-tool.md).  
  
4. Uygulama yapılandırma dosyasında diğer hizmet ayarlarını yapılandırın. Bir bileşeni yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: com+ hizmet ayarlarını yapılandırma](how-to-configure-com-service-settings.md).  
  
## <a name="supported-interfaces"></a>Desteklenen arabirimler  
 Bir Web hizmeti olarak açığa çıkarılabilen arabirimlerin türü üzerinde bazı kısıtlamalar vardır. Aşağıdaki arabirim türleri desteklenmez:  
  
- Nesne başvurularını parametre olarak geçiren arabirimler-aşağıdaki sınırlı nesne başvuru yaklaşımı, sınırlı nesne başvurusu desteği bölümünde açıklanmıştır.  
  
- .NET Framework COM birlikte çalışabilirlik dönüşümleriyle uyumlu olmayan türleri geçiren arabirimler.  
  
- COM+ tarafından barındırıldığı zaman uygulama havuzu etkin olan uygulamalar için arabirimler.  
  
- Uygulamaya özel olarak işaretlenen bileşenlerin arabirimleri.  
  
- COM+ altyapı arabirimleri.  
  
- Sistem uygulamasından arabirimler.  
  
- Genel bütünleştirilmiş kod önbelleğine eklenmemiş kurumsal hizmetler bileşenlerinden arabirimler.  
  
### <a name="limited-object-reference-support"></a>Sınırlı nesne başvurusu desteği  
 Dağıtılan bir dizi COM+ bileşeni, bir ADO kayıt kümesi nesnesi döndüren nesneleri başvuru parametrelerine göre kullandığından, COM+ tümleştirmesi nesne başvuru parametreleri için sınırlı destek içerir. Destek, com arabirimini uygulayan nesnelerle sınırlıdır `IPersistStream` . Bu, ADO kayıt kümesi nesnelerini içerir ve uygulamaya özgü COM nesneleri için uygulanabilir.  
  
 Bu desteği etkinleştirmek için ComSvcConfig. exe aracı, normal yöntem imza parametresini devre dışı bırakan **allowreferences** anahtarını sağlar ve nesnenin başvuru parametrelerinin kullanılmadığından emin olmak için aracın çalıştığını denetler. Ayrıca, parametre olarak geçirdiğiniz nesne türleri, `persistableTypes` <> öğesinin bir alt öğesi olan <> yapılandırma öğesinde adlandırılmalıdır ve tanımlanmalıdır `comContract` .  
  
 Bu özellik kullanıldığında, COM+ tümleştirme hizmeti, `IPersistStream` nesne örneğini seri hale getirmek veya seri durumdan çıkarmak için arabirimini kullanır. Nesne örneği desteklemiyorsa `IPersistStream` , bir özel durum oluşturulur.  
  
 Bir istemci uygulaması içinde, nesnesindeki Yöntemler <xref:System.ServiceModel.ComIntegration.PersistStreamTypeWrapper> bir hizmete bir nesneyi iletmek için ve benzer şekilde bir nesne almak için kullanılabilir.  
  
> [!NOTE]
> Serileştirme yaklaşımının özel ve platforma özgü doğası nedeniyle bu, WCF istemcileri ve WCF hizmetleri arasında kullanılması için idealdir.  
  
## <a name="selecting-the-hosting-mode"></a>Barındırma modunu seçme  
 COM+, Web hizmetlerini aşağıdaki barındırma modlarından birinde kullanıma sunar:  
  
- COM+-barındırılan  
  
     Web hizmeti, uygulamanın adanmış COM+ sunucu işlemi (Dllhost. exe) içinde barındırılır. Bu mod, Web hizmeti isteklerini almadan önce uygulamanın açıkça başlatılmasını gerektirir. Uygulamanın ve hizmetlerinin boş kapatılmasını engellemek için "NT hizmeti olarak çalıştır" veya "boşta olduğunda çalışmayı bırak" COM+ seçenekleri kullanılabilir. Bu mod, sunucu uygulamasına hem Web hizmeti hem de DCOM erişimi sağlar.  
  
- Web 'de barındırılan  
  
     Web hizmeti bir Web sunucusu çalışan işlemi içinde barındırılır. Bu mod, ilk istek alındığında COM+ ' ın etkin olmasını gerektirmez. Bu istek alındığında uygulama etkin değilse, istek işlenmeden önce otomatik olarak etkinleştirilir. Bu mod ayrıca sunucu uygulamasına hem Web hizmeti hem de DCOM erişimi sağlar, ancak Web hizmeti istekleri için bir işlem atlamaya neden olur. Bu, genellikle istemcinin kimliğe bürünme özelliğini etkinleştirmesini gerektirir. WCF 'de, bu, <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> <xref:System.ServiceModel.Security.WindowsClientCredential> genel sınıfın bir özelliği <xref:System.ServiceModel.ChannelFactory%601> ve numaralandırma değeri olarak erişilen sınıfının özelliği ile yapılabilir <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> .  
  
- Web 'de barındırılan işleme  
  
     Web hizmeti ve COM+ uygulama mantığı, Web sunucusu çalışan işlemi içinde barındırılır. Bu, Web hizmeti istekleri için bir işlem atlamaya neden olmadan Web 'de barındırılan modunun otomatik olarak etkinleştirilmesini sağlar. Dezavantajı, sunucu uygulamasına DCOM üzerinden erişilemeyeceğini unutmayın.  
  
### <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler  
 Diğer WCF Hizmetleri gibi, gösterilen hizmetin güvenlik ayarları WCF kanalının yapılandırma ayarları aracılığıyla yönetilir. DCOM makine genelinde izin ayarları gibi geleneksel DCOM güvenlik ayarları zorlanmaz. COM+ uygulama rollerini zorlamak için, bileşen için "bileşen düzeyinde erişim denetimleri" yetkilendirmesi etkinleştirilmelidir.  
  
 Güvenli olmayan bir bağlamanın kullanımı, izinsiz veya bilgilerin açığa çıkması için iletişimin açık kalmasına neden olabilir. Bunu engellemek için güvenli bağlama kullanmanız önerilir.  
  
 COM+ barındırılan ve Web 'de barındırılan modlar için, istemci uygulamaların istemci kullanıcının kimliğine bürünmesi için sunucu işlemine izin vermesi gerekir. Bu işlem, kimliğe bürünme düzeyi olarak ayarlanarak WCF istemcilerinde yapılabilir <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> .  
  
 HTTP aktarımını kullanan Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti (WAS) ile, bir taşıma uç noktası adresini ayırmak için Httpcfg. exe aracı kullanılabilir. Diğer yapılandırmalarda, amaçlanan hizmet olarak davranan standart dışı hizmetlere karşı korunması önemlidir. Standart dışı bir hizmetin istenen uç noktada başlamasını engellemek için, meşru hizmet bir NT hizmeti olarak çalışacak şekilde yapılandırılabilir. Bu, meşru bir hizmetin, herhangi bir standart dışı hizmetlerden önce Endpoint adresini talep etmesini sağlar.  
  
 Yapılandırılmış COM+ rolleriyle bir COM+ uygulamasını Web 'de barındırılan bir hizmet olarak kullanıma sunana zaman, uygulamanın rollerinin birine "IIS Işlem hesabı 'nı Başlat" eklenmelidir. Bu hesap genellikle IWAM_machinename adıyla birlikte, nesnelerin temiz kapatılmasını etkinleştirmek için eklenmelidir. Hesaba herhangi bir ek izin verilmemelidir.  
  
 COM+ işlem geri dönüştürme özellikleri tümleşik uygulamalarda kullanılamaz. Uygulama, işlem geri dönüşümünü kullanacak şekilde yapılandırıldıysa ve bileşenler COM+ barındırılan bir işlemde çalışıyorsa, hizmet başlatılamaz. Bu gereksinim, işlem geri dönüştürme ayarları uygulanmadığından, Web 'de barındırılan işlem içi modu kullanılarak hizmetler içermez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM Uygulamaları ile Tümleştirme Genel Bakış](integrating-with-com-applications-overview.md)
