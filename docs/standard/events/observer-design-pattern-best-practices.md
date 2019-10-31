---
title: Gözlemci Tasarım Deseni En İyi Yöntemleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- observer design pattern [.NET Framework], best practices
- best practices [.NET Framework], observer design pattern
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
ms.openlocfilehash: 2da29e0baf429142707d0ddd39b1a11c13a17a90
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141543"
---
# <a name="observer-design-pattern-best-practices"></a>Gözlemci Tasarım Deseni En İyi Yöntemleri
.NET Framework, gözlemci tasarım deseninin bir dizi arabirim olarak uygulanması gerekir. <xref:System.IObservable%601?displayProperty=nameWithType> arabirimi, gözlemcilerin 'ın bildirimlerden aboneliklerini kaldırma izni veren <xref:System.IDisposable> bir uygulama sağlamaktan de sorumlu olan veri sağlayıcısını temsil eder. <xref:System.IObserver%601?displayProperty=nameWithType> arabirimi gözlemciyi temsil eder. Bu konuda, bu arabirimleri kullanarak gözlemci tasarım modelini uygularken geliştiricilerin izlenmesi gereken en iyi uygulamalar açıklanmaktadır.  
  
## <a name="threading"></a>İş Parçacığı Oluşturma  
 Genellikle, bir sağlayıcı, bazı koleksiyon nesneleri tarafından temsil edilen bir abone listesine belirli bir gözlemci ekleyerek <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> yöntemini uygular ve abone listesinden belirli bir gözlemci kaldırarak <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metodunu uygular. Bir gözlemci, bu yöntemleri dilediğiniz zaman çağırabilir. Ayrıca, sağlayıcı/gözlemci <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> geri çağırma yönteminden sonra aboneliği kaldırmaktan sorumlu kişiyi belirtmediğinden, sağlayıcı ve gözlemci aynı üyeyi listeden kaldırmayı deneyebilir. Bu nedenle, <xref:System.IObservable%601.Subscribe%2A> ve <xref:System.IDisposable.Dispose%2A> yöntemlerinin her ikisi de iş parçacığı açısından güvenli olmalıdır. Genellikle, bu, [eş zamanlı bir koleksiyonun](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md) veya kilidin kullanılmasını içerir. İş parçacığı açısından güvenli olmayan uygulamalar, açık bir şekilde belgelemelidir.  
  
 Ek garantiler sağlayıcının/gözlemci sözleşmesinin en üstündeki bir katmanda belirtilmelidir. Uygulayıcılar, gözlemciye ilişkin Kullanıcı karışıklığına engel olmak için ek gereksinimler gerçekleştirdiklerinde açıkça bir çağrı çağırmalıdır.  
  
## <a name="handling-exceptions"></a>Özel Durumları İşleme  
 Bir veri sağlayıcısı ve gözlemci arasındaki gevşek bağlantısı nedeniyle, gözlemci tasarım düzenindeki özel durumlar bilgilendirme amaçlıdır. Bu, sağlayıcının ve gözlemcilerin 'ın gözlemci tasarım modelinde özel durumları nasıl işleyeceğini etkiler.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Sağlayıcı--HATADÜZEYİ yöntemi çağrılıyor  
 <xref:System.IObserver%601.OnError%2A> yöntemi, observers için <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> yöntemine benzer bir bilgilendirici ileti olarak hazırlanmıştır. Ancak <xref:System.IObserver%601.OnNext%2A> yöntemi, geçerli veya güncelleştirilmiş verilerle bir gözlemci sağlamak üzere tasarlanmıştır, ancak <xref:System.IObserver%601.OnError%2A> yöntemi sağlayıcının geçerli verileri sağlayamayacağı konusunda bir şekilde tasarlanmıştır.  
  
 Sağlayıcı, özel durumları işlerken ve <xref:System.IObserver%601.OnError%2A> yöntemi çağırırken bu en iyi yöntemleri izlemelidir:  
  
