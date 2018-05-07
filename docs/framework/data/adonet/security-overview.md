---
title: Güvenlik genel bakış 2
ms.date: 03/30/2017
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
ms.openlocfilehash: 4e8d1502096dc452d21158e4fb3684298be9b982
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="security-overview"></a>Güvenlik Genel Bakış
Bir uygulama güvenliğini sağlamaya devam eden bir işlemdir. Hiçbir zaman bir geliştirici gelecekteki saldırıları yeni teknolojileri tür ortaya çıkarır tahmin etmek mümkün olduğundan, bir uygulamanın tüm saldırılarına karşı güvenli olduğu garanti edebilir noktası olacaktır. Buna karşılık, yalnızca hiç kimse olduğundan henüz bulunan (veya yayımlanmış) güvenlik açıkları sistemindeki gelmez hiçbiri mevcut veya mevcut. Yanı sıra güvenlik için proje tasarım aşamasında planlama güvenlik uygulama ömrü boyunca nasıl sürdürüleceği planlamak gerekir.  
  
## <a name="design-for-security"></a>Güvenlik için Tasarım  
 Güvenli uygulamalar geliştirme konusunda en büyük sorun güvenlik genellikle bir sonradan akla, bir proje kodunu tamamlandıktan sonra uygulamak için bir şey olduğunu biridir. Bir uygulama güvenli kılan için çok az düşünce verilmiş olduğundan güvenliği bir uygulamaya outset adresindeki oluşturma değil güvenli olmayan uygulamalar için yol gösterir.  
  
 Son dakika güvenlik uygulaması olarak yazılım sonları yeni kısıtlamaları altında daha fazla hataları için müşteri adayları veya beklenmeyen işlevselliği uyum sağlayacak şekilde yazılması gerekir. Her yeniden düzenlenen kod satırı yeni bir hatanın Tanıtımı olasılığını içerir. Böylece yeni özellikler geliştirme ile art arda devam edebilirsiniz, bu nedenle, güvenlik geliştirme sürecinin başlarında düşünmelisiniz.  
  
### <a name="threat-modeling"></a>Tehdit modelleme  
 İçin sunulan tüm olası saldırılara karşı anlamadan sistem saldırılara karşı koruyamaz. Güvenlik tehditlerine karşı değerlendirme sürecini adlı *tehdit modelleme*, güvenlik ihlallerini ADO.NET uygulamanızda ayrımlar ve olasılığını belirlemek gereklidir.  
  
 Tehdit modelleme üç üst düzey adımdan oluşur: etkilemeyi'nın Görünüm anlama sistem güvenliğini characterizing ve tehditleri belirleme.  
  
 Tehdit modelleme en hassas verileri göstermek için çok tehlikeli olanlar bulmak için uygulamanızın güvenlik açıkları değerlendiriliyor yinelemeli bir yaklaşımdır. Güvenlik açıklarını belirleme sonra önem sırasına göre derecelendirmek ve tehditleri sayaç için önlemler öncelikli kümesi oluşturun.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Tehdit modelleme](http://go.microsoft.com/fwlink/?LinkId=98353) MSDN güvenlik Geliştirici Merkezi sitesinde|Bu sayfadaki kaynaklardan işlem modelleme tehdit anlamak ve kendi uygulamaların güvenliğini sağlamak için kullanabileceğiniz tehdit modelleri oluşturmanıza yardımcı olur|  
  
## <a name="the-principle-of-least-privilege"></a>En az ayrıcalık prensibi  
 Tasarlama, derleme ve uygulamanızı dağıtmak, uygulamanızın saldırıya olduğunu varsayalım gerekir. Genellikle bu saldırıların kodu çalıştıran kullanıcının izinleriyle yürüten kötü amaçlı kod gelmektedir. Başkalarının saldırgan tarafından kötü amaçlı iyi niyetli koduyla kaynaklanan. Güvenlik planlarken, her zaman en kötü durum senaryo ortaya çıkar varsayalım.  
  
 Uygulayabileceğiniz bir karşı ölçü ile en az ayrıcalık çalıştırarak mümkün olduğu kadar duvarları kodunuzu geçici erect denemektir. En az ayrıcalık prensibi verilen herhangi bir ayrıcalık kodu işin tamamlanması için gereken süreyi en kısa süre için gerekli en az miktarda verilmesi gerektiğini söyler.  
  
 Güvenli uygulamalar oluşturmak için en iyi hiçbir izinlerle hiç başlatın ve sonra gerçekleştirilen belirli bir görev için dar izinleri eklemek için bir uygulamadır. Bunun aksine, tüm izinleri ile başlayan ve tek tek olanları engelleme müşteri adayları test ve güvenlik açıklarını gerekli daha fazla izin istemeden verme var olabilir çünkü sağlamak zor güvenli olmayan uygulamaları için.  
  
 Uygulamalarınızın güvenliğini sağlama konusunda daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Uygulamalarının Güvenliğini Sağlama](/visualstudio/ide/securing-applications)|Genel güvenlik konulara bağlantılar içerir. Ayrıca dağıtılmış uygulamalar, Web uygulamaları, mobil uygulamalar ve Masaüstü uygulamaları güvenliğini sağlamaya yönelik konulara bağlantılar içerir.|  
  
