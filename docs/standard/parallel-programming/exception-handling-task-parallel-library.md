---
title: Özel durum işleme (Görev Paralel Kitaplığı)
ms.date: 04/20/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
ms.openlocfilehash: aa6d4b706eb11921ffd419402bcf4cf059a29b11
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021503"
---
# <a name="exception-handling-task-parallel-library"></a>Özel durum işleme (Görev Paralel Kitaplığı)

Bir görev içinde çalışan kullanıcı kodu tarafından atılan işlenmemiş özel durumlar, bu konuda daha sonra açıklanan belirli senaryolar dışında çağrı iş parçacığına geri yayılır. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> Statik veya örnek yöntemlerinden birini kullandığınızda özel durumlar yayılır ve çağrıyı bir `try` / `catch` deyimle ekleyerek bunları işlersiniz. Bir görev, eklenmiş alt görevlerin üst öğesiyse veya birden çok görevde bekliyorsanız, birden çok özel durum atılabilir.

Tüm özel durumları çağrı yapan iş parçacığına geri yaymak için, Görev altyapısı onları bir <xref:System.AggregateException> örneği içine sarar. Özel <xref:System.AggregateException> durum, <xref:System.AggregateException.InnerExceptions%2A> atılan tüm özgün özel durumları incelemek için numaralandırılabilen ve her birini ayrı ayrı işlemek (veya işlemeyen) bir özelliğe sahiptir. Ayrıca <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemi kullanarak özgün özel durumlar işleyebilir.

Yalnızca bir özel durum atılsa bile, <xref:System.AggregateException> aşağıdaki örnekte görüldüğü gibi yine de bir özel durumla sarılır.

