---
title: Gözlemci Tasarım Deseni En İyi Yöntemleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- observer design pattern [.NET Framework], best practices
- best practices [.NET Framework], observer design pattern
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
ms.openlocfilehash: 2da29e0baf429142707d0ddd39b1a11c13a17a90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141543"
---
# <a name="observer-design-pattern-best-practices"></a>Gözlemci Tasarım Deseni En İyi Yöntemleri
.NET Framework'de gözlemci tasarım deseni bir arabirim kümesi olarak uygulanır. Arabirim, <xref:System.IObservable%601?displayProperty=nameWithType> gözlemcilerin bildirimlerden aboneliğini iptal <xref:System.IDisposable> etmelerine olanak tanıyan bir uygulama sağlamaktan da sorumlu olan veri sağlayıcısını temsil eder. Arayüz <xref:System.IObserver%601?displayProperty=nameWithType> gözlemciyi temsil eder. Bu konu, bu arabirimleri kullanarak gözlemci tasarım deseni uygularken geliştiricilerin izlemesi gereken en iyi uygulamaları açıklar.  
  
## <a name="threading"></a>İş Parçacığı Oluşturma  
 Genellikle, bir sağlayıcı, <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> belirli bir koleksiyon nesnesi tarafından temsil edilen bir abone listesine belirli <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> bir gözlemci ekleyerek yöntemi uygular ve belirli bir gözlemciyi abone listesinden kaldırarak yöntemi uygular. Bir gözlemci bu yöntemleri istediği zaman arayabilir. Buna ek olarak, sağlayıcı/gözlemci sözleşmesi <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> geri arama yönteminden sonra aboneliği niçin sorumlu olduğunu belirtmediği için, sağlayıcı ve gözlemci aynı üyeyi listeden çıkarmaya çalışabilir. Bu olasılık nedeniyle, <xref:System.IObservable%601.Subscribe%2A> hem <xref:System.IDisposable.Dispose%2A> yöntem hem de iş parçacığı güvenli olmalıdır. Genellikle, bu eşzamanlı bir [koleksiyon](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md) veya kilit kullanarak içerir. İş parçacığı güvenli olmayan uygulamalar, bunların güvenli olmadığını açıkça belgelemelidir.  
  
 Herhangi bir ek garanti sağlayıcı / gözlemci sözleşme üstüne bir katman halinde belirtilmelidir. Uygulayıcılar, gözlemci sözleşmesi yle ilgili kullanıcı karışıklığını önlemek için ek gereksinimler dayattığında açıkça çağrılmalıdır.  
  
## <a name="handling-exceptions"></a>Özel Durumları İşleme  
 Bir veri sağlayıcısı ve bir gözlemci arasındaki gevşek bağlantı nedeniyle, gözlemci tasarım desenindeki istisnaların bilgilendirici olması amaçlanmıştır. Bu, sağlayıcıların ve gözlemcilerin gözlemci tasarım modelindeki özel durumları nasıl ele alacaklarını etkiler.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Sağlayıcı -- OnError Yöntemini Çağırma  
 Yöntem, <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> tıpkı yöntem gibi gözlemcilere bir bilgilendirme mesajı olarak tasarlanmıştır. Ancak, <xref:System.IObserver%601.OnNext%2A> yöntem bir gözlemciye geçerli veya güncelleştirilmiş verileri <xref:System.IObserver%601.OnError%2A> sağlamak üzere tasarlanmıştır, ancak yöntem sağlayıcının geçerli verileri sağlayamadığını belirtmek için tasarlanmıştır.  
  
 Sağlayıcı, özel durumları işlerken ve <xref:System.IObserver%601.OnError%2A> yöntemi ararken aşağıdaki en iyi uygulamaları izlemelidir:  
  
- Sağlayıcı, belirli gereksinimleri varsa kendi özel durumlarını ele almalıdır.  
  
- Sağlayıcı, gözlemcilerin özel durumları belirli bir şekilde ele almalarını beklememeli veya gerektirmemelidir.  
  
- Sağlayıcı, güncelleştirmeleri <xref:System.IObserver%601.OnError%2A> sağlama yeteneğini tehlikeye atan bir özel durum işlediğinde yöntemi aramalıdır. Bu tür istisnalar hakkındaki bilgiler gözlemciye iletilebilir. Diğer durumlarda, gözlemcilere bir istisna bildiriminde bulunmanız gerekmez.  
  
 Sağlayıcı <xref:System.IObserver%601.OnError%2A> veya <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> yöntemi çağırdıktan sonra, başka bildirim olmamalıdır ve sağlayıcı gözlemcilerinin aboneliğini iptal edebilir. Ancak, gözlemciler bir bildirim almadan <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> önce ve sonra da dahil olmak üzere, istedikleri zaman aboneliklerini iptal edebilirler. Gözlemci tasarım deseni, sağlayıcının veya gözlemcinin aboneliğin sorumlusunun olup olmadığını belirlemez; bu nedenle, her ikisi nin de aboneliğini iptal etmeye çalışabilme olasılığı vardır. Genellikle, gözlemciler aboneliğini iptal ettiklerinde, abone koleksiyonundan kaldırılırlar. Tek iş parçacığı uygulamasında, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulama nesne başvurusunun geçerli olduğundan ve nesnenin kaldırmayı denemeden önce abone koleksiyonunun bir üyesi olduğundan emin olmalıdır. Çok iş parçacığı uygulamasında, nesne gibi iş parçacığı <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> güvenli bir koleksiyon nesnesi kullanılmalıdır.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>Gözlemci -- OnError Yönteminin Uygulanması  
 Bir gözlemci bir sağlayıcıdan hata bildirimi aldığında, gözlemci özel durumu bilgilendirici olarak ele almalıdır ve belirli bir eylemde bulunmaları gerekmemelidir.  
  
 Gözlemci, bir sağlayıcıdan gelen bir <xref:System.IObserver%601.OnError%2A> yöntem çağrısına yanıt verirken aşağıdaki en iyi uygulamaları izlemelidir:  
  
- Gözlemci, arayüz uygulamalarından istisnalar atmamalıdır, <xref:System.IObserver%601.OnNext%2A> örneğin. <xref:System.IObserver%601.OnError%2A> Ancak, gözlemci özel durumlar atarsa, bu özel durumların işlenmemiş olmasını beklemelidir.  
  
- Çağrı yığınını korumak için, <xref:System.Exception> <xref:System.IObserver%601.OnError%2A> yöntemine geçirilen bir nesneyi atmak isteyen bir gözlemci, onu atmadan önce özel durumu saran bir gözlemci olmalıdır. Bu amaç için standart bir özel durum nesnesi kullanılmalıdır.  
  
## <a name="additional-best-practices"></a>Ek En İyi Uygulamalar  
 <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> Yöntemde kaydını kaldırmaya çalışmak geçersiz bir başvuruyla sonuçlanabilir. Bu nedenle, bu uygulamadan kaçınmanızı öneririz.  
  
 Birden çok sağlayıcıya gözlemci eklemek mümkün olsa da, önerilen <xref:System.IObserver%601> desen yalnızca <xref:System.IObservable%601> bir örneğe bir örnek eklemektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gözlemci Tasarım Deseni](../../../docs/standard/events/observer-design-pattern.md)
- [Nasıl yapılır: Gözlemci Uygulama](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Nasıl yapılır: Sağlayıcıyı Uygulama](../../../docs/standard/events/how-to-implement-a-provider.md)
