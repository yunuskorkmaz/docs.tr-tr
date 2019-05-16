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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3e602057bfd2dea15887daee9058b12f26992f2
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639041"
---
# <a name="exception-handling-task-parallel-library"></a>Özel durum işleme (görev paralel kitaplığı)

Bir görev içinde çalışan kullanıcı kodu tarafından oluşturulan işlenmeyen özel durumları çağırma iş parçacığına geri, dışında bu konunun ilerleyen bölümlerinde anlatılan belirli senaryolarda yayılır. Özel durumlar, statik birini kullandığınızda yayılır veya örnek <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemleri, onları işleyebilirsiniz çağrısında kapsayan tarafından bir `try` / `catch` deyimi. Bir görev, iliştirilen alt görevlerin üst ise veya birden çok görevi bekliyorsanız, birden çok özel durum oluşturulabilir.

Tüm özel durumları çağrı yapan iş parçacığına geri yaymak için, Görev altyapısı onları bir <xref:System.AggregateException> örneği içine sarar. <xref:System.AggregateException> Özel durumuna sahip bir <xref:System.AggregateException.InnerExceptions%2A> , oluşturulan tüm orijinal özel durumları incelemek için numaralandırılabilen ve her biri işlemek (veya işlememek) özelliği ayrı ayrı. Kullanarak ayrıca orijinal özel durumları işleyebilir <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemi.

Yalnızca bir özel durum oluşsa bile, yine de içine sarmalanır bir <xref:System.AggregateException> aşağıdaki örnekte gösterildiği gibi bir özel durum.

