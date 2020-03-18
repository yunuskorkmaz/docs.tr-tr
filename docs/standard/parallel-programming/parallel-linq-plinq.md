---
title: Paralel LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
ms.openlocfilehash: 1ea880c6403a5fc8b26ba67fe21dfce79c4683db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140044"
---
# <a name="parallel-linq-plinq"></a>Paralel LINQ (PLINQ)
Paralel LINQ (PLINQ), LINQ'nin Nesnelere paralel bir uygulamasıdır. PLINQ, ad alanı için uzantı yöntemleri olarak LINQ standart sorgu işleçlerinin tam kümesini <xref:System.Linq> uygular ve paralel işlemler için ek işleçlere sahiptir. PLINQ, LINQ sözdiziminin basitliğini ve okunabilirliğini paralel programlamanın gücüyle birleştirir. Görev Paralel Kitaplığı hedefleyen kod gibi, PLINQ sorguları da ana bilgisayarın özelliklerine göre eşzamanlılık derecesine göre ölçeklenir.  
  
 Birçok senaryoda PLINQ, ana bilgisayardaki tüm kullanılabilir çekirdekleri daha verimli kullanarak LINQ'nin Nesnelersorgularına hızını önemli ölçüde artırabilir. Bu artan performans, masaüstüne yüksek performanslı bilgi işlem gücü getirir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [PLINQ'e Giriş](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [PLINQ'te Hızlandırmayı Anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [PLINQ'te Sıra Koruma](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [PLINQ'te Birleştirme Seçenekleri](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [Nasıl yapılır: PLINQ Sorgusunu İptal Etme](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [Nasıl Yapılır: Özel Bir PLINQ Toplama İşlevi Yazma](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [Nasıl yapılır: PLINQ ile Dosya Dizinlerini Yineleme](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [Nasıl yapılır: PLINQ Sorgu Performansını Ölçme](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [PLINQ Veri Örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable>
- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
- [Dil-Entegre Sorgu (LINQ) - C #](../../csharp/programming-guide/concepts/linq/index.md)  
- [Dil-Entegre Sorgu (LINQ) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md)  
