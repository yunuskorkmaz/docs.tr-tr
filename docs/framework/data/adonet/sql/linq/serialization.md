---
title: Serialization2
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
ms.openlocfilehash: 56ebe888b816972f8d72873e4fca9f5204e6c772
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58408931"
---
# <a name="serialization"></a>Serileştirme
Bu konu başlığı altında açıklanır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] seri hale getirme özellikleri. İzleyen paragrafları serileştirme kod oluşturma sırasında tasarım zamanı ve çalışma zamanı serileştirme davranışını ekleme hakkında bilgi sağlayan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sınıfları.  
  
 Serileştirme kodu aşağıdaki yöntemlerden birini bir tasarım zamanında ekleyebilirsiniz:  
  
-   İçinde [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], değiştirme **serileştirme modunu** özelliğini **tek yönlü**.  
  
-   SQLMetal komut satırında ekleme **/serialization** seçeneği. Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Genel Bakış  
 Tarafından oluşturulan kodu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan olarak ertelenmiş yükleme özellikleri sağlar. Ertelenen yükleme Orta katmanda çok isteğe bağlı olarak saydam yüklenmesi için uygundur. Ertelenen yükleme veya istenip istenmediğini ertelenmiş yükleniyor seri hale getirici tetikler. ancak, seri hale getirme için sorunlu olmasıdır. Aslında, bir nesne seri olduğunda, tüm giden erteleme yüklenen başvuruları altında geçişli kendi kapatma seri hale getirilir.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Seri hale getirme özelliğini öncelikle iki mekanizma bu sorunu giderir:  
  
-   A <xref:System.Data.Linq.DataContext> geciktirilmiş yüklemeyi kapatma modunu (<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>). Daha fazla bilgi için bkz. <xref:System.Data.Linq.DataContext>.  
  
-   Oluşturmak için bir kod üretimi anahtar <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> ve <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> oluşturulan varlıkları öznitelikleri. Erteleme yükleme sınıfları serileştirme altında davranışını dahil olmak üzere bu yönü, bu konunun önemli bir konudur.  
  
### <a name="definitions"></a>Tanımlar  
  
-   *DataContract seri hale getirici*: Varsayılan olarak .NET Framework 3.0 veya sonraki sürümleri, Windows Communication Framework (WCF) bileşeni tarafından kullanılan serileştirici.  
  
-   *Tek yönlü serileştirme*: (Bir döngü önlemek için) yalnızca bir tek yönlü ilişkilendirme özellik içeren bir sınıf seri hale getirilmiş sürümü. Kural gereği, birincil yabancı anahtar ilişkisi üst tarafındaki özelliği seri hale getirme için işaretlenmiş. Diğer tarafta çift yönlü bir ilişkilendirmeye serileştirilmemiş.  
  
     Tek yönlü seri hale getirme serileştirme tarafından desteklenen tek tür [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## <a name="code-example"></a>Kod Örneği  
 Aşağıdaki kod geleneksel kullanır `Customer` ve `Order` Northwind örnek veritabanından sınıfları ve bu sınıflar serileştirme öznitelikleri ile donatılmış nasıl gösterir.  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 İçin `Order` aşağıdaki örnekte, yalnızca ters ilişkilendirme özelliğine karşılık gelen sınıf `Customer` sınıfı uzatmamak için gösterilir. Sahip olmadığı bir <xref:System.Runtime.Serialization.DataMemberAttribute> bir döngü önlemek için özniteliği.  
  
 [!code-csharp[DLinqSerialization#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#4)]
 [!code-vb[DLinqSerialization#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#4)]  
  
 [!code-csharp[DLinqSerialization#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#5)]
 [!code-vb[DLinqSerialization#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#5)]  
  
### <a name="how-to-serialize-the-entities"></a>Varlıkları seri hale getirmek nasıl  
 Önceki bölümde aşağıdaki şekilde gösterilen kodları varlıklarda serileştirebiliyorsa;  
  
 [!code-csharp[DLinqSerialization#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/Program.cs#6)]
 [!code-vb[DLinqSerialization#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/Module1.vb#6)]  
  
### <a name="self-recursive-relationships"></a>Kendi kendine yinelenen ilişkileri  
 Kendi kendine yinelenen ilişkileri aynı düzeni uygular. Yabancı anahtara karşılık gelen association özelliğine sahip değil bir <xref:System.Runtime.Serialization.DataMemberAttribute> üst özellik yok ise, öznitelik.  
  
 İki self-özyinelemeli ilişkilerine aşağıdaki sınıf göz önünde bulundurun: Employee.Manager/Reports ve Employee.Mentor/Mentees.  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [SqlMetal.exe (Kod Üretme Aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [Nasıl yapılır: Varlıkları serileştirilebilir yapmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)