- Belirli gereksinimlere sahipse sağlayıcı kendi özel durumlarını işlemelidir.  
  
- Sağlayıcı, gözlemcilerin 'ın özel durumları belirli bir şekilde işlemesini beklememelidir veya gerektirmemelidir.  
  
- Sağlayıcı, güncelleştirme sağlama yeteneğini karşılayan bir özel durum işlediğinde <xref:System.IObserver%601.OnError%2A> yöntemini çağırmalıdır. Bu tür özel durumlarla ilgili bilgiler gözlemciye geçirilebilir. Diğer durumlarda, bir özel durumun gözlemcilerin 'a bildirimde olması gerekmez.  
  
 Sağlayıcı <xref:System.IObserver%601.OnError%2A> veya <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> yöntemini çağırdığında, daha fazla bildirim olmaması gerekir ve sağlayıcı observers aboneliğini iptal edebilir. Ancak, gözlemcilerin Ayrıca, bir <xref:System.IObserver%601.OnError%2A> veya <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> bildirimi aldıktan sonra da dahil olmak üzere herhangi bir zamanda kendi aboneliklerini da kaldırabilirsiniz. Gözlemci tasarım deseninin, sağlayıcının veya gözlemci aboneliği kaldırma işleminden sorumlu olup olmadığı görünmez; Bu nedenle, her ikisinin de aboneliği kaldırma girişiminde bulunduğu bir olasılık vardır. Genellikle, gözlemcilerin aboneliği kaldırıldığında bir abone koleksiyonundan kaldırılır. Tek iş parçacıklı bir uygulamada, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulama bir nesne başvurusunun geçerli olduğundan ve nesnenin kaldırmayı denemeden önce aboneler koleksiyonunun bir üyesi olduğundan emin olmalıdır. Çok iş parçacıklı bir uygulamada, <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> nesnesi gibi iş parçacığı güvenli bir koleksiyon nesnesi kullanılmalıdır.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>Gözlemci--HataDurumunda yöntemi uygulama  
 Bir gözlemci bir sağlayıcıdan bir hata bildirimi aldığında, gözlemci özel durumu bilgilendirici olarak kabul etmelidir ve belirli bir eylemi gerçekleştirmek için gerekli değildir.  
  
 Gözlemci, bir sağlayıcıdan <xref:System.IObserver%601.OnError%2A> yöntem çağrısına yanıt vermediğinde bu en iyi yöntemleri izlemelidir:  
  
- Gözlemci, <xref:System.IObserver%601.OnNext%2A> veya <xref:System.IObserver%601.OnError%2A>gibi arabirim uygulamalarından özel durumlar oluşturmaz. Ancak, gözlemci özel durum fırlatsam, bu özel durumların işlenmemiş olması beklenir.  
  
- Çağrı yığınını korumak için, <xref:System.IObserver%601.OnError%2A> yöntemine geçirilmiş bir <xref:System.Exception> nesnesi oluşturması için bir gözlemci, özel durumu oluşturmadan önce sarmalıdır. Bu amaçla bir standart özel durum nesnesi kullanılmalıdır.  
  
## <a name="additional-best-practices"></a>Diğer En Iyi Yöntemler  
 <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> yönteminde kaydı kaldırılmaya çalışılması null başvuruya neden olabilir. Bu nedenle, bu uygulamalardan kaçınmanızı öneririz.  
  
 Birden çok sağlayıcıya bir gözlemci iliştirmek mümkün olsa da, önerilen model yalnızca bir <xref:System.IObservable%601> örneğine <xref:System.IObserver%601> bir örnek eklemektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gözlemci Tasarım Deseni](../../../docs/standard/events/observer-design-pattern.md)
- [Nasıl yapılır: Gözlemci Uygulama](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Nasıl yapılır: Sağlayıcıyı Uygulama](../../../docs/standard/events/how-to-implement-a-provider.md)
