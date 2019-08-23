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
ms.openlocfilehash: 2652c080951823e5289785b5906d2b0f48f5d658
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950781"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama
Fark edilebilir gecikme olabilecek bazı işlemlerle bir sınıf yazıyorsanız, [olay tabanlı zaman uyumsuz düzene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)' ı uygulayarak zaman uyumsuz işlevsellik vermeyi düşünün.  
  
 Bu izlenecek yol, olay tabanlı zaman uyumsuz model uygulayan bir bileşenin nasıl oluşturulacağını göstermektedir. Bu, bileşenin ASP.net, konsol uygulamaları ve <xref:System.ComponentModel?displayProperty=nameWithType> Windows Forms uygulamaları dahil olmak üzere herhangi bir uygulama modelinde doğru şekilde çalıştığından emin olmak üzere ad alanından yardımcı sınıflar kullanılarak uygulanır. Bu bileşen ayrıca bir <xref:System.Windows.Forms.PropertyGrid> denetimle ve kendi özel tasarımcılarına göre de genişletilebilir.  
  
 İşlem sırasında, ana sayıları zaman uyumsuz olarak hesaplayan bir uygulamaya sahip olursunuz. Uygulamanız ana kullanıcı arabirimi (UI) iş parçacığına ve her asal sayı hesaplaması için bir iş parçacığına sahip olacaktır. Büyük bir sayının asal olup olmadığını test etmek, fark edilebilir bir süre alabilir, ancak ana kullanıcı arabirimi iş parçacığı bu gecikmeyle kesintiye uğramaz ve hesaplamalar sırasında form yanıt verir. Aynı anda istediğiniz sayıda hesaplama çalıştırabilir ve bekleyen hesaplamaları seçmeli olarak iptal edebilirsiniz.  
  
 Bu izlenecek yolda gösterilen görevler şunlardır:  
  
- Bileşeni oluşturma  
  
- Ortak zaman uyumsuz olayları ve temsilcileri tanımlama  
  
- Özel temsilciler tanımlama  
  
- Ortak olayları uygulama  
  
- Tamamlama yöntemini uygulama  
  
- Çalışan yöntemlerini uygulama  
  
- Start ve Cancel yöntemlerini uygulama  
  
 Bu konudaki kodu tek bir liste olarak kopyalamak için bkz [. nasıl yapılır: Olay tabanlı zaman uyumsuz deseninin](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)istemcisini uygulayın.  
  
## <a name="creating-the-component"></a>Bileşeni oluşturma  
 İlk adım, olay tabanlı zaman uyumsuz düzene uygulanacak bileşeni oluşturmaktır.  
  
### <a name="to-create-the-component"></a>Bileşeni oluşturmak için  
  
- `PrimeNumberCalculator` Öğesinden<xref:System.ComponentModel.Component>devralan adlı bir sınıf oluşturun.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Ortak zaman uyumsuz olayları ve temsilcileri tanımlama  
 Bileşeniniz, olayları kullanarak istemcilerle iletişim kurar. _MethodName_ olay uyarıları istemcileri, zaman uyumsuz bir görevin tamamlanmasını sağlar ve _MethodName_**ProgressChanged & lt** olayı, zaman uyumsuz bir görevin ilerleme durumunu istemcilere bildirir.  
  
### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Bileşeninizin istemcilerine yönelik zaman uyumsuz olayları tanımlamak için:  
  
1. <xref:System.Threading?displayProperty=nameWithType> Ve<xref:System.Collections.Specialized?displayProperty=nameWithType> ad alanlarını dosyanızın en üstüne aktarın.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2. `PrimeNumberCalculator` Sınıf tanımından önce, ilerleme ve tamamlanma olayları için temsilciler bildirin.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3. `PrimeNumberCalculator` Sınıf tanımında, ilerlemeyi raporlamaya ve istemcilere tamamlamaya yönelik olayları bildirin.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4. Sınıf tanımından sonra, her hesaplamanın sonucunu `CalculatePrimeCompletedEventArgs` , `CalculatePrimeCompleted`. Event için istemcinin olay işleyicisine bildirmek üzere sınıfını türetebilirsiniz. `PrimeNumberCalculator` Bu sınıf, `AsyncCompletedEventArgs` özelliklere ek olarak, istemcinin hangi sayının test edildiğini, asal olup olmadığını ve ilk bölen ana değilse ne olduğunu belirlemesini sağlar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi test etmek için  
  
