---
title: Özel durum işleme (görev paralel kitaplığı)
ms.date: 04/20/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
ms.openlocfilehash: 674abcfe4477e14295f131e766a48422779391de
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290051"
---
# <a name="exception-handling-task-parallel-library"></a>Özel durum işleme (görev paralel kitaplığı)

Bir görevde çalışan Kullanıcı kodu tarafından oluşturulan işlenmemiş özel durumlar, bu konunun ilerleyen kısımlarında açıklanan bazı senaryolar dışında, çağıran iş parçacığına geri yayılır. Statik veya örnek yöntemlerinden birini kullandığınızda özel durumlar yayılır <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> ve çağrıyı bir deyime ekleyerek bunları işleyebilirsiniz `try` / `catch` . Bir görev, iliştirilmiş alt görevlerin üst öğesi ise veya birden çok görevi bekliyorsa, birden çok özel durum oluşturulabilir.

Tüm özel durumları çağrı yapan iş parçacığına geri yaymak için, Görev altyapısı onları bir <xref:System.AggregateException> örneği içine sarar. <xref:System.AggregateException>Özel durum, <xref:System.AggregateException.InnerExceptions%2A> oluşturulan tüm orijinal özel durumları incelemek için Numaralandırılabilir bir özelliğe sahiptir ve her birini ayrı ayrı (tanıtıcı değil) işler. Ayrıca, yöntemini kullanarak özgün özel durumları işleyebilirsiniz <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> .

Yalnızca bir özel durum oluşturulmuş olsa da, <xref:System.AggregateException> Aşağıdaki örnekte gösterildiği gibi, bir özel durumla hala sarmalanır.

