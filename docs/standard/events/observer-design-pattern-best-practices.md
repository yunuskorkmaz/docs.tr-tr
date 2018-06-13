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
ms.openlocfilehash: 030b62688ba8985a2659769fe20b6ae527471df5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579398"
---
# <a name="observer-design-pattern-best-practices"></a>Gözlemci Tasarım Deseni En İyi Yöntemleri
.NET Framework'teki gözlemci tasarım deseni arabirimleri kümesi uygulanır. <xref:System.IObservable%601?displayProperty=nameWithType> Arabirimi temsil eder, aynı zamanda sağlamaktan sorumludur veri sağlayıcısı bir <xref:System.IDisposable> bildirim aboneliği gözlemcilerin sağlayan uygulama. <xref:System.IObserver%601?displayProperty=nameWithType> Arabirimi gözlemci temsil eder. Bu konu, geliştiriciler bu arabirimleri kullanarak gözlemci tasarım deseni uygularken izlemeniz gereken en iyi uygulamaları açıklar.  
  
## <a name="threading"></a>İş Parçacığı Oluşturma  
 Genellikle, bir sağlayıcı uygulayan <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> belirli bir gözlemci bazı koleksiyon nesnesi ve onu tarafından temsil edilen bir abone listesine ekleyerek yöntemi uygulayan <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> belirli bir gözlemci abone listesinden kaldırarak yöntemi. Bir gözlemci bu yöntemlerin herhangi bir zamanda çağırabilirsiniz. Ayrıca, sağlayıcı/gözlemci sözleşme belirtmediği çünkü sorumlu sonra aboneliği için <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> geri çağırma yöntemi, sağlayıcı ve gözlemci her ikisi de deneyebilir aynı üye listesinden kaldırmak. Bu olasılığı nedeniyle hem <xref:System.IObservable%601.Subscribe%2A> ve <xref:System.IDisposable.Dispose%2A> yöntemleri iş parçacığı açısından güvenli olması gerekir. Bu genellikle, kullanılmasına bir [eşzamanlı koleksiyonu](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md) ya da bir kilit. İş parçacığı güvenli olmayan uygulamaları, onlara açıkça belgelemeniz gerekir.  
  
 Ek garanti sağlayıcı/gözlemci sözleşme üstünde katmanda belirtilmesi gerekir. Bunlar gözlemci sözleşme hakkında kullanıcı Karışıklığı önlemek için ek gereksinimleri olduğunda Implementers açıkça duyurmak.  
  
## <a name="handling-exceptions"></a>Özel Durumları İşleme  
 Veri sağlayıcı ve bir gözlemci arasında gevşek bağlantı nedeniyle gözlemci tasarım deseni durumlar bilgilendirme olacak şekilde tasarlanmıştır. Bu sağlayıcıları ve gözlemcilerin gözlemci tasarım deseni özel durumları nasıl işleneceğini etkiler.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Sağlayıcısı--OnError yöntemi çağırma  
 <xref:System.IObserver%601.OnError%2A> Yöntemi amaçlanmıştır gözlemcilerin, bir bilgilendirme iletisi olarak çok gibi <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> yöntemi. Ancak, <xref:System.IObserver%601.OnNext%2A> yöntemi geçerli ya da güncelleştirilmiş verilerle bir gözlemci sağlamak için tasarlanmıştır ancak <xref:System.IObserver%601.OnError%2A> yöntemi sağlayıcı geçerli veri sağlayamaz olduğunu göstermek için tasarlanmıştır.  
  
 Sağlayıcı özel durumları işleme olduğunda bu en iyi uygulamaları izlemelisiniz ve çağırma <xref:System.IObserver%601.OnError%2A> yöntemi:  
  
-   Belirli gereksinimlere varsa, sağlayıcı kendi özel durumlarını işlemelidir.  
  
-   Sağlayıcı beklediğiniz veya gözlemcilerin belirli herhangi bir yolla özel durumları işleme gerektiren gerekir.  
  
-   Sağlayıcı çağırmalıdır <xref:System.IObserver%601.OnError%2A> güncelleştirmeleri sağlama yeteneğini etkilediğinde bir özel durum işleme yöntemi. Bu tür özel durumlar hakkında bilgi gözlemci geçirilebilir. Diğer durumlarda, bir özel durum gözlemcilerin bildirmek için gerek yoktur.  
  
 Bir kez sağlayıcısı çağrıları <xref:System.IObserver%601.OnError%2A> veya <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> yöntemi, başka hiçbir bildirim olmalıdır ve sağlayıcı kendi gözlemcilerin aboneliğinizi iptal edebilirsiniz. Ancak, gözlemcilerin de kendilerini önce ve sonra aldıkları her ikisi de dahil, herhangi bir zamanda sona erdirebilirsiniz bir <xref:System.IObserver%601.OnError%2A> veya <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> bildirim. Gözlemci tasarım deseni sağlayıcı veya gözlemci aboneliği için sorumlu olduğunu dikte etmez; Bu nedenle olasılığı yok her ikisi de aboneliğinizi iptal etmek deneyebilir. Genellikle, gözlemcilerin aboneliğinizi kaldırdığınızda, aboneler koleksiyondan kaldırılır. Bir tek iş parçacıklı uygulamada <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulama nesne başvurusu geçerli olduğunu ve nesne Kaldırmaya çalışmadan önce aboneleri koleksiyonun üyesi olduğundan emin olun. Birden çok iş parçacıklı bir uygulamada bir iş parçacığı koleksiyonunun nesnesi gibi bir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> nesne, kullanılmalıdır.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>--Gözlemci OnError yöntemi uygulama  
 Bir gözlemci bir sağlayıcıdan bir hata bildirimi aldığında, gözlemci özel bilgi olarak değerlendirmeniz gerekir ve herhangi bir işlem yapması için gerekli olmamalıdır.  
  
 Gözlemci için yanıt verirken bu en iyi uygulamaları izlemelisiniz bir <xref:System.IObserver%601.OnError%2A> yöntem çağrısı bir sağlayıcıdan:  
  
-   Gözlemci onun arabirim uygulamaları özel durumlar gibi oluşturmamalıdır <xref:System.IObserver%601.OnNext%2A> veya <xref:System.IObserver%601.OnError%2A>. Ancak, gözlemci özel durumlar oluşturma, işlenmemiş gitmek için bu özel durumlar beklemelisiniz.  
  
-   Çağrı yığını, throw istediği bir gözlemci korumak için bir <xref:System.Exception> geçirilmedi nesne kendi <xref:System.IObserver%601.OnError%2A> yöntemi, atma önce özel durum sarmalamak. Standart özel durum nesnesi bu amaç için kullanılmalıdır.  
  
## <a name="additional-best-practices"></a>Diğer en iyi yöntemler  
 İçinde kaydı çalışılıyor <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> yöntemi null başvuru neden olabilir. Bu nedenle, bu yöntem kaçının öneririz.  
  
 Bir gözlemci birden çok sağlayıcı eklemek mümkün olsa da, önerilen desenini eklemektir bir <xref:System.IObserver%601> yalnızca bir örneğine <xref:System.IObservable%601> örneği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gözlemci Tasarım Deseni](../../../docs/standard/events/observer-design-pattern.md)  
 [Nasıl yapılır: Gözlemci Uygulama](../../../docs/standard/events/how-to-implement-an-observer.md)  
 [Nasıl yapılır: Sağlayıcıyı Uygulama](../../../docs/standard/events/how-to-implement-a-provider.md)
