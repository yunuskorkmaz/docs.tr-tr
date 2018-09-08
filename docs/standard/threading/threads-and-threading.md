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
ms.openlocfilehash: ef464b0d4c22d04d42f9b6f953abefe7582b4957
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188546"
---
# <a name="threads-and-threading"></a>İş Parçacıkları ve İş Parçacığı Oluşturma
İşletim sistemleri, yürütülen farklı uygulamaları ayırmak için işlemleri kullanın. Temel birim, bir işletim sisteminin işlemci süresi ayırdığı akışlardır ve birden fazla iş parçacığı, işlem içinde kod yürütülüyor. Her iş parçacığı, özel durum işleyicileri, zamanlama önceliğini ve yapıları, zamanlanan kadar iş parçacığı bağlamını kaydetmek için sistem kullanır kümesi tutar. İş parçacığı bağlamını iş parçacığı yürütme iş parçacığının ana bilgisayar işlemi adres alanında iş parçacığının dizi CPU kaydeder ve yığını da dahil olmak üzere, sorunsuz bir şekilde devam etmek için gereken tüm bilgileri içerir.  
  
 Tarafından temsil edilen uygulama etki alanı adı verilen hafif yönetilen alt işlemden, içine .NET Framework başka bir işletim sistemi işlemi kesen ve onun <xref:System.AppDomain?displayProperty=nameWithType>. Bir veya daha fazla yönetilen iş parçacıkları (tarafından temsil edilen <xref:System.Threading.Thread?displayProperty=nameWithType>) birini veya yönetilen aynı işlem içinde uygulama etki alanları sayısı çalıştırabilirsiniz. Her uygulama etki alanı ile tek bir iş parçacığı başlatıldı ancak kodu, uygulama etki alanındaki ek bir uygulama etki alanları ve ek iş parçacıkları oluşturabilirsiniz. Yönetilen iş parçacığı yönetilen aynı işlem içinde uygulama etki alanları arasında serbestçe taşınabildiğini sonucudur; birden çok uygulama etki alanları arasında taşıma yalnızca tek bir iş parçacığı olabilir.  
  
 Preemptive çok görevli destekleyen bir işletim sistemi, birden çok işlemlerden birden çok iş parçacıklarının eş zamanlı yürütme efekti oluşturur. Bunu yapar kullanılabilir işlemci zamanı gereksinim iş parçacıkları arasında bölünmesi, birbiri ardına işlemci zaman dilimi için her bir iş parçacığı ayırma. Kendi saat dilimi geçen ve başka sürdürür çalışan iş parçacığı, yürütülmekte olan iş parçacığını askıya alınır. Sistem bir iş parçacığından diğerine geçtiğinde, preempted iş parçacığının iş parçacığı bağlamını kaydeder ve kaydedilmiş iş parçacığı bağlamını sonraki iş parçacığının iş parçacığı sırasındaki yeniden yükler.  
  
 Zaman dilimi uzunluğu, işletim sistemi ve işlemci bağlıdır. Her zaman dilimi küçük olduğundan, aynı anda yürütülmesi için birden çok iş parçacığı tek bir işlemci olsa bile görünür. Bu gerçekten çok işlemcili sistemlerde yürütülebilir iş parçacığı kullanılabilir işlemci arasında dağıtıldığı bir durumdur.  
  