- Bileşeni derleyin.  
  
     İki derleyici uyarısı alacaksınız:  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Bu uyarılar sonraki bölümde temizlenir.  
  
## <a name="defining-private-delegates"></a>Özel temsilciler tanımlama  
 `PrimeNumberCalculator` Bileşenin zaman uyumsuz yönleri, olarak bilinen özel bir <xref:System.Threading.SendOrPostCallback>temsilci ile dahili olarak uygulanır. Bir <xref:System.Threading.SendOrPostCallback> <xref:System.Threading.ThreadPool> iş parçacığında yürütülen bir geri çağırma yöntemini temsil eder. Geri çağırma yöntemi türünde <xref:System.Object>tek bir parametre alan bir imzaya sahip olmalıdır, bu, bir sarmalayıcı sınıfında temsilciler arasında durum geçirmeniz gereken anlamına gelir. Daha fazla bilgi için bkz. <xref:System.Threading.SendOrPostCallback>.  
  
### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Bileşeninizin iç zaman uyumsuz davranışını uygulamak için:  
  
1. <xref:System.Threading.SendOrPostCallback> Sınıfında Temsilciler`PrimeNumberCalculator` bildirin ve oluşturun. <xref:System.Threading.SendOrPostCallback> Adlı`InitializeDelegates`bir yardımcı program yönteminde nesneleri oluşturun.  
  
     İki temsilcinin olması gerekir: biri istemciye ilerleme durumunu raporlamak için bir diğeri ise istemciye tamamlanmayı rapor eder.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2. Bileşenin oluşturucusunda `InitializeDelegates` yöntemini çağırın.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3. Zaman uyumsuz olarak yapılacak gerçek `PrimeNumberCalculator` işleri işleyen sınıfta bir temsilci bildirin. Bu temsilci, bir sayının asal olup olmadığını test eden çalışan yöntemini sarmalanmış. Temsilci, zaman uyumsuz <xref:System.ComponentModel.AsyncOperation> işlemin ömrünü izlemek için kullanılacak bir parametre alır.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4. Bekleyen zaman uyumsuz işlemlerin yaşam sürelerini yönetmek için bir koleksiyon oluşturun. İstemci, yürütüldüğü ve tamamlandıkları sırada işlemleri izlemek için bir yönteme ihtiyaç duyuyor ve bu izleme, istemci zaman uyumsuz metoda çağrı yaptığında, istemcinin benzersiz bir belirteç veya görev KIMLIĞI geçmesini gerektirerek yapılır. `PrimeNumberCalculator` Bileşen, görev kimliğini karşılık gelen çağrıdan ilişkilendirerek her bir çağrıyı takip etmelidir. İstemci benzersiz olmayan bir görev kimliği geçirirse, `PrimeNumberCalculator` bileşen bir özel durum yükseltmelidir.  
  
     Bileşen `PrimeNumberCalculator` , adlı özel bir <xref:System.Collections.Specialized.HybridDictionary>koleksiyon sınıfını kullanarak görev kimliğini izler. Sınıf tanımında, adlı bir <xref:System.Collections.Specialized.HybridDictionary> adı `userTokenToLifetime`oluşturun.  
  
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
  
 Bu yöntem, istemcinin görev KIMLIĞININ, benzersiz istemci belirteçleri iç koleksiyonundan kaldırıldığı yerdir. Bu yöntem, karşılık gelen <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> <xref:System.ComponentModel.AsyncOperation>yöntemini çağırarak belirli bir zaman uyumsuz işlemin ömrünü de sonlandırır. Bu çağrı, uygulama modeli için uygun olan iş parçacığında tamamlanma olayını başlatır. Yöntemi çağrıldıktan sonra, bu <xref:System.ComponentModel.AsyncOperation> örneği artık kullanılamaz ve bunu kullanmaya yönelik sonraki girişimler bir özel durum oluşturur. <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>  
  
 `CompletionMethod` İmza, zaman uyumsuz işlemin sonucunu anlatmak için gereken tüm durumu tutmalıdır. Bu, belirli zaman uyumsuz işlem tarafından test edilen numaranın, sayının asal olup olmadığı ve asal sayı değilse ilk bölenin değerinin durumunu barındırır. Ayrıca, oluşan tüm özel durumları ve <xref:System.ComponentModel.AsyncOperation> bu göreve karşılık gelen durumu açıklayan durumu da barındırır.  
  
