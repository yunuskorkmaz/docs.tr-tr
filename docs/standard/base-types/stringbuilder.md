---
title: StringBuilder Sınıfını .NET'te kullanma
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121671"
---
# <a name="using-the-stringbuilder-class-in-net"></a>StringBuilder Sınıfını .NET'te kullanma
Nesne <xref:System.String> değişmez. <xref:System.String?displayProperty=nameWithType> Sınıftaki yöntemlerden birini her kullandığınızda, bellekte yeni bir dize nesnesi oluşturursunuz ve bu yeni nesne için yeni bir alan ayırmagerektirir. Bir dizede tekrarlanan değişiklikler gerçekleştirmeniz gereken durumlarda, yeni <xref:System.String> bir nesne oluşturmayla ilişkili ek yükü maliyetli olabilir. Sınıf, <xref:System.Text.StringBuilder?displayProperty=nameWithType> yeni bir nesne oluşturmadan bir dize değiştirmek istediğinizde kullanılabilir. Örneğin, <xref:System.Text.StringBuilder> sınıfı kullanmak, birçok dizeleri bir döngü içinde bir araya getirirken performansı artırabilir.  
  
## <a name="importing-the-systemtext-namespace"></a>System.Text Namespace Alma  
 Sınıf <xref:System.Text.StringBuilder> <xref:System.Text> ad alanında bulunur.  Kodunuzda tam nitelikli bir tür adı sağlamak zorunda kalmamak için <xref:System.Text> ad alanını içe aktarabilirsiniz:  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>StringBuilder Nesnesi Anında  
 Aşağıdaki örnekte gösterildiği gibi, değişkeninizi aşırı yüklü yapıcı yöntemlerinden biriyle baş harfe alarak <xref:System.Text.StringBuilder> sınıfın yeni bir örneğini oluşturabilirsiniz.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Kapasite ve Uzunluğu Ayarlama  
 Bu, <xref:System.Text.StringBuilder> kapsüllediğiniz dizedeki karakter sayısını genişletmenize olanak tanıyan dinamik bir nesne olsa da, tutabileceği maksimum karakter sayısı için bir değer belirtebilirsiniz. Bu değer nesnenin kapasitesi olarak adlandırılır ve akımın <xref:System.Text.StringBuilder> tuttuğu dize uzunluğu ile karıştırılmamalıdır. Örneğin, uzunluğu 5 olan "Merhaba" dizesiyle <xref:System.Text.StringBuilder> sınıfın yeni bir örneğini oluşturabilir ve nesnenin en fazla 25 kapasiteye sahip olduğunu belirtebilirsiniz. <xref:System.Text.StringBuilder>Değiştirdiğinizde, kapasiteye ulaşılıncaya kadar boyutu kendisi için yeniden tahsis etmez. Bu durumda, yeni alan otomatik olarak ayrılır ve kapasite iki katına çıkarılır. Aşırı yüklü yapıcılardan <xref:System.Text.StringBuilder> birini kullanarak sınıfın kapasitesini belirtebilirsiniz. Aşağıdaki örnek, nesnenin `myStringBuilder` en fazla 25 boşalana genişletilebileceği belirtilmeye değerdir.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 Ayrıca, nesnenizin maksimum uzunluğunu ayarlamak için okuma/yazma <xref:System.Text.StringBuilder.Capacity%2A> özelliğini kullanabilirsiniz. Aşağıdaki örnekte, maksimum nesne uzunluğunu tanımlamak için **Kapasite** özelliği ni kullanır.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 Yöntem <xref:System.Text.StringBuilder.EnsureCapacity%2A> geçerli **StringBuilder**kapasitesini kontrol etmek için kullanılabilir. Kapasite geçirilen değerden büyükse, hiçbir değişiklik yapılmaz; ancak, kapasite geçirilen değerden daha küçükse, geçerli kapasite geçirilen değerle eşleşecek şekilde değiştirilir.  
  
 Özellik <xref:System.Text.StringBuilder.Length%2A> de görüntülenebilir veya ayarlanabilir. **Uzunluk** özelliğini **Kapasite** özelliğinden büyük bir değere ayarlarsanız, **Kapasite** özelliği otomatik olarak **Uzunluk** özelliğiyle aynı değere değiştirilir. **Uzunluk** özelliğini geçerli **StringBuilder** içindeki dize uzunluğundan daha az bir değere ayarlama dizeyi kısaltır.  
  