[!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
[!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]

Yalnızca <xref:System.AggregateException> öğesini yakalayarak ve dahili özel durumların hiç birini gözlemeyerek bir işlenmeyen özel durumu önleyebilirsiniz. Bununla birlikte, bu işlemi, temel <xref:System.Exception> türü paralel olmayan senaryolarda yakalamak için, bunu yapmanızı öneririz. Bir özel durumu yakalayıp bu durumdan kurtulmak için belirli eylemleri yapmazsanız uygulamanız belirsiz bir durumda kalabilir.

<xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>Görevin tamamlanmasını beklemek için yöntemini çağırmak istemiyorsanız, <xref:System.AggregateException> <xref:System.Threading.Tasks.Task.Exception%2A> Aşağıdaki örnekte gösterildiği gibi görevin özelliğinden özel durumu da alabilirsiniz. Daha fazla bilgi için bu konunun [Task. Exception özelliğini kullanarak özel durumları gözlemleme](#observing-exceptions-by-using-the-taskexception-property) bölümüne bakın.

[!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
[!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]

Bir özel durum yayan bir görevi beklemeyin veya <xref:System.Threading.Tasks.Task.Exception%2A> özelliğine eriştiğinizde, görev çöp topladığında .NET özel durum ilkesine göre özel durum ilerletildi.

Özel durumların katılan iş parçacığına balon ekleme yapmasına izin verildiğinde, özel durum oluşturulduktan sonra bir görev bazı öğeleri işlemeye devam edebilir.

> [!NOTE]
> "Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler. Bu hata zararsız. F5 tuşuna basarak devam edebilir ve bu örneklerde gösterilen özel durum işleme davranışını görebilirsiniz. Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altındaki **Etkinleştir yalnızca kendi kodum** onay kutusunun işaretini kaldırmanız yeterlidir.

## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Bağlı alt görevler ve iç içe geçmiş AggregateExceptions

Bir göreve ekli, özel durum oluşturan bir alt görev varsa, o özel durum üst göreve yayılmadan önce bir <xref:System.AggregateException> öğesi içine sarmalanır ve bu da o özel durumu çağıran iş parçacığına geri yaymadan önce kendi <xref:System.AggregateException> öğesine sarmalar. Bu gibi durumlarda,, <xref:System.AggregateException.InnerExceptions%2A> <xref:System.AggregateException> veya yönteminde yakalanan özel durumun özelliği, <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WaitAny%2A> <xref:System.Threading.Tasks.Task.WaitAll%2A> <xref:System.AggregateException> hataya neden olan özgün özel durumlar yerine bir veya daha fazla örnek içerir. İç içe geçmiş özel durumların üzerinde yineleme yapmaktan kaçınmak için, <xref:System.AggregateException> özelliğini kullanarak <xref:System.AggregateException.Flatten%2A> tüm iç içe geçmiş özel durumları kaldırabilirsiniz <xref:System.AggregateException> . böylece, <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> özelliğin özgün özel durumları içermesi gerekir. Aşağıdaki örnekte, iç içe geçmiş <xref:System.AggregateException> örnekleri yalnızca tek bir döngüde düzleştirilip işlenir.

[!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
[!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]

<xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> <xref:System.AggregateException> <xref:System.AggregateException> Aşağıdaki örnekte gösterildiği gibi, tek bir örnekte birden çok görev tarafından oluşturulan birden çok örnekten iç özel durumları yeniden oluşturmak için yöntemini de kullanabilirsiniz.

[!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
[!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]

## <a name="exceptions-from-detached-child-tasks"></a>Ayrılmış alt görevlerden özel durumlar

Varsayılan olarak, özel durumlar ayrılmış olarak oluşturulur. Ayrılmış görevlerde oluşturulan özel durumlar bir üst görev içinde işlenmeli ve yeniden harekete geçirilmelidir; bu özel durumlar eklenen alt görevlerde olduğu şekilde çağıran iş parçacığına geri yayılmaz. En üstteki üst öğe, ayrılmış bir alt öğeden bir özel durumu el ile yeniden oluşturabilir ve bu, bir ' a sarmalanmış <xref:System.AggregateException> ve çağıran iş parçacığına geri yayılmasını sağlar.

[!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
[!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]

Bir alt görevdeki özel durumu gözlemek için bir devamlılık kullanıyor olsanız bile, özel durum yine de üst görev tarafından gözlenmelidir.

## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Birlikte iptalleri belirten özel durumlar

Bir görevdeki kullanıcı kodu bir iptal isteğine yanıt verdiğinde, doğru işlem isteğin iletildiği iptal belirtecini geçiren bir <xref:System.OperationCanceledException> öğesi oluşturmaktır. Özel durumu yaymadan önce, görev örneği, özel durumdaki belirteci, oluşturulurken geçilen belirteçle karşılaştırır. Aynılarsa, görev, <xref:System.Threading.Tasks.TaskCanceledException> öğesine sarmalanmış bir <xref:System.AggregateException> öğesi oluşturur ve bu öğe, iç özel durumlar incelenirken görülebilir. Ancak, çağıran iş parçacığı görevde beklemmez, bu özel durum yayılmaz. Daha fazla bilgi için bkz. [Görev iptali](task-cancellation.md).

[!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
[!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]

## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>İç özel durumları filtrelemek için tanıtıcı metodunu kullanma

İşlenmiş olarak davranabileceğiniz özel durumları başka bir işleme gerek kalmadan filtrelemek için <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. Yöntemine sağlanan Kullanıcı temsilcisinde <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> , özel durum türünü, <xref:System.Exception.Message%2A> özelliğini veya onunla ilgili herhangi bir bilgiyi, onun zararsız olup olmadığını belirlemenize olanak sağlayacak başka herhangi bir bilgi inceleyebilirsiniz. Temsilcinin döndürdüğü tüm özel durumlar, `false` <xref:System.AggregateException> yöntemin döndürdüğü yeni bir örnekte hemen yeniden oluşturulur <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> .

Aşağıdaki örnek, koleksiyondaki her bir özel durumu inceleyerek bu konudaki ilk örneğe işlevsel olarak eşdeğerdir <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> .  Bunun yerine, bu özel durum işleyicisi <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> her özel durum için yöntem nesnesini çağırır ve yalnızca örnek olmayan özel durumları yeniden atar `CustomException` .

[!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
[!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]

Aşağıda, <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> dosyaları numaralandırılırken özel bir durum için özel işleme sağlamak üzere yöntemi kullanan daha kapsamlı bir örnek verilmiştir <xref:System.UnauthorizedAccessException> .

[!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
[!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]

## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Task. Exception özelliğini kullanarak özel durumları gözlemleme

Eğer bir görev <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> durumunda tamamlanırsa, hatayı tam olarak hangi özel durumun oluşturduğunu bulmak için <xref:System.Threading.Tasks.Task.Exception%2A> özelliği incelenebilir. <xref:System.Threading.Tasks.Task.Exception%2A> özelliğini incelemenin iyi bir yolu, aşağıdaki örnekte gösterildiği gibi yalnızca öncül görev hata verirse çalışan bir devamlılık kullanmaktır.

[!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
[!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]

Anlamlı bir uygulamada devamlılık temsilcisi özel durumla ilgili ayrıntılı bilgileri günlüğe kaydeder ve büyük olasılıkla özel durumdan kurtarmak için yeni görevler oluşturabilir. Bir görev hatası varsa, aşağıdaki ifadeler özel durumu oluşturur:

- `await task`
- `task.Wait()`
- `task.Result`
- `task.GetAwaiter().GetResult()`

[`try-catch`](../../csharp/language-reference/keywords/try-catch.md)Oluşan özel durumları işlemek ve gözlemlemek için bir ifade kullanın. Alternatif olarak, özelliğine erişerek özel durumu gözlemleyin <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> .

## <a name="unobservedtaskexception-event"></a>UnobservedTaskException olayı

Güvenilmeyen eklentileri barındırmak gibi bazı senaryolarda, zararsız özel durumlar sık gerçekleşebilir ve hepsini el ile gözlemek çok zor olabilir. Bu durumlarda, <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType> olayını işleyebilirsiniz. İşleyicinize geçirilen <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType> örneği, gözlemlenmemiş özel durumun birleşen iş parçacığına geri yayılmasını önlemek için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](task-parallel-library-tpl.md)
