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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71957364"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama
Fark edilebilir gecikmelere neden olabilecek bazı işlemlere sahip bir sınıf yazıyorsanız, Olay tabanlı [Asynchronous Desen Genel Bakış'ı](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)uygulayarak bu sınıfa eşzamanlı işlevsellik vermeyi düşünün.  
  
 Bu izbis, Olay tabanlı Asynchronous Deseni'ni uygulayan bir bileşenin nasıl oluşturulacağını gösterir. Ad alanından <xref:System.ComponentModel?displayProperty=nameWithType> yardımcı sınıflar kullanılarak uygulanır, bu da bileşenin ASP.NET, Konsol uygulamaları ve Windows Forms uygulamaları da dahil olmak üzere herhangi bir uygulama modeli altında doğru çalışmasını sağlar. Bu bileşen aynı zamanda <xref:System.Windows.Forms.PropertyGrid> bir kontrol ve kendi özel tasarımcılar ile tasarlanabilir.  
  
 İşi bittiğinde, asal sayıları eşit olarak hesaplayan bir uygulamanız olacaktır. Uygulamanızda bir ana kullanıcı arabirimi (UI) iş parçacığı ve her asal sayı hesaplaması için bir iş parçacığı olacaktır. Çok sayıda asal olup olmadığını test etmek belirgin bir süre alabilir, ancak ana UI iş parçacığı bu gecikme tarafından kesintiye uğramaz ve form hesaplamalar sırasında yanıt olacaktır. Aynı anda istediğiniz kadar hesaplama çalıştırabilir ve bekleyen hesaplamaları seçarak iptal edebilirsiniz.  
  
 Bu gözden geçirmede gösterilen görevler şunlardır:  
  
- Bileşeni Oluşturma  
  
- Genel Eşzamanlı Olayları ve Temsilcileri Tanımlama  
  
- Özel Delegelerin Tanımlanması  
  
- Genel Etkinliklerin Uygulanması  
  
- Tamamlama Yönteminin Uygulanması  
  
- İşçi Yöntemlerinin Uygulanması  
  
- Başlat ve İptal Yöntemlerini Uygulama  
  
 Bu konudaki kodu tek bir giriş olarak kopyalamak [için bkz: Olay tabanlı Asynchronous Deseni'nin istemcisini uygulama.](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
  
## <a name="creating-the-component"></a>Bileşeni Oluşturma  
 İlk adım, Olay tabanlı Asynchronous Modelini uygulayacak bileşeni oluşturmaktır.  
  
### <a name="to-create-the-component"></a>Bileşeni oluşturmak için  
  
- 'den `PrimeNumberCalculator` <xref:System.ComponentModel.Component>devralan adlı bir sınıf oluşturun.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Genel Eşzamanlı Olayları ve Temsilcileri Tanımlama  
 Bileşeniniz olayları kullanarak istemcilere iletişim kurar. _MethodName_**Completed** olay asynchronous görevin tamamlanması için istemcileri uyarır ve _MethodName_**ProgressChanged** olay istemcileri bir eşzamanlı görevin ilerleme bilgilendirir.  
  
### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Bileşeninizin istemcileri için eşzamanlı olaylar tanımlamak için:  
  
1. Dosyanızın <xref:System.Threading?displayProperty=nameWithType> <xref:System.Collections.Specialized?displayProperty=nameWithType> en üstündeki ad alanlarını ve ad alanlarını içeri aktarın.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2. Sınıf `PrimeNumberCalculator` tanımından önce, ilerleme ve tamamlama olayları için temsilci bildirin.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3. Sınıf `PrimeNumberCalculator` tanımında, ilerleme ve tamamlama yı bildiren olayları istemcilere bildirin.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4. Sınıf `PrimeNumberCalculator` tanımından sonra, `CalculatePrimeCompletedEventArgs` her hesaplamanın sonucunu .event için istemcinin olay işleyicisine bildirmek için `CalculatePrimeCompleted`sınıfı türetin. Bu sınıf, `AsyncCompletedEventArgs` özelliklere ek olarak istemcinin hangi sayının test edildiğini, asal olup olmadığını ve asal değilse ilk bölenin ne olduğunu belirlemesini sağlar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi sınamak için  
  
- Bileşeni derle.  
  
     İki derleyici uyarısı alacaksınız:  
  
    ```console  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Bu uyarılar bir sonraki bölümde temizlenecektir.  
  
## <a name="defining-private-delegates"></a>Özel Delegelerin Tanımlanması  
 Bileşenin `PrimeNumberCalculator` eşzamanlı yönleri, ". <xref:System.Threading.SendOrPostCallback> A, <xref:System.Threading.SendOrPostCallback> iş parçacığı üzerinde çalıştıran <xref:System.Threading.ThreadPool> bir geri arama yöntemini temsil eder. Geri arama yöntemi, tek bir tür <xref:System.Object>parametresi alan bir imzaya sahip olmalıdır, bu da bir sarıcı sınıfındaki temsilciler arasında durumu geçmeniz gerektiği anlamına gelir. Daha fazla bilgi için bkz. <xref:System.Threading.SendOrPostCallback>.  
  
### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Bileşeninizin dahili eşzamanlı davranışını uygulamak için:  
  
1. Sınıftaki delegeleri <xref:System.Threading.SendOrPostCallback> bildirin `PrimeNumberCalculator` ve oluşturun. <xref:System.Threading.SendOrPostCallback> Nesneleri ' yi adı verilen `InitializeDelegates`bir yardımcı program yönteminde oluşturun.  
  
     Biri ilerlemeyi istemciye raporlamak için, diğeri de tamamlanmasını istemciye raporlamak için olmak üzere iki temsilciye ihtiyacınız olacaktır.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2. Bileşeninizin oluşturucusundaki `InitializeDelegates` yöntemi arayın.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3. Eşit bir şekilde `PrimeNumberCalculator` yapılacak fiili işi işleyen sınıfta bir temsilci bildirin. Bu temsilci, bir sayının asal olup olmadığını sınayan alt yöntemi sarar. Temsilci, eşzamanlı <xref:System.ComponentModel.AsyncOperation> işlemin ömrünü izlemek için kullanılacak bir parametre alır.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4. Bekleyen eşzamanlı işlemlerin ömür lerini yönetmek için bir koleksiyon oluşturun. İstemci, yürütülürken ve tamamlanırken işlemleri izlemek için bir yol gerekir ve bu izleme, istemci çağrıyı eşzamanlı yönteme yaptığında istemcinin benzersiz bir belirteci veya görev kimliği geçirmesini gerektirerek yapılır. Bileşen, `PrimeNumberCalculator` görev kimliğini ilgili çağırmayla ilişkilendirerek her aramayı takip etmelidir. İstemci benzersiz olmayan bir görev kimliği `PrimeNumberCalculator` geçerse, bileşenbir özel durum yükseltmesi gerekir.  
  
     Bileşen, `PrimeNumberCalculator` a <xref:System.Collections.Specialized.HybridDictionary>adı verilen özel bir koleksiyon sınıfı kullanarak görev kimliğini izler. Sınıf <xref:System.Collections.Specialized.HybridDictionary> tanımında, bir `userTokenToLifetime`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Genel Etkinliklerin Uygulanması  
 Olay tabanlı Asynchronous Modelini uygulayan bileşenler, olayları kullanarak istemcilere iletin. Bu olaylar <xref:System.ComponentModel.AsyncOperation> sınıfın yardımıyla uygun iş parçacığı üzerinde çağrılır.  
  
### <a name="to-raise-events-to-your-components-clients"></a>Bileşeninizin istemcilerine olayları yükseltmek için:  
  
1. İstemcilere raporlama kiçin herkese açık etkinlikleri uygulayın. İlerlemeyi raporlamak için bir olay ve tamamlanma yı raporlamak için bir olay gerekir.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Tamamlama Yönteminin Uygulanması  
 Tamamlama temsilcisi, eş zamanlı işlem başarılı tamamlama, hata veya iptal ile sona erdiğinde altta yatan, serbest iş parçacığı eşzamanlı eşzamanlı davranışın çağıracağı yöntemdir. Bu çağırma rasgele bir iş parçacığı üzerinde olur.  
  
 Bu yöntem, istemcinin görev kimliğinin benzersiz istemci belirteçleri iç koleksiyonundan kaldırıldığı yöntemdir. Bu yöntem aynı zamanda ilgili <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> <xref:System.ComponentModel.AsyncOperation>yöntem çağırarak belirli bir eşzamanlı işlemin ömrünü sona erdiriyor. Bu çağrı, uygulama modeli için uygun iş parçacığı üzerinde tamamlama olay yükseltir. <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> Yöntem çağrıldıktan sonra, bu <xref:System.ComponentModel.AsyncOperation> örnek artık kullanılamaz ve sonraki herhangi bir sonraki kullanılma girişimleri bir özel durum atacaktır.  
  
 İmza, `CompletionMethod` eşzamanlı işlemin sonucunu açıklamak için gerekli tüm durumu tutmalıdır. Bu özel eşzamanlı işlem tarafından test edilen sayı için durum tutar, sayı asal olup olmadığını, ve bir asal sayı değilse ilk bölenin değeri. Ayrıca, oluşan herhangi bir özel durum açıklayan <xref:System.ComponentModel.AsyncOperation> devlet tutar ve bu özel göreve karşılık gelen.  
  
### <a name="to-complete-an-asynchronous-operation"></a>Bir eşzamanlı işlemi tamamlamak için:  
  
- Tamamlama yöntemini uygulayın. İstemci aracılığıyla istemciye döndürülen `CalculatePrimeCompletedEventArgs` bir paramı doldurmak için kullandığı `CalculatePrimeCompletedEventHandler`altı parametre alır. İstemcinin görev kimliği belirtecisini iç koleksiyondan kaldırır ve eşzamanlı işlemin kullanım ömrünü <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>bir çağrıyla sona erdirir. Çağrıyı, <xref:System.ComponentModel.AsyncOperation> uygulama modeline uygun olan iş parçacığına veya içeriğe çağırır.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi sınamak için  
  
- Bileşeni derle.  
  
     Bir derleyici uyarısı alacaksınız:  
  
    ```console  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Bu uyarı sonraki bölümde çözülür.  
  
## <a name="implementing-the-worker-methods"></a>İşçi Yöntemlerinin Uygulanması  
 Şimdiye kadar, bileşen için destekleyici asynchronous kodu `PrimeNumberCalculator` uyguladınız. Artık fiili işi yapan kodu uygulayabilirsiniz. Üç yöntem `CalculateWorker`uygulayacak: `BuildPrimeNumberList`, `IsPrime`, ve . Birlikte, `BuildPrimeNumberList` `IsPrime` ve test numarasının kare köküne kadar tüm asal sayıları bularak bir sayının asal olup olmadığını belirleyen Eratosthenes Elek adlı tanınmış bir algoritma oluşur. Bu noktada bölen bulunmazsa, test numarası asal olur.  
  
 Bu bileşen maksimum verimlilik için yazılmışsa, farklı test numaraları için çeşitli çağırmalar tarafından keşfedilen tüm asal sayıları hatırlar. Ayrıca 2, 3 ve 5 gibi önemsiz bölenler için kontrol edecek. Bu örneğin amacı, zaman alan işlemlerin nasıl eşzamanlı olarak yürütülebileceğini göstermektir, böylece bu optimizasyonlar sizin için bir alıştırma olarak bırakılır.  
  
 Yöntem `CalculateWorker` bir temsilciye sarılır ve `BeginInvoke`'' için bir çağrı ile eş senkronize olarak çağrılır  
  
> [!NOTE]
> İlerleme raporlama `BuildPrimeNumberList` yönteminde uygulanır. Hızlı bilgisayarlarda `ProgressChanged` olaylar art arda yükseltilebilir. Bu olayların yükseltildiği istemci iş parçacığı, bu durumu ele alabilmesi gerekir. Kullanıcı arabirim kodu iletilerle dolup taşabilir ve buna yetişemez ve yanıt vermemeye neden olabilir. Bu durumu işleyen örnek bir kullanıcı arabirimi için [bkz.](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
  
### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Asal sayı hesaplamasını eşzamanlı olarak yürütmek için:  
  
1. Yardımcı `TaskCanceled` program yöntemini uygulayın. Bu, verilen görev kimliği için görev yaşam `true` boyu koleksiyonunu denetler ve görev kimliği bulunmazsa döndürür.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2. Yöntemi `CalculateWorker` uygulayın. Bu iki parametre alır: test <xref:System.ComponentModel.AsyncOperation>etmek için bir sayı ve bir .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3. Uygulayın. `BuildPrimeNumberList` Bu iki parametre alır: test <xref:System.ComponentModel.AsyncOperation>etmek için sayı ve bir . İlerleme ve <xref:System.ComponentModel.AsyncOperation> artımlı sonuçları bildirmek için kullanır. Bu, istemcinin olay işleyicilerinin uygulama modeli için uygun iş parçacığı veya bağlam üzerinde çağrılması sağlar. Bir `BuildPrimeNumberList` asal sayı bulduğunda, bunu `ProgressChanged` istemcinin olay işleyicisine artımlı bir sonuç olarak bildirir. Bu, bir ek özelliği `CalculatePrimeProgressChangedEventArgs`olan " , `LatestPrimeNumber`"türetilmiş" bir sınıf gerektirir. <xref:System.ComponentModel.ProgressChangedEventArgs>  
  
     Yöntem `BuildPrimeNumberList` de periyodik olarak `TaskCanceled` yöntem çağırır ve yöntem `true`dönerse çıkar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4. Uygulayın. `IsPrime` Üç parametre alır: bilinen asal sayıların listesi, test edilecek sayı ve bulunan ilk bölen için bir çıktı parametresi. Asal sayılar listesi göz önüne alındığında, test numarasının asal olup olmadığını belirler.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5. `CalculatePrimeProgressChangedEventArgs` Türetin <xref:System.ComponentModel.ProgressChangedEventArgs>. Bu sınıf, olay için istemcinin olay işleyicisine artımlı sonuçları raporlamak `ProgressChanged` için gereklidir. Bu denilen `LatestPrimeNumber`bir ek özelliği vardır.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi sınamak için  
  
- Bileşeni derle.  
  
     Yazılması gereken tek şey, eşzamanlı işlemleri başlatmak ve iptal `CalculatePrimeAsync` etmek `CancelAsync`için kullanılan yöntemlerdir ve.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Başlat ve İptal Yöntemlerini Uygulama  
 İşçi yöntemini, onu saran `BeginInvoke` temsilciyi çağırarak kendi iş parçacığı üzerinde başlamalısınız. Belirli bir eşzamanlı işlemin kullanım ömrünü yönetmek <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> <xref:System.ComponentModel.AsyncOperationManager> için, yardımcı sınıftayöntemi çağırırsınız. Bu, <xref:System.ComponentModel.AsyncOperation>istemcinin olay işleyicilerini uygun iş parçacığına veya içeriğe çağıran bir , döndürür.  
  
 Bekleyen belirli bir işlemi <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> ilgili <xref:System.ComponentModel.AsyncOperation>işlemi çağırarak iptal emzsiniz. Bu işlem sona erer ve sonraki <xref:System.ComponentModel.AsyncOperation> çağrılar bir özel durum ortaya atar.  
  
### <a name="to-implement-start-and-cancel-functionality"></a>Başlat ve İptal işlevini uygulamak için:  
  
1. Yöntemi `CalculatePrimeAsync` uygulayın. İstemci tarafından sağlanan belirteç (görev kimliği) şu anda bekleyen görevleri temsil eden tüm belirteçleri ile ilgili benzersiz olduğundan emin olun. İstemci benzersiz olmayan bir belirteç geçerse, `CalculatePrimeAsync` bir özel durum yükseltir. Aksi takdirde, belirteç görev kimliği koleksiyonuna eklenir.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2. Yöntemi `CancelAsync` uygulayın. `taskId` Parametre belirteç koleksiyonunda varsa, kaldırılır. Bu, çalışmaya başlamamış iptal edilen görevleri önler. Görev çalışıyorsa, `BuildPrimeNumberList` görev kimliğinin yaşam boyu koleksiyondan kaldırıldığını algıladığında yöntem çıkar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Bu noktada, bileşeni oluşturabilirsiniz.  
  
### <a name="to-test-your-component"></a>Bileşeninizi sınamak için  
  
- Bileşeni derle.  
  
 Bileşen `PrimeNumberCalculator` artık tamamlandı ve kullanıma hazır.  
  
 `PrimeNumberCalculator` Bileşeni kullanan örnek bir istemci için [bkz: Olay tabanlı Asynchronous Deseni'nin istemcisini uygulama.](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu örneği yöntemin eşzamanlı `CalculatePrime`eşdeğerini `CalculatePrimeAsync` yazarak doldurabilirsiniz. Bu, `PrimeNumberCalculator` bileşeni Olay tabanlı Asynchronous Deseni ile tam olarak uyumlu hale getirecektir.  
  
 Bu örneği, farklı test numaraları için çeşitli çağırmalar tarafından keşfedilen tüm asal sayıların listesini koruyarak geliştirebilirsiniz. Bu yaklaşımı kullanarak, her görev önceki görevler tarafından yapılan işten yararlanacaktır. Bölgelerle `lock` bu listeyi korumaya dikkat edin, bu nedenle listeye farklı iş parçacıklarına göre erişim seri hale getirilir.  
  
 Ayrıca, 2, 3 ve 5 gibi önemsiz bölenler için test ederek bu örneği geliştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
