---
title: İş Parçacıkları ve İş Parçacığı Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework]
- threading [.NET Framework], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4380c509a08ebe59f9561a9e6fc596458768917f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="threads-and-threading"></a>İş Parçacıkları ve İş Parçacığı Oluşturma
İşletim sistemleri işlemleri yürütülmekte olduğunu farklı uygulamaları ayırmak için kullanır. İş parçacığı bir işletim sistemi işlemci zamanı tarafından ayrılan temel birimi olan ve birden çok iş parçacığı işlem içinde kod yürütme. Her iş parçacığı, özel durum işleyicileri, bir zamanlama önceliği ve sistem zamanlandığı süreye kadar iş parçacığı içeriği kaydetmek için kullandığı yapıları kümesi tutar. İş parçacığı bağlamını sorunsuz bir şekilde yürütme iş parçacığının ana bilgisayar işlemi adres alanında CPU kaydeder ve yığını, iş parçacığının kümesi de dahil olmak üzere, devam etmek için iş parçacığı gereken tüm bilgileri içerir.  
  
 Daha fazla .NET Framework tarafından temsil edilen uygulama etki alanı adı verilen hafif yönetilen alt içine bir işletim sistemi işlemi subdivides <xref:System.AppDomain?displayProperty=nameWithType>. Bir veya daha fazla yönetilen iş parçacığı (tarafından temsil edilen <xref:System.Threading.Thread?displayProperty=nameWithType>) birini veya bunların sayısı aynı yönetilen işlemi içinde uygulama etki alanları olarak çalıştırabilirsiniz. Her uygulama etki alanı ile tek bir iş parçacığı çalışmaya olsa da, bu uygulama etki alanı kodunda ek uygulama etki alanları ve ek iş parçacığı oluşturabilirsiniz. Yönetilen iş parçacığı aynı yönetilen işlem içinde uygulama etki alanları arasında serbestçe taşıyabilirsiniz sonucudur; birçok uygulama etki alanları arasında taşıma yalnızca tek bir iş parçacığı olabilir.  
  
 PreEmptive tarafından görevli destekleyen bir işletim sistemi aynı anda birden çok iş parçacığı yürütülmesi etkisini birden çok işlemlerini oluşturur. Bunu yapar kullanılabilir işlemci zamanı ihtiyaç iş parçacıkları arasında bölünmesi, her iş parçacığı için işlemci zaman dilimi birbiri ardından ayrılıyor. Dilim sona erdiğinde, saat ve başka sürdürür çalışan iş parçacığı, şu anda yürütülen iş parçacığı askıya alındı. Sistem bir iş parçacığından diğerine geçtiğinde, iş parçacığı içeriği preempted iş parçacığının kaydeder ve iş parçacığı sırasındaki sonraki iş parçacığı kaydedilmiş iş parçacığı bağlamı yeniden yükler.  
  
 Zaman dilimi uzunluğu işletim sistemi ve işlemci bağlıdır. Her zaman dilimi küçük olduğundan, sadece bir işlemci olsa bile birden çok iş parçacığı aynı anda yürütülen görünür. Bu gerçekten çok işlemcili sistemlerde yürütülebilir iş parçacıkları arasında kullanılabilir işlemci dağıtıldığı bir durumdur.  
  