### <a name="to-complete-an-asynchronous-operation"></a>Zaman uyumsuz bir işlemi gerçekleştirmek için:  
  
- Tamamlama yöntemini uygulayın. İstemciye, istemci tarafından döndürülen bir `CalculatePrimeCompletedEventArgs` istemciyi `CalculatePrimeCompletedEventHandler`doldurmak için kullandığı altı parametre alır. İstemci görev KIMLIĞI belirtecini iç koleksiyondan kaldırır ve çağrısı <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>ile zaman uyumsuz işlemin ömrünü sonlandırır. , <xref:System.ComponentModel.AsyncOperation> Uygulama modeli için uygun olan iş parçacığına veya içeriğe yapılan çağrıyı sıralar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi test etmek için  
  
- Bileşeni derleyin.  
  
     Bir derleyici uyarısı alacaksınız:  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Bu uyarı sonraki bölümde çözümlenir.  
  
## <a name="implementing-the-worker-methods"></a>Çalışan yöntemlerini uygulama  
 Şimdiye kadar, `PrimeNumberCalculator` bileşen için zaman uyumsuz kod destekleme kodu uyguladık. Artık gerçek işi yapan kodu uygulayabilirsiniz. Üç yöntem uygulayacaksınız: `CalculateWorker`, `BuildPrimeNumberList`, ve `IsPrime`. Birlikte, `BuildPrimeNumberList` `IsPrime` bir sayının, test numarasının kare köküne kadar tüm asal sayıları bularak bir sayının asal olup olmadığını belirleyen, en iyi bilinen bir algoritma oluşturur. Bu nokta tarafından hiçbir izleme bulunmazsa, test numarası asal olur.  
  
 Bu bileşen en yüksek verimlilik için yazılmışsa, farklı test numaraları için çeşitli etkinleştirmeleri tarafından bulunan tüm asal sayıları hatırlayacaktı. Ayrıca, 2, 3 ve 5 gibi önemsiz bir göz atın. Bu örneğin amacı, zaman alan işlemlerin zaman uyumsuz olarak nasıl yürütülebileceğini göstermek, ancak bu iyileştirmelerin sizin için bir alıştırma olarak ayrılmamaktır.  
  
 Yöntemi bir temsilciye sarmalanmış ve `BeginInvoke`çağrısı ile zaman uyumsuz olarak çağırılır. `CalculateWorker`  
  
> [!NOTE]
> İlerleme raporlaması `BuildPrimeNumberList` yönteminde uygulanır. Hızlı bilgisayarlarda, `ProgressChanged` olaylar hızlı bir şekilde birbirini izleyen bir şekilde oluşturulabilir. Bu olayların oluşturulduğu istemci iş parçacığı, bu durumu işleyebilmelidir. Kullanıcı arabirimi kodu iletilerle taştı ve devam edemiyor olabilir ve yanıt vermeyebilir. Bu durumu işleyen örnek bir kullanıcı arabirimi için bkz [. nasıl yapılır: Olay tabanlı zaman uyumsuz deseninin](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)istemcisini uygulayın.  
  
### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Ana sayı hesaplamasını zaman uyumsuz olarak yürütmek için:  
  
1. `TaskCanceled` Yardımcı program yöntemini uygulayın. Bu, verilen görev kimliği için görev ömrü toplamayı denetler ve görev kimliği bulunmazsa `true` döndürür.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2. `CalculateWorker` Yöntemini uygulayın. İki parametre alır: sınanacak sayı ve bir <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3. Uygulayın `BuildPrimeNumberList`. İki parametre alır: sınanacak sayı ve bir <xref:System.ComponentModel.AsyncOperation>. İlerleme durumunu ve <xref:System.ComponentModel.AsyncOperation> artımlı sonuçları raporlamak için öğesini kullanır. Bu, istemcinin olay işleyicilerinin uygulama modeli için uygun iş parçacığında veya içerikte çağrılması sağlar. Bir asal sayı `ProgressChanged` `BuildPrimeNumberList` bulduğunda, bu, olayı için istemcinin olay işleyicisine artımlı bir sonuç olarak bildirir. Bu, eklenen bir özelliği <xref:System.ComponentModel.ProgressChangedEventArgs> `LatestPrimeNumber`olan adlı `CalculatePrimeProgressChangedEventArgs`öğesinden türetilmiş bir sınıf gerektirir.  
  
     Yöntemi ayrıca yöntemi düzenli olarak `TaskCanceled` çağırır ve Yöntem döndürüyorsa `true`çıkar. `BuildPrimeNumberList`  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4. Uygulayın `IsPrime`. Üç parametre vardır: bilinen asal sayıların listesi, sınanacak sayı ve bulunan ilk bölen için bir çıktı parametresi. Asal sayıların listesi verildiğinde, test numarasının asal olup olmadığını belirler.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5. `CalculatePrimeProgressChangedEventArgs` Türet .<xref:System.ComponentModel.ProgressChangedEventArgs> Bu sınıf, `ProgressChanged` olay için istemcinin olay işleyicisine artımlı sonuçlar bildirmek için gereklidir. Adında `LatestPrimeNumber`eklenen bir özelliğe sahiptir.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi test etmek için  
  
