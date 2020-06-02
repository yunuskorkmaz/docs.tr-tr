---
title: Gözlemci Tasarım Deseni En İyi Yöntemleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- observer design pattern [.NET Framework], best practices
- best practices [.NET Framework], observer design pattern
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
ms.openlocfilehash: b4f8e568dcb6790dac1dc8fc5c969d6fa1367c4e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288465"
---
# <a name="observer-design-pattern-best-practices"></a>Gözlemci Tasarım Deseni En İyi Yöntemleri
.NET Framework, gözlemci tasarım deseninin bir dizi arabirim olarak uygulanması gerekir. <xref:System.IObservable%601?displayProperty=nameWithType>Arabirim, <xref:System.IDisposable> gözlemcilerin 'ın bildirimlerden aboneliklerini kaldırma olanağı sağlayan bir uygulama sağlamaktan de sorumlu olan veri sağlayıcısını temsil eder. <xref:System.IObserver%601?displayProperty=nameWithType>Arabirim, gözlemciyi temsil eder. Bu konuda, bu arabirimleri kullanarak gözlemci tasarım modelini uygularken geliştiricilerin izlenmesi gereken en iyi uygulamalar açıklanmaktadır.  
  
## <a name="threading"></a>İş Parçacığı Oluşturma  
 Genellikle, bir sağlayıcı, <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> bazı koleksiyon nesneleri tarafından temsil edilen bir abone listesine belirli bir gözlemci ekleyerek yöntemini uygular ve <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> abone listesinden belirli bir gözlemci kaldırarak yöntemi uygular. Bir gözlemci, bu yöntemleri dilediğiniz zaman çağırabilir. Ayrıca, sağlayıcı/gözlemci, geri çağırma yönteminden sonra aboneliği kaldırmaktan sorumlu kişiyi belirtmediğinden <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> , sağlayıcı ve gözlemci aynı üyeyi listeden kaldırmayı deneyebilir. Bu olasılığa göre, ve yöntemlerinin her ikisi de <xref:System.IObservable%601.Subscribe%2A> <xref:System.IDisposable.Dispose%2A> iş parçacığı açısından güvenli olmalıdır. Genellikle, bu, [eş zamanlı bir koleksiyonun](../parallel-programming/data-structures-for-parallel-programming.md) veya kilidin kullanılmasını içerir. İş parçacığı açısından güvenli olmayan uygulamalar, açık bir şekilde belgelemelidir.  
  
 Ek garantiler sağlayıcının/gözlemci sözleşmesinin en üstündeki bir katmanda belirtilmelidir. Uygulayıcılar, gözlemciye ilişkin Kullanıcı karışıklığına engel olmak için ek gereksinimler gerçekleştirdiklerinde açıkça bir çağrı çağırmalıdır.  
  
## <a name="handling-exceptions"></a>Özel Durumları İşleme  
 Bir veri sağlayıcısı ve gözlemci arasındaki gevşek bağlantısı nedeniyle, gözlemci tasarım düzenindeki özel durumlar bilgilendirme amaçlıdır. Bu, sağlayıcının ve gözlemcilerin 'ın gözlemci tasarım modelinde özel durumları nasıl işleyeceğini etkiler.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Sağlayıcı--HATADÜZEYİ yöntemi çağrılıyor  
 <xref:System.IObserver%601.OnError%2A>Yöntemi, observers 'e, yöntemi gibi bir bilgi iletisi olarak tasarlanmıştır <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> . Ancak, <xref:System.IObserver%601.OnNext%2A> yöntemi geçerli veya güncelleştirilmiş verilerle bir gözlemci sağlamak üzere tasarlanmıştır, ancak <xref:System.IObserver%601.OnError%2A> yöntem sağlayıcının geçerli verileri sağlayamayacağı olduğunu göstermek için tasarlanmıştır.  
  
 Sağlayıcı, özel durumları işlerken ve yöntemi çağırırken bu en iyi yöntemleri izlemelidir <xref:System.IObserver%601.OnError%2A> :  
  
