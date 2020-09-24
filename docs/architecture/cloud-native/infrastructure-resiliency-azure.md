---
title: Azure platformu dayanıklılığı
description: Azure için Cloud Native .NET uygulamaları tasarlama | Azure ile bulut altyapısı dayanıklılığı
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 88634bc60df15cc93b1769a85879795ae383757a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163771"
---
# <a name="azure-platform-resiliency"></a>Azure platformu dayanıklılığı

Bulutta güvenilir bir uygulama oluşturmak, geleneksel şirket içi uygulama geliştirmeden farklıdır. Tarihsel olarak, ölçeğini ölçekleyerek bir bulut ortamında ölçeklendirmek için daha yüksek kaliteli donanımlar satın aldınız. Bu, hatalardan kaçınmak yerine, etkilerini en aza indirmek ve sistemi kararlı tutmaktır.

Bununla birlikte, güvenilir bulut uygulamaları farklı özellikleri görüntüler:

- Bunlar esnektir, sorunsuz bir şekilde kurtarılır ve çalışmaya devam eder.
- Bunlar yüksek oranda kullanılabilir (HA) ve önemli bir kesinti olmadan sağlıklı bir durumda tasarlanan şekilde çalışır.

Bu özelliklerin birlikte nasıl çalıştığını ve güvenilir bir bulutta yerel uygulama oluşturmak için maliyeti nasıl etkileyeceğini anlama. Azure bulutundaki özelliklerden yararlanarak, bulutta yerel uygulamalarınız için dayanıklılık ve kullanılabilirlik oluşturabileceğiniz yöntemlere bakacağız.

## <a name="design-with-resiliency"></a>Dayanıklılık ile tasarım

