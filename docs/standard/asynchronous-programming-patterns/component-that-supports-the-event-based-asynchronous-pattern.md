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
ms.openlocfilehash: 83a60e0e793f33b8b0a1cec8342942fd05c82f55
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289895"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama
Fark edilebilir gecikme olabilecek bazı işlemlerle bir sınıf yazıyorsanız, [olay tabanlı zaman uyumsuz düzene genel bakış](event-based-asynchronous-pattern-overview.md)' ı uygulayarak zaman uyumsuz işlevsellik vermeyi düşünün.  
  
 Bu izlenecek yol, olay tabanlı zaman uyumsuz model uygulayan bir bileşenin nasıl oluşturulacağını göstermektedir. Bu, <xref:System.ComponentModel?displayProperty=nameWithType> bileşenin ASP.net, konsol uygulamaları ve Windows Forms uygulamaları dahil olmak üzere herhangi bir uygulama modelinde doğru şekilde çalıştığından emin olmak üzere ad alanından yardımcı sınıflar kullanılarak uygulanır. Bu bileşen ayrıca bir <xref:System.Windows.Forms.PropertyGrid> denetimle ve kendi özel tasarımcılarına göre de genişletilebilir.  
  
 İşlem sırasında, ana sayıları zaman uyumsuz olarak hesaplayan bir uygulamaya sahip olursunuz. Uygulamanız ana kullanıcı arabirimi (UI) iş parçacığına ve her asal sayı hesaplaması için bir iş parçacığına sahip olacaktır. Büyük bir sayının asal olup olmadığını test etmek, fark edilebilir bir süre alabilir, ancak ana kullanıcı arabirimi iş parçacığı bu gecikmeyle kesintiye uğramaz ve hesaplamalar sırasında form yanıt verir. Aynı anda istediğiniz sayıda hesaplama çalıştırabilir ve bekleyen hesaplamaları seçmeli olarak iptal edebilirsiniz.  
  
 Bu izlenecek yolda gösterilen görevler şunlardır:  
  
- Bileşeni oluşturma  
  
- Ortak zaman uyumsuz olayları ve temsilcileri tanımlama  
  
- Özel temsilciler tanımlama  
  
- Ortak olayları uygulama  
  
- Tamamlama yöntemini uygulama  
  
- Çalışan yöntemlerini uygulama  
  
