---
title: "İzlenecek yol: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a3e69ea3de0ac418956d51c6e942e33d90575c1d
ms.sourcegitcommit: 957c696f25e39f923a827fc3ad5e8ab72768838c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2018
---
# <a name="walkthrough-implementing-a-component-that-supports-the-event-based-asynchronous-pattern"></a>İzlenecek yol: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama
Belirgin gecikmeler maruz kalabilirsiniz bazı işlemler sınıfıyla yazıyorsanız uygulayarak zaman uyumsuz işlevselliği vermiş göz önünde bulundurun [olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Bu kılavuz, olay tabanlı zaman uyumsuz desen uygulayan bileşeni oluşturulacağını gösterir. Yardımcı sınıfları kullanılarak uygulanır <xref:System.ComponentModel?displayProperty=nameWithType> bileşeni düzgün herhangi bir uygulama modeli altında çalıştığını sağlar, ad alanı dahil olmak üzere [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], konsol uygulamaları ve Windows Forms uygulamaları. Bu bileşen ayrıca ile designable bir <xref:System.Windows.Forms.PropertyGrid> denetimi ve kendi özel tasarımcıları.  
  
 Aracılığıyla olduğunda asal sayılar zaman uyumsuz olarak hesaplar bir uygulamaya sahip olursunuz. Uygulamanızı bir ana kullanıcı arabirimi (UI) iş parçacığı ve her asal sayı hesaplama için bir iş parçacığı sahip olacaktır. Büyük bir sayı olup olmadığını test rağmen asal belirgin bir süre alabilir, ana kullanıcı Arabirimi iş parçacığı tarafından bu gecikme kesilmez ve form hesaplamalar sırasında yanıt verebilir durumda olacaktır. Eş zamanlı olarak ve seçmeli olarak istediğiniz gibi pek çok hesaplama hesaplamalar iptal farklı çalıştır kuramaz.  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Bileşeni oluşturma  
  
-   Genel zaman uyumsuz olaylar ve temsilciler tanımlama  
  
-   Özel temsilcileri tanımlama  
  
-   Ortak olaylar uygulama  
  
-   Tamamlama yöntemi uygulama  
  
-   Çalışan yöntemlerini uygulama  
  
-   Uygulama başlangıç ve iptal yöntemleri  
  
 Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Bileşeni oluşturma  
 İlk adım, olay tabanlı zaman uyumsuz desen uygulamak bileşeni oluşturmaktır.  
  
#### <a name="to-create-the-component"></a>Bileşen oluşturmak için  
  
-   Adlı bir sınıf oluşturmak `PrimeNumberCalculator` devraldığı <xref:System.ComponentModel.Component>.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Genel zaman uyumsuz olaylar ve temsilciler tanımlama  
 Bileşeniniz olayları kullanan istemciler için iletişim kurar. *MethodName *** tamamlandı** olay uyarıları bir zaman uyumsuz görev tamamlandığında istemcilere ve *MethodName *** ProgressChanged** olay zaman uyumsuz bir görevi ilerlemesini istemcileri bildirir.  
  
#### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Bileşeniniz istemciler için zaman uyumsuz olayları tanımlamak için:  
  
1.  İçeri aktarma <xref:System.Threading?displayProperty=nameWithType> ve <xref:System.Collections.Specialized?displayProperty=nameWithType> dosyanızı üstündeki ad alanları.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2.  Önce `PrimeNumberCalculator` sınıf tanımının, ilerleme ve tamamlanmayı olayları için temsilciler bildirin.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3.  İçinde `PrimeNumberCalculator` sınıf tanımının, ilerleme ve tamamlanmayı istemcilere raporlama olayları bildirme.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4.  Sonra `PrimeNumberCalculator` sınıf tanımının, türetilen `CalculatePrimeCompletedEventArgs` için istemcinin olay işleyicisi için her hesaplama sonucunu raporlama sınıfı `CalculatePrimeCompleted`.event. Ek olarak `AsyncCompletedEventArgs` özellikler, bu sınıfı hangi numarasını test edilmiştir, Hazırla olup ve prime değilse, ilk bölen olduğunu belirlemek için istemcinin sağlar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu noktada, bileşen oluşturabilirsiniz.  
  
#### <a name="to-test-your-component"></a>Bileşeniniz sınamak için  
  
-   Bileşen derleyin.  
  
     İki derleyici uyarıları alırsınız:  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Bu uyarılar sonraki bölümde temizlenir.  
  
## <a name="defining-private-delegates"></a>Özel temsilcileri tanımlama  
 Zaman uyumsuz yönlerini `PrimeNumberCalculator` bileşen uygulanır dahili olarak bilinen özel bir temsilci ile bir <xref:System.Threading.SendOrPostCallback>. A <xref:System.Threading.SendOrPostCallback> üzerinde yürüten bir geri çağırma yöntemi temsil eden bir <xref:System.Threading.ThreadPool> iş parçacığı. Geri çağırma yöntemi türü tek bir parametre alan bir imzaya sahip olmalıdır <xref:System.Object>, durumu bir sarmalayıcı sınıfı temsilcileri arasında geçirmek anlamına gelir gerekir. Daha fazla bilgi için bkz. <xref:System.Threading.SendOrPostCallback>.  
  
#### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Bileşenin iç zaman uyumsuz davranışı uygulamak için:  
  
1.  Bildirme ve oluşturma <xref:System.Threading.SendOrPostCallback> içinde Temsilciler `PrimeNumberCalculator` sınıfı. Oluşturma <xref:System.Threading.SendOrPostCallback> bir yardımcı program yöntemi nesneleri adlı `InitializeDelegates`.  
  
     İki temsilciler gerekir: biri istemciye ilerleme durumu raporlama için ve biri istemciye tamamlama raporlama.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2.  Çağrı `InitializeDelegates` , bileşenin Oluşturucusu yöntemi.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3.  Bir temsilci bildirme `PrimeNumberCalculator` asıl işi zaman uyumsuz olarak yapılacak işler sınıfı. Bu temsilci asal bir sayı olup olmadığını sınar çalışan yöntemi sarmalar. Temsilci geçen bir <xref:System.ComponentModel.AsyncOperation> zaman uyumsuz işlem ömrü izlemek için kullanılan parametre.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4.  Bekleyen zaman uyumsuz işlemleri ömrü yönetmek için bir koleksiyon oluşturun. İstemcinin yürütülen ve tamamlandı ve bu izleme, istemci zaman uyumsuz yöntem çağrısı yaptığında benzersiz belirteci ya da görev kimliği geçirmek istemcinin kılarak gerçekleştirilir gibi işlemleri izlemek için bir yol gerekir. `PrimeNumberCalculator` Bileşen gerekir izlemek her çağrı karşılık gelen çağırmayla görev kimliği ilişkilendirerek. İstemci, benzersiz olmayan bir görev kimliği geçerse `PrimeNumberCalculator` bileşen bir özel durum yükseltmek gerekir.  
  
     `PrimeNumberCalculator` Bileşen izler görev kimliği adlı bir özel koleksiyon sınıfı kullanarak bir <xref:System.Collections.Specialized.HybridDictionary>. Sınıf tanımı'nda oluşturma bir <xref:System.Collections.Specialized.HybridDictionary> adlı `userTokenToLifetime`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Ortak olaylar uygulama  
 Olay tabanlı zaman uyumsuz desen uygulamak bileşenleri olayları kullanan istemciler için iletişim kurar. Bu olaylar yardımıyla uygun parçacığında çağrılan <xref:System.ComponentModel.AsyncOperation> sınıfı.  
  
#### <a name="to-raise-events-to-your-components-clients"></a>Olaylar, bileşenin istemcilere yükseltmek için:  
  
1.  İstemciler için raporlama için ortak olaylar uygulayın. İlerleme durumunu ve bir raporlama tamamlanması için raporlama için bir olay gerekir.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Tamamlama yöntemi uygulama  
 Tamamlama temsilci zaman uyumsuz işlemi başarıyla tamamlandığında, hata ya da iptal sona erdiğinde, temel alınan, ücretsiz iş parçacıklı zaman uyumsuz davranışı çağıracağı yöntemidir. Bu çağrıyı rasgele bir iş parçacığı üzerinde gerçekleşir.  
  
 Bu yöntem, istemcinin görev kimliği benzersiz istemci belirteçleri iç koleksiyonundan burada kaldırılır kullanılır. Bu yöntem de belirli bir zaman uyumsuz işlem ömrü sona erer <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> karşılık gelen yöntemi <xref:System.ComponentModel.AsyncOperation>. Bu çağrı uygulama modeli için uygun olan iş parçacığında tamamlama olayını başlatır. Sonra <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> yöntemi çağrıldığında, bu örneği <xref:System.ComponentModel.AsyncOperation> artık kullanılmamaktadır ve kullanmak için sonraki girişiminde herhangi bir özel durum oluşturur.  
  
 `CompletionMethod` İmza gerekir tutun tüm durumu zaman uyumsuz işlem sonucunu açıklamak gerekli. Sayının asal ve ilk bölen değerini olup asal sayı değilse bu belirli zaman uyumsuz işlemi tarafından test edilmiştir numarası için durum tutar. Ayrıca durumu oluştu, hiçbir özel durumu açıklayan tutar ve <xref:System.ComponentModel.AsyncOperation> bu belirli görevine karşılık gelen.  
  
#### <a name="to-complete-an-asynchronous-operation"></a>Zaman uyumsuz bir işlem tamamlamak için:  
  
-   Tamamlama yöntemini uygulayın. Doldurmak için kullandığı altı parametreler isteyen bir `CalculatePrimeCompletedEventArgs` istemcinin aracılığıyla istemciye döndürülen `CalculatePrimeCompletedEventHandler`. İstemcinin görev kimliği belirtecini iç koleksiyonundan kaldırır ve çağrısıyla zaman uyumsuz işlem ömrü sona erer <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>. <xref:System.ComponentModel.AsyncOperation> İş parçacığı veya uygulama modeli için uygun olan içerik çağrısı sıralar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu noktada, bileşen oluşturabilirsiniz.  
  
#### <a name="to-test-your-component"></a>Bileşeniniz sınamak için  
  
-   Bileşen derleyin.  
  
     Bir derleyici uyarısı alırsınız:  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Bu uyarı bir sonraki bölümde çözümlenir.  
  
## <a name="implementing-the-worker-methods"></a>Çalışan yöntemlerini uygulama  
 Şu ana kadar destekleyen zaman uyumsuz kodunu uyguladık `PrimeNumberCalculator` bileşeni. Şimdi asıl işi yapan kod uygulayabilirsiniz. Üç yöntem gerçekleştireceksiniz: `CalculateWorker`, `BuildPrimeNumberList`, ve `IsPrime`. Birlikte `BuildPrimeNumberList` ve `IsPrime` Sieve, test sayının kare kökünü kadar tüm asal sayılar bularak bir sayının asal olup olmadığını belirleyen Eratosthenes, adlı iyi bilinen bir algoritma oluşturan. Hiçbir divisors bu noktası tarafından bulunursa, test asal sayısıdır.  
  
 Bu bileşen için en yüksek verimlilik yazılmışsa, farklı bir test numaraları için çeşitli çağrılarına tarafından bulunan tüm asal sayıları unutmayın. Ayrıca 2, 3 ve 5 gibi Önemsiz divisors kontrol. Bu örneğin amacı nasıl uzun süren işlem göstermektir bu iyileştirmeler sizin için bir alıştırma olarak kalması için zaman uyumsuz olarak ancak çalıştırılabilir.  
  
 `CalculateWorker` Yöntemi bir temsilci paketlenir ve çağrısıyla zaman uyumsuz olarak çağrılır `BeginInvoke`.  
  
> [!NOTE]
>  İlerleme durumu raporlama uygulandığına `BuildPrimeNumberList` yöntemi. Hızlı bilgisayarlarda `ProgressChanged` olayları hızlı art arda gerçekleştirilen. İstemci üzerinde bu olaylar oluşturulur, iş parçacığı, bu durum kaldırabilir olmalıdır. Kullanıcı arabirimi kodu davranışı asılı kaynaklanan iletilerle yayılmamış ve yukarı, devam edilemiyor olabilir. Bu durum işleyen bir örnek için kullanıcı arabirimi, bkz: [nasıl yapılır: olay tabanlı zaman uyumsuz desenin istemcisini uygulama](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
#### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Asal sayı hesaplama zaman uyumsuz olarak çalıştırmak için:  
  
1.  Uygulama `TaskCanceled` yardımcı yöntemi. Bu görev ömrü koleksiyonu belirtilen görev kimliği için denetler ve döndürür `true` görev kimliği bulunmazsa.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2.  Uygulama `CalculateWorker` yöntemi. İki parametre alır: bir test etmek için Numaraysa ve bir <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3.  Uygulama `BuildPrimeNumberList`. İki parametre alır: test etmek için sayı ve bir <xref:System.ComponentModel.AsyncOperation>. Kullandığı <xref:System.ComponentModel.AsyncOperation> rapor ilerleyişini ve artımlı sonuçları. Bu, istemcinin olay işleyicileri uygun iş parçacığı veya uygulama modeli bağlamının çağırılır sağlar. Zaman `BuildPrimeNumberList` asal sayı bir bulursa, onu raporları bu artımlı bir sonucu olarak istemcinin olay işleyicisi için `ProgressChanged` olay. Bu türetilmiş bir sınıf gerektirir <xref:System.ComponentModel.ProgressChangedEventArgs>adlı `CalculatePrimeProgressChangedEventArgs`, hangi bir adlı özellik eklemiştir `LatestPrimeNumber`.  
  
     `BuildPrimeNumberList` Yöntemini de düzenli olarak çağırır `TaskCanceled` yöntemi ve yöntem döndürüyorsa çıkar `true`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4.  Uygulama `IsPrime`. Üç parametre alır: bilinen asal sayılar, test etmek için numarası ve bir output parametresi bulunamadı ilk bölen için listesi. Asal sayılar listesini verildiğinde, bu test sayının asal olup olmadığını belirler.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5.  Türetilen `CalculatePrimeProgressChangedEventArgs` gelen <xref:System.ComponentModel.ProgressChangedEventArgs>. Bu sınıf istemcinin olay işleyicisi için artımlı sonuçlarını raporlama için gerekli olan `ProgressChanged` olay. Adlı bir eklenen özelliğe sahiptir `LatestPrimeNumber`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu noktada, bileşen oluşturabilirsiniz.  
  
#### <a name="to-test-your-component"></a>Bileşeniniz sınamak için  
  
-   Bileşen derleyin.  
  
     Tüm bu yazılacak kalır başlatmak ve zaman uyumsuz işlemleri iptal etmek için yöntemlerdir `CalculatePrimeAsync` ve `CancelAsync`.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Başlangıç ve iptal yöntemleri uygulama  
 Çalışan yöntemi çağrılarak kendi iş parçacığında Başlat `BeginInvoke` sarmaladığı temsilci üzerinde. Belirli bir zaman uyumsuz işlem ömrünü yönetmek için arama <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> yöntemi <xref:System.ComponentModel.AsyncOperationManager> yardımcı sınıfı. Bu döndürür bir <xref:System.ComponentModel.AsyncOperation>, istemcinin olay işleyicileri çağrılarını uygun iş parçacığı veya bağlam sıralar.  
  
 Belirli bir bekleyen işlemi iptal <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> ilgili üzerinde <xref:System.ComponentModel.AsyncOperation>. Bu, işlem ve yapılan sonraki çağrılar sona erer kendi <xref:System.ComponentModel.AsyncOperation> bir özel durum oluşturur.  
  
#### <a name="to-implement-start-and-cancel-functionality"></a>Başlangıç uygulamak için ve işlevselliği iptal et:  
  
1.  Uygulama `CalculatePrimeAsync` yöntemi. İstemci tarafından sağlanan belirteç (görev kimliği) şu anda görevleri temsil eden tüm belirteçleri göre benzersiz olduğundan emin olun. İstemci benzersiz olmayan bir belirtece geçiyorsa `CalculatePrimeAsync` bir özel durum oluşturur. Aksi takdirde, belirteç görev kimliği koleksiyonuna eklenir.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2.  Uygulama `CancelAsync` yöntemi. Varsa `taskId` parametresi var. belirteci koleksiyonda, kaldırılmadan. Bu çalışmasını başlamadı iptal edilmiş görevleri önler. Görev çalışıyorsa `BuildPrimeNumberList` görev kimliği ömrü koleksiyondan kaldırıldı algıladığında yöntemi çıkar.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu noktada, bileşen oluşturabilirsiniz.  
  
#### <a name="to-test-your-component"></a>Bileşeniniz sınamak için  
  
-   Bileşen derleyin.  
  
 `PrimeNumberCalculator` Bileşenidir şimdi tam ve kullanıma hazır.  
  
 Kullanan bir örnek istemcisi için `PrimeNumberCalculator` bileşeni Bkz [nasıl yapılır: olay tabanlı zaman uyumsuz desenin istemcisini uygulama](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu örnek yazarak doldurabilirsiniz `CalculatePrime`, zaman uyumlu denk `CalculatePrimeAsync` yöntemi. Bu yapacak `PrimeNumberCalculator` bileşen olay tabanlı zaman uyumsuz desen ile tamamen uyumlu.  
  
 Bu örnekte, farklı bir test numaraları için çeşitli çağrılarına tarafından bulunan tüm asal numaralarının listesini koruyarak artırabilir. Bu yaklaşımı kullanarak, önceki görevleri tarafından çalışmanın her görev yararlı olacak. Bu liste ile korumak dikkatli olun `lock` bölgeler, farklı iş parçacıkları tarafından listeye erişim serileştirilmiş şekilde.  
  
 Bu örnek 2, 3 ve 5 gibi Önemsiz divisors için test ederek de artırabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [IN derleme değil: Visual Basic'te çoklu iş parçacığı kullanımı](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)  
 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [Olay Tabanlı Zaman Uyumsuz Desenle Çok İş Parçacıklı Programlama](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