[!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
[!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]

Yalnızca <xref:System.AggregateException> öğesini yakalayarak ve dahili özel durumların hiç birini gözlemeyerek bir işlenmeyen özel durumu önleyebilirsiniz. Ancak, paralel olmayan senaryolarda taban <xref:System.Exception> türünü yakalamaya benzediği için bunu yapmamanızı öneririz. Bir özel durumu yakalayıp bu durumdan kurtulmak için belirli eylemleri yapmazsanız uygulamanız belirsiz bir durumda kalabilir.

Görevin tamamlanmasını <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> beklemek için yöntemi çağırmak istemiyorsanız, aşağıdaki örnekte <xref:System.AggregateException> görüldüğü gibi görev <xref:System.Threading.Tasks.Task.Exception%2A> özelliğinden de özel durum alabilirsiniz. Daha fazla bilgi için, bu konuda [Task.Exception özelliği](#observing-exceptions-by-using-the-taskexception-property) bölümünü kullanarak Özel Durum özelliğibölümünü kullanarak Özel Durum Gözlemlemeye bölümüne bakın.

[!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
[!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]

Bir özel durum yayan bir görevi beklemezseniz veya <xref:System.Threading.Tasks.Task.Exception%2A> özelliğine erişirseniz, görev çöp toplandığında özel durum .NET özel durum ilkesine göre yükseltilir.

Özel durumların birleştirme iş parçacığına geri dönmesine izin verildiğinde, bir görevin özel durum yükseltildikten sonra bazı öğeleri işlemeye devam etmesi mümkündür.

> [!NOTE]
> "Yalnızca Kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satırda kırılır ve "kullanıcı kodu tarafından işlenmemiş özel durum" yazan bir hata iletisi görüntüler. Bu hata iyi huylu. F5 tuşuna basarak devam edebilir ve bu örneklerde gösterilen özel durum işleme davranışını görebilirsiniz. Visual Studio'nun ilk hatayı kırmasını önlemek **için, Araçlar, Seçenekler, Hata Ayıklama, Genel**altında **Yalnızca Kodum** onay kutusunu etkinleştir'in işaretlerini kaldırın.

## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Eklenen alt görevler ve iç içe olan Toplu Özel Durumlar

Bir göreve ekli, özel durum oluşturan bir alt görev varsa, o özel durum üst göreve yayılmadan önce bir <xref:System.AggregateException> öğesi içine sarmalanır ve bu da o özel durumu çağıran iş parçacığına geri yaymadan önce kendi <xref:System.AggregateException> öğesine sarmalar. <xref:System.AggregateException.InnerExceptions%2A> Bu gibi durumlarda, , <xref:System.AggregateException> <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAny%2A>veya <xref:System.Threading.Tasks.Task.WaitAll%2A> yöntem yakalanan özel durum özelliği, hataya neden olan özgün özel durumlar değil, bir veya daha fazla <xref:System.AggregateException> örnek içerir. <xref:System.AggregateException> İç içe gelen özel durumlar üzerinde yinelenmeyi önlemek <xref:System.AggregateException.Flatten%2A> için, <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> özelliğin <xref:System.AggregateException> özgün özel durumları içermesi için tüm iç içe olan özel durumları kaldırmak için yöntemi kullanabilirsiniz. Aşağıdaki örnekte, iç içe geçmiş <xref:System.AggregateException> örnekleri yalnızca tek bir döngüde düzleştirilip işlenir.

[!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
[!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]

Aşağıdaki örnekte <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> görüldüğü gibi, tek bir <xref:System.AggregateException> durumda <xref:System.AggregateException> birden çok görev tarafından atılan birden çok örnekten iç özel durumları yeniden atmak için de yöntemi kullanabilirsiniz.

[!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
[!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]

## <a name="exceptions-from-detached-child-tasks"></a>Ayrılmış alt görevlerden istisnalar

Varsayılan olarak, özel durumlar ayrılmış olarak oluşturulur. Ayrılmış görevlerde oluşturulan özel durumlar bir üst görev içinde işlenmeli ve yeniden harekete geçirilmelidir; bu özel durumlar eklenen alt görevlerde olduğu şekilde çağıran iş parçacığına geri yayılmaz. En üstteki üst öğe, bir özel durum öğesine sarılmış <xref:System.AggregateException> ve çağrı iş parçacığına geri yayılmasına neden olmak için ayrılmış bir çocuktan bir özel durumu el ile yeniden atabilir.

[!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
[!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]

Bir alt görevdeki özel durumu gözlemek için bir devamlılık kullanıyor olsanız bile, özel durum yine de üst görev tarafından gözlenmelidir.

## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Kooperatif iptalini gösteren istisnalar

Bir görevdeki kullanıcı kodu bir iptal isteğine yanıt verdiğinde, doğru işlem isteğin iletildiği iptal belirtecini geçiren bir <xref:System.OperationCanceledException> öğesi oluşturmaktır. Özel durumu yaymadan önce, görev örneği, özel durumdaki belirteci, oluşturulurken geçilen belirteçle karşılaştırır. Aynılarsa, görev, <xref:System.Threading.Tasks.TaskCanceledException> öğesine sarmalanmış bir <xref:System.AggregateException> öğesi oluşturur ve bu öğe, iç özel durumlar incelenirken görülebilir. Ancak, arama iş parçacığı görevde beklemiyorsa, bu özel özel durum yayılmaz. Daha fazla bilgi için [Görev İptal'e](../../../docs/standard/parallel-programming/task-cancellation.md)bakın.

[!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
[!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]

## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>İç özel durumları filtrelemek için tutamak yöntemini kullanma

İşlenmiş olarak davranabileceğiniz özel durumları başka bir işleme gerek kalmadan filtrelemek için <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> Yönteme verilen kullanıcı temsilcisinde, iyi huylu olup olmadığını belirlemenize izin veren özel durum türünü, özelliğini <xref:System.Exception.Message%2A> veya bu konudaki diğer bilgileri inceleyebilirsiniz. Temsilcinin döndürdettiği `false` özel <xref:System.AggregateException> <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> durumlar, yöntem döndükten hemen sonra yeni bir durumda yeniden atılır.

Aşağıdaki örnek, <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> koleksiyondaki her özel durumu inceleyen bu konudaki ilk örneğe işlevsel olarak eşdeğerdir.  Bunun yerine, bu özel <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> durum işleyicisi her özel durum için `CustomException` yöntem nesnesi çağırır ve yalnızca örnek olmayan özel durumları yeniden atar.

[!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
[!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]

Aşağıda, dosyaları sayısalarken özel <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> bir durum için <xref:System.UnauthorizedAccessException> özel işleme sağlamak için yöntemi kullanan daha eksiksiz bir örnek verilmiştir.

[!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
[!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]

## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Task.Exception özelliğini kullanarak özel durumları gözlemleme

Eğer bir görev <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> durumunda tamamlanırsa, hatayı tam olarak hangi özel durumun oluşturduğunu bulmak için <xref:System.Threading.Tasks.Task.Exception%2A> özelliği incelenebilir. <xref:System.Threading.Tasks.Task.Exception%2A> özelliğini incelemenin iyi bir yolu, aşağıdaki örnekte gösterildiği gibi yalnızca öncül görev hata verirse çalışan bir devamlılık kullanmaktır.

[!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
[!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]

Anlamlı bir uygulamada, devam temsilcisi özel durum hakkında ayrıntılı bilgileri günlüğe kaydedebilir ve büyük olasılıkla özel durum kurtarmak için yeni görevler yumurtlayabilir. Bir görev hata yaparsa, aşağıdaki ifadeler özel durum atar:

- `await task`
- `task.Wait()`
- `task.Result`
- `task.GetAwaiter().GetResult()`

Atılan [`try-catch`](../../csharp/language-reference/keywords/try-catch.md) özel durumları işlemek ve gözlemlemek için bir deyim kullanın. Alternatif olarak, <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özel liğe erişerek özel durumu gözlemleyin.

## <a name="unobservedtaskexception-event"></a>Gözlenmeyen TaskException olayı

Güvenilmeyen eklentileri barındırmak gibi bazı senaryolarda, zararsız özel durumlar sık gerçekleşebilir ve hepsini el ile gözlemek çok zor olabilir. Bu durumlarda, <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType> olayını işleyebilirsiniz. İşleyicinize geçirilen <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType> örneği, gözlemlenmemiş özel durumun birleşen iş parçacığına geri yayılmasını önlemek için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
