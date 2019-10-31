---
title: Özel durum işleme (görev paralel kitaplığı)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
ms.openlocfilehash: 12777a5f34b8aadcc80977b8796fc2cd53c626a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134258"
---
# <a name="exception-handling-task-parallel-library"></a>Özel durum işleme (görev paralel kitaplığı)

Bir görevde çalışan Kullanıcı kodu tarafından oluşturulan işlenmemiş özel durumlar, bu konunun ilerleyen kısımlarında açıklanan bazı senaryolar dışında, çağıran iş parçacığına geri yayılır. Statik veya örnek <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemlerinden birini kullandığınızda özel durumlar yayılır ve çağrıyı bir `try`/`catch` ifadesinde çevreleyerek bunları işleyebilirsiniz. Bir görev, iliştirilmiş alt görevlerin üst öğesi ise veya birden çok görevi bekliyorsa, birden çok özel durum oluşturulabilir.

Tüm özel durumları çağrı yapan iş parçacığına geri yaymak için, Görev altyapısı onları bir <xref:System.AggregateException> örneği içine sarar. <xref:System.AggregateException> özel durumu, oluşturulan tüm orijinal özel durumları incelemek için Numaralandırılabilir bir <xref:System.AggregateException.InnerExceptions%2A> özelliğine sahiptir ve her birini ayrı ayrı işleyebilir (veya işlemez). Ayrıca, <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemini kullanarak özgün özel durumları işleyebilirsiniz.

Yalnızca bir özel durum oluşturulursa bile, aşağıdaki örnekte gösterildiği gibi <xref:System.AggregateException> bir özel durum ile sarmalanır.

