---
title: Serialization2
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
ms.openlocfilehash: bf303f9a79fbcab85d33fcb3ebb132d1d3e2041d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781104"
---
# <a name="serialization"></a>Serileştirme
Bu konu serileştirme [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yeteneklerini açıklamaktadır. Aşağıdaki paragraflar, tasarım zamanında kod oluşturma sırasında serileştirme ekleme ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sınıfların çalışma zamanı serileştirme davranışı ile ilgili bilgiler sağlar.  
  
 Aşağıdaki yöntemlerden biriyle, tasarım zamanında serileştirme kodu ekleyebilirsiniz:  
  
- Nesne İlişkisel Tasarımcısı **serileştirme modu** özelliğini **tek yönlü**olarak değiştirin.  
  
- SQLMetal komut satırında **/Serialization** seçeneğini ekleyin. Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Genel Bakış  
 Tarafından [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oluşturulan kod, varsayılan olarak ertelenmiş yükleme özellikleri sağlar. Ertelenmiş yükleme, verileri isteğe bağlı olarak şeffaf bir şekilde yüklemek için orta katman üzerinde çok uygundur. Bununla birlikte, serileştirici, ertelenmiş yüklemenin amaçlanıp ertelenmediği ertelenmiş yüklemeyi tetiklediği için serileştirme açısından sorunlu değildir. Aslında, bir nesne serileştirildiğinde, tüm giden erteleme başvuruları altındaki geçişli kapatma serileştirilir.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Serileştirme özelliği, öncelikle iki mekanizmalarla bu sorunu ele alınmaktadır:  
  
- Ertelenmiş <xref:System.Data.Linq.DataContext> yüklemeyi (<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>) kapatmak için bir mod. Daha fazla bilgi için bkz. <xref:System.Data.Linq.DataContext>.  
  
- Oluşturulan varlıklarda ve <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> öznitelikleri oluşturmak için kod oluşturma anahtarı. Bu değer, serileştirme altındaki erteleme sınıflarının davranışı da dahil olmak üzere bu konunun önemli konusudur.  
  
### <a name="definitions"></a>Tanımlar  
  
- *DataContract seri hale getirici*: .NET Framework 3,0 veya sonraki sürümlerin Windows Communication Framework (WCF) bileşeni tarafından kullanılan varsayılan seri hale getirici.  
  
- *Tek yönlü serileştirme*: Yalnızca tek yönlü bir ilişkilendirme özelliği içeren bir sınıfın serileştirilmiş sürümü (döngüyü önlemek için). Kurala göre, birincil yabancı anahtar ilişkisinin üst tarafındaki özelliği serileştirme olarak işaretlenir. Çift yönlü ilişkilendirmedeki diğer kenar serileştirilmez.  
  
     Tek yönlü serileştirme tarafından [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]desteklenen tek seri hale getirme türüdür.  
  
## <a name="code-example"></a>Kod Örneği  
 Aşağıdaki kod, Northwind örnek veritabanındaki `Customer` geleneksel `Order` ve sınıfları kullanır ve bu sınıfların serileştirme öznitelikleriyle nasıl donatılmış olduğunu gösterir.  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 `Customer` Aşağıdaki örnekteki `Order` sınıfı için, yalnızca sınıfına karşılık gelen ters ilişkilendirme özelliği kısaltma için gösterilir. Döngüden kaçınmak için bir <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği yok.  
  
 [!code-csharp[DLinqSerialization#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#4)]
 [!code-vb[DLinqSerialization#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#4)]  
  
 [!code-csharp[DLinqSerialization#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#5)]
 [!code-vb[DLinqSerialization#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#5)]  
  
### <a name="how-to-serialize-the-entities"></a>Varlıkları seri hale getirme  
 Önceki bölümde gösterilen kodlardan varlıkları aşağıdaki gibi seri hale getirebilirsiniz.  
  
 [!code-csharp[DLinqSerialization#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/Program.cs#6)]
 [!code-vb[DLinqSerialization#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/Module1.vb#6)]  
  
### <a name="self-recursive-relationships"></a>Kendinden özyinelemeli Ilişkiler  
 Kendinden özyinelemeli ilişkiler aynı kalıbı izler. Yabancı anahtara karşılık gelen ilişkilendirme özelliğinin bir <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği yoktur, ancak Parent özelliği bunu yapar.  
  
 İki otomatik özyinelemeli ilişki içeren aşağıdaki sınıfı göz önünde bulundurun: Employee. Manager/Reports ve Employee. Mentor/Mentees.  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
- [SqlMetal.exe (Kod Üretme Aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Nasıl yapılır: Varlıkları seri hale getirilebilir yap](how-to-make-entities-serializable.md)
