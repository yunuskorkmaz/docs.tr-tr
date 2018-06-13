---
title: Özel Durum İşleme (Görev Paralel Kitaplığı)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16ab0b8967ac394540f201fcc9098024faaccaa7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591302"
---
# <a name="exception-handling-task-parallel-library"></a>Özel Durum İşleme (Görev Paralel Kitaplığı)
İçinde bir görevin çalıştığı kullanıcı kodu tarafından oluşturulan işlenmemiş özel durumlardan geri çağırma akışa dışında bu konunun ilerleyen bölümlerinde açıklanan belirli senaryolarda yayılır. Özel durumlar statik birini kullandığınızda yayılır veya örnek <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> veya <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` yöntemleri ve işlemek bunları çağrısında kapsayan tarafından bir `try` / `catch` deyimi. Ekli alt görevler üst bir görevdir ya da birden çok görevlerde bekleyen varsa, birden çok özel durum.  
  
 Tüm özel durumları çağrı yapan iş parçacığına geri yaymak için, Görev altyapısı onları bir <xref:System.AggregateException> örneği içine sarar. <xref:System.AggregateException> Özel durum olan bir <xref:System.AggregateException.InnerExceptions%2A> oluşturulan özgün durumlar incelemek için numaralandırılmış ve her biri ele (veya değil tanıtıcı) özelliği ayrı ayrı. Kullanarak özgün özel durumlar işleyebilir <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemi.  
  
 Yalnızca bir özel durum olsa bile, yine de kaydırılan bir <xref:System.AggregateException> aşağıdaki örnekte gösterildiği gibi bir özel durum.  
  
 [!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
 [!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]  
  
 Yalnızca <xref:System.AggregateException> öğesini yakalayarak ve dahili özel durumların hiç birini gözlemeyerek bir işlenmeyen özel durumu önleyebilirsiniz. Ancak, temel yakalama için benzer olduğundan, bunu yapmamanızı öneririz <xref:System.Exception> paralel olmayan senaryolarda türü. Bir özel durumu yakalayıp bu durumdan kurtulmak için belirli eylemleri yapmazsanız uygulamanız belirsiz bir durumda kalabilir.  
  
 Çağrılacak istemiyorsanız <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> veya <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` bir görevin tamamlanmasını bekleme yöntemi de alabilirsiniz <xref:System.AggregateException> görevin öğesinden özel durum <xref:System.Threading.Tasks.Task.Exception%2A> özelliği, aşağıdaki örnekte gösterildiği gibi. Daha fazla bilgi için bkz: [Task.Exception özelliğini kullanarak özel durumlar Gözlemleme](#ExceptionProp) bölümüne bakın.  
  
 [!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
 [!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]  
  
 Bir özel durum ya da erişim yayan bir görev bekleme durumunda kendi <xref:System.Threading.Tasks.Task.Exception%2A> özelliği, özel görev çöpünün toplanma olduğunda .NET özel durumu ilkesine göre ilerletilen.  
  
 Özel durumlar katılma iş parçacığı geri Kabarcık izin verildiğinde bir görev özel durum oluşturulduktan sonra bazı öğeler işlemeye devam edebilir mümkündür.  
  
> [!NOTE]
>  "Sadece kendi kodumu" etkinleştirildiğinde, Visual Studio bazı durumlarda, özel durum oluşturur satır başı ve "özel durum kullanıcı kodu tarafından işlenmiyor." diyen bir hata iletisi görüntülenir Bu hata zararsız kaynaklanır. F5 tuşuna basarak devam edebilir ve bu örneklerde gösterilen özel durum işleme davranışını görebilirsiniz. Visual Studio ilk hatada kesilmesini önlemek için yalnızca işaretini **sadece kendi kodumu etkinleştir** altındaki onay kutusunu **Araçlar, seçenekleri, hata ayıklama, genel**.  
  
## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Eklenen Alt Görevler ve İç İçe Geçmiş AggregateException Öğeleri  
 Bir göreve ekli, özel durum oluşturan bir alt görev varsa, o özel durum üst göreve yayılmadan önce bir <xref:System.AggregateException> öğesi içine sarmalanır ve bu da o özel durumu çağıran iş parçacığına geri yaymadan önce kendi <xref:System.AggregateException> öğesine sarmalar. Böyle durumlarda, <xref:System.AggregateException.InnerExceptions%2A> özelliği <xref:System.AggregateException> sırasında yakalanan özel durum <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> veya <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` veya <xref:System.Threading.Tasks.Task.WaitAny%2A> veya <xref:System.Threading.Tasks.Task.WaitAll%2A> yöntemini içeren bir veya daha fazla <xref:System.AggregateException> örnekleri değil hatasına neden oldu özgün özel durumlar. Üzerinden yinelemek zorunda kalmamak için iç içe geçmiş <xref:System.AggregateException> kullanabileceğiniz özel durumlar, <xref:System.AggregateException.Flatten%2A> tümünü kaldırmak için yöntem iç içe <xref:System.AggregateException> özel durumlar, böylece <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> özelliği, özgün özel durumları içerir. Aşağıdaki örnekte, iç içe geçmiş <xref:System.AggregateException> örnekleri yalnızca tek bir döngüde düzleştirilip işlenir.  
  
 [!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
 [!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]  
  
 Aynı zamanda <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> birden çok iç özel durum yeniden oluşturulması için yöntemi <xref:System.AggregateException> tek bir birden çok görevi tarafından oluşturulan örnekleri <xref:System.AggregateException> örneği, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
 [!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]  
  
## <a name="exceptions-from-detached-child-tasks"></a>Ayrılmış Alt Görevlerden Gelen Özel Durumlar  
 Varsayılan olarak, özel durumlar ayrılmış olarak oluşturulur. Ayrılmış görevlerde oluşturulan özel durumlar bir üst görev içinde işlenmeli ve yeniden harekete geçirilmelidir; bu özel durumlar eklenen alt görevlerde olduğu şekilde çağıran iş parçacığına geri yayılmaz. En üstteki üst el ile bir özel durum olarak sarmalamak neden için ayrılmış bir alt gelen yeniden oluşturulması bir <xref:System.AggregateException> çağıran iş parçacığı geri yayıldığı.  
  
 [!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
 [!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]  
  
 Bir alt görevdeki özel durumu gözlemek için bir devamlılık kullanıyor olsanız bile, özel durum yine de üst görev tarafından gözlenmelidir.  
  
## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Birlikte İptal Olduğunu Belirten Özel Durumlar  
 Bir görevdeki kullanıcı kodu bir iptal isteğine yanıt verdiğinde, doğru işlem isteğin iletildiği iptal belirtecini geçiren bir <xref:System.OperationCanceledException> öğesi oluşturmaktır. Özel durumu yaymadan önce, görev örneği, özel durumdaki belirteci, oluşturulurken geçilen belirteçle karşılaştırır. Aynılarsa, görev, <xref:System.Threading.Tasks.TaskCanceledException> öğesine sarmalanmış bir <xref:System.AggregateException> öğesi oluşturur ve bu öğe, iç özel durumlar incelenirken görülebilir. Ancak, çağıran iş parçacığı görevi beklenmiyor varsa, bu bir özel durum dağıtılmaz. Daha fazla bilgi için bkz: [görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
 [!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
 [!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]  
  
## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>İç Özel Durumları Filtrelemek İçin Handle Yöntemini Kullanma  
 İşlenmiş olarak davranabileceğiniz özel durumları başka bir işleme gerek kalmadan filtrelemek için <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. İçin sağlanan kullanıcı temsilci olarak <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> yöntemi, özel durum türü inceleyebilirsiniz kendi <xref:System.Exception.Message%2A> özelliği veya zararsız olup olmadığını belirlemenize izin veren diğer hakkında bilgiler. Temsilci döndüğü özel durumlar `false` yeni bir işlenemezse <xref:System.AggregateException> hemen sonra örnek <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemi döndürür.  
  
 Aşağıdaki örnek ilk örnekte her özel durum inceler Bu konu, işlevsel olarak eşdeğerdir <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> koleksiyonu.  Bunun yerine, bu özel durum işleyici çağırır <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemi nesne her özel durumu ve değil yalnızca yeniden oluşturur özel durumlar için `CustomException` örnekleri.  
  
 [!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
 [!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]  
  
 Aşağıdaki kullanır daha kapsamlı bir örnektir <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemi için özel işleme sağlamak için bir <xref:System.UnauthorizedAccessException> dosyaları numaralandırılırken özel durum.  
  
 [!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
 [!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]  
  
<a name="ExceptionProp"></a>   
## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Özel durumlar Task.Exception özelliğini kullanarak Gözlemleme  
 Eğer bir görev <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> durumunda tamamlanırsa, hatayı tam olarak hangi özel durumun oluşturduğunu bulmak için <xref:System.Threading.Tasks.Task.Exception%2A> özelliği incelenebilir. <xref:System.Threading.Tasks.Task.Exception%2A> özelliğini incelemenin iyi bir yolu, aşağıdaki örnekte gösterildiği gibi yalnızca öncül görev hata verirse çalışan bir devamlılık kullanmaktır.  
  
 [!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
 [!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]  
  
 Gerçek bir uygulamada, devamlılık temsilcisi özel durum hakkında ayrıntılı bilgi kaydedebilir ve uygulamayı özel durumdan kurtarmak için yeni görevler oluşturabilir.  
  
## <a name="unobservedtaskexception-event"></a>UnobservedTaskException Olayı  
 Güvenilmeyen eklentileri barındırmak gibi bazı senaryolarda, zararsız özel durumlar sık gerçekleşebilir ve hepsini el ile gözlemek çok zor olabilir. Bu durumlarda, <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType> olayını işleyebilirsiniz. İşleyicinize geçirilen <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType> örneği, gözlemlenmemiş özel durumun birleşen iş parçacığına geri yayılmasını önlemek için kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
