---
title: .NET 'teki StringBuilder sınıfını kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Remove method
- strings [.NET Framework], capacities
- StringBuilder object
- Replace method
- AppendFormat method
- Append method
- Insert method
- strings [.NET Framework], StringBuilder object
ms.assetid: 5c14867c-9a99-45bc-ae7f-2686700d377a
ms.openlocfilehash: 19ee90f3300e3b610eeefd4949baa2759b834a60
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121671"
---
# <a name="using-the-stringbuilder-class-in-net"></a>.NET 'teki StringBuilder sınıfını kullanma
<xref:System.String> nesnesi sabittir. <xref:System.String?displayProperty=nameWithType> sınıfındaki yöntemlerden birini her kullandığınızda, bellekte yeni bir boş alan alanı gerektiren yeni bir dize nesnesi oluşturursunuz. Bir dizeye yinelenen değişiklikler gerçekleştirmeniz gereken durumlarda, yeni bir <xref:System.String> nesnesi oluşturmayla ilişkili ek yük maliyetli olabilir. <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıfı, yeni bir nesne oluşturmadan bir dizeyi değiştirmek istediğinizde kullanılabilir. Örneğin, <xref:System.Text.StringBuilder> sınıfını kullanmak bir döngüde birçok dizeyi birlikte birleştirirken performansı artırabilir.  
  
## <a name="importing-the-systemtext-namespace"></a>System. Text ad alanını içeri aktarma  
 <xref:System.Text.StringBuilder> sınıfı <xref:System.Text> ad alanında bulunur.  Kodunuzda tam nitelikli bir tür adı sağlamak zorunda kalmamak için <xref:System.Text> ad alanını içeri aktarabilirsiniz:  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>Bir StringBuilder nesnesini örnekleme  
 Aşağıdaki örnekte gösterildiği gibi, değişkeninizi aşırı yüklenmiş Oluşturucu yöntemlerinden biri ile başlatarak <xref:System.Text.StringBuilder> sınıfının yeni bir örneğini oluşturabilirsiniz.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Kapasiteyi ve uzunluğu ayarlama  
 <xref:System.Text.StringBuilder>, sarmalayan dizedeki karakter sayısını genişletmenizi sağlayan dinamik bir nesne olsa da, tutabileceğiniz en fazla karakter sayısı için bir değer belirtebilirsiniz. Bu değere nesnenin kapasitesi denir ve geçerli <xref:System.Text.StringBuilder> tutan dizenin uzunluğu ile karıştırılmamalıdır. Örneğin, 5 uzunluğuna sahip bir <xref:System.Text.StringBuilder> sınıfının yeni bir örneğini oluşturabilir ve bu dizenin en fazla 25 kapasiteye sahip olduğunu belirtebilirsiniz. <xref:System.Text.StringBuilder>değiştirdiğinizde, kapasiteye ulaşılana kadar kendi boyutunu yeniden tahsis etmez. Bu gerçekleştiğinde, yeni alan otomatik olarak ayrılır ve kapasite iki katına çıkar. <xref:System.Text.StringBuilder> sınıfının kapasitesini, aşırı yüklenmiş oluşturuculardan birini kullanarak belirtebilirsiniz. Aşağıdaki örnek, `myStringBuilder` nesnesinin en fazla 25 boşluğa genişletilebilecek olduğunu belirtir.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 Ayrıca, nesnenizin maksimum uzunluğunu ayarlamak için okuma/yazma <xref:System.Text.StringBuilder.Capacity%2A> özelliğini de kullanabilirsiniz. Aşağıdaki örnek, en fazla nesne uzunluğunu tanımlamak için **Kapasite** özelliğini kullanır.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 <xref:System.Text.StringBuilder.EnsureCapacity%2A> yöntemi, geçerli **StringBuilder**'ın kapasitesini denetlemek için kullanılabilir. Kapasite geçilen değerden büyükse, hiçbir değişiklik yapılmaz; Ancak, kapasite geçilen değerden küçükse, geçerli kapasite geçen değerle eşleşecek şekilde değiştirilir.  
  
 <xref:System.Text.StringBuilder.Length%2A> özelliği de görüntülenebilir veya ayarlanabilir. **Length** özelliğini **Kapasite** özelliğinden daha büyük bir değere ayarlarsanız, **Kapasite** özelliği otomatik olarak **length** özelliği ile aynı değere değiştirilir. **Length** özelliğinin, geçerli **StringBuilder** içindeki dizenin uzunluğundan daha küçük bir değere ayarlanması dizeyi kısaltır.  
  