## <a name="when-to-use-multiple-threads"></a>Birden çok iş parçacığı kullanma zamanı  
 Kullanıcı etkileşimi gerektiren yazılım, kullanıcının etkinlikler için zengin bir kullanıcı deneyimi sağlamak için mümkün olduğunca hızlı bir şekilde tepki gerekir. Aynı anda ancak bunu kadar hızlı kullanıcıya verileri sunmak gerekli hesaplama yapmanız gerekir. Uygulamanızı yürütme yalnızca bir iş parçacığı kullanıyorsa, birleştirebilirsiniz [zaman uyumsuz programlama](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md) ile[.NET Framework remoting](https://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462) veya [XML Web Hizmetleri](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c) ASP kullanılarak oluşturulan Diğer bilgisayarların işleme süresi ek olarak, artırmak için kendi yanıtlama hızı azaltma, uygulamanızın veri işleme süresini ve kullanıcı için kullanılacak .NET. Yoğun giriş/çıkış iş yapıyorsanız, g/ç tamamlama bağlantı noktaları, uygulamanızın yanıt hızını artırmak için kullanabilirsiniz.  
  
### <a name="advantages-of-multiple-threads"></a>Birden çok iş parçacığı avantajları  
 Birden çok iş parçacığı kullanan, ancak en güçlü kullanıcı yanıt verme hızını artırmak ve neredeyse aynı anda işin tamamlanması gereken verileri işlemek kullanılabilir tekniğidir. Bir işlemciye sahip bir bilgisayar üzerinde birden çok iş parçacığı arka planda verileri işlemek için kullanıcı olaylarını Between kısa sürelerle yararlanarak, bu etkiyi oluşturabilirsiniz. Örneğin, başka bir iş parçacığı aynı uygulama içinde elektronik tablo diğer bölümleri yeniden hesaplama sırasında bir kullanıcı bir elektronik tablo düzenleyebilirsiniz.  
  
 Değişiklik yapılmadan, aynı uygulamanın önemli ölçüde birden çok işlemciye sahip bir bilgisayar üzerinde çalıştırdığınızda, kullanıcı memnuniyetini artırır. Tek bir uygulama etki alanınızın birden çok iş parçacığı aşağıdaki görevleri gerçekleştirmek için kullanabilirsiniz:  
  
-   Bir Web sunucusu ve veritabanı için bir ağ üzerinden iletişim kurar.  
  
-   Büyük bir zaman miktarıdır ele işlemleri gerçekleştirir.  
  
-   Değişen öncelikli görevler ayırt etmek. Örneğin, yüksek öncelikli iş parçacığı zaman açısından kritik görevleri yönetir ve düşük öncelikli iş parçacığı diğer görevleri gerçekleştirir.  
  
-   Arka plan görevleri süresi ayrılırken yanıt verebilir durumda, kalması için kullanıcı arabirimi sağlar.  
  
### <a name="disadvantages-of-multiple-threads"></a>Birden çok iş parçacığı dezavantajları  
 En az iş parçacığı olası, böylece işletim sistemi kaynaklarının kullanımını en aza indirmenizi ve performans artırılır olarak kullanmanız önerilir. İş parçacığı oluşturma Ayrıca kaynak gereksinimlerini ve olası çakışmaları uygulamanızı tasarlarken göz önünde bulundurulması gerekir. Kaynak gereksinimleri aşağıdaki gibidir:  
  
-   Sistem belleğini işlemler tarafından gereken bağlam bilgilerini tükettiğini **AppDomain** nesneleri ve iş parçacığı sayısı. Bu nedenle, işlem, sayısı **AppDomain** nesneleri ve oluşturulabilir iş parçacıkları tarafından kullanılabilen bellek sınırlandırılmıştır.  
  
-   Çok sayıda iş parçacığı izlemek önemli ölçüde işlemci zamanı tüketir. Çok fazla iş parçacığı varsa, bunların çoğu önemli ilerleme yapmaz. Geçerli iş parçacığı çoğunu tek bir işlemde varsa, diğer işlemlerin iş parçacıklarında daha az sıklıkta zamanlanır.  
  
-   Kod yürütmeyi birçok iş parçacığı ile denetleme karmaşıktır ve çoğu hataların bir kaynak olabilir.  
  
-   İş parçacıklarını yok etme meydana gelebilir bilerek ve bu sorunları işleme gerektirir.  
  
 Paylaşılan kaynaklara erişim sağlayan çakışmaları oluşturabilirsiniz. Çakışmaları önlemek için eşitleme veya, paylaşılan kaynaklara erişimi denetlemek. Erişim düzgün (aynı veya farklı uygulama etki alanları) eşitlemek için hata kilitlenmeler (iki hangi iş parçacıkları her diğer tamamlanmasını beklerken vermiyor) gibi sorunlara yol açabilir ve (nedeniyle anormal bir sonuç ortaya çıktığında koşullar izler bir beklenmeyen kritik bağımlılığı iki olay zamanlaması). Sistem kaynak arasında birden çok iş parçacığı paylaşımı koordine etmek için kullanılan eşitleme nesneleri sağlar. İş parçacığı sayısını azaltarak kaynakları eşitlemek kolaylaştırır.  
  
 Eşitleme gerektiren kaynaklara şunları içerir:  
  
-   Sistem kaynakları (örneğin, iletişim bağlantı noktaları).  
  
-   Birden çok işlemler (örneğin, dosya tanıtıcıları) tarafından paylaşılan kaynaklar.  
  
-   Kaynakları tek bir uygulama etki alanı üyesi (Genel, statik gibi ve örneği alanları) birden çok iş parçacığı tarafından erişilebilir.  
  
### <a name="threading-and-application-design"></a>İş parçacığı oluşturma ve uygulama tasarımı  
 Genel olarak, kullanarak <xref:System.Threading.ThreadPool> en kolay yolu, değil engeller başka bir iş parçacığı ve ne zaman değil beklediğiniz herhangi belirli görevlerin zamanlamasını görece kısa görevler için birden çok iş parçacığı işlemek için bir sınıftır. Ancak, bir sayı kendi iş parçacığı oluşturma nedenleri vardır:  
  
-   Belirli bir önceliği olan bir görev gerekiyorsa.  
  
-   Uzun süre çalışan (ve bu nedenle diğer görevleri engelleme) bir görev varsa.  
  
-   İş parçacığı bir tek iş parçacıklı yerleştirilecek gerekir (tüm **Threadpool'u** iş parçacığı sayısı olan birden çok iş parçacıklı grupta).  
  
-   İş parçacığı ile ilişkili kararlı bir kimlik gerekiyorsa. Örneğin, o iş parçacığı durdurmak, askıya veya ada göre bulmak için adanmış bir iş parçacığı kullanmanız gerekir.  
  
-   Kullanıcı arabirimiyle etkileşim arka plan iş parçacıkları çalıştırmanız gerekiyorsa, .NET Framework sürüm 2.0 sağlayan bir <xref:System.ComponentModel.BackgroundWorker> olayları, kullanıcı arabirimi iş parçacığı için iş parçacıkları arası sıralama ile kullanarak iletişim kurar bileşeni.  
  
### <a name="threading-and-exceptions"></a>Parçacıkları ve özel durumlar  
 İş parçacıklarında özel durumlar işleyin. İş parçacığı, hatta arka plan iş parçacıkları, işlenmemiş özel durumlardan genellikle işlemi sonlandırın. Bu kural için üç özel durum vardır:  
  
-   A <xref:System.Threading.ThreadAbortException> bir iş parçacığı, çünkü atılır <xref:System.Threading.Thread.Abort%2A> çağrıldı.  
  
-   Bir <xref:System.AppDomainUnloadedException> uygulama etki alanı bellekten olduğundan bir iş parçacığında oluşturuldu.  
  
-   Ortak dil çalışma zamanı ya da bir ana bilgisayar işlemi iş parçacığı sonlanır.  
  
 Daha fazla bilgi için bkz: [yönetilen iş parçacıklarında özel durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  .NET Framework sürüm 1.0 ve 1.1, ortak dil çalışma zamanı sessizce bazı durumlar, örneğin iş parçacığı havuzu iş parçacıkları yakalar. Bu uygulama durumu bozuk ve hata ayıklamak oldukça zor olabilir askıda kalmasına uygulamaları neden.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.ThreadPool>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Çoklu İş Parçacığı Kullanımı için Veri Eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 [Yönetilen İş Parçacığı Havuzu](../../../docs/standard/threading/the-managed-thread-pool.md)
