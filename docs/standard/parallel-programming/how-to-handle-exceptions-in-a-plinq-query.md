---
title: 'Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
ms.openlocfilehash: 3645f5dc470ef53710aa7f4c78c60431fb27ecfa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123099"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme

Bu konudaki ilk örnek, bir <xref:System.AggregateException?displayProperty=nameWithType> PLINQ sorgusundan yürütüldüğünde atılabilir nasıl işleyeceğini gösterir. İkinci örnek, özel durum atılacağına mümkün olduğunca yakın, temsilciler içinde try-catch blokları koymak nasıl gösterir. Bu şekilde, bunları en kısa sürede onlar meydana gelir gelmez yakalamak ve büyük olasılıkla sorgu yürütme devam edebilirsiniz. Özel durumların birleştirme iş parçacığına geri dönmesine izin verildiğinde, özel durum yükseltildikten sonra bir sorgunun bazı öğeleri işlemeye devam etmesi mümkündür.

PlinQ'un sıralı yürütmeye geri düştüğü ve bir özel durum oluştuğu bazı durumlarda, özel durum <xref:System.AggregateException>doğrudan yayılabilir ve bir . Ayrıca, <xref:System.Threading.ThreadAbortException>s her zaman doğrudan yayılır.

> [!NOTE]
> "Yalnızca Kodum" etkinleştirildiğinde, Visual Studio özel durumu atan satırda kırılır ve "kullanıcı kodu tarafından işlenmemiş özel durum" yazan bir hata iletisi görüntüler. Bu hata iyi huylu. Devam etmek için F5 tuşuna basabilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını görebilirsiniz. Visual Studio'nun ilk hatayı kırmasını önlemek **için, Araçlar, Seçenekler, Hata Ayıklama, Genel**altında "Sadece Kodum" onay kutusunun işaretlerini kaldırın.
>
> Bu örnek, kullanımı göstermek için tasarlanmıştır ve Nesneler sorgusuna eşdeğer ardışık LINQ'dan daha hızlı çalışmayabilir. Hız hakkında daha fazla bilgi için [PLINQ'da Hızları Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın.

## <a name="example"></a>Örnek

Bu örnek, atılan <xref:System.AggregateException?displayProperty=nameWithType>s'leri yakalamak için sorguyu yürüten kodun etrafına try-catch bloklarının nasıl yerleştirilebildiğini gösterir.

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

Bu örnekte, özel durum atıldıktan sonra sorgu devam edemez. Uygulama kodunuz özel durumu yakaladığında, PLINQ tüm iş parçacıklarındaki sorguyu zaten durdurmuştur.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir özel durum yakalamak ve sorgu yürütme ile devam etmek mümkün kılmak için bir temsilci bir try-catch blok koymak nasıl gösterir.

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a>Kod Derleniyor

- Bu örnekleri derlemek ve çalıştırmak için bunları PLINQ Veri Örneği örneğine kopyalayın ve yöntemi Main'den arayın.

## <a name="robust-programming"></a>Güçlü Programlama

Programınızın durumunu bozmamak için nasıl işleyeceğinizkonusunda bir özel durum yakalamayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable>
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