Dayanıklılık, uygulamanızın hataya tepki vermesini ve hala işlevsel kalmasını sağlar. [Azure 'Da esnekliği](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)teknik Incelemesi, Azure platformunda esnekliği 'e ulaşmak için rehberlik sağlar. Aşağıda bazı önemli öneriler verilmiştir:

- *Donanım hatası.* Farklı hata etki alanlarına bileşen dağıtarak uygulama üzerinde artıklık oluşturun. Örneğin, Azure VM 'lerinin kullanılabilirlik kümeleri kullanılarak farklı raflara yerleştirildiğinden emin olun.

- *Veri merkezi hatası.* Veri merkezlerinde hata yalıtımı alanları ile uygulama üzerinde artıklık oluşturun. Örneğin, Azure VM 'lerinin Azure Kullanılabilirlik Alanları kullanılarak farklı hata yalıtılmış veri merkezlerine yerleştirildiğinden emin olun.

- *Bölgesel hata.* Uygulamaların hızlı bir şekilde kurtarılmasını sağlamak için verileri ve bileşenleri başka bir bölgeye çoğaltın. Örneğin, Azure VM 'lerini başka bir Azure bölgesine çoğaltmak için Azure Site Recovery kullanın.

- *Ağır yük.* Kullanımdaki artışları işlemek için örneklerin genelinde yük dengelemesi yapın. Örneğin, trafiği tüm VM 'lere dağıtmak için bir yük dengeleyicinin arkasına iki veya daha fazla Azure VM yerleştirin.

- *Yanlışlıkla veri silme veya bozulma.* Veriler, herhangi bir silme veya bozulma durumunda geri yüklenebilmeleri için yedeklenir. Örneğin, Azure VM 'lerinizi düzenli olarak yedeklemek için Azure Backup kullanın.

## <a name="design-with-redundancy"></a>Yedeklilik ile tasarım

Sorunlar, etki kapsamında farklılık gösterir. Hatalı disk gibi bir donanım arızası, kümedeki tek bir düğümü etkileyebilir. Başarısız bir ağ anahtarı sunucu rafından tamamını etkileyebilir. Güç kaybı gibi yaygın olarak karşılaşılan sorunlar, tüm veri merkezini kesintiye uğratabilir. Nadiren, bir bölgenin tamamı kullanılamaz hale gelir.

[Artıklık](/azure/architecture/guide/design-principles/redundancy) , uygulama esnekliği sağlamanın bir yoludur. Gereken artıklık düzeyi, iş gereksinimlerinize bağlıdır ve sisteminizin maliyetini ve karmaşıklığını etkiler. Örneğin, çok bölgeli bir dağıtım, tek bölgeli bir dağıtıma göre yönetilmesi daha pahalıdır ve daha karmaşıktır. Yük devretme ve yeniden çalışma işlemlerini yönetmek için işlemsel yordamlara ihtiyacınız olacak. Ek maliyet ve karmaşıklık bazı iş senaryoları için değişebilir, ancak diğerleri için kullanılamaz.

Yedekliliği mimARDA uygulamak için uygulamanızdaki kritik yolları belirlemeniz ve sonra yoldaki her bir noktada artıklık olup olmadığını belirlemeniz gerekir mi? Bir alt sistem başarısız olursa, uygulama başka bir şeye devredilecek mi? Son olarak, Azure bulut platformunda yerleşik olarak bulunan ve artıklık gereksinimlerinizi karşılamak için kullanabileceğiniz özellikleri net bir şekilde kavramanız gerekir. Yedeklilik mimarisi için öneriler aşağıda verilmiştir:

- *Birden çok hizmet örneğini dağıtın.* Uygulamanız bir hizmetin tek bir örneğine bağımlıysa, tek bir hata noktası oluşturur. Birden çok örnek sağlanması hem dayanıklılık hem de ölçeklenebilirliği geliştirir. Azure Kubernetes hizmetinde barındırırken, Kubernetes bildirim dosyasında gereksiz örnekleri (çoğaltma kümeleri) bildirimli olarak yapılandırabilirsiniz. Çoğaltma sayısı değeri programlı olarak, portalda veya otomatik ölçeklendirme özellikleri aracılığıyla yönetilebilir.

- *Yük dengeleyiciyi kullanma.* Yük Dengeleme, uygulamanızın isteklerini sağlıklı hizmet örneklerine dağıtır ve sağlıksız örnekleri otomatik olarak dönüşten kaldırır. Kubernetes 'e dağıtım yaparken, hizmetler bölümündeki Kubernetes bildirim dosyasında Yük Dengeleme belirlenebilir.

- *Çok bölgeli dağıtımını planlayın.* Uygulamanızı tek bir bölgeye dağıtırsanız ve bu bölge kullanılamaz duruma gelirse, uygulamanız da kullanılamaz hale gelir. Bu, uygulamanızın hizmet düzeyi sözleşmeleri koşullarında kabul edilebilir olmayabilir. Bunun yerine, uygulamanızı ve hizmetlerini birden çok bölgeye dağıtmaya dikkat edin. Örneğin, bir Azure Kubernetes hizmeti (AKS) kümesi tek bir bölgeye dağıtılır. Sisteminizi bölgesel bir hatadan korumak için, uygulamanızı farklı bölgelerde birden çok AKS kümesine dağıtabilir ve [eşleştirilmiş bölgeler](https://buildazure.com/2017/01/06/azure-region-pairs-explained/) özelliğini kullanarak platform güncelleştirmelerini koordine edebilir ve kurtarma çalışmalarını önceliklendirin.

- *[Coğrafi çoğaltmayı](/azure/sql-database/sql-database-active-geo-replication)etkinleştirin.* Azure SQL veritabanı ve Cosmos DB gibi hizmetler için coğrafi çoğaltma, verilerinizin birden çok bölgede ikincil çoğaltmalarını oluşturacaktır. Her iki hizmet de aynı bölgedeki verileri otomatik olarak çoğaltarak, coğrafi çoğaltma, bir ikincil bölgeye yük devretmek için bölgesel bir kesinti ile karşı koruma sağlar. Kapsayıcı görüntülerinin depolandığı coğrafi çoğaltma merkezleri için bir en iyi yöntem. AKS 'de bir hizmet dağıtmak için, görüntüyü depolamanız ve bir depodan çekmeniz gerekir. Azure Container Registry, AKS ile tümleşir ve kapsayıcı görüntülerini güvenli bir şekilde saklayabilir. Performansı ve kullanılabilirliği artırmak için, görüntülerinizi bir AKS kümeniz olan her bölgedeki bir kayıt defterine coğrafi olarak çoğaltmayı göz önünde bulundurun. Ardından, her bir AKS kümesi, Şekil 6-4 ' de gösterildiği gibi bölgesinde yerel kapsayıcı kayıt defterinden kapsayıcı görüntülerini çeker:

![Bölgeler arasında çoğaltılan kaynaklar](./media/replicated-resources.png)

**Şekil 6-4**. Bölgeler arasında çoğaltılan kaynaklar

- *Bir DNS trafiği yük dengeleyici uygulayın.* [Azure Traffic Manager](/azure/traffic-manager/traffic-manager-overview) , DNS düzeyinde yük dengelemeye göre kritik uygulamalar için yüksek kullanılabilirlik sağlar. Coğrafi konum, küme yanıt süresi ve hatta uygulama uç noktası sistem durumu temelinde trafiği farklı bölgelere yönlendirebilir. Örneğin, Azure Traffic Manager müşterileri en yakın AKS kümesine ve uygulama örneğine yönlendirebilir. Farklı bölgelerde birden fazla AKS kümeniz varsa, trafiğin her kümede çalışan uygulamalara nasıl akacağını denetlemek için Traffic Manager kullanın. Şekil 6-5, bu senaryoyu gösterir.

![AKS ve Azure Traffic Manager](./media/aks-traffic-manager.png)

**Şekil 6-5**. AKS ve Azure Traffic Manager

## <a name="design-for-scalability"></a>Ölçeklenebilirlik için tasarım

Bulut ölçeklendiriliyor. Sistem yükünü artırmak/azaltmak için sistem kaynaklarını artırma/azaltma yeteneği, Azure bulutunun önemli bir özelliğidir. Ancak, bir uygulamayı etkin bir şekilde ölçeklendirmek için uygulamanıza dahil ettiğiniz her bir Azure hizmetinin ölçekleme özelliklerinin anlaşılmasına gerek duyarsınız.  Sisteminizde ölçeklendirmeyi etkili bir şekilde uygulamaya yönelik öneriler aşağıda verilmiştir.

- *Ölçeklendirme için tasarlayın.* Uygulamanın ölçeklendirilmesi için tasarlanmış olması gerekir. Başlamak için hizmetlerin durum bilgisiz olması gerekir, bu nedenle istekler herhangi bir örneğe yönlendirilebilir. Durum bilgisi olmayan hizmetlerin olması, bir örneği eklemenin veya kaldırmanın geçerli kullanıcıları olumsuz yönde etkilemediği anlamına gelir.

- *Bölüm iş yükleri*. Etki alanlarının bağımsız bir şekilde çıkarılması, kendi kendine kapsanan mikro hizmetlere, her hizmetin diğerlerinden bağımsız olarak ölçeklendirilmesine olanak tanır. Genellikle, hizmetler farklı ölçeklenebilirlik gereksinimlerine ve gereksinimlerine sahip olur. Bölümlendirme, bir uygulamanın tamamını ölçeklendirmeye yönelik gereksiz maliyet olmadan yalnızca ölçeklendirilmesi gerekenleri ölçeklendirmenize olanak sağlar.

- *Ölçeği genişletme tercih edin.* Bulut tabanlı uygulamalar, ölçeklendirmenin aksine kaynakları ölçeklendirmeye tercih ister. Ölçeği genişletme (yatay ölçeklendirme olarak da bilinir), istenen bir performans düzeyini karşılamak ve paylaşmak üzere mevcut bir sisteme daha fazla hizmet kaynağı eklenmesini içerir. Ölçeği artırma (dikey ölçeklendirme olarak da bilinir), var olan kaynakları daha güçlü donanımla (daha fazla disk, bellek ve işlem çekirdeği) değiştirmeyi içerir. Ölçeği genişletme, bazı Azure bulut kaynaklarında bulunan otomatik ölçeklendirme özellikleriyle otomatik olarak çağrılabilir. Birden çok kaynak arasında ölçeklendirme yapmak, genel sisteme artıklık de ekler. Son olarak, tek bir kaynağın ölçeklendirilmesi genellikle pek çok daha küçük kaynak arasında ölçeklendirmeden daha pahalıdır. Şekil 6-6 iki yaklaşımı gösterir:

![Ölçeği büyütme ve ölçeği genişletme](./media/scale-up-scale-out.png)

**Şekil 6-6.** Ölçeği büyütme ve ölçeği genişletme

- *Orantılı olarak ölçeklendirin.* Bir hizmeti ölçeklendirirken, *kaynak kümeleri*açısından göz önünde bulundurun. Belirli bir hizmeti önemli ölçüde ölçeklendirmeniz durumunda, arka uç veri depoları, önbellekler ve bağımlı hizmetler üzerinde hangi etkileri vardır? Cosmos DB gibi bazı kaynaklar orantılı bir şekilde ölçeklenebilir, ancak diğerleri pek çok olamaz. Kaynağı, diğer ilişkili kaynakları tüketdirecek bir noktaya ölçeklendirdiğinizden emin olmak istiyorsunuz.

- *Benzeşim kullanmaktan kaçının.* Bir düğümün, genellikle bir *yapışkan oturum*olarak adlandırılan yerel benzeşim gerektirmemesini sağlamak en iyi uygulamadır. Bir istek herhangi bir örneğe yönlendiribilmelidir. Durumu kalıcı hale getirmeniz gerekiyorsa, [Azure redsıs Cache](https://azure.microsoft.com/services/cache/)gibi dağıtılmış bir önbelleğe kaydedilmelidir.

- *Platform otomatik ölçeklendirme özelliklerinin avantajlarından yararlanın.* Özel veya üçüncü taraf mekanizmalarının yerine, mümkün olduğunda yerleşik otomatik ölçeklendirme özellikleri kullanın. Mümkün olduğunda, kaynakların bir başlangıç gecikmesi olmadan kullanılabilir olduğundan emin olmak için zamanlanmış ölçekleme kurallarını kullanın, ancak kurallara uygun şekilde, isteğe bağlı olarak, talep halinde beklenmedik değişikliklerle ve bu kurallara otomatik ölçeklendirme ekleyin. Daha fazla bilgi için bkz. [Otomatik ölçeklendirme Kılavuzu](/azure/architecture/best-practices/auto-scaling).

- *Ölçeği daraltma.* Son bir uygulama, iş kaybı olmadan trafikte anında ani artışları hızlı bir şekilde karşılayabilmeniz için kararlılığı en iyi şekilde genişletmek olacaktır. Ve sonra, sistem kararlı tutmaya yönelik olarak ölçeği ölçeklendirin (gereksiz örnekleri kaldırır). Bunu yapmanın basit bir yolu, ölçeklendirme işlemleri arasında bekleme süresi, kaynak eklemek için beş dakika, örnekleri kaldırmak için en fazla 15 dakika olan seyrek erişimli süreyi ayarlamanıza yöneliktir.

## <a name="built-in-retry-in-services"></a>Hizmetlerde yerleşik yeniden deneme

Daha önceki bir bölümde programlı yeniden deneme işlemleri uygulamak için en iyi uygulama önerilir. Birçok Azure hizmeti ve bunlara karşılık gelen istemci SDK 'larının yeniden deneme mekanizmalarını de dahil olduğunu aklınızda bulundurun. Aşağıdaki listede, bu kitapta tartışılan birçok Azure hizmeti için yeniden deneme özellikleri özetlenmektedir:

- *Azure Cosmos DB.* <xref:Microsoft.Azure.Documents.Client.DocumentClient>ISTEMCI API 'sindeki sınıf başarısız denemeleri otomatik olarak yeniden oluşturur. Yeniden deneme sayısı ve en fazla bekleme süresi yapılandırılabilir. İstemci API 'SI tarafından oluşturulan özel durumlar, yeniden deneme ilkesini veya geçici olmayan hataları aşan isteklerdir.

- *Azure Redis Cache.* Redsıs StackExchange istemcisi, başarısız denemelerde yeniden denemeler içeren bir bağlantı Yöneticisi sınıfı kullanır. Yeniden deneme sayısı, belirli bir yeniden deneme ilkesi ve bekleme süresi yapılandırılabilir.

- *Azure Service Bus.* Service Bus istemcisi bir geri alma aralığı, yeniden deneme sayısı ve bir işlemin ne zaman sürebileceği maksimum süreyi belirten bir [Retrypolicy sınıfı](xref:Microsoft.ServiceBus.RetryPolicy) kullanıma sunar <xref:Microsoft.ServiceBus.RetryExponential.TerminationTimeBuffer%2A> . Varsayılan ilke, denemeler arasında 30 saniyelik geri alma süresi olan dokuz en fazla yeniden deneme girişimdir.

- *Azure SQL Veritabanı* [Entity Framework Core](/ef/core/miscellaneous/connection-resiliency) kitaplığı kullanılırken yeniden deneme desteği sağlanır.

- *Azure depolama.* Depolama istemci kitaplığı, yeniden deneme işlemlerini destekler. Stratejiler, Azure depolama tabloları, blob 'lar ve kuyruklar arasında farklılık gösterir. Ayrıca, coğrafi artıklık özelliği etkinken, alternatif yeniden denemeler birincil ve ikincil depolama hizmetleri konumları arasında geçiş yapar.

- *Azure Event Hubs.* Olay Hub 'ı istemci kitaplığı, yapılandırılabilir bir üstel geri alma özelliği içeren bir RetryPolicy özelliğine sahiptir.

>[!div class="step-by-step"]
>[Önceki](application-resiliency-patterns.md) 
> [Sonraki](resilient-communications.md)
