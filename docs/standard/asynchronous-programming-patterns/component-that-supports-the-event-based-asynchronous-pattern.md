---
title: 'Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 61f676b5-936f-40f6-83ce-f22805ec9c2f
ms.openlocfilehash: 44a1019ac8169138aa95b03e2027d9539cbf8391
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957364"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama
Fark edilebilir gecikme olabilecek bazı işlemlerle bir sınıf yazıyorsanız, [olay tabanlı zaman uyumsuz düzene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)' ı uygulayarak zaman uyumsuz işlevsellik vermeyi düşünün.  
  
 Bu izlenecek yol, olay tabanlı zaman uyumsuz model uygulayan bir bileşenin nasıl oluşturulacağını göstermektedir. Bu, bileşenin ASP.NET, konsol uygulamaları ve Windows Forms uygulamalar dahil olmak üzere herhangi bir uygulama modelinde doğru şekilde çalıştığından emin olmak için <xref:System.ComponentModel?displayProperty=nameWithType> ad alanındaki yardımcı sınıflar kullanılarak uygulanır. Bu bileşen ayrıca bir <xref:System.Windows.Forms.PropertyGrid> denetimiyle ve kendi özel tasarımcılarınız ile de genişletilebilir.  
  
 İşlem sırasında, ana sayıları zaman uyumsuz olarak hesaplayan bir uygulamaya sahip olursunuz. Uygulamanız ana kullanıcı arabirimi (UI) iş parçacığına ve her asal sayı hesaplaması için bir iş parçacığına sahip olacaktır. Büyük bir sayının asal olup olmadığını test etmek, fark edilebilir bir süre alabilir, ancak ana kullanıcı arabirimi iş parçacığı bu gecikmeyle kesintiye uğramaz ve hesaplamalar sırasında form yanıt verir. Aynı anda istediğiniz sayıda hesaplama çalıştırabilir ve bekleyen hesaplamaları seçmeli olarak iptal edebilirsiniz.  
  
 Bu izlenecek yolda gösterilen görevler şunlardır:  
  
- Bileşeni oluşturma  
  
- Ortak zaman uyumsuz olayları ve temsilcileri tanımlama  
  
- Özel temsilciler tanımlama  
  
- Ortak olayları uygulama  
  
- Tamamlama yöntemini uygulama  
  
- Çalışan yöntemlerini uygulama  
  
