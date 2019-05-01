---
title: SyncLock deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: 3a12c3ac7250ee2904d571406d5008d451c9dc35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783831"
---
# <a name="synclock-statement"></a>SyncLock Deyimi
Bir deyim bloğunu için özel bir kilit bloğu yürütmeden önce alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Bölümler  
 `lockobject`  
 Gerekli. Bir nesne başvurusu için değerlendirilen bir ifade.  
  
 `block`  
 İsteğe bağlı. Kilit alınıncaya sonra yürütülecek olan bir deyimler bloğunu.  
  
 `End SyncLock`  
 Sonlandıran bir `SyncLock` blok.  
  
## <a name="remarks"></a>Açıklamalar  
 `SyncLock` Bildirimi birden çok iş parçacığı deyim bloğunu aynı anda yürütmemesini sağlar. `SyncLock` Her iş parçacığı başka bir iş parçacığında yürütülen kadar blok girmesini engeller.  
  
 En yaygın kullanımı `SyncLock` birden fazla iş parçacığı tarafından aynı anda güncelleştirilmesini verilerin korunmasını sağlamaktır. Verileri işlemek için ifadeleri kesintisiz tamamlanması için geçmesi gereken, bunları içine yerleştirebilirsiniz bir `SyncLock` blok.  
  
 Özel bir kilit tarafından korunan bir deyim bloğunu adlandırılan bir *kritik bölüm*.  
  
## <a name="rules"></a>Kurallar  
  
- Dal oluşturma. Dal oluşturamazsınız bir `SyncLock` blok dışındaysa önleyin.  
  
- Kilit nesne değeri. Değerini `lockobject` olamaz `Nothing`. İçinde kullanmadan önce nesnesi kilitlenemedi oluşturmalısınız bir `SyncLock` deyimi.  
  
     Değerini değiştiremezsiniz `lockobject` yürütülürken bir `SyncLock` blok. Mekanizması nesnesi kilitlenemedi değişmeden kalmasını gerektirir.  
  
- Kullanamazsınız [Await](../../../visual-basic/language-reference/operators/await-operator.md) işlecinde bir `SyncLock` blok.  
  
## <a name="behavior"></a>Davranış  
  
- Mekanizması. Bir iş parçacığı ulaştığında `SyncLock` deyimi olarak değerlendirilir `lockobject` deyim ve ifade tarafından döndürülen nesne üzerinde özel bir kilit alması kadar yürütmeyi askıya alır. Başka bir iş parçacığı ulaştığında `SyncLock` deyimi, onu değil bir kilit alınması ilk iş parçacığında yürütülene kadar `End SyncLock` deyimi.  
  
- Korunan veriler. Varsa `lockobject` olduğu bir `Shared` değişken, özel bir kilit herhangi bir sınıfın örneğini bir iş parçacığında yürütülmesini engeller `SyncLock` başka bir iş parçacığı yürütülürken engelleyin. Bu, tüm örnekler arasında paylaşılan verileri korur.  
  
     Varsa `lockobject` bir örneği değişkenidir (değil `Shared`), kilit yürütülmesini geçerli örneğinde çalışan iş parçacığı engeller `SyncLock` başka bir iş parçacığıyla aynı örneğinde aynı anda blok. Bu, tek bir örnek tarafından tutulan verileri korur.  
  
- Alım ve yayın. A `SyncLock` blok davranacağını gibi bir `Try...Finally` oluşturma, hangi `Try` blok üzerinde özel bir kilit alması `lockobject` ve `Finally` blok yayımlar. Bu nedenle, `SyncLock` blok blok çıkış ne olursa olsun kilit, yayın garanti eder. İşlenmeyen özel durum söz konusu olduğunda bile bu geçerlidir.  
  
- Framework çağırır. `SyncLock` Blok edinme ve özel bir kilit çağırarak serbest `Enter` ve `Exit` yöntemlerinin `Monitor` sınıfını <xref:System.Threading> ad alanı.  
  
## <a name="programming-practices"></a>Programlama yöntemler  
 `lockobject` İfade her zaman özel olarak, sınıfın ait olduğu bir nesneye değerlendirin. Size bildirmelidir bir `Private` geçerli örneğine ait verileri korumak için nesne değişkeni veya bir `Private Shared` için tüm örnekleri ortak verileri korumak için nesne değişkeni.  
  
 Kullanmamalısınız `Me` anahtar sözcüğü bir kilit sağlamak için nesne örneği için veri. Kodu sınıfınıza dış bir başvuru sınıfının bir örneği varsa, bunun için bir kilit nesnesi olarak bu başvuruyu kullanabilir bir `SyncLock` blok sizinkinden, tamamen farklı farklı veri koruma. Bu şekilde, sınıfınıza ve diğer sınıf birbiriyle ilgisiz kendi yürütülmesini engelleyebilecek `SyncLock` engeller. Aynı kilit işlemi kullanarak aynı dize içindeki diğer kodlardan paylaşacak beri benzer şekilde bir dizesine kilitleme sorunlara neden olabilir.  
  
 Ayrıca kullanmamalısınız `Me.GetType` yöntemi için bir kilit nesnesi sağlamak için paylaşılan veri. Bunun nedeni, `GetType` her zaman aynı döndürür `Type` nesne için belirli bir sınıf adı. Dış kod arama `GetType` sınıfınızın ve kullanmakta olduğunuz aynı kilit nesnesini alın. Bu iki sınıf birbirinden engelleme neden olur, `SyncLock` engeller.  
  
## <a name="examples"></a>Örnekler  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, basit bir iletiler listesini tutar bir sınıfı gösterir. Bir dizide iletileri tutar ve son öğe, dizinin bir değişkende kullanılır. `addAnotherMessage` Yordam son öğeyi artırır ve yeni iletinin depolar. Bu iki işlem tarafından korunan `SyncLock` ve `End SyncLock` deyimleri, çünkü son öğeyi artırıldıktan sonra başka bir iş parçacığı son öğeyi yeniden artırabilirsiniz önce yeni iletinin depolanması gerekir.  
  
 Varsa `simpleMessageList` sınıfın tüm örnekleri, değişkenleri arasında iletilerinin bir listesini paylaşılan `messagesList` ve `messagesLast` olarak bildirilmesi `Shared`. Bu durumda, değişken `messagesLock` ayrıca olmalıdır `Shared`, her örnek için kullanılan tek kilit nesnesi böylece olacaktır.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, iş parçacığı kullanır ve `SyncLock`. Sürece `SyncLock` deyimi, deyim bloğunu kritik bir bölümdür ve `balance` hiçbir zaman negatif bir sayı olur. Açıklama `SyncLock` ve `End SyncLock` bırakarak etkisini görmek için ifadeleri `SyncLock` anahtar sözcüğü.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Eşitleme temellerine genel bakış](../../../standard/threading/overview-of-synchronization-primitives.md)