- Belirli gereksinimlere sahipse sağlayıcı kendi özel durumlarını işlemelidir.  
  
- Sağlayıcı, gözlemcilerin 'ın özel durumları belirli bir şekilde işlemesini beklememelidir veya gerektirmemelidir.  
  
- Sağlayıcı, <xref:System.IObserver%601.OnError%2A> güncelleştirme sağlama yeteneğini karşılayan bir özel durum işlediğinde yöntemi çağırmalıdır. Bu tür özel durumlarla ilgili bilgiler gözlemciye geçirilebilir. Diğer durumlarda, bir özel durumun gözlemcilerin 'a bildirimde olması gerekmez.  
  
 Sağlayıcı <xref:System.IObserver%601.OnError%2A> veya <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> yöntemini çağırdığında, başka bildirim olmaması gerekir ve sağlayıcı observers aboneliğini iptal edebilir. Ancak, gözlemcilerin, bir veya bildirimi aldıktan sonra da dahil olmak üzere herhangi bir zamanda kendi aboneliklerini da kaldırabilirsiniz <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> . Gözlemci tasarım deseninin, sağlayıcının veya gözlemci aboneliği kaldırma işleminden sorumlu olup olmadığı görünmez; Bu nedenle, her ikisinin de aboneliği kaldırma girişiminde bulunduğu bir olasılık vardır. Genellikle, gözlemcilerin aboneliği kaldırıldığında bir abone koleksiyonundan kaldırılır. Tek iş parçacıklı bir uygulamada, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulama bir nesne başvurusunun geçerli olduğundan ve nesnenin kaldırmayı denemeden önce aboneler koleksiyonunun bir üyesi olduğundan emin olmalıdır. Çok iş parçacıklı bir uygulamada, nesne gibi bir iş parçacığı güvenli koleksiyon nesnesi <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> kullanılmalıdır.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>Gözlemci--HataDurumunda yöntemi uygulama  
 Bir gözlemci bir sağlayıcıdan bir hata bildirimi aldığında, gözlemci özel durumu bilgilendirici olarak kabul etmelidir ve belirli bir eylemi gerçekleştirmek için gerekli değildir.  
  
 Gözlemci <xref:System.IObserver%601.OnError%2A> bir sağlayıcıdan gelen yöntem çağrısına yanıt vermediğinde, bu en iyi yöntemleri izlemelidir:  
  
- Gözlemci, veya gibi arabirim uygulamalarından özel durumlar oluşturmaz <xref:System.IObserver%601.OnNext%2A> <xref:System.IObserver%601.OnError%2A> . Ancak, gözlemci özel durum fırlatsam, bu özel durumların işlenmemiş olması beklenir.  
  
- Çağrı yığınını korumak için, metoduna geçirilen bir nesne oluşturmak isteyen bir gözlemci, <xref:System.Exception> <xref:System.IObserver%601.OnError%2A> özel durumu oluşturmadan önce sarmalıdır. Bu amaçla bir standart özel durum nesnesi kullanılmalıdır.  
  
## <a name="additional-best-practices"></a>Diğer En Iyi Yöntemler  
 Yönteminde kaydı kaldırılmaya çalışılması <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> null başvuruya neden olabilir. Bu nedenle, bu uygulamalardan kaçınmanızı öneririz.  
  
 Birden çok sağlayıcıya bir gözlemci iliştirmek mümkün olsa da, önerilen model <xref:System.IObserver%601> yalnızca bir örneğe örnek eklemektir <xref:System.IObservable%601> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gözlemci tasarım kalıbı](observer-design-pattern.md)
- [Nasıl yapılır: gözlemci uygulama](how-to-implement-an-observer.md)
- [Nasıl yapılır: sağlayıcı uygulama](how-to-implement-a-provider.md)