## <a name="code-access-security-cas"></a>Kod Erişimi Güvenliği (CAS)  
 Kod erişim güvenliği (CAS), korunan kaynaklara ve işlemlere koduna sahip erişimi sınırlamak yardımcı olan bir mekanizmadır. .NET Framework'teki CA'lar aşağıdaki işlevleri gerçekleştirir:  
  
-   İzinler ve çeşitli sistem kaynaklarına erişim hakkı temsil izin kümeleri tanımlar.  
  
-   İzin kümeleri code (kod grupları) gruplarıyla ilişkilendirme tarafından güvenlik ilkesini yapılandırmak Yöneticiler sağlar.  
  
-   Olması yararlı olacaktır izinleri yanı sıra gerektirir çalıştırmak için izinleri istemek kod etkinleştirir ve kod hiçbir zaman olmalıdır hangi izinleri belirtir.  
  
-   Yüklendiğinde, her derleme için izinleri verir temel kod tarafından istenen izinleri ve güvenlik ilkesi tarafından izin verilen işlemler.  
  
-   İsteğe bağlı kendi arayanlar belirli izinlere sahip olduğunuzu kodu sağlar.  
  
-   Kod talep böylece korunan kod çağırmak yalnızca belirli bir kuruluş veya sitesinden arayanlara izin verme kendi arayanlar dijital bir imza sahip olmasını sağlar.  
  
-   Kod kısıtlamalar çalışma zamanında her çağıran arayanlar olmalıdır izinlerine çağrı yığınında verilen izinleri karşılaştırarak zorlar.  
  
 Saldırının başarılı olursa, ortaya zarar en aza indirmek için bir güvenlik bağlamı yalnızca kendi iş tamamlandı ve artık almak için gereken kaynakları erişim veren kodunuz için seçin.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Kod Erişimi Güvenliği ve ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)|Kod erişimi güvenliği, rol tabanlı güvenlik ve ADO.NET uygulamanın perspektifinden kısmen güvenilen ortamlar arasındaki etkileşimler açıklanmaktadır.|  
|[Kod erişimi güvenliği](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)|.NET Framework CA'LARDA açıklayan ek konulara bağlantılar içerir.|  
  
## <a name="database-security"></a>Veritabanı güvenliği  
 En az ayrıcalık prensibi veri kaynağınız için de geçerlidir. Veritabanı güvenliği için bazı genel yönergeleri içerir:  
  
-   En düşük olası ayrıcalıkları olan hesapları oluşturun.  
  
-   Kullanıcıların yalnızca kod çalışabilmesi için Yönetici hesaplarına erişim izin verme.  
  
-   Sunucu tarafı hata iletileri istemci uygulamalar döndürmeyin.  
  
-   Hem istemci hem de sunucunun tüm giriş doğrulayın.  
  
-   Parametreli Komutlar kullanın ve dinamik SQL deyimleri kaçının.  
  
-   Denetim ve böylece tüm güvenlik ihlallerini uyarılırsınız kullanmakta olduğunuz veritabanı için günlük güvenlik sağlar.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[SQL Server Güvenliği](../../../../docs/framework/data/adonet/sql/sql-server-security.md)|SQL Server'ı hedefleyen güvenli ADO.NET uygulamaları oluşturmak için kılavuzluk uygulama senaryoları ile SQL Server güvenlik genel bir bakış sağlar.|  
|[Veri erişim stratejileri için öneriler](http://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)|Verilere erişme ve veritabanı işlemleri için öneriler sağlar.|  
  
## <a name="security-policy-and-administration"></a>Güvenlik İlkesi ve yönetim  
 Yanlış kod erişim güvenliği (CAS) ilkesi yönetme, olası güvenlik zayıf oluşturabilirsiniz. Uygulama dağıtıldığında, güvenlik izleme teknikleri kullanılmalıdır ve yeni tehditleri değerlendirilen riskleri ortaya çıkan.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[NIB: Güvenlik İlkesi Yönetimi](http://msdn.microsoft.com/library/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9)|Oluşturma ve Güvenlik İlkesi'ni yönetme hakkında bilgi sağlar.|  
|[NIB: İlke en iyi güvenlik uygulamaları](http://msdn.microsoft.com/library/d49bc4d5-efb7-4caa-a2fe-e4d3cec63c05)|Güvenlik ilkesini yönetmek nasıl açıklayan bağlantılar sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Yerel Güvenlik ve .NET Framework kodu PAVE](http://msdn.microsoft.com/library/bd61be84-c143-409a-a75a-44253724f784)  
 [SQL Server Güvenliği](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
