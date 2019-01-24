---
title: Projeksiyonlar düzenleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 9b32ee4c7745fda482561311dc116e0e38b49ab7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599160"
---
# <a name="formulate-projections"></a>Projeksiyonlar düzenleme
Aşağıdaki örneklerde gösterildiği nasıl `select` deyiminde C# ve `Select` deyimi Visual Basic'te, form sorgu projeksiyonları diğer özellikleri ile birleştirilebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Select` Visual Basic'te yan tümcesi (`select` yan tümcesinde C#) için kişi adlarını bir dizisini döndürmek için `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Select` Visual Basic'te yan tümcesi (`select` yan tümcesinde C#) ve *anonim türler* kişi adlarını bir dizisini döndürmek için telefon numaraları için `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Select` Visual Basic'te yan tümcesi (`select` yan tümcesinde C#) ve *anonim türler* adları bir dizisini döndürmek ve çalışanlar için telefonu numaraları. `FirstName` Ve `LastName` alanları tek bir alana birleştirilir (`Name`) ve `HomePhone` alan yeniden adlandırılamaz `Phone` elde edilen sırada.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Select` Visual Basic'te yan tümcesi (`select` yan tümcesinde C#) ve *anonim türler* tüm bir dizisini döndürmek için `ProductID`s ve adlı hesaplanan değeri `HalfPrice`. Bu değeri şuna ayarlı `UnitPrice` 2 tarafından ayrılmış.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Select` Visual Basic'te yan tümcesi (`select` yan tümcesinde C#) ve bir *koşullu ifade* ürün adı ve ürün kullanılabilirliği bir dizisini döndürmek için.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir Visual Basic kullanan `Select` yan tümcesi (`select` yan tümcesinde C#) ve bir *türü bilinen* çalışanlar adlarını bir dizisini döndürmek için (ad).  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Select` ve `Where` Visual Basic'te (`select` ve `where` içinde C#) döndürülecek bir *dizisi filtrelenmiş* kişi adlarının Londra bulunan müşteriler için.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir `Select` Visual Basic'te yan tümcesi (`select` yan tümcesinde C#) ve *anonim türler* döndürülecek bir *alt şeklinde* müşterilerle ilgili veri.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iç içe sorgu sonrasında şu sonuçların döndürülmesi için kullanır:  
  
-   Tüm siparişleri ve bunlara karşılık gelen bir dizi `OrderID`s.  
  
-   İndirim siparişi öğeler bir alt dizi.  
  
-   Sevkiyat ücreti dahil edilmezse kaydedilmiş para miktarı.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