- Bileşeni derleyin.  
  
     Yazılması gereken işlemler, `CalculatePrimeAsync` `CancelAsync`zaman uyumsuz işlemleri başlatma ve iptal etme yöntemleridir.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Start ve Cancel yöntemlerini uygulama  
 Çalışan metodunu, sarmalayan temsilciyi çağırarak `BeginInvoke` kendi iş parçacığında başlatabilirsiniz. Belirli bir zaman uyumsuz işlemin ömrünü yönetmek için <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> <xref:System.ComponentModel.AsyncOperationManager> yardımcı sınıfında yöntemi çağırın. Bu, istemci <xref:System.ComponentModel.AsyncOperation>olay işleyicilerinde doğru iş parçacığına veya içeriğe çağrı getiren bir döndürür.  
  
 Kendisine karşılık gelen <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> <xref:System.ComponentModel.AsyncOperation>bir bekleyen işlemi çağırarak iptal edersiniz. Bu işlem sonlanır ve bundan sonraki çağrılar <xref:System.ComponentModel.AsyncOperation> bir özel durum oluşturur.  
  
### <a name="to-implement-start-and-cancel-functionality"></a>Start ve Cancel işlevlerini uygulamak için:  
  
1. `CalculatePrimeAsync` Yöntemini uygulayın. İstemci tarafından sağlanan belirtecin (görev KIMLIĞI), şu anda bekleyen görevleri temsil eden tüm belirteçlere göre benzersiz olduğundan emin olun. İstemci benzersiz olmayan bir belirteçte `CalculatePrimeAsync` geçerse bir özel durum oluşturur. Aksi takdirde, belirteç görev KIMLIĞI koleksiyonuna eklenir.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2. `CancelAsync` Yöntemini uygulayın. `taskId` Parametre belirteç koleksiyonunda varsa, kaldırılır. Bu, çalışmayı başlatmayan iptal edilen görevleri engeller. Görev çalışıyorsa `BuildPrimeNumberList` yöntemi, görev kimliğinin ömür koleksiyonundan kaldırıldığını algıladığında çıkar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi test etmek için  
  
- Bileşeni derleyin.  
  
 `PrimeNumberCalculator` Bileşen artık tamamlanmıştır ve kullanıma hazırdır.  
  
 `PrimeNumberCalculator` Bileşenini kullanan örnek bir istemci için bkz [. nasıl yapılır: Olay tabanlı zaman uyumsuz deseninin](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)istemcisini uygulayın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 `CalculatePrimeAsync` Yöntemin zaman uyumlu eşdeğerini yazarak `CalculatePrime`bu örneği doldurabilirsiniz. Bu, `PrimeNumberCalculator` bileşeni olay tabanlı zaman uyumsuz düzeniyle tamamen uyumlu hale getirir.  
  
 Farklı test numaraları için çeşitli etkinleştirmeleri tarafından bulunan tüm asal sayıların listesini koruyarak bu örneği geliştirebilirsiniz. Bu yaklaşımı kullanarak, her görev önceki görevler tarafından gerçekleştirilen işin avantajına sahip olur. Bu listeyi `lock` bölgelerle korumamaya dikkat edin, bu nedenle listeye farklı iş parçacıkları tarafından erişim serileştirilir.  
  
 Bu örneği Ayrıca, 2, 3 ve 5 gibi önemsiz ve daha fazla bilgi için test ederek geliştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Arka planda Işlem çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
