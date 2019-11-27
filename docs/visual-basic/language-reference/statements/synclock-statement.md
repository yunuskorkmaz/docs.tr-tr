---
title: SyncLock Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: 0f430edce99513b0de9ef437d70648a128b336b8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352811"
---
# <a name="synclock-statement"></a>SyncLock Deyimi
Bloğu yürütmeden önce bir ifade bloğu için özel bir kilit elde edin.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Bölümler  
 `lockobject`  
 Gerekli. Bir nesne başvurusunu değerlendiren ifade.  
  
 `block`  
 İsteğe bağlı. Kilit elde edildiğinde yürütülecek deyimler bloğu.  
  
 `End SyncLock`  
 Bir `SyncLock` bloğunu sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 `SyncLock` deyimleri, birden çok iş parçacığının aynı anda ekstre bloğunu yürütmemesini sağlar. `SyncLock`, başka bir iş parçacığı yürütülene kadar her bir iş parçacığının blok girmesini önler.  
  
 `SyncLock` en yaygın kullanımı, verilerin birden fazla iş parçacığı tarafından aynı anda güncelleştirilmesini sağlar. Verileri işleyen deyimlerin kesintiye uğramadan tamamlanması gerekiyorsa, bunları bir `SyncLock` bloğunun içine koyun.  
  
 Özel bir kilit tarafından korunan bir ifade bloğu bazen *kritik bir bölüm*olarak adlandırılır.  
  
## <a name="rules"></a>Kurallar  
  
- Dallanma. Bloğunun dışından bir `SyncLock` bloğuna dallandırılamıyor.  
  
- Nesne değerini kilitle. `lockobject` değeri `Nothing`olamaz. Kilit nesnesini bir `SyncLock` ifadesinde kullanmadan önce oluşturmanız gerekir.  
  
     `SyncLock` bloğunu yürütürken `lockobject` değerini değiştiremezsiniz. Mekanizma, kilit nesnesinin değişmeden kalmasını gerektirir.  
  
- `SyncLock` bloğunda [await](../../../visual-basic/language-reference/operators/await-operator.md) işlecini kullanamazsınız.  
  
## <a name="behavior"></a>Davranış  
  
- Mekanizmadır. Bir iş parçacığı `SyncLock` deyimine ulaştığında, `lockobject` ifadesini değerlendirir ve ifadenin döndürdüğü nesne üzerinde dışlamalı bir kilit elde edene kadar yürütmeyi askıya alır. Başka bir iş parçacığı `SyncLock` ifadesine ulaştığında, ilk iş parçacığı `End SyncLock` ifadesini çalıştırana kadar bir kilit almaz.  
  
- Korumalı veriler. `lockobject` bir `Shared` değişkense, dışlamalı kilit, herhangi bir iş parçacığı yürütülürken sınıfın herhangi bir örneğindeki bir iş parçacığının `SyncLock` bloğunu yürütmesini engeller. Bu, tüm örnekler arasında paylaşılan verileri korur.  
  
     `lockobject` bir örnek değişkenidir (`Shared`değil), kilit, geçerli örnekte çalışan bir iş parçacığının aynı anda aynı örnekteki diğer bir iş parçacığıyla `SyncLock` bloğunu yürütmesini engeller. Bu, bireysel örnek tarafından tutulan verileri korur.  
  
- Alma ve yayınlama. `SyncLock` bloğu, `Try` bloğunun `lockobject` üzerinde dışlamalı bir kilit elde `Try...Finally` oluşturma gibi davranır ve `Finally` bloğu bunu serbest bırakır. Bu nedenle, bloğundan nasıl çıktığınızda bağımsız olarak `SyncLock` bloğu kilit sürümünü garanti eder. Bu, işlenmemiş bir özel durum durumunda bile geçerlidir.  
  
- Çerçeve çağrıları. `SyncLock` bloğu, <xref:System.Threading> ad alanındaki `Monitor` sınıfının `Enter` ve `Exit` yöntemlerini çağırarak dışlamalı kilidi alır ve yayınlar.  
  
## <a name="programming-practices"></a>Programlama uygulamaları  
 `lockobject` ifadesi her zaman yalnızca sınıfınıza ait olan bir nesne olarak değerlendirilir. Geçerli örneğe ait verileri korumak için bir `Private` nesne değişkeni veya tüm örneklerde ortak olan verileri korumak için bir `Private Shared` nesne değişkeni bildirmeniz gerekir.  
  
 Örnek verileri için bir kilit nesnesi sağlamak üzere `Me` anahtar sözcüğünü kullanmamalısınız. Sınıfınıza dış kod, sınıfınızın bir örneğine başvuru içeriyorsa, bu başvuruyu sizinki farklı verileri koruyan bir `SyncLock` bloğu için bir kilit nesnesi olarak kullanabilir. Bu şekilde, sınıfınız ve diğer sınıfı birbirini ilgisiz `SyncLock` bloklarını yürütmelerini engelleyebilir. Aynı dizeyi kullanan işlemdeki diğer kodlar aynı kilidi paylaştığından, bir dizedeki aynı şekilde kilitleme sorunlu olabilir.  
  
 Ayrıca, paylaşılan veriler için bir kilit nesnesi sağlamak üzere `Me.GetType` metodunu kullanmamalısınız. Bunun nedeni, `GetType` her zaman belirli bir sınıf adı için aynı `Type` nesnesini döndürmektedir. Dış kod, sınıfınıza `GetType` çağırabilir ve kullanmakta olduğunuz kilit nesnesini alabilir. Bu, iki sınıfın `SyncLock` bloklarında birbirini engellemesine neden olur.  
  
## <a name="examples"></a>Örnekler  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir ileti listesini tutan bir sınıfı gösterir. Bir dizideki iletileri ve bu dizinin son kullanılan öğesini bir değişkende tutar. `addAnotherMessage` yordamı son öğeyi artırır ve yeni iletiyi depolar. Bu iki işlem `SyncLock` ve `End SyncLock` deyimleri tarafından korunur, çünkü son öğe artdıktan sonra yeni ileti, diğer herhangi bir iş parçacığının son öğeyi yeniden artırılabilmesi için önce depolanmalıdır.  
  
 `simpleMessageList` sınıfı tüm örnekleri arasında bir ileti listesi paylaşmışsa, `messagesList` ve `messagesLast` değişkenleri `Shared`olarak bildirilebilecek. Bu durumda, değişken `messagesLock`, her örnek tarafından kullanılan tek bir kilit nesnesi olacak şekilde `Shared`de olmalıdır.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, iş parçacıklarını ve `SyncLock`kullanır. `SyncLock` deyimin bulunduğu sürece, ifade bloğu kritik bir bölümdür ve `balance` hiçbir zaman negatif bir sayı haline geçmez. `SyncLock` anahtar sözcüğünü bırakma etkisini görmek için `SyncLock` ve `End SyncLock` deyimlerini açıklama ekleyebilirsiniz.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Eşitleme temelleri 'ne genel bakış](../../../standard/threading/overview-of-synchronization-primitives.md)
