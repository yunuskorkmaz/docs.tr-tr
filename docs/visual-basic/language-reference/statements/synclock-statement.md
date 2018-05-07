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
ms.openlocfilehash: cf2aad9ec2ba67200d175fbcddfcb49afeac6efc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="synclock-statement"></a>SyncLock Deyimi
Özel bir kilit deyimi bloğu için blok yürütmeden önce devralır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Bölümler  
 `lockobject`  
 Gerekli. Bir nesne başvurusu veren ifade.  
  
 `block`  
 İsteğe bağlı. Kilit alındığında yürütmek üzere olduğunuz deyimleri bloğu.  
  
 `End SyncLock`  
 Sonlandırır bir `SyncLock` bloğu.  
  
## <a name="remarks"></a>Açıklamalar  
 `SyncLock` Deyimi sağlar birden çok iş parçacığı aynı anda deyimi blok yürütülmez. `SyncLock` Her iş parçacığı, başka bir iş parçacığı, yürütülmekte olduğu kadar blok geçmesini engeller.  
  
 En yaygın kullanımı `SyncLock` verileri birden çok iş parçacığı tarafından eşzamanlı olarak güncelleştirilmesini korumaktır. Verileri işlemek deyimleri kesintisiz tamamlama gerekir giderseniz, bunları içine yerleştirin bir `SyncLock` bloğu.  
  
 Özel bir kilit tarafından korunan bir ifade bloğu adlandırılan bir *kritik bölüm*.  
  
## <a name="rules"></a>Kurallar  
  
-   Dal oluşturma. İçine dallanamıyor bir `SyncLock` dışında blok önleyin.  
  
-   Kilit nesne değeri. Değeri `lockobject` olamaz `Nothing`. İçinde kullanmadan önce kilit nesnesi oluşturmanız gerekir bir `SyncLock` deyimi.  
  
     Değeri değiştiremezsiniz `lockobject` yürütülürken bir `SyncLock` bloğu. Kilit nesnesi değişmeden mekanizması gerektirir.  
  
-   Kullanamazsınız [bekleme](../../../visual-basic/language-reference/operators/await-operator.md) işlecinde bir `SyncLock` bloğu.  
  
## <a name="behavior"></a>Davranış  
  
-   Mekanizması. Bir iş parçacığı ulaştığında `SyncLock` deyimi, bu hesaplar `lockobject` ifade ve özel bir kilit ifadesi tarafından döndürülen nesne üzerinde edinir kadar yürütme askıya alır. Başka bir iş parçacığı ulaştığında `SyncLock` deyimi, onu olmayan bir kilit alınması ilk iş parçacığı yürütür kadar `End SyncLock` deyimi.  
  
-   Korunan veriler. Varsa `lockobject` olan bir `Shared` değişken, özel kullanım kilidi sınıfının bir örneğini bir iş parçacığında yürütülmesini engeller `SyncLock` başka bir iş parçacığı yürütülürken engelleyin. Bu, tüm örnekler arasında paylaşılan verileri korur.  
  
     Varsa `lockobject` bir örnek değişkeni (değil `Shared`), kilit yürütülmesini geçerli örneğinde çalışan iş parçacığı engeller `SyncLock` başka bir iş parçacığı aynı örneğinde aynı zamanda bloğu. Bu, tek tek örneği tarafından tutulan verileri korur.  
  
-   Edinme ve sürüm. A `SyncLock` engelleme davranacağını gibi bir `Try...Finally` yapım, `Try` blok üzerinde özel bir kilit edinir `lockobject` ve `Finally` blok yayımlar. Bu nedenle, `SyncLock` blok blok çıkmak nasıl olsun kilidi sürümü güvence altına alır. Bu, hatta işlenmeyen bir özel durum söz konusu olduğunda geçerlidir.  
  
-   Framework çağırır. `SyncLock` Bloğu edinir ve çağırarak özel kullanım kilidi serbest `Enter` ve `Exit` yöntemlerinin `Monitor` sınıfını <xref:System.Threading> ad alanı.  
  
## <a name="programming-practices"></a>Programlama yöntemler  
 `lockobject` İfade her zaman özel olarak sınıfa ait bir nesneye değerlendirin. Bildirmeniz gerekir bir `Private` geçerli örneğine ait olan verileri korumak için nesne değişkeni veya `Private Shared` için tüm örnekleri ortak verileri korumak için nesne değişkeni.  
  
 Kullanılamaz `Me` anahtar sözcüğü bir kilit sağlamak için nesne örneği için veri. Kodu sınıfınıza dış sınıfının bir örneğine başvuru varsa, bunun için bir kilit nesnesi olarak bu başvuruyu kullanabilir bir `SyncLock` blok sizin tamamen farklı farklı veri koruma. Bu şekilde, sizin ve diğer sınıf birbiriyle ilgisiz kendi yürütülmesini engelleyin `SyncLock` engeller. Aynı dize kullanarak işlemdeki başka bir kod aynı kilit paylaşacak beri benzer şekilde bir dizesine kilitleme sorunlu olabilir.  
  
 Ayrıca kullanılamaz `Me.GetType` yöntemi için bir kilit nesnesi sağlamak için paylaşılan veri. Bunun nedeni, `GetType` her zaman aynı döndürür `Type` nesne belirtilen sınıf adı. Harici kod çağrısı `GetType` sınıfınızın ve kullandığınız aynı kilit nesnesini alın. Bu birbirinden engelleme iki sınıf ile sonuçlandı kendi `SyncLock` engeller.  
  
## <a name="examples"></a>Örnekler  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte basit iletilerin listesini tutar bir sınıfı gösterir. Bir dizi iletileri tutar ve son bu dizinin öğesi bir değişkende kullanılır. `addAnotherMessage` Yordamı son öğe artırır ve yeni ileti depolar. Bu iki işlemler tarafından korunan `SyncLock` ve `End SyncLock` deyimleri, son öğe artar sonra başka bir iş parçacığı son öğe yeniden artırabilirsiniz önce yeni ileti depolanması gerekir çünkü.  
  
 Varsa `simpleMessageList` sınıfı paylaşılan tüm örneklerini, değişkenleri arasında iletilerinin bir listesini `messagesList` ve `messagesLast` olarak bildirilmesi `Shared`. Bu durumda, değişkeni `messagesLock` ayrıca olmalıdır `Shared`her örneği tarafından kullanılan tek kilit nesnesi böylece bulunmaz.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, iş parçacığı kullanır ve `SyncLock`. Sürece `SyncLock` deyimi varsa, deyimi blok kritik bir bölümdür ve `balance` hiçbir zaman negatif bir sayı olur. Out açıklama `SyncLock` ve `End SyncLock` bırakarak etkisini görmek için deyimleri `SyncLock` anahtar sözcüğü.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [İş Parçacığı Eşitleme](../../programming-guide/concepts/threading/thread-synchronization.md)  
 [İş parçacığı oluşturma](../../programming-guide/concepts/threading/index.md)