## <a name="when-to-use-multiple-threads"></a>Birden çok iş parçacığı kullanma zamanı  
 Kullanıcı etkileşimi gerektiren yazılım kullanıcının etkinlikleri için zengin bir kullanıcı deneyimi sağlamak için mümkün olduğunca hızlı bir şekilde tepki gerekir. Aynı zamanda, ancak bunu mümkün olduğunca hızlı kullanıcı verileri sunmak gerekli hesaplamalar yapmanız gerekir. Uygulamanız yalnızca bir iş parçacığı yürütme kullanıyorsa birleştirebilirsiniz [zaman uyumsuz programlama](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md) ile[.NET Framework remoting](https://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462) veya [XML Web Hizmetleri](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c) ASP kullanılarak oluşturulan Diğer bilgisayarların işleme süresini artırmak için kendi yanıt süresi kullanıcı ve uygulama veri işleme süresini azaltmak için ayrıca kullanmak için .NET. Yoğun giriş/çıkış iş yapıyorsanız, g/ç tamamlama bağlantı noktaları, uygulamanızın yanıt hızını artırmak için de kullanabilirsiniz.  
  
### <a name="advantages-of-multiple-threads"></a>Birden çok iş parçacığı avantajları  
 Birden fazla iş parçacığı kullanan, ancak en güçlü kullanıcıya yanıt verme hızını artırmak ve neredeyse aynı zamanda işin tamamlanması için gereken verileri işlemek kullanılabilir tekniğidir. Bir işlemciye sahip bir bilgisayar üzerinde birden çok iş parçacığı arka planda verileri işlemek için kullanıcı olaylar arasında küçük sürelerle yararlanarak, bu etkiyi oluşturabilirsiniz. Örneğin, bir kullanıcı başka bir iş parçacığı aynı uygulama içinde elektronik diğer bölümlerini yeniden hesaplama sırasında bir elektronik tablo düzenleyebilirsiniz.  
  
 Değişiklik yapılmadan, aynı uygulamanın birden fazla işlemciye sahip bir bilgisayarda çalıştırdığınızda kullanıcı memnuniyeti önemli ölçüde yükseltir. Tek bir uygulama etki alanınız birden çok iş parçacığı, aşağıdaki görevleri gerçekleştirmek için kullanabilirsiniz:  
  
-   Bir Web sunucusu ve veritabanı için bir ağ üzerinden iletişim kurar.  
  
-   Büyük miktarda zaman alan işlemleri gerçekleştirir.  
  
-   Görevler çeşitli öncelik ayırt. Örneğin, zaman açısından kritik görevleri bir yüksek öncelikli iş parçacığını yöneten ve düşük öncelikli iş parçacığı diğer görevleri gerçekleştirir.  
  
-   Arka plan görevleri süresi vmscaleset ayrılırken, esnek, kalması kullanıcı arabirimi sağlar.  
  
### <a name="disadvantages-of-multiple-threads"></a>Birden çok iş parçacığı dezavantajları  
 Olası, böylece işletim sistemi kaynaklarının kullanımını en aza indirmek ve performansı iyileştirme olabildiğince az iş parçacığı kullanmanız önerilir. İş parçacığı kaynak gereksinimlerini ve olası çakışmaları uygulamanızı tasarlarken dikkate de vardır. Kaynak gereksinimleri aşağıdaki gibidir:  
  
-   Sistem işlemleri tarafından gereken bağlam bilgilerini bellek tüketir **AppDomain** nesneleri ve iş parçacıkları. Bu nedenle, işlem sayısını **AppDomain** nesneleri ve oluşturulabilmesi için iş parçacığı tarafından kullanılabilir bellek sınırlıdır.  
  
-   Çok sayıda iş parçacığı izlemek önemli bir işlemci zamanı kullanıyor. Çok fazla iş parçacığı varsa, bunların çoğu önemli ilerleme yapmaz. Diğer işlemleri iş parçacıklarının, geçerli iş parçacığı bir işlem içinde çoğu, daha az sıklıkta zamanlanır.  
  
-   Birçok iş parçacığı ile kod yürütmeyi denetleme, karmaşık ve birçok hata, bir kaynak olabilir.  
  
-   İş parçacıklarını yok etme, bilerek ne meydana gelmiş olabilir ve bu sorunların işleme gerektirir.  
  
 Paylaşılan kaynaklara erişim sağlayan, çakışmaları oluşturabilirsiniz. Çakışmaları önlemek için eşitleme veya, paylaşılan kaynaklara erişimi denetler. Doğru (aynı veya farklı uygulama etki alanlarında) erişimi eşitleme hatası (iki iş parçacığı her diğer tamamlanmasını beklerken yanıt vermeyi durdurma) kilitlenmeler gibi sorunları açabilir ve yarış koşulları (nedeniyle anormal bir sonuç ortaya çıktığında bir beklenmeyen kritik düzeyde bağımlı iki olay zamanlaması). Sistem kaynak arasında birden çok iş parçacığı paylaşımı koordine etmek için kullanılan eşitleme nesneleri sağlar. İş parçacığı sayısını azaltma, kaynakların eşitlemek kolaylaştırır.  
  
 Eşitleme iste kaynaklar şunları içerir:  
  
-   Sistem kaynakları (örneğin, iletişim bağlantı noktaları).  
  
-   Kaynaklar (örneğin, dosya tanıtıcıları) birden çok işlem tarafından paylaşılır.  
  
-   Tek bir uygulama etki alanı kaynaklarına (gibi genel, statik ve örnek alanları) birden çok iş parçacığı tarafından erişilebilir.  
  
### <a name="threading-and-application-design"></a>İş parçacığı ve uygulama tasarımı  
 Genel olarak, kullanarak <xref:System.Threading.ThreadPool> sınıfı, birden çok iş parçacığı, değil engeller diğer iş parçacıkları ve ne zaman girmek istemediğiniz herhangi belirli görevler için zamanlama görece kısa görevler için işlemek için en kolay yoludur. Ancak, kendi iş parçacığı oluşturmak için nedenlerden biri vardır:  
  
-   Belirli bir önceliğe sahip olarak bir görevi ihtiyaç duyuyorsanız.  
  
-   Uzun süre çalıştırın (ve bu nedenle diğer görevleri engellemek) bir görev varsa.  
  
-   İş parçacığı bir tek iş parçacıklı grup yerleştirmek ihtiyacınız varsa (tüm **iş parçacığı havuzu** akışlardır birden çok iş parçacıklı apartmanda).  
  
-   İş parçacığı ile ilişkili bir kararlı kimlik ihtiyaç duyuyorsanız. Örneğin, iş parçacığı durdurmak, askıya veya ada göre bulmak için adanmış bir iş parçacığı kullanmalısınız.  
  
-   Kullanıcı arabirimi ile etkileşim kuran arka plan iş parçacığı çalıştırmanız gerekiyorsa, .NET Framework sürüm 2.0 sağlayan bir <xref:System.ComponentModel.BackgroundWorker> olaylarını, iş parçacıkları arası kullanıcı arabirimi iş parçacığına sıralama ile kullanarak iletişim kuran bileşeni.  
  
### <a name="threading-and-exceptions"></a>Parçacıkları ve özel durumlar  
 İş parçacıklarında özel durumlar işleyin. İşlenmeyen özel durumları iş parçacıkları, hatta arka plan iş parçacığı, genellikle işlemi sonlandırın. Bu kural için üç özel durum vardır:  
  
-   A <xref:System.Threading.ThreadAbortException> çünkü bir iş parçacığında oluşturulan <xref:System.Threading.Thread.Abort%2A> çağrıldı.  
  
-   Bir <xref:System.AppDomainUnloadedException> uygulama etki alanı kaldırıldı çünkü bir dizi oluşturulur.  
  
-   Ortak dil çalışma zamanı ya da bir ana bilgisayar işlemi iş parçacığı sonlanır.  
  
 Daha fazla bilgi için [yönetilen iş parçacıklarında özel durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  .NET Framework sürüm 1.0 ve 1.1, ortak dil çalışma zamanı iş parçacığı havuzu iş parçacıkları, örneğin bazı özel durumlar sessizce yakalar. Bu uygulama durumu bozuk ve hata ayıklamak oldukça zor olabilecek askıda kalmasına uygulamalar neden.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ThreadPool>  
- <xref:System.ComponentModel.BackgroundWorker>  
- [Çoklu İş Parçacığı Kullanımı için Veri Eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
- [Yönetilen İş Parçacığı Havuzu](../../../docs/standard/threading/the-managed-thread-pool.md)