- Start ve Cancel yöntemlerini uygulama  
  
 Bu konudaki kodu tek bir liste olarak kopyalamak için bkz. [nasıl yapılır: olay tabanlı zaman uyumsuz düzendeki bir Istemciyi uygulama](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Bileşeni oluşturma  
 İlk adım, olay tabanlı zaman uyumsuz düzene uygulanacak bileşeni oluşturmaktır.  
  
### <a name="to-create-the-component"></a>Bileşeni oluşturmak için  
  
- @No__t-1 ' den devralan `PrimeNumberCalculator` adlı bir sınıf oluşturun.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Ortak zaman uyumsuz olayları ve temsilcileri tanımlama  
 Bileşeniniz, olayları kullanarak istemcilerle iletişim kurar. _MethodName_**olay uyarıları** istemcileri, zaman uyumsuz bir görevin tamamlanmasını sağlar ve _MethodName_**ProgressChanged & lt** olayı, zaman uyumsuz bir görevin ilerleme durumunu istemcilere bildirir.  
  
### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Bileşeninizin istemcilerine yönelik zaman uyumsuz olayları tanımlamak için:  
  
1. @No__t-0 ve <xref:System.Collections.Specialized?displayProperty=nameWithType> ad alanlarını dosyanın en üstüne aktarın.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2. @No__t-0 sınıf tanımından önce, ilerleme ve tamamlanma olayları için temsilciler bildirin.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3. @No__t-0 sınıf tanımında, ilerlemeyi raporlamak ve istemcilere tamamlamak için olaylar bildirin.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4. @No__t-0 sınıf tanımından sonra, her hesaplamanın sonucunu, @no__t -2. Event için istemcinin olay işleyicisine bildirmek üzere `CalculatePrimeCompletedEventArgs` sınıfını türetirsiniz. @No__t-0 özelliklerine ek olarak, bu sınıf istemcinin hangi sayının test edildiğini, asal olup olmadığını ve ilk bölen ana değer değilse ne olduğunu belirlemesini sağlar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Mak  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi test etmek için  
  
- Bileşeni derleyin.  
  
     İki derleyici uyarısı alacaksınız:  
  
    ```console  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Bu uyarılar sonraki bölümde temizlenir.  
  
## <a name="defining-private-delegates"></a>Özel temsilciler tanımlama  
 @No__t-0 bileşeninin zaman uyumsuz yönleri, <xref:System.Threading.SendOrPostCallback> olarak bilinen özel bir temsilci ile dahili olarak uygulanır. @No__t-0 <xref:System.Threading.ThreadPool> iş parçacığında yürütülen bir geri çağırma yöntemini temsil eder. Geri çağırma yöntemi, <xref:System.Object> türünde tek bir parametre alan bir imzaya sahip olmalıdır; bu, bir sarmalayıcı sınıfında temsilciler arasında durum geçirmeniz gereken anlamına gelir. Daha fazla bilgi için bkz. <xref:System.Threading.SendOrPostCallback>.  
  
### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Bileşeninizin iç zaman uyumsuz davranışını uygulamak için:  
  
1. @No__t-1 sınıfında <xref:System.Threading.SendOrPostCallback> temsilcileri bildirin ve oluşturun. @No__t-1 adlı bir yardımcı program yönteminde <xref:System.Threading.SendOrPostCallback> nesneleri oluşturun.  
  
     İki temsilcinin olması gerekir: biri istemciye ilerleme durumunu raporlamak için bir diğeri ise istemciye tamamlanmayı rapor eder.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2. Bileşeninizin oluşturucusunda `InitializeDelegates` yöntemini çağırın.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3. Zaman uyumsuz olarak yapılacak gerçek işleri işleyen `PrimeNumberCalculator` sınıfında bir temsilci bildirin. Bu temsilci, bir sayının asal olup olmadığını test eden çalışan yöntemini sarmalanmış. Temsilci, zaman uyumsuz işlemin ömrünü izlemek için kullanılacak bir <xref:System.ComponentModel.AsyncOperation> parametresi alır.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4. Bekleyen zaman uyumsuz işlemlerin yaşam sürelerini yönetmek için bir koleksiyon oluşturun. İstemci, yürütüldüğü ve tamamlandıkları sırada işlemleri izlemek için bir yönteme ihtiyaç duyuyor ve bu izleme, istemci zaman uyumsuz metoda çağrı yaptığında, istemcinin benzersiz bir belirteç veya görev KIMLIĞI geçmesini gerektirerek yapılır. @No__t-0 bileşeni, görev KIMLIĞINI karşılık gelen çağrıdan ilişkilendirerek her çağrının izlenmelidir. İstemci benzersiz olmayan bir görev KIMLIĞI geçirirse `PrimeNumberCalculator` bileşeni bir özel durum yükseltmelidir.  
  
     @No__t-0 bileşeni, <xref:System.Collections.Specialized.HybridDictionary> adlı özel bir koleksiyon sınıfını kullanarak görev KIMLIĞINI izler. Sınıf tanımında, `userTokenToLifetime` adlı <xref:System.Collections.Specialized.HybridDictionary> oluşturun.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Ortak olayları uygulama  
 Olay tabanlı zaman uyumsuz model uygulayan bileşenler olayları kullanarak istemcilerle iletişim kurar. Bu olaylar, <xref:System.ComponentModel.AsyncOperation> sınıfının yardımıyla uygun iş parçacığında çağrılır.  
  
### <a name="to-raise-events-to-your-components-clients"></a>Bileşenin istemcilerine olay yükseltmek için:  
  
1. İstemcilere raporlama için ortak olayları uygulayın. İlerlemeyi raporlamak için bir olaya ve bir etkinliğin tamamlanmasını raporlamaya ihtiyacınız olacak.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Tamamlama yöntemini uygulama  
 Tamamlanma temsilcisi, zaman uyumsuz işlem başarılı tamamlama, hata veya iptal ile sona erdiğinde, temel alınan, serbest iş parçacıklı zaman uyumsuz davranışın çağıracağı yöntemdir. Bu çağrı, rastgele bir iş parçacığında gerçekleşir.  
  
 Bu yöntem, istemcinin görev KIMLIĞININ, benzersiz istemci belirteçleri iç koleksiyonundan kaldırıldığı yerdir. Bu yöntem ayrıca, karşılık gelen <xref:System.ComponentModel.AsyncOperation> ' de <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> yöntemini çağırarak belirli bir zaman uyumsuz işlemin ömrünü sonlandırır. Bu çağrı, uygulama modeli için uygun olan iş parçacığında tamamlanma olayını başlatır. @No__t-0 yöntemi çağrıldıktan sonra, <xref:System.ComponentModel.AsyncOperation> ' in bu örneği artık kullanılamaz ve bu işlemi kullanmaya yönelik sonraki girişimler bir özel durum oluşturur.  
  
 @No__t-0 imzası, zaman uyumsuz işlemin sonucunu anlatmak için gereken tüm durumu tutmalıdır. Bu, belirli zaman uyumsuz işlem tarafından test edilen numaranın, sayının asal olup olmadığı ve asal sayı değilse ilk bölenin değerinin durumunu barındırır. Ayrıca, oluşan tüm özel durumları açıklayan durumu ve bu göreve karşılık gelen <xref:System.ComponentModel.AsyncOperation> ' ı barındırır.  
  
### <a name="to-complete-an-asynchronous-operation"></a>Zaman uyumsuz bir işlemi gerçekleştirmek için:  
  
- Tamamlama yöntemini uygulayın. İstemcinin `CalculatePrimeCompletedEventHandler` aracılığıyla istemciye döndürülen `CalculatePrimeCompletedEventArgs` ' ı doldurmak için kullandığı altı parametre alır. İstemci görev KIMLIĞI belirtecini iç koleksiyondan kaldırır ve zaman uyumsuz işlemin yaşam süresini <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> çağrısıyla sonlandırır. @No__t-0, uygulama modeli için uygun olan iş parçacığına veya içeriğe çağrıyı sıralar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Mak  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi test etmek için  
  
- Bileşeni derleyin.  
  
     Bir derleyici uyarısı alacaksınız:  
  
    ```console  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Bu uyarı sonraki bölümde çözümlenir.  
  
## <a name="implementing-the-worker-methods"></a>Çalışan yöntemlerini uygulama  
 Şimdiye kadar, `PrimeNumberCalculator` bileşeni için desteklenen zaman uyumsuz kodu uyguladık. Artık gerçek işi yapan kodu uygulayabilirsiniz. Üç yöntem uygulayacaksınız: `CalculateWorker`, `BuildPrimeNumberList` ve `IsPrime`. Birlikte, `BuildPrimeNumberList` ve `IsPrime`, test numarasının kare köküne kadar olan tüm asal sayıları bularak bir sayının asal olup olmadığını belirleyen Elekbıx 'in Ifeli olarak adlandırılan, iyi bilinen bir algoritmayı kapsar. Bu nokta tarafından hiçbir izleme bulunmazsa, test numarası asal olur.  
  
 Bu bileşen en yüksek verimlilik için yazılmışsa, farklı test numaraları için çeşitli etkinleştirmeleri tarafından bulunan tüm asal sayıları hatırlayacaktı. Ayrıca, 2, 3 ve 5 gibi önemsiz bir göz atın. Bu örneğin amacı, zaman alan işlemlerin zaman uyumsuz olarak nasıl yürütülebileceğini göstermek, ancak bu iyileştirmelerin sizin için bir alıştırma olarak ayrılmamaktır.  
  
 @No__t-0 yöntemi bir temsilciye sarmalanmış ve `BeginInvoke` çağrısıyla zaman uyumsuz olarak çağrıldı.  
  
> [!NOTE]
> İlerleme raporlaması `BuildPrimeNumberList` yönteminde uygulanır. Hızlı bilgisayarlarda `ProgressChanged` olayları hızlı bir şekilde art arda oluşturulabilir. Bu olayların oluşturulduğu istemci iş parçacığı, bu durumu işleyebilmelidir. Kullanıcı arabirimi kodu iletilerle taştı ve devam edemiyor olabilir ve yanıt vermeyebilir. Bu durumu işleyen örnek bir kullanıcı arabirimi için bkz. [nasıl yapılır: olay tabanlı zaman uyumsuz düzendeki bir Istemciyi uygulama](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Ana sayı hesaplamasını zaman uyumsuz olarak yürütmek için:  
  
1. @No__t-0 yardımcı program yöntemini uygulayın. Bu, belirtilen görev KIMLIĞI için görev yaşam süresi toplamayı denetler ve görev KIMLIĞI bulunmazsa `true` döndürür.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2. @No__t-0 yöntemini uygulayın. İki parametre alır: sınanacak sayı ve bir <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3. @No__t Uygula-0. İki parametre alır: sınanacak sayı ve bir <xref:System.ComponentModel.AsyncOperation>. İlerleme ve artımlı sonuçları raporlamak için <xref:System.ComponentModel.AsyncOperation> kullanır. Bu, istemcinin olay işleyicilerinin uygulama modeli için uygun iş parçacığında veya içerikte çağrılması sağlar. @No__t-0 bir asal sayı bulduğunda, bunu `ProgressChanged` olayı için istemcinin olay işleyicisine artımlı bir sonuç olarak bildirir. Bu, `LatestPrimeNumber` adlı bir eklenmiş özelliği olan `CalculatePrimeProgressChangedEventArgs` adlı <xref:System.ComponentModel.ProgressChangedEventArgs> ' dan türetilmiş bir sınıf gerektirir.  
  
     @No__t-0 yöntemi Ayrıca, düzenli aralıklarla `TaskCanceled` yöntemini çağırır ve Yöntem `true` döndürürse çıkar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4. @No__t Uygula-0. Üç parametre vardır: bilinen asal sayıların listesi, sınanacak sayı ve bulunan ilk bölen için bir çıktı parametresi. Asal sayıların listesi verildiğinde, test numarasının asal olup olmadığını belirler.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5. @No__t-0 ' dan <xref:System.ComponentModel.ProgressChangedEventArgs> türet. Bu sınıf, `ProgressChanged` olayı için istemcinin olay işleyicisine artımlı sonuçlar bildirmek için gereklidir. @No__t-0 adlı, eklenen bir özelliğe sahiptir.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Mak  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi test etmek için  
  
- Bileşeni derleyin.  
  
     Her şey yazılmak üzere kaldığı zaman uyumsuz işlemleri başlatma ve iptal etme metodlarıdır, `CalculatePrimeAsync` ve `CancelAsync`.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Start ve Cancel yöntemlerini uygulama  
 Çalışan bir temsilci üzerinde `BeginInvoke` çağırarak çalışan yöntemini kendi iş parçacığında başlatabilirsiniz. Belirli bir zaman uyumsuz işlemin ömrünü yönetmek için, <xref:System.ComponentModel.AsyncOperationManager> yardımcı sınıfında <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> yöntemini çağırın. Bu, istemcinin olay işleyicilerinde doğru iş parçacığına veya içeriğe çağrı getiren bir <xref:System.ComponentModel.AsyncOperation> döndürür.  
  
 Karşılık gelen <xref:System.ComponentModel.AsyncOperation> ' de <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> ' a çağırarak belirli bir bekleyen işlemi iptal edersiniz. Bu işlem sonlanır ve <xref:System.ComponentModel.AsyncOperation> ' a yönelik sonraki çağrılar bir özel durum oluşturur.  
  
### <a name="to-implement-start-and-cancel-functionality"></a>Start ve Cancel işlevlerini uygulamak için:  
  
1. @No__t-0 yöntemini uygulayın. İstemci tarafından sağlanan belirtecin (görev KIMLIĞI), şu anda bekleyen görevleri temsil eden tüm belirteçlere göre benzersiz olduğundan emin olun. İstemci benzersiz olmayan bir belirtece geçerse `CalculatePrimeAsync` bir özel durum oluşturur. Aksi takdirde, belirteç görev KIMLIĞI koleksiyonuna eklenir.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2. @No__t-0 yöntemini uygulayın. Belirteç koleksiyonunda `taskId` parametresi varsa, kaldırılır. Bu, çalışmayı başlatmayan iptal edilen görevleri engeller. Görev çalışıyorsa, görev KIMLIĞININ ömür koleksiyonundan kaldırıldığını algıladığında `BuildPrimeNumberList` yöntemi çıkar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Mak  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi test etmek için  
  
- Bileşeni derleyin.  
  
 @No__t-0 bileşeni artık tamamlanmıştır ve kullanıma hazırdır.  
  
 @No__t-0 bileşenini kullanan örnek bir istemci için bkz. [nasıl yapılır: olay tabanlı zaman uyumsuz düzende Istemci uygulama](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 @No__t-1 yönteminin zaman uyumlu eşdeğerini `CalculatePrime` yazarak bu örneği doldurabilirsiniz. Bu, `PrimeNumberCalculator` bileşenini olay tabanlı zaman uyumsuz düzeniyle tamamen uyumlu hale getirir.  
  
 Farklı test numaraları için çeşitli etkinleştirmeleri tarafından bulunan tüm asal sayıların listesini koruyarak bu örneği geliştirebilirsiniz. Bu yaklaşımı kullanarak, her görev önceki görevler tarafından gerçekleştirilen işin avantajına sahip olur. Bu listeyi `lock` bölgeleriyle korumamaya dikkat edin, bu nedenle listeye farklı iş parçacıkları tarafından erişim serileştirilir.  
  
 Bu örneği Ayrıca, 2, 3 ve 5 gibi önemsiz ve daha fazla bilgi için test ederek geliştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