- Start ve Cancel yöntemlerini uygulama  
  
 Bu konudaki kodu tek bir liste olarak kopyalamak için bkz. [nasıl yapılır: olay tabanlı zaman uyumsuz düzendeki bir Istemciyi uygulama](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Bileşeni oluşturma  
 İlk adım, olay tabanlı zaman uyumsuz düzene uygulanacak bileşeni oluşturmaktır.  
  
### <a name="to-create-the-component"></a>Bileşeni oluşturmak için  
  
- Öğesinden devralan adlı bir sınıf oluşturun `PrimeNumberCalculator` <xref:System.ComponentModel.Component> .  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Ortak zaman uyumsuz olayları ve temsilcileri tanımlama  
 Bileşeniniz, olayları kullanarak istemcilerle iletişim kurar. _MethodName_**olay uyarıları** istemcileri, zaman uyumsuz bir görevin tamamlanmasını sağlar ve _MethodName_**ProgressChanged & lt** olayı, zaman uyumsuz bir görevin ilerleme durumunu istemcilere bildirir.  
  
### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Bileşeninizin istemcilerine yönelik zaman uyumsuz olayları tanımlamak için:  
  
1. <xref:System.Threading?displayProperty=nameWithType>Ve <xref:System.Collections.Specialized?displayProperty=nameWithType> ad alanlarını dosyanızın en üstüne aktarın.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2. `PrimeNumberCalculator`Sınıf tanımından önce, ilerleme ve tamamlanma olayları için temsilciler bildirin.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3. `PrimeNumberCalculator`Sınıf tanımında, ilerlemeyi raporlamaya ve istemcilere tamamlamaya yönelik olayları bildirin.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4. `PrimeNumberCalculator`Sınıf tanımından sonra, `CalculatePrimeCompletedEventArgs` her hesaplamanın sonucunu,. Event için istemcinin olay işleyicisine bildirmek üzere sınıfını türetebilirsiniz `CalculatePrimeCompleted` . `AsyncCompletedEventArgs`Bu sınıf, özelliklere ek olarak, istemcinin hangi sayının test edildiğini, asal olup olmadığını ve ilk bölen ana değilse ne olduğunu belirlemesini sağlar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Checkpoint  
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
 Bileşenin zaman uyumsuz yönleri, `PrimeNumberCalculator` olarak bilinen özel bir temsilci ile dahili olarak uygulanır <xref:System.Threading.SendOrPostCallback> . Bir <xref:System.Threading.SendOrPostCallback> iş parçacığında yürütülen bir geri çağırma yöntemini temsil eder <xref:System.Threading.ThreadPool> . Geri çağırma yöntemi türünde tek bir parametre alan bir imzaya sahip olmalıdır <xref:System.Object> , bu, bir sarmalayıcı sınıfında temsilciler arasında durum geçirmeniz gereken anlamına gelir. Daha fazla bilgi için bkz. <xref:System.Threading.SendOrPostCallback>.  
  
### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Bileşeninizin iç zaman uyumsuz davranışını uygulamak için:  
  
1. Sınıfında temsilciler bildirin ve oluşturun <xref:System.Threading.SendOrPostCallback> `PrimeNumberCalculator` . <xref:System.Threading.SendOrPostCallback>Adlı bir yardımcı program yönteminde nesneleri oluşturun `InitializeDelegates` .  
  
     İki temsilcinin olması gerekir: biri istemciye ilerleme durumunu raporlamak için bir diğeri ise istemciye tamamlanmayı rapor eder.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2. `InitializeDelegates`Bileşenin oluşturucusunda yöntemini çağırın.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3. `PrimeNumberCalculator`Zaman uyumsuz olarak yapılacak gerçek işleri işleyen sınıfta bir temsilci bildirin. Bu temsilci, bir sayının asal olup olmadığını test eden çalışan yöntemini sarmalanmış. Temsilci, <xref:System.ComponentModel.AsyncOperation> zaman uyumsuz işlemin ömrünü izlemek için kullanılacak bir parametre alır.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4. Bekleyen zaman uyumsuz işlemlerin yaşam sürelerini yönetmek için bir koleksiyon oluşturun. İstemci, yürütüldüğü ve tamamlandıkları sırada işlemleri izlemek için bir yönteme ihtiyaç duyuyor ve bu izleme, istemci zaman uyumsuz metoda çağrı yaptığında, istemcinin benzersiz bir belirteç veya görev KIMLIĞI geçmesini gerektirerek yapılır. `PrimeNumberCalculator`Bileşen, görev kimliğini karşılık gelen çağrıdan ilişkilendirerek her bir çağrıyı takip etmelidir. İstemci benzersiz olmayan bir görev KIMLIĞI geçirirse, `PrimeNumberCalculator` bileşen bir özel durum yükseltmelidir.  
  
     `PrimeNumberCalculator`Bileşen, adlı özel bir koleksiyon sınıfını kullanarak görev kimliğini izler <xref:System.Collections.Specialized.HybridDictionary> . Sınıf tanımında, adlı bir adı oluşturun <xref:System.Collections.Specialized.HybridDictionary> `userTokenToLifetime` .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Ortak olayları uygulama  
 Olay tabanlı zaman uyumsuz model uygulayan bileşenler olayları kullanarak istemcilerle iletişim kurar. Bu olaylar, sınıfının yardımıyla uygun iş parçacığında çağrılır <xref:System.ComponentModel.AsyncOperation> .  
  
### <a name="to-raise-events-to-your-components-clients"></a>Bileşenin istemcilerine olay yükseltmek için:  
  
1. İstemcilere raporlama için ortak olayları uygulayın. İlerlemeyi raporlamak için bir olaya ve bir etkinliğin tamamlanmasını raporlamaya ihtiyacınız olacak.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Tamamlama yöntemini uygulama  
 Tamamlanma temsilcisi, zaman uyumsuz işlem başarılı tamamlama, hata veya iptal ile sona erdiğinde, temel alınan, serbest iş parçacıklı zaman uyumsuz davranışın çağıracağı yöntemdir. Bu çağrı, rastgele bir iş parçacığında gerçekleşir.  
  
 Bu yöntem, istemcinin görev KIMLIĞININ, benzersiz istemci belirteçleri iç koleksiyonundan kaldırıldığı yerdir. Bu yöntem, karşılık gelen yöntemini çağırarak belirli bir zaman uyumsuz işlemin ömrünü de sonlandırır <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> <xref:System.ComponentModel.AsyncOperation> . Bu çağrı, uygulama modeli için uygun olan iş parçacığında tamamlanma olayını başlatır. <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>Yöntemi çağrıldıktan sonra, bu örneği <xref:System.ComponentModel.AsyncOperation> artık kullanılamaz ve bunu kullanmaya yönelik sonraki girişimler bir özel durum oluşturur.  
  
 `CompletionMethod`İmza, zaman uyumsuz işlemin sonucunu anlatmak için gereken tüm durumu tutmalıdır. Bu, belirli zaman uyumsuz işlem tarafından test edilen numaranın, sayının asal olup olmadığı ve asal sayı değilse ilk bölenin değerinin durumunu barındırır. Ayrıca, oluşan tüm özel durumları ve <xref:System.ComponentModel.AsyncOperation> Bu göreve karşılık gelen durumu açıklayan durumu da barındırır.  
  
### <a name="to-complete-an-asynchronous-operation"></a>Zaman uyumsuz bir işlemi gerçekleştirmek için:  
  
- Tamamlama yöntemini uygulayın. İstemciye, istemci tarafından döndürülen bir istemciyi doldurmak için kullandığı altı parametre alır `CalculatePrimeCompletedEventArgs` `CalculatePrimeCompletedEventHandler` . İstemci görev KIMLIĞI belirtecini iç koleksiyondan kaldırır ve çağrısı ile zaman uyumsuz işlemin ömrünü sonlandırır <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> . , <xref:System.ComponentModel.AsyncOperation> Uygulama modeli için uygun olan iş parçacığına veya içeriğe yapılan çağrıyı sıralar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi test etmek için  
  
- Bileşeni derleyin.  
  
     Bir derleyici uyarısı alacaksınız:  
  
    ```console  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Bu uyarı sonraki bölümde çözümlenir.  
  
## <a name="implementing-the-worker-methods"></a>Çalışan yöntemlerini uygulama  
 Şimdiye kadar, bileşen için zaman uyumsuz kod destekleme kodu uyguladık `PrimeNumberCalculator` . Artık gerçek işi yapan kodu uygulayabilirsiniz. Üç yöntem uygulayacaksınız: `CalculateWorker` , `BuildPrimeNumberList` , ve `IsPrime` . Birlikte, `BuildPrimeNumberList` `IsPrime` bir sayının, test numarasının kare köküne kadar tüm asal sayıları bularak bir sayının asal olup olmadığını belirleyen, en iyi bilinen bir algoritma oluşturur. Bu nokta tarafından hiçbir izleme bulunmazsa, test numarası asal olur.  
  
 Bu bileşen en yüksek verimlilik için yazılmışsa, farklı test numaraları için çeşitli etkinleştirmeleri tarafından bulunan tüm asal sayıları hatırlayacaktı. Ayrıca, 2, 3 ve 5 gibi önemsiz bir göz atın. Bu örneğin amacı, zaman alan işlemlerin zaman uyumsuz olarak nasıl yürütülebileceğini göstermek, ancak bu iyileştirmelerin sizin için bir alıştırma olarak ayrılmamaktır.  
  
 `CalculateWorker`Yöntemi bir temsilciye sarmalanmış ve çağrısı ile zaman uyumsuz olarak çağırılır `BeginInvoke` .  
  
> [!NOTE]
> İlerleme raporlaması `BuildPrimeNumberList` yönteminde uygulanır. Hızlı bilgisayarlarda, `ProgressChanged` Olaylar hızlı bir şekilde birbirini izleyen bir şekilde oluşturulabilir. Bu olayların oluşturulduğu istemci iş parçacığı, bu durumu işleyebilmelidir. Kullanıcı arabirimi kodu iletilerle taştı ve devam edemiyor olabilir ve yanıt vermeyebilir. Bu durumu işleyen örnek bir kullanıcı arabirimi için bkz. [nasıl yapılır: olay tabanlı zaman uyumsuz düzendeki bir Istemciyi uygulama](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Ana sayı hesaplamasını zaman uyumsuz olarak yürütmek için:  
  
1. `TaskCanceled`Yardımcı program yöntemini uygulayın. Bu, verilen görev KIMLIĞI için görev ömrü toplamayı denetler ve `true` görev kimliği bulunmazsa döndürür.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2. Yöntemini uygulayın `CalculateWorker` . İki parametre alır: sınanacak sayı ve bir <xref:System.ComponentModel.AsyncOperation> .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3. Uygulayın `BuildPrimeNumberList` . İki parametre alır: sınanacak sayı ve bir <xref:System.ComponentModel.AsyncOperation> . <xref:System.ComponentModel.AsyncOperation>İlerleme durumunu ve artımlı sonuçları raporlamak için öğesini kullanır. Bu, istemcinin olay işleyicilerinin uygulama modeli için uygun iş parçacığında veya içerikte çağrılması sağlar. `BuildPrimeNumberList`Bir asal sayı bulduğunda, bu, olayı için istemcinin olay işleyicisine artımlı bir sonuç olarak bildirir `ProgressChanged` . Bu, <xref:System.ComponentModel.ProgressChangedEventArgs> `CalculatePrimeProgressChangedEventArgs` eklenen bir özelliği olan adlı öğesinden türetilmiş bir sınıf gerektirir `LatestPrimeNumber` .  
  
     Yöntemi `BuildPrimeNumberList` Ayrıca yöntemi düzenli olarak çağırır `TaskCanceled` ve Yöntem döndürüyorsa çıkar `true` .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4. Uygulayın `IsPrime` . Üç parametre vardır: bilinen asal sayıların listesi, sınanacak sayı ve bulunan ilk bölen için bir çıktı parametresi. Asal sayıların listesi verildiğinde, test numarasının asal olup olmadığını belirler.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5. Türet `CalculatePrimeProgressChangedEventArgs` <xref:System.ComponentModel.ProgressChangedEventArgs> . Bu sınıf, olay için istemcinin olay işleyicisine artımlı sonuçlar bildirmek için gereklidir `ProgressChanged` . Adında eklenen bir özelliğe sahiptir `LatestPrimeNumber` .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi test etmek için  
  
- Bileşeni derleyin.  
  
     Yazılması gereken işlemler, zaman uyumsuz işlemleri başlatma ve iptal etme yöntemleridir `CalculatePrimeAsync` `CancelAsync` .  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Start ve Cancel yöntemlerini uygulama  
 Çalışan metodunu, sarmalayan temsilciyi çağırarak kendi iş parçacığında başlatabilirsiniz `BeginInvoke` . Belirli bir zaman uyumsuz işlemin ömrünü yönetmek için <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> <xref:System.ComponentModel.AsyncOperationManager> yardımcı sınıfında yöntemi çağırın. Bu <xref:System.ComponentModel.AsyncOperation> , istemci olay işleyicilerinde doğru iş parçacığına veya içeriğe çağrı getiren bir döndürür.  
  
 Kendisine karşılık gelen bir bekleyen işlemi çağırarak iptal edersiniz <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> <xref:System.ComponentModel.AsyncOperation> . Bu işlem sonlanır ve bundan sonraki çağrılar <xref:System.ComponentModel.AsyncOperation> bir özel durum oluşturur.  
  
### <a name="to-implement-start-and-cancel-functionality"></a>Start ve Cancel işlevlerini uygulamak için:  
  
1. Yöntemini uygulayın `CalculatePrimeAsync` . İstemci tarafından sağlanan belirtecin (görev KIMLIĞI), şu anda bekleyen görevleri temsil eden tüm belirteçlere göre benzersiz olduğundan emin olun. İstemci benzersiz olmayan bir belirteçte geçerse `CalculatePrimeAsync` bir özel durum oluşturur. Aksi takdirde, belirteç görev KIMLIĞI koleksiyonuna eklenir.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2. Yöntemini uygulayın `CancelAsync` . `taskId`Parametre belirteç koleksiyonunda varsa, kaldırılır. Bu, çalışmayı başlatmayan iptal edilen görevleri engeller. Görev çalışıyorsa `BuildPrimeNumberList` yöntemi, görev kimliğinin ömür koleksiyonundan kaldırıldığını algıladığında çıkar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi test etmek için  
  
- Bileşeni derleyin.  
  
 `PrimeNumberCalculator`Bileşen artık tamamlanmıştır ve kullanıma hazırdır.  
  
 Bileşenini kullanan örnek bir istemci için `PrimeNumberCalculator` bkz. [nasıl yapılır: olay tabanlı zaman uyumsuz düzende istemci uygulama](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 `CalculatePrime`Yöntemin zaman uyumlu eşdeğerini yazarak bu örneği doldurabilirsiniz `CalculatePrimeAsync` . Bu, `PrimeNumberCalculator` bileşeni olay tabanlı zaman uyumsuz düzeniyle tamamen uyumlu hale getirir.  
  
 Farklı test numaraları için çeşitli etkinleştirmeleri tarafından bulunan tüm asal sayıların listesini koruyarak bu örneği geliştirebilirsiniz. Bu yaklaşımı kullanarak, her görev önceki görevler tarafından gerçekleştirilen işin avantajına sahip olur. Bu listeyi bölgelerle korumamaya dikkat `lock` edin, bu nedenle listeye farklı iş parçacıkları tarafından erişim serileştirilir.  
  
 Bu örneği Ayrıca, 2, 3 ve 5 gibi önemsiz ve daha fazla bilgi için test ederek geliştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](event-based-asynchronous-pattern-overview.md)
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](event-based-asynchronous-pattern-eap.md)