[!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
[!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]

Yalnızca <xref:System.AggregateException> öğesini yakalayarak ve dahili özel durumların hiç birini gözlemeyerek bir işlenmeyen özel durumu önleyebilirsiniz. Bununla birlikte, bu işlemi yapmanızı öneririz çünkü temel <xref:System.Exception> türünü paralel olmayan senaryolarda yakalamak benzerdir. Bir özel durumu yakalayıp bu durumdan kurtulmak için belirli eylemleri yapmazsanız uygulamanız belirsiz bir durumda kalabilir.

Görevin tamamlanmasını beklemek için <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemini çağırmak istemiyorsanız, aşağıdaki örnekte gösterildiği gibi görevin <xref:System.Threading.Tasks.Task.Exception%2A> özelliğinden <xref:System.AggregateException> özel durumunu da alabilirsiniz. Daha fazla bilgi için bu konunun [Task. Exception özelliğini kullanarak özel durumları gözlemleme](#observing-exceptions-by-using-the-taskexception-property) bölümüne bakın.

[!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
[!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]

Özel durum yayan bir görevi beklemeyin veya <xref:System.Threading.Tasks.Task.Exception%2A> özelliğine eriştiğinizde, görev çöp topladığında .NET özel durum ilkesine göre özel durum ilerletildi.

Özel durumların katılan iş parçacığına balon ekleme yapmasına izin verildiğinde, özel durum oluşturulduktan sonra bir görev bazı öğeleri işlemeye devam edebilir.

> [!NOTE]
> "Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler. Bu hata zararsız. F5 tuşuna basarak devam edebilir ve bu örneklerde gösterilen özel durum işleme davranışını görebilirsiniz. Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altındaki **Etkinleştir yalnızca kendi kodum** onay kutusunun işaretini kaldırmanız yeterlidir.

## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Bağlı alt görevler ve iç içe geçmiş AggregateExceptions

Bir göreve ekli, özel durum oluşturan bir alt görev varsa, o özel durum üst göreve yayılmadan önce bir <xref:System.AggregateException> öğesi içine sarmalanır ve bu da o özel durumu çağıran iş parçacığına geri yaymadan önce kendi <xref:System.AggregateException> öğesine sarmalar. Bu gibi durumlarda, <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAny%2A>veya <xref:System.Threading.Tasks.Task.WaitAll%2A> yönteminde yakalanan <xref:System.AggregateException> özel durumun <xref:System.AggregateException.InnerExceptions%2A> özelliği, hataya neden olan özgün özel durumları değil, bir veya daha fazla <xref:System.AggregateException> örneği içerir. İç içe geçmiş <xref:System.AggregateException> özel durumlarını yinelemek zorunda kalmamak için, tüm iç içe geçmiş <xref:System.AggregateException> özel durumlarını kaldırmak üzere <xref:System.AggregateException.Flatten%2A> metodunu kullanarak <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> özelliği özgün özel durumları içerir. Aşağıdaki örnekte, iç içe geçmiş <xref:System.AggregateException> örnekleri yalnızca tek bir döngüde düzleştirilip işlenir.

[!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
[!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]

Aşağıdaki örnekte gösterildiği gibi, tek bir <xref:System.AggregateException> örneğinde birden çok görev tarafından oluşturulan birden çok <xref:System.AggregateException> örneğinden iç özel durumları yeniden oluşturmak için <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> yöntemini de kullanabilirsiniz.

[!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
[!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]

## <a name="exceptions-from-detached-child-tasks"></a>Ayrılmış alt görevlerden özel durumlar

Varsayılan olarak, özel durumlar ayrılmış olarak oluşturulur. Ayrılmış görevlerde oluşturulan özel durumlar bir üst görev içinde işlenmeli ve yeniden harekete geçirilmelidir; bu özel durumlar eklenen alt görevlerde olduğu şekilde çağıran iş parçacığına geri yayılmaz. En üstteki üst öğe, ayrılmış bir alt öğeden, bir <xref:System.AggregateException> sarmalanmasına ve çağıran iş parçacığına geri yayılmasına neden olacak şekilde el ile yeniden bir özel durum oluşturabilir.

[!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
[!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]

Bir alt görevdeki özel durumu gözlemek için bir devamlılık kullanıyor olsanız bile, özel durum yine de üst görev tarafından gözlenmelidir.

## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Birlikte iptalleri belirten özel durumlar

Bir görevdeki kullanıcı kodu bir iptal isteğine yanıt verdiğinde, doğru işlem isteğin iletildiği iptal belirtecini geçiren bir <xref:System.OperationCanceledException> öğesi oluşturmaktır. Özel durumu yaymadan önce, görev örneği, özel durumdaki belirteci, oluşturulurken geçilen belirteçle karşılaştırır. Aynılarsa, görev, <xref:System.Threading.Tasks.TaskCanceledException> öğesine sarmalanmış bir <xref:System.AggregateException> öğesi oluşturur ve bu öğe, iç özel durumlar incelenirken görülebilir. Ancak, çağıran iş parçacığı görevde beklemmez, bu özel durum yayılmaz. Daha fazla bilgi için bkz. [Görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md).

[!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
[!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]

## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>İç özel durumları filtrelemek için tanıtıcı metodunu kullanma

İşlenmiş olarak davranabileceğiniz özel durumları başka bir işleme gerek kalmadan filtrelemek için <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> yöntemine sağlanan Kullanıcı temsilcisinde, özel durum türünü, <xref:System.Exception.Message%2A> özelliğini veya onunla ilgili herhangi bir bilgiyi, onun zararsız olup olmadığını belirlemenize olanak sağlayacak başka herhangi bir bilgi inceleyebilirsiniz. Temsilci `false` döndürdüğü tüm özel durumlar, <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemi döndüğünde hemen sonra yeni bir <xref:System.AggregateException> örneğinde yeniden oluşturulur.

Aşağıdaki örnek, <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> koleksiyonundaki her bir özel durumu inceleyerek, bu konudaki ilk örneğe işlevsel olarak eşdeğerdir.  Bunun yerine, bu özel durum işleyicisi her özel durum için <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemi nesnesini çağırır ve yalnızca `CustomException` örnekleri olmayan özel durumları yeniden oluşturur.

[!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
[!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]

Aşağıda, dosyaları numaralandırılırken bir <xref:System.UnauthorizedAccessException> özel durum için özel işleme sağlamak üzere <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemi kullanan daha kapsamlı bir örnek verilmiştir.

[!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
[!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]

## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Task. Exception özelliğini kullanarak özel durumları gözlemleme

Eğer bir görev <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> durumunda tamamlanırsa, hatayı tam olarak hangi özel durumun oluşturduğunu bulmak için <xref:System.Threading.Tasks.Task.Exception%2A> özelliği incelenebilir. <xref:System.Threading.Tasks.Task.Exception%2A> özelliğini incelemenin iyi bir yolu, aşağıdaki örnekte gösterildiği gibi yalnızca öncül görev hata verirse çalışan bir devamlılık kullanmaktır.

[!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
[!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]

Gerçek bir uygulamada, devamlılık temsilcisi özel durum hakkında ayrıntılı bilgi kaydedebilir ve uygulamayı özel durumdan kurtarmak için yeni görevler oluşturabilir.

## <a name="unobservedtaskexception-event"></a>UnobservedTaskException olayı

Güvenilmeyen eklentileri barındırmak gibi bazı senaryolarda, zararsız özel durumlar sık gerçekleşebilir ve hepsini el ile gözlemek çok zor olabilir. Bu durumlarda, <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType> olayını işleyebilirsiniz. İşleyicinize geçirilen <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType> örneği, gözlemlenmemiş özel durumun birleşen iş parçacığına geri yayılmasını önlemek için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
