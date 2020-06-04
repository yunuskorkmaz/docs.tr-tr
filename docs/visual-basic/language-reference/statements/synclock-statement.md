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
ms.openlocfilehash: fd932a20af274faf2b56136a94675b28399989b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404167"
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
 Gereklidir. Bir nesne başvurusunu değerlendiren ifade.  
  
 `block`  
 İsteğe bağlı. Kilit elde edildiğinde yürütülecek deyimler bloğu.  
  
 `End SyncLock`  
 Bir `SyncLock` bloğu sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 `SyncLock`İfade, birden çok iş parçacığının aynı anda ekstre bloğunu yürütmemesini sağlar. `SyncLock`başka bir iş parçacığı yürütülene kadar her bir iş parçacığının blok girmesini engeller.  
  
 En yaygın kullanımı, `SyncLock` verilerin birden fazla iş parçacığı tarafından aynı anda güncelleştirilmesini sağlar. Verileri işleyen deyimlerin kesinti olmadan tamamlanmasına gitmesi gerekiyorsa, bunları bir blok içine koyun `SyncLock` .  
  
 Özel bir kilit tarafından korunan bir ifade bloğu bazen *kritik bir bölüm*olarak adlandırılır.  
  
## <a name="rules"></a>Kurallar  
  
- Dallanma. Bloğunun dışından bir bloğa dallandırılamıyor `SyncLock` .  
  
- Nesne değerini kilitle. Değeri olamaz `lockobject` `Nothing` . Bir ifadede kullanmadan önce Lock nesnesini oluşturmanız gerekir `SyncLock` .  
  
     `lockobject`Bir blok yürütülürken değerini değiştiremezsiniz `SyncLock` . Mekanizma, kilit nesnesinin değişmeden kalmasını gerektirir.  
  
- Bir blokta [await](../operators/await-operator.md) işlecini kullanamazsınız `SyncLock` .  
  
## <a name="behavior"></a>Davranış  
  
- Mekanizmadır. Bir iş parçacığı ifadeye ulaştığında `SyncLock` , ifadeyi değerlendirir `lockobject` ve ifadenin döndürdüğü nesne üzerinde dışlamalı bir kilit elde edene kadar yürütmeyi askıya alır. Başka bir iş parçacığı `SyncLock` ifadeye ulaştığında, ilk iş parçacığı ifadeyi çalıştırana kadar bir kilit almaz `End SyncLock` .  
  
- Korumalı veriler. `lockobject`Bir `Shared` değişkense, dışlamalı kilit, `SyncLock` başka bir iş parçacığı yürütülürken, sınıfın herhangi bir örneğindeki bir iş parçacığının bloğunu yürütmesini engeller. Bu, tüm örnekler arasında paylaşılan verileri korur.  
  
     `lockobject`Bir örnek değişkenidir (değil `Shared` ), kilit, geçerli örnekte çalışan bir iş parçacığının `SyncLock` aynı anda aynı örnekteki başka bir iş parçacığı ile aynı zamanda yürütülmesini önler. Bu, bireysel örnek tarafından tutulan verileri korur.  
  
- Alma ve yayınlama. Bir `SyncLock` blok `Try...Finally` , blok üzerinde özel bir kilit elde eden bir oluşturma gibi davranır `Try` `lockobject` ve `Finally` blok onu yayınlar. Bu nedenle, bloğundan `SyncLock` çıktığınızda, blok kilidi garanti eder. Bu, işlenmemiş bir özel durum durumunda bile geçerlidir.  
  
- Çerçeve çağrıları. `SyncLock`Bloğu, `Enter` `Exit` `Monitor` ad alanındaki sınıfının ve yöntemlerini çağırarak dışlamalı kilidi alır ve serbest bırakır <xref:System.Threading> .  
  
## <a name="programming-practices"></a>Programlama uygulamaları  
 `lockobject`İfade her zaman yalnızca kendi sınıfınıza ait olan bir nesne olarak değerlendirilir. `Private`Geçerli örneğe ait verileri korumak için bir nesne değişkeni veya `Private Shared` tüm örneklerde ortak olan verileri korumak için bir nesne değişkeni bildirmeniz gerekir.  
  
 `Me`Örnek verileri için bir kilit nesnesi sağlamak üzere anahtar sözcüğünü kullanmamalısınız. Sınıfınıza dış kod, sınıfınızın bir örneğine başvuru içeriyorsa, bu başvuruyu `SyncLock` kendi sizinkinden tamamen farklı, farklı verileri koruyan bir blok için bir kilit nesnesi olarak kullanabilir. Bu şekilde, sınıfınız ve diğer sınıf, birbirini ilgisiz blokları yürütmelerini engelleyebilir `SyncLock` . Aynı dizeyi kullanan işlemdeki diğer kodlar aynı kilidi paylaştığından, bir dizedeki aynı şekilde kilitleme sorunlu olabilir.  
  
 Ayrıca, `Me.GetType` paylaşılan veriler için bir kilit nesnesi sağlamak üzere metodunu kullanmamalısınız. Bunun nedeni, `GetType` her zaman `Type` belirli bir sınıf adı için aynı nesneyi döndürmektedir. Dış kod `GetType` , sınıfınıza çağrı verebilir ve kullanmakta olduğunuz kilit nesnesini alabilir. Bu, iki sınıfın bloklarından birbirini engellemesine neden olur `SyncLock` .  
  
## <a name="examples"></a>Örnekler  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir ileti listesini tutan bir sınıfı gösterir. Bir dizideki iletileri ve bu dizinin son kullanılan öğesini bir değişkende tutar. `addAnotherMessage`Yordam, son öğeyi artırır ve yeni iletiyi depolar. Bu iki işlem ve deyimleri tarafından korunur `SyncLock` `End SyncLock` , çünkü son öğe artdıktan sonra yeni ileti, diğer herhangi bir iş parçacığının son öğeyi yeniden artırılabilmesi için önce depolanmalıdır.  
  
 Sınıf, `simpleMessageList` tüm örnekleri arasında bir ileti listesi paylaşmışsa, değişkenleri `messagesList` ve `messagesLast` olarak olarak bildirilenler `Shared` . Bu durumda, değişken `messagesLock` de olmalıdır `Shared` , böylece her örnek tarafından kullanılan tek bir kilit nesnesi olur.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>Description  
 Aşağıdaki örnek, ve iş parçacıklarını kullanır `SyncLock` . Deyimin bulunduğu sürece `SyncLock` , ifade bloğu kritik bir bölümdür ve `balance` hiçbir zaman negatif bir sayı değildir. `SyncLock` `End SyncLock` Anahtar sözcüğünü bırakma etkisini görmek için ve deyimlerini açıklama ekleyebilirsiniz `SyncLock` .  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>Yorumlar  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Eşitleme temellerine genel bakış](../../../standard/threading/overview-of-synchronization-primitives.md)
