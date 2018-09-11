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
ms.openlocfilehash: 3fd01e19bc8aad8af709aee2fdaa020d8192d530
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339558"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama
Bir sınıf belirgin gecikmeler kaynaklanabilecek bazı işlemleri yazıyorsanız uygulayarak zaman uyumsuz işlevleri vererek göz önünde bulundurun [olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Bu izlenecek yol, olay tabanlı zaman uyumsuz desen uygulayan bir bileşen oluşturma işlemini gösterir. Yardımcı sınıflarından kullanılarak uygulanır <xref:System.ComponentModel?displayProperty=nameWithType> bileşen herhangi bir uygulama modeli altında düzgün çalıştığını sağlar, ad alanı dahil olmak üzere [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], konsol uygulamaları ve Windows Forms uygulamaları. Bu bileşen ayrıca designable ile bir <xref:System.Windows.Forms.PropertyGrid> denetimi ve kendi özel tasarımcılar.  
  
 Aracılığıyla işiniz asal sayıları zaman uyumsuz olarak hesaplayan bir uygulamaya sahip olursunuz. Uygulamanızın ana kullanıcı arabirimi (UI) iş parçacığı ve her asal sayı hesaplaması için bir iş parçacığı olacaktır. Büyük bir sayı olup olmadığını test olsa da asal belirgin bir süre alabilir, ana UI iş parçacığı tarafından bu gecikme durdurulmaz ve form hesaplama sırasında hızlı yanıt veren olacaktır. Eş zamanlı olarak ve seçmeli olarak istediğiniz gibi çok sayıda hesaplama hesaplamalar iptal olarak çalıştırmak mümkün olacaktır.  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Bileşeni oluşturma  
  
-   Genel zaman uyumsuz olayları ve temsilcileri tanımlama  
  
-   Özel temsilcileri tanımlama  
  
-   Genel olaylar uygulama  
  
-   Tamamlama yöntemi uygulama  
  
-   Çalışan yöntemlerini uygulayan  
  
-   Uygulama başlatma ve iptal yöntemi  
  
 Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: olay tabanlı zaman uyumsuz desenin istemcisini uygulama](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Bileşeni oluşturma  
 İlk adım, olay tabanlı zaman uyumsuz desen uygulayan bileşeni oluşturmaktır.  
  
#### <a name="to-create-the-component"></a>Bileşeni oluşturmak için  
  
-   Adlı bir sınıf oluşturmak `PrimeNumberCalculator` öğesinden devralan <xref:System.ComponentModel.Component>.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Genel zaman uyumsuz olayları ve temsilcileri tanımlama  
 Bileşeniniz olayları kullanan istemciler için iletişim kurar. _MethodName_**tamamlandı** olay uyarıları zaman uyumsuz bir görev tamamlandığında istemcilere ve _MethodName_**ProgressChanged**olay bildiren istemciler ilerleme durumunu zaman uyumsuz bir görev.  
  
#### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Bileşeninizin istemciler için zaman uyumsuz olayları tanımlamak için:  
  
1.  İçeri aktarma <xref:System.Threading?displayProperty=nameWithType> ve <xref:System.Collections.Specialized?displayProperty=nameWithType> dosyanızın üst kısmındaki ad alanları.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2.  Önce `PrimeNumberCalculator` sınıf tanımını, ilerleme ve tamamlanmayı olay için temsilcileri bildirin.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3.  İçinde `PrimeNumberCalculator` sınıf tanımını, ilerleme ve tamamlanmayı istemcilere raporlama olayları bildirme.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4.  Sonra `PrimeNumberCalculator` sınıf tanımını, türetilen `CalculatePrimeCompletedEventArgs` her hesaplama için istemcinin olay işleyicisine sonucunu raporlama sınıfı `CalculatePrimeCompleted`.event. Ek olarak `AsyncCompletedEventArgs` özellikleri, bu sınıfı, hangi numarasını test edilmiştir, Hazırla olmasına ve birinci değilse, ilk bölen nedir belirlemek üzere istemci sağlar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu noktada, bileşen oluşturabilirsiniz.  
  
#### <a name="to-test-your-component"></a>Bileşeninizin test etmek için  
  
-   Bileşen derleyin.  
  
     İki Derleyici uyarılarını alırsınız:  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Bu uyarılar, sonraki bölümde temizlenir.  
  
## <a name="defining-private-delegates"></a>Özel temsilcileri tanımlama  
 Zaman uyumsuz yönlerini `PrimeNumberCalculator` bileşeni uygulanır dahili olarak bilinen özel bir temsilci ile bir <xref:System.Threading.SendOrPostCallback>. A <xref:System.Threading.SendOrPostCallback> üzerinde yürüten bir geri çağırma yöntemi temsil eden bir <xref:System.Threading.ThreadPool> iş parçacığı. Geri çağırma yöntemi türünde tek bir parametre alan bir imza içermelidir <xref:System.Object>, bunun anlamı bir sarmalayıcı sınıfı varyans arasında durumu iletmeniz gerekir. Daha fazla bilgi için bkz. <xref:System.Threading.SendOrPostCallback>.  
  
#### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Bileşeninizin iç zaman uyumsuz davranışı uygulamak için:  
  
1.  Bildirme ve oluşturma <xref:System.Threading.SendOrPostCallback> , temsilciler `PrimeNumberCalculator` sınıfı. Oluşturma <xref:System.Threading.SendOrPostCallback> bir yardımcı yöntem nesneleri adlı `InitializeDelegates`.  
  
     İki temsilci olduğunda gerekir: bir istemciye ilerleme durumunu raporlama ve bir raporlama istemci tamamlanması için.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2.  Çağrı `InitializeDelegates` bileşeninizin oluşturucuda yöntemi.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3.  Bir temsilci bildirmeniz `PrimeNumberCalculator` asıl işi zaman uyumsuz olarak yapılacak işler sınıfı. Bu temsilci, bir sayı üssü olup olmadığını test çalışan yönteminde sarmalar. Temsilciyi alır bir <xref:System.ComponentModel.AsyncOperation> zaman uyumsuz işlem ömrünü izlemek için kullanılan parametre.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4.  Eklentilerin ömrü bekleyen zaman uyumsuz işlemleri yönetmek için bir koleksiyon oluşturun. İstemci, yürütülen ve tamamlandı ve bu izleme istemcinin benzersiz belirteç veya görev kimliği, istemci zaman uyumsuz yöntem çağrısı yaptığında geçirilecek kılarak yapılan işlemleri izlemek için bir yönteme ihtiyaç duyar. `PrimeNumberCalculator` Bileşeni gerekir izlemek her çağrının görev kimliği ile ilgili kendi çağrılmasına ilişkilendirerek. İstemcinin benzersiz olmayan bir görev kimliği geçerse `PrimeNumberCalculator` bileşeni özel durum Yükselt gerekir.  
  
     `PrimeNumberCalculator` Bileşeni izler görev kimliği adlı bir özel koleksiyon sınıfını kullanarak bir <xref:System.Collections.Specialized.HybridDictionary>. Sınıf tanımında oluşturma bir <xref:System.Collections.Specialized.HybridDictionary> adlı `userTokenToLifetime`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Genel olaylar uygulama  
 Olay tabanlı zaman uyumsuz deseni uygulama bileşenleri olayları kullanan istemciler için iletişim kurar. Bu olaylar, Yardım uygun iş parçacığı üzerinde çağrılır <xref:System.ComponentModel.AsyncOperation> sınıfı.  
  
#### <a name="to-raise-events-to-your-components-clients"></a>Olayları bileşeninizin istemcilere yükseltmek için:  
  
1.  İstemcilere raporlama genel olaylar uygulayın. Bir olay için raporlama ilerleme ve raporlama tamamlanması için bir tane gerekir.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Tamamlama yöntemi uygulama  
 Tamamlama temsilci zaman uyumsuz işlemi başarıyla tamamlandığında, hata veya iptal etme sona erdiğinde, temel alınan, ücretsiz iş parçacıklı zaman uyumsuz davranışı çağıracaktır yöntemidir. Bu çağrıyı rastgele bir iş parçacığı üzerinde gerçekleştirilir.  
  
 Burada istemcinin görev kimliği benzersiz istemci belirteçlerin iç koleksiyondan kaldırılır, bu yöntem kullanılır. Ayrıca bu yöntemi çağırarak belirli bir zaman uyumsuz işlem ömrü sona <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> yöntemi buna karşılık gelen <xref:System.ComponentModel.AsyncOperation>. Bu çağrı, uygulama modeli için uygun olan iş parçacığında tamamlama olayını başlatır. Sonra <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> yöntemi çağrıldığında, bu örneği <xref:System.ComponentModel.AsyncOperation> artık kullanılmamaktadır ve kullanmak için sonraki girişiminde herhangi bir özel durum oluşturur.  
  
 `CompletionMethod` İmza gerekir tutun tüm durumu zaman uyumsuz işlemin sonucunu açıklamak gerekli. Asal sayı değilse asal ve değeri, ilk bölen sayı olup olmadığını, bu belirli zaman uyumsuz işlem tarafından test edilen numaralı durum tutar. Ayrıca bir durum oluştu, herhangi bir özel durumu açıklayan tutar ve <xref:System.ComponentModel.AsyncOperation> bu belirli görev için karşılık gelen.  
  
#### <a name="to-complete-an-asynchronous-operation"></a>Zaman uyumsuz bir işlemi tamamlamak için:  
  
-   Tamamlama yöntemini uygulayın. Doldurmak için kullandığı altı parametreleri alan bir `CalculatePrimeCompletedEventArgs` aracılığıyla istemcinin istemciye döndürülen `CalculatePrimeCompletedEventHandler`. İstemcinin görev kimlik belirteci iç koleksiyondan kaldırır ve bir çağrı ile zaman uyumsuz işlem yaşam süresi sona ermeden <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>. <xref:System.ComponentModel.AsyncOperation> İş parçacığı veya uygulama modeli için uygun olan bir bağlam çağrısı sürekliliğe devreder.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu noktada, bileşen oluşturabilirsiniz.  
  
#### <a name="to-test-your-component"></a>Bileşeninizin test etmek için  
  
-   Bileşen derleyin.  
  
     Bir derleyici uyarısı alırsınız:  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Sonraki bölümde bu uyarı çözümlenir.  
  
## <a name="implementing-the-worker-methods"></a>Çalışan yöntemlerini uygulayan  
 Destek zaman uyumsuz kod için şu ana kadar uyguladıysanız `PrimeNumberCalculator` bileşeni. Şimdi asıl işi yapan kod uygulayabilirsiniz. Üç yöntemi uygular: `CalculateWorker`, `BuildPrimeNumberList`, ve `IsPrime`. Birlikte `BuildPrimeNumberList` ve `IsPrime` Sieve, test Sayının karekökünü kadar tüm asal sayıları bularak bir sayı üssü olup olmadığını belirleyen Eratosthenes, adlı iyi bilinen bir algoritma oluşturan. Bu nokta hiçbir divisors bulunamazsa, test asal sayısıdır.  
  
 Bu bileşen için en yüksek verimliliğin yazılmışsa, çeşitli çağrıları farklı test sayılar için tarafından bulunan tüm asal sayıları unutmayın. 2, 3 ve 5 gibi Önemsiz divisors için ayrıca kontrol. Bu örneğin amacı, ne zaman operations göstermektir bu iyileştirmeler, bir alıştırma olarak kalması için zaman uyumsuz olarak, ancak yürütülebilir.  
  
 `CalculateWorker` Yöntemi bir Temsilcide paketlenir ve zaman uyumsuz olarak çağrısı ile çağrılan `BeginInvoke`.  
  
> [!NOTE]
>  İlerleme durumunu bildirme içinde gerçekleştirilir `BuildPrimeNumberList` yöntemi. Hızlı bilgisayarlarda `ProgressChanged` olayları hızlı art arda gerçekleştirilen. İstemci iş parçacığı üzerinde bu olaylar oluşturulur, bu durum işleyebilir olması gerekir. Kullanıcı arabirimi kodu davranışı asılı elde edilen iletilerle yayılmamış ve, devam edilemiyor olabilir. Bu durum işleyen bir örnek kullanıcı arabirimi için bkz: [nasıl yapılır: olay tabanlı zaman uyumsuz desenin istemcisini uygulama](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
#### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Asal numarası hesaplamayı zaman uyumsuz olarak çalıştırmak için:  
  
1.  Uygulama `TaskCanceled` yardımcı yöntemi. Bu görev ömrü koleksiyonunun belirtilen görev kimliği denetler ve döndürür `true` , görev kimliği bulunamadı.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2.  Uygulama `CalculateWorker` yöntemi. İki parametre alır: bir test etmek için sayı ve bir <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3.  Uygulama `BuildPrimeNumberList`. İki parametre alır: test etmek için sayı ve bir <xref:System.ComponentModel.AsyncOperation>. Kullandığı <xref:System.ComponentModel.AsyncOperation> ilerleme durumunu ve artımlı sonuçları. Bu, istemcinin olay işleyicileri, uygun iş parçacığı veya uygulama modeli için bağlam çağırılır sağlar. Zaman `BuildPrimeNumberList` asal sayı bir bulursa, rapor bu artımlı bir sonucu olarak istemcinin olay işleyicisi için `ProgressChanged` olay. Bu, türetilen bir sınıf gerektirir <xref:System.ComponentModel.ProgressChangedEventArgs>adlı `CalculatePrimeProgressChangedEventArgs`, hangi bir adlı bir özellik eklemiştir `LatestPrimeNumber`.  
  
     `BuildPrimeNumberList` Yöntemi de düzenli olarak çağıran `TaskCanceled` yöntemi ve yöntem döndürüyorsa çıkar `true`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4.  Uygulama `IsPrime`. Üç parametreleri alır: bilinen asal sayıları, test etmek için sayı ve bir output parametresi bulunan ilk bölen için listesi. Asal sayıları içeren listenin göz önünde bulundurulduğunda, bu test sayı üssü olup olmadığını belirler.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5.  Türetilen `CalculatePrimeProgressChangedEventArgs` gelen <xref:System.ComponentModel.ProgressChangedEventArgs>. Bu sınıf için istemcinin olay işleyicisine artımlı sonuçlarını raporlama için gerekli `ProgressChanged` olay. Adlı bir özelliği eklendi sahip `LatestPrimeNumber`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu noktada, bileşen oluşturabilirsiniz.  
  
#### <a name="to-test-your-component"></a>Bileşeninizin test etmek için  
  
-   Bileşen derleyin.  
  
     Tüm bu yazılacak kalır başlatmak ve zaman uyumsuz işlemleri iptal etmek için yöntemler şunlardır `CalculatePrimeAsync` ve `CancelAsync`.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Uygulama başlatma ve iptal yöntemi  
 Çalışan yöntemi çağırarak kendi iş parçacığında Başlat `BeginInvoke` sarmaladığı temsilci üzerinde. Belirli bir zaman uyumsuz işlem ömrünü yönetmek için çağrı <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> metodunda <xref:System.ComponentModel.AsyncOperationManager> yardımcı sınıfı. Bu döndürür bir <xref:System.ComponentModel.AsyncOperation>, uygun iş parçacığı veya bağlam istemcinin olay işleyicileri çağrı sürekliliğe devreder.  
  
 Belirli bir bekleyen bir işlem iptal <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> , buna karşılık gelen <xref:System.ComponentModel.AsyncOperation>. Bu, işlemi ve yapılan sonraki çağrılar sona kendi <xref:System.ComponentModel.AsyncOperation> bir özel durum oluşturur.  
  
#### <a name="to-implement-start-and-cancel-functionality"></a>Başlangıç uygulamak ve iptal et işlevi:  
  
1.  Uygulama `CalculatePrimeAsync` yöntemi. İstemci tarafından sağlanan belirtecin (görev kimliği) göre şu anda bekleyen görevler temsil eden tüm belirteçlerin benzersiz olduğundan emin olun. İstemci benzersiz olmayan bir belirtece geçiyorsa `CalculatePrimeAsync` bir özel durum oluşturur. Aksi takdirde, belirteç, görev kimliği koleksiyona eklenir.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2.  Uygulama `CancelAsync` yöntemi. Varsa `taskId` parametresi var. belirteci koleksiyonda, kaldırılmadan. Bu, çalışmasını başlatılmayan iptal edilen görevler engeller. Görev çalışıyorsa `BuildPrimeNumberList` yöntemi, görev kimliği ömrü koleksiyondan kaldırıldı algıladığında çıkar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu noktada, bileşen oluşturabilirsiniz.  
  
#### <a name="to-test-your-component"></a>Bileşeninizin test etmek için  
  
-   Bileşen derleyin.  
  
 `PrimeNumberCalculator` Bileşendir artık tamamlandı ve kullanıma hazır.  
  
 Kullanan bir örnek istemci için `PrimeNumberCalculator` bileşeni Bkz [nasıl yapılır: olay tabanlı zaman uyumsuz desenin istemcisini uygulama](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu örnek yazarak doldurabilirsiniz `CalculatePrime`, zaman uyumlu karşılığı `CalculatePrimeAsync` yöntemi. Bunu yapmak `PrimeNumberCalculator` bileşeni olay tabanlı zaman uyumsuz desen ile tamamen uyumlu.  
  
 Bu örnekte, farklı test sayılar için çeşitli çağrılarına tarafından bulunan tüm asal sayıları listesini koruyarak artırabilir. Bu yaklaşımı kullanarak, önceki görevler tarafından çalışmanın her görev yararlı olacaktır. Bu liste korumak özen `lock` erişim listesine farklı iş parçacıkları tarafından seri hale getirilmiş şekilde bölgeleri.  
  
 Bu örnekte, 2, 3 ve 5 gibi Önemsiz divisors için test ederek de artırabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
