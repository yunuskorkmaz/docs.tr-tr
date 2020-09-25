---
title: Serialization2
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
ms.openlocfilehash: 778cc73575ffc7421854fd89592f1c4eaa284678
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203559"
---
# <a name="serialization"></a>Serileştirme

Bu konu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] serileştirme yeteneklerini açıklamaktadır. Aşağıdaki paragraflar, tasarım zamanında kod oluşturma sırasında serileştirme ekleme ve sınıfların çalışma zamanı serileştirme davranışı ile ilgili bilgiler sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
 Aşağıdaki yöntemlerden biriyle, tasarım zamanında serileştirme kodu ekleyebilirsiniz:  
  
- Nesne İlişkisel Tasarımcısı **serileştirme modu** özelliğini **tek yönlü**olarak değiştirin.  
  
- SQLMetal komut satırında **/Serialization** seçeneğini ekleyin. Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Genel Bakış  

 Tarafından oluşturulan kod, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Varsayılan olarak ertelenmiş yükleme özellikleri sağlar. Ertelenmiş yükleme, verileri isteğe bağlı olarak şeffaf bir şekilde yüklemek için orta katman üzerinde çok uygundur. Bununla birlikte, serileştirici, ertelenmiş yüklemenin amaçlanıp ertelenmediği ertelenmiş yüklemeyi tetiklediği için serileştirme açısından sorunlu değildir. Aslında, bir nesne serileştirildiğinde, tüm giden erteleme başvuruları altındaki geçişli kapatma serileştirilir.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Serileştirme özelliği, öncelikle iki mekanizmalarla bu sorunu ele alınmaktadır:  
  
- <xref:System.Data.Linq.DataContext>Ertelenmiş yüklemeyi () kapatmak için bir mod <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> . Daha fazla bilgi için bkz. <xref:System.Data.Linq.DataContext>.  
  
- <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>Oluşturulan varlıklarda ve öznitelikleri oluşturmak için kod oluşturma anahtarı <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> . Bu değer, serileştirme altındaki erteleme sınıflarının davranışı da dahil olmak üzere bu konunun önemli konusudur.  
  
### <a name="definitions"></a>Tanımlar  
  
- *DataContract seri hale getirici*: .NET Framework 3,0 veya sonraki sürümlerin Windows Communication Framework (WCF) bileşeni tarafından kullanılan varsayılan seri hale getirici.  
  
- Tek yönlü *serileştirme*: yalnızca tek yönlü bir ilişkilendirme özelliği içeren bir sınıfın serileştirilmiş sürümü (döngüyü önlemek için). Kurala göre, birincil yabancı anahtar ilişkisinin üst tarafındaki özelliği serileştirme olarak işaretlenir. Çift yönlü ilişkilendirmedeki diğer kenar serileştirilmez.  
  
     Tek yönlü serileştirme tarafından desteklenen tek seri hale getirme türüdür [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
## <a name="code-example"></a>Kod Örneği  

 Aşağıdaki kod, `Customer` `Order` Northwind örnek veritabanındaki geleneksel ve sınıfları kullanır ve bu sınıfların serileştirme öznitelikleriyle nasıl donatılmış olduğunu gösterir.  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 `Order`Aşağıdaki örnekteki sınıfı için, yalnızca sınıfına karşılık gelen ters ilişkilendirme özelliği `Customer` kısaltma için gösterilir. <xref:System.Runtime.Serialization.DataMemberAttribute>Döngüden kaçınmak için bir özniteliği yok.  
  
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
  
 İki otomatik özyinelemeli ilişkiye sahip olan aşağıdaki sınıfı göz önünde bulundurun: Employee. Manager/Reports ve Employee. Mentor/Mentees.  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
- [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme](how-to-make-entities-serializable.md)