[!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
[!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]

Yalnızca <xref:System.AggregateException> öğesini yakalayarak ve dahili özel durumların hiç birini gözlemeyerek bir işlenmeyen özel durumu önleyebilirsiniz. Ancak, temel yakalamaya olduğundan, bunu yapmamanızı öneririz <xref:System.Exception> paralel olmayan senaryolarda türü. Bir özel durumu yakalayıp bu durumdan kurtulmak için belirli eylemleri yapmazsanız uygulamanız belirsiz bir durumda kalabilir.

Çağrılacak istemiyorsanız <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> görevin tamamlanmasını bekle yöntemini ayrıca Al <xref:System.AggregateException> görev özel durum <xref:System.Threading.Tasks.Task.Exception%2A> özelliği, aşağıdaki örnekte gösterildiği gibi. Daha fazla bilgi için [Task.Exception özelliğini kullanarak özel durumları gözleme](#observing-exceptions-by-using-the-taskexception-property) bölümüne bakın.

[!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
[!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]

Bir özel durum ya da erişim yayan bir görevi beklemezseniz değil, kendi <xref:System.Threading.Tasks.Task.Exception%2A> görev atık olarak toplanmış olduğunda özelliği, özel durum .NET özel durum ilkesine göre ilerletilmiş.

Özel durumların katılan iş parçacığına geri yukarı Kabarcık halinde çıkmasına izin verildiğinde bir görev özel durum oluşturulduktan sonra bazı öğeleri işlemeye devam edebilir.

> [!NOTE]
> "Yalnızca kendi kodum" etkin olduğunda, bazı durumlarda Visual Studio özel durum oluşturan satırda bölme ve "özel durum kullanıcı kodu tarafından işlenmemiş." diyen bir hata iletisini görüntüler Bu hata zararsızdır. F5 tuşuna basarak devam edebilir ve bu örneklerde gösterilen özel durum işleme davranışını görebilirsiniz. Visual Studio'nun çalışmasının ilk hatada kesilmesini önlemek için yalnızca temizleyin **yalnızca benim kodumu etkinleştir** onay kutusunun **Araçlar, Seçenekler, hata ayıklama, genel**.

## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Eklenen alt görevler ve iç içe geçmiş AggregateException öğeleri

Bir göreve ekli, özel durum oluşturan bir alt görev varsa, o özel durum üst göreve yayılmadan önce bir <xref:System.AggregateException> öğesi içine sarmalanır ve bu da o özel durumu çağıran iş parçacığına geri yaymadan önce kendi <xref:System.AggregateException> öğesine sarmalar. Bu gibi durumlarda <xref:System.AggregateException.InnerExceptions%2A> özelliği <xref:System.AggregateException> sırasında yakalanan bir özel durum <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAny%2A>, veya <xref:System.Threading.Tasks.Task.WaitAll%2A> yöntemi içeren bir veya daha fazla <xref:System.AggregateException> örnekler, hataya neden olmayan orijinal özel durumları. Üzerinden yinelemek zorunda kalmamak için iç içe geçmiş <xref:System.AggregateException> kullanabileceğiniz özel durumlar, <xref:System.AggregateException.Flatten%2A> yöntemi tümünü kaldırmak için iç içe <xref:System.AggregateException> özel durumlar, böylece <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> özelliği, orijinal özel durumları içerir. Aşağıdaki örnekte, iç içe geçmiş <xref:System.AggregateException> örnekleri yalnızca tek bir döngüde düzleştirilip işlenir.

[!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
[!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]

Ayrıca <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> birden çok iç özel durumlar yeniden oluşturulması için yöntemi <xref:System.AggregateException> tek bir birden çok görev tarafından oluşturulan örnekleri <xref:System.AggregateException> örneği, aşağıdaki örnekte gösterildiği gibi.

[!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
[!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]

## <a name="exceptions-from-detached-child-tasks"></a>Ayrılmış alt görevlerden gelen özel durumlar

Varsayılan olarak, özel durumlar ayrılmış olarak oluşturulur. Ayrılmış görevlerde oluşturulan özel durumlar bir üst görev içinde işlenmeli ve yeniden harekete geçirilmelidir; bu özel durumlar eklenen alt görevlerde olduğu şekilde çağıran iş parçacığına geri yayılmaz. En üst öğe ayrılmış bir alt öğesinde neden'dan bir özel durumu el ile yeniden bir <xref:System.AggregateException> ve çağıran iş parçacığına geri yayılır.

[!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
[!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]

Bir alt görevdeki özel durumu gözlemek için bir devamlılık kullanıyor olsanız bile, özel durum yine de üst görev tarafından gözlenmelidir.

## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Birlikte iptal olduğunu belirten özel durumlar

Bir görevdeki kullanıcı kodu bir iptal isteğine yanıt verdiğinde, doğru işlem isteğin iletildiği iptal belirtecini geçiren bir <xref:System.OperationCanceledException> öğesi oluşturmaktır. Özel durumu yaymadan önce, görev örneği, özel durumdaki belirteci, oluşturulurken geçilen belirteçle karşılaştırır. Aynılarsa, görev, <xref:System.Threading.Tasks.TaskCanceledException> öğesine sarmalanmış bir <xref:System.AggregateException> öğesi oluşturur ve bu öğe, iç özel durumlar incelenirken görülebilir. Ancak, çağıran iş parçacığı görevi beklemiyorsa, bu özel durum yayılmaz. Daha fazla bilgi için [görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md).

[!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
[!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]

## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>İç özel durumları filtrelemek için handle yöntemini kullanma

İşlenmiş olarak davranabileceğiniz özel durumları başka bir işleme gerek kalmadan filtrelemek için <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. Sağlanan kullanıcı temsilcisinde <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> yöntemi özel durum türü inceleyebilirsiniz kendi <xref:System.Exception.Message%2A> özelliği veya ilgili zararsız olduğunu belirlemenizi sağlayacak diğer bilgileri. Temsilci döndüren özel durumların `false` yeni bir işlenemezse <xref:System.AggregateException> hemen sonra örnek <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemi döndürür.

Aşağıdaki örnek bu konu, her bir özel durum inceler ilk örnekte işlevsel olarak eşdeğerdir, <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> koleksiyonu.  Bunun yerine, bu özel durum işleyici çağırır <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemi nesnenin her özel durum ve değil yalnızca beklerseniz özel durumlar için `CustomException` örnekleri.

[!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
[!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]

Kullanan daha eksiksiz bir örnek verilmiştir <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> yöntemi için özel işleme sağlamak için bir <xref:System.UnauthorizedAccessException> dosyaları listelenirken bir özel durum.

[!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
[!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]

## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Task.Exception özelliğini kullanarak özel durumları gözleme

Eğer bir görev <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> durumunda tamamlanırsa, hatayı tam olarak hangi özel durumun oluşturduğunu bulmak için <xref:System.Threading.Tasks.Task.Exception%2A> özelliği incelenebilir. <xref:System.Threading.Tasks.Task.Exception%2A> özelliğini incelemenin iyi bir yolu, aşağıdaki örnekte gösterildiği gibi yalnızca öncül görev hata verirse çalışan bir devamlılık kullanmaktır.

[!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
[!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]

Gerçek bir uygulamada, devamlılık temsilcisi özel durum hakkında ayrıntılı bilgi kaydedebilir ve uygulamayı özel durumdan kurtarmak için yeni görevler oluşturabilir.

## <a name="unobservedtaskexception-event"></a>UnobservedTaskException olayı

Güvenilmeyen eklentileri barındırmak gibi bazı senaryolarda, zararsız özel durumlar sık gerçekleşebilir ve hepsini el ile gözlemek çok zor olabilir. Bu durumlarda, <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType> olayını işleyebilirsiniz. İşleyicinize geçirilen <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType> örneği, gözlemlenmemiş özel durumun birleşen iş parçacığına geri yayılmasını önlemek için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
