---
title: Gözlemci Tasarım Deseni En İyi Yöntemleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- observer design pattern [.NET Framework], best practices
- best practices [.NET Framework], observer design pattern
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 839772fac51ab006d03875920360824a73b033e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770402"
---
# <a name="observer-design-pattern-best-practices"></a>Gözlemci Tasarım Deseni En İyi Yöntemleri
Gözlemci tasarım deseni, .NET Framework'teki arabirimleri kümesi uygulanır. <xref:System.IObservable%601?displayProperty=nameWithType> Arabirimi temsil eder, aynı zamanda sağlamaktan sorumlu olan veri sağlayıcısı bir <xref:System.IDisposable> bildirim aboneliği gözlemciler sağlayan uygulama. <xref:System.IObserver%601?displayProperty=nameWithType> Arabiriminin gözlemcisi temsil eder. Bu konu, geliştiricilerin bu arabirimleri kullanarak gözlemci tasarım deseni uygularken izlemelidir en iyi uygulamaları açıklar.  
  
## <a name="threading"></a>İş Parçacığı Oluşturma  
 Genellikle, bir sağlayıcıyı uygular <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> belirli bir gözlemci bazı koleksiyon nesnesi ve tarafından temsil edilen bir abone listesine ekleyerek yöntemini uygulayan <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> belirli bir gözlemci abone listeden kaldırma yöntemi. Gözlemci herhangi bir zamanda bu yöntemleri çağırabilir. Ayrıca, çünkü sağlayıcı/gözlemci sözleşme belirttiğinde sorumlu sonra aboneliği için <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> geri çağırma yöntemi, sağlayıcı ve gözlemci hem de çalışın aynı üye listesinden kaldırır. Bu olasılığı nedeniyle hem <xref:System.IObservable%601.Subscribe%2A> ve <xref:System.IDisposable.Dispose%2A> yöntemleri, iş parçacığı açısından güvenli olmalıdır. Bu genellikle, kullanılmasına bir [eşzamanlı koleksiyon](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md) ya da bir kilit. İş parçacığı güvenli olmayan uygulamaları, onlara açıkça belgelemeniz gerekir.  
  
 Ek konusunda garanti sağlayıcısı/gözlemci sözleşme üzerinde bir katman belirtilmesi gerekir. Bunlar gözlemci sözleşmeyle ilgili kullanıcı Karışıklığı önlemek için ek gereksinimler dayatır olduğunda uygulayıcılar açıkça duyurmak.  
  
## <a name="handling-exceptions"></a>Özel Durumları İşleme  
 Arasındaki bu sıkı bağ nedeniyle bir veri sağlayıcısı ve gözlemci, gözlemci tasarım deseni durumlar bilgilendirici olacak şekilde tasarlanmıştır. Bu sağlayıcıları ve gözlemciler gözlemci tasarım deseni özel durumların nasıl işleneceğini etkiler.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Sağlayıcısı--OnError yöntemi çağırma  
 <xref:System.IObserver%601.OnError%2A> Yöntemi amaçlanmıştır gözlemciler, bir bilgilendirme iletisi olarak çok gibi <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> yöntemi. Ancak, <xref:System.IObserver%601.OnNext%2A> yöntemi geçerli ya da güncelleştirilen verilerle bir gözlemci sağlamak için tasarlanmıştır ancak <xref:System.IObserver%601.OnError%2A> yöntemi sağlayıcısı geçerli verileri sağlayamadı olduğunu göstermek için tasarlanmıştır.  
  
 Sağlayıcı özel durumları işleme olduğunda bu en iyi uygulamaları izlemelisiniz ve çağırma <xref:System.IObserver%601.OnError%2A> yöntemi:  
  
- Belirli gereksinimlere sahipse, sağlayıcı kendi özel durumlarını işlemelidir.  
  
- Sağlayıcı beklemez veya gözlemciler herhangi belirli bir şekilde özel durumları işlemek gerektiren.  
  
- Sağlayıcı çağırmalıdır <xref:System.IObserver%601.OnError%2A> güncelleştirmeleri sağlamak üzere güncelleyebileceği etkilediğinde bir özel durum işleme yöntemi. Bu tür özel durumların bilgi gözlemci geçirilebilir. Diğer durumlarda, bir özel durumun gözlemciler bildirmek için gerek yoktur.  
  
 Bir kez sağlayıcısı çağrıları <xref:System.IObserver%601.OnError%2A> veya <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> yöntemi, daha fazla bildirim olmalıdır ve sağlayıcı kendi gözlemciler abonelikten çıkabilirsiniz. Ancak gözlemciler ayrıca kendilerini önce ve sonra aldıkları dahil olmak üzere istediğiniz zaman abonelikten çıkabilirsiniz bir <xref:System.IObserver%601.OnError%2A> veya <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> bildirim. Gözlemci tasarım deseni sağlayıcı veya gözlemci aboneliği için sorumlu olduğunu dikte etmez; Bu nedenle, bir olasılık yoktur hem iptal etme deneyebilir. Genellikle, gözlemciler aboneliğinizi kaldırdığınızda, abonelerin koleksiyondan kaldırılır. Tek iş parçacıklı bir uygulamada <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulama bir nesne başvurusu geçerli olduğunu ve nesne Kaldırmaya çalışmadan önce aboneleri koleksiyonunun bir üyesi olduğundan emin olun. Çok iş parçacıklı bir uygulamada, bir iş parçacığı koleksiyon nesnesi gibi bir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> nesne, kullanılmalıdır.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>Gözlemci--OnError yöntemi uygulama  
 Gözlemci sağlayıcıdan bir hata bildirimi aldığında gözlemci özel bilgi olarak kabul etmelidir ve herhangi bir işlem yapmanız için gerekli olmamalıdır.  
  
 Gözlemci yanıt vermek bu en iyi uygulamaları izlemelisiniz bir <xref:System.IObserver%601.OnError%2A> yöntem çağrısı bir sağlayıcısı:  
  
- Gözlemci onun arabirim uygulamaları özel durumlar gibi oluşturmamalıdır <xref:System.IObserver%601.OnNext%2A> veya <xref:System.IObserver%601.OnError%2A>. Ancak, gözlemci özel durum oluşturmaz, bu özel durum işlenmemiş gitmek için beklemeniz gerekir.  
  
- Throw isteyen bir gözlemci çağrı yığını korumak için bir <xref:System.Exception> geçildi nesne kendi <xref:System.IObserver%601.OnError%2A> yöntemi özel durum, özel durum atma önce kaydırma. Bir standart özel durum nesnesi, bu amaç için kullanılmalıdır.  
  
## <a name="additional-best-practices"></a>Diğer en iyi yöntemler  
 İçinde kaydını çalışılıyor <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> yöntemi null başvuru neden olabilir. Bu nedenle, bu yöntem kaçınmanızı öneririz.  
  
 Birden çok sağlayıcı için bir gözlemci eklemek mümkün olsa da, önerilen Düzen eklemektir bir <xref:System.IObserver%601> yalnızca bir örneğine <xref:System.IObservable%601> örneği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gözlemci Tasarım Deseni](../../../docs/standard/events/observer-design-pattern.md)
- [Nasıl yapılır: Gözlemci uygulama](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Nasıl yapılır: Sağlayıcıyı uygulama](../../../docs/standard/events/how-to-implement-a-provider.md)