## <a name="modifying-the-stringbuilder-string"></a>StringBuilder Dizesini Değiştirme  
 Aşağıdaki tabloda **StringBuilder**içeriğini değiştirmek için kullanabileceğiniz yöntemler listelenebilmiştir.  
  
|Yöntem adı|Kullanım|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Geçerli **StringBuilder**sonuna bilgi ekler.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Bir dize geçirilen biçimlendirme belirticinin yerine biçimlendirilmiş metin le birlikte geçer.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Geçerli **StringBuilder'ın**belirtilen dizinine bir dize veya nesne ekler.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Geçerli **StringBuilder'dan**belirli sayıda karakter kaldırır.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Belirtilen dizinde belirtilen bir karakteri değiştirir.|  
  
### <a name="append"></a>Ekle  
 **Append** yöntemi, geçerli **StringBuilder**tarafından temsil edilen bir dize sonuna metin veya bir nesnenin dize gösterimi eklemek için kullanılabilir. Aşağıdaki örnek, **StringBuilder'ı** "Hello World" olarak algılar ve sonra nesnenin sonuna bir metin ekler. Alan gerektiği gibi otomatik olarak ayrılır.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>Appendformat  
 Yöntem <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder> nesnenin sonuna metin ekler. Biçimlendirilecek nesne veya nesnelerin <xref:System.IFormattable> uygulanmasını çağırarak bileşik biçimlendirme özelliğini (daha fazla bilgi için, [bkz. Bileşik Biçimlendirme)](../../../docs/standard/base-types/composite-formatting.md)destekler. Bu nedenle, sayısal, tarih ve saat ve numaralandırma değerleri için standart biçim dizeleri, sayısal ve tarih ve saat değerleri için özel biçim dizeleri ve özel türleri için tanımlanan biçim dizeleri kabul eder. (Biçimlendirme hakkında bilgi için [bkz.](../../../docs/standard/base-types/formatting-types.md) Değişkenlerin biçimini özelleştirmek ve bu değerleri bir <xref:System.Text.StringBuilder>. Aşağıdaki örnek, <xref:System.Text.StringBuilder.AppendFormat%2A> <xref:System.Text.StringBuilder> nesnenin sonuna para birimi değeri olarak biçimlendirilmiş bir tamsayı değeri yerleştirmek için yöntemi kullanır.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Ekle  
 Yöntem, <xref:System.Text.StringBuilder.Insert%2A> geçerli <xref:System.Text.StringBuilder> nesnedeki belirli bir konuma bir dize veya nesne ekler. Aşağıdaki örnek, bir sözcüğü nesnenin <xref:System.Text.StringBuilder> altıncı konumuna eklemek için bu yöntemi kullanır.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>Kaldır  
 Belirtilen sıfır **Remove** tabanlı dizinten başlayarak geçerli <xref:System.Text.StringBuilder> nesneden belirli sayıda karakter kaldırmak için Kaldır yöntemini kullanabilirsiniz. Aşağıdaki örnek, **Remove** bir <xref:System.Text.StringBuilder> nesneyi kısaltmak için Kaldır yöntemini kullanır.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>Değiştir  
 **Nesne** içindeki <xref:System.Text.StringBuilder> karakterleri başka bir belirtilen karakterle değiştirmek için Değiştir yöntemi kullanılabilir. Aşağıdaki örnek, **Replace** ünlem işareti <xref:System.Text.StringBuilder> karakterinin tüm örnekleri (!) için bir nesneyi aramak ve bunları soru işareti karakteri (?) ile değiştirmek için Değiştir yöntemini kullanır.  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>StringBuilder Nesnesini Dize dönüştürme  
 Nesne tarafından <xref:System.Text.StringBuilder> temsil edilen <xref:System.String> dizeyi <xref:System.String> parametreye geçirebilmek veya kullanıcı arabiriminde görüntülemek için nesneyi bir nesneye dönüştürmeniz gerekir. <xref:System.Text.StringBuilder> Bu dönüştürmeyi <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> yöntemi arayarak yaparsınız. Aşağıdaki örnekte bir <xref:System.Text.StringBuilder> dizi yöntem çağrır ve ardından dizeyi <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> görüntülemek için yöntemi çağırır.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.StringBuilder?displayProperty=nameWithType>
- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