## <a name="modifying-the-stringbuilder-string"></a>StringBuilder dizesini değiştirme  
 Aşağıdaki tabloda, bir **StringBuilder**'ın içeriğini değiştirmek için kullanabileceğiniz yöntemler listelenmiştir.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Bilgileri geçerli **StringBuilder**'ın sonuna ekler.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Bir dizede geçirilen biçim belirticisini biçimli metinle değiştirir.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Geçerli **StringBuilder**'ın belirtilen dizinine bir dize veya nesne ekler.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Geçerli **StringBuilder**'dan belirtilen sayıda karakteri kaldırır.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Belirtilen bir dizindeki belirtilen karakteri değiştirir.|  
  
### <a name="append"></a>Ýna  
 **Append** yöntemi, geçerli **StringBuilder**tarafından temsil edilen bir dizenin sonuna bir nesnenin metin veya dize gösterimini eklemek için kullanılabilir. Aşağıdaki örnek, bir **StringBuilder** 'ı "Merhaba Dünya" olarak başlatır ve sonra nesnenin sonuna bir metin ekler. Boşluk gerektiğinde otomatik olarak ayrılır.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>AppendFormat  
 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> yöntemi <xref:System.Text.StringBuilder> nesnesinin sonuna metin ekler. Biçimlendirilmiş biçimlendirme özelliğini destekler (daha fazla bilgi için bkz. [Bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)) nesne veya nesnelerin <xref:System.IFormattable> uygulamasını çağırarak. Bu nedenle, sayısal, tarih ve saat ve numaralandırma değerleri için standart biçim dizelerini, sayısal ve Tarih ve saat değerleri için özel biçim dizelerini ve özel türler için tanımlanan biçim dizelerini kabul eder. (Biçimlendirme hakkında bilgi için bkz. [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md).) Değişkenlerin biçimini özelleştirmek ve bu değerleri bir <xref:System.Text.StringBuilder>eklemek için bu yöntemi kullanabilirsiniz. Aşağıdaki örnek, bir <xref:System.Text.StringBuilder> nesnesinin sonunda para birimi değeri olarak biçimlendirilen bir tamsayı değeri yerleştirmek için <xref:System.Text.StringBuilder.AppendFormat%2A> yöntemini kullanır.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Ekleme  
 <xref:System.Text.StringBuilder.Insert%2A> yöntemi, geçerli <xref:System.Text.StringBuilder> nesnesinde belirtilen konuma bir dize veya nesne ekler. Aşağıdaki örnek, bir <xref:System.Text.StringBuilder> nesnesinin altıncı konumuna bir sözcük eklemek için bu yöntemi kullanır.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>Kaldır  
 Belirli bir sıfır tabanlı dizinden başlayarak geçerli <xref:System.Text.StringBuilder> nesnesinden belirtilen sayıda karakteri kaldırmak için **Remove** metodunu kullanabilirsiniz. Aşağıdaki örnek, <xref:System.Text.StringBuilder> nesnesini kısaltmak için **Remove** metodunu kullanır.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>değiştirin  
 **Replace** yöntemi, <xref:System.Text.StringBuilder> nesnesi içindeki karakterlerin belirtilen başka bir karakterle değiştirilmesini sağlamak için kullanılabilir. Aşağıdaki örnek, bir <xref:System.Text.StringBuilder> nesnesini ünlem işareti karakterinin (!) tüm örnekleri için aramak ve bunları soru işareti karakteriyle (?) değiştirmek için **Replace** metodunu kullanır.  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>StringBuilder nesnesini dizeye dönüştürme  
 <xref:System.Text.StringBuilder> nesnesi tarafından temsil edilen dizeyi <xref:System.String> parametresine sahip bir yönteme geçirebilmeniz veya Kullanıcı arabiriminde gösterebilmek için <xref:System.Text.StringBuilder> nesnesini bir <xref:System.String> nesnesine dönüştürmeniz gerekir. Bu dönüştürme <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> yöntemini çağırarak yapabilirsiniz. Aşağıdaki örnek bir dizi <xref:System.Text.StringBuilder> yöntemi çağırır ve sonra dizeyi göstermek için <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> yöntemini çağırır.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.StringBuilder?displayProperty=nameWithType>
- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
