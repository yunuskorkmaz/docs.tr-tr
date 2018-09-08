---
title: . NET'te StringBuilder sınıfını kullanma
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 099e2de40458e42c9df34e74dee8d9fc7c425dea
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197320"
---
# <a name="using-the-stringbuilder-class-in-net"></a>. NET'te StringBuilder sınıfını kullanma
<xref:System.String> Nesne değişmez. Metotlarından birini her kullanışınızda <xref:System.String?displayProperty=nameWithType> sınıf yeni nesne için yeni bir ayırma alanı gerektiren bellekte yeni bir dize nesnesi oluşturun. Bir dizeye yinelenen değişiklikleri uygulamak için ihtiyacınız olduğu durumlarda ek yükü ilişkili yeni oluşturma ile <xref:System.String> nesne maliyetli olabilir. <xref:System.Text.StringBuilder?displayProperty=nameWithType> Sınıfı, bir dize yeni bir nesne oluşturulmadan değiştirmek istediğinizde kullanılabilir. Örneğin, kullanarak <xref:System.Text.StringBuilder> sınıfı döngü içinde birlikte birçok dizeleri birleştirme, performansı artırmak.  
  
## <a name="importing-the-systemtext-namespace"></a>System.Text Namespace alma  
 <xref:System.Text.StringBuilder> Sınıfı içinde bulunan <xref:System.Text> ad alanı.  Tam olarak nitelenmiş tür adları, kodunuzda sağlamak zorunda kalmamak için alabileceğiniz <xref:System.Text> ad alanı:  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>Bir StringBuilder nesnesini örnekleme  
 Yeni bir örneğini oluşturabilirsiniz <xref:System.Text.StringBuilder> aşağıdaki örnekte gösterildiği gibi değişken yöntemlerinden biri olan aşırı yüklenmiş Oluşturucu ile başlatma tarafından sınıfı.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Kapasite ve uzunluğunu ayarlama  
 Ancak <xref:System.Text.StringBuilder> bunu kapsülleyen dizedeki karakter sayısını artıracak olanak tanıyan dinamik bir nesnedir içerebileceği karakter sayısı için bir değer belirtebilirsiniz. Bu değer nesnesinin capacity ve dizenin uzunluğu ile karıştırılmamalıdır, geçerli <xref:System.Text.StringBuilder> tutar. Örneğin, yeni bir örneğini oluşturabilirsiniz <xref:System.Text.StringBuilder> 5 ve uzunluğu "Hello" dizesi ile sınıfı belirtin nesne 25 kapasiteye sahiptir. Değiştirdiğinizde <xref:System.Text.StringBuilder>, kapasite sınırına kadar bu boyutu kendisi için yeniden tahsis değil. Bu durumda, yeni alan otomatik olarak ayrılır ve kapasite sayısı iki katına çıkar. Kapasitesini belirtebilirsiniz <xref:System.Text.StringBuilder> aşırı yüklü oluşturucular birini kullanarak sınıfı. Aşağıdaki örnek belirten `myStringBuilder` nesne en fazla 25 alanları için genişletilebilir.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 Ayrıca, okuma/yazma kullanabilirsiniz <xref:System.Text.StringBuilder.Capacity%2A> nesnenizin uzunluğu en fazla ayarlamak için özellik. Aşağıdaki örnekte **kapasite** uzunluğu en fazla nesne tanımlamak için özellik.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 <xref:System.Text.StringBuilder.EnsureCapacity%2A> Yöntemi, geçerli kapasite denetlemek için kullanılabilir **StringBuilder**. Kapasite geçen değerinden daha büyük ise, hiçbir değişiklik yapıldığında; Ancak, kapasite geçirilen değerinden küçükse, geçerli kapasite geçirilen değerle eşleşecek şekilde değiştirilir.  
  
 <xref:System.Text.StringBuilder.Length%2A> Özelliği de görüntülenebilir veya ayarlayın. Ayarlarsanız **uzunluğu** değerinden büyük bir değere **kapasite** özelliği **kapasite** özelliği aynı değere otomatikolarakdeğiştirildiğinde **Uzunluğu** özelliği. Ayarı **uzunluğu** geçerli içindeki dizenin uzunluğu'dan küçük bir değere **StringBuilder** dize kısaltır.  
  
## <a name="modifying-the-stringbuilder-string"></a>StringBuilder dizeyi değiştirme  
 Aşağıdaki tabloda içeriğini değiştirmek için kullanabileceğiniz yöntemler listelenmiştir bir **StringBuilder**.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Bilgi geçerli sonuna ekler **StringBuilder**.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Biçimlendirilmiş metin içeren bir dize geçirilen bir biçim belirtici değiştirir.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Bir dize veya nesne geçerli belirtilen dizine ekler **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Geçerli belirtilen sayıda karakteri kaldırır **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Belirtilen dizindeki belirtilen bir karakterin yerini alır.|  
  
### <a name="append"></a>Ekleme  
 **Ekleme** yöntemi, metin veya bir nesnenin dize gösterimini geçerli tarafından temsil edilen bir dizenin sonuna eklemek için kullanılabilir **StringBuilder**. Aşağıdaki örnek başlatır bir **StringBuilder** "Hello World" ve ardından metin nesnesinin sonuna ekler. Alanı gerektiğinde otomatik olarak ayrılır.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>AppendFormat  
 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> Yöntemi sonuna metin ekler <xref:System.Text.StringBuilder> nesne. Bileşik biçimlendirme özelliği destekler (daha fazla bilgi için [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)) çağırarak <xref:System.IFormattable> nesne veya nesneler Biçimlendirilecek uygulamasıdır. Bu nedenle, sayısal, tarih ve saat ile sabit listesi değerleri, özel biçim dizeleri için sayısal ve tarih ve saat değerleri için standart biçim dizeleri ve özel türleri için tanımlanan biçim dizeleri kabul eder. (Biçimlendirme hakkında daha fazla bilgi için bkz. [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md).) Değişkenleri biçimini özelleştirmek ve bu değer eklemek için bu yöntemi kullanabilirsiniz bir <xref:System.Text.StringBuilder>. Aşağıdaki örnekte <xref:System.Text.StringBuilder.AppendFormat%2A> yöntemi bir tamsayı değeri yerleştirmek için biçimlendirilmiş sonunda bir para birimi değeri olarak bir <xref:System.Text.StringBuilder> nesne.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Ekleme  
 <xref:System.Text.StringBuilder.Insert%2A> Geçerli belirtilen konuma yöntemi ekler bir dize veya nesne <xref:System.Text.StringBuilder> nesne. Aşağıdaki örnek, bir sözcük altıncı konumunu eklemek için bu yöntemi kullanır. bir <xref:System.Text.StringBuilder> nesne.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>Kaldır  
 Kullanabileceğiniz **Kaldır** yöntemi belirtilen sayıda karakteri geçerli kaldırmak için <xref:System.Text.StringBuilder> nesne, sıfır tabanlı bir belirtilen dizinden başlayarak. Aşağıdaki örnekte **Kaldır** kısaltmak için yöntemi bir <xref:System.Text.StringBuilder> nesne.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>Değiştir  
 **Değiştirin** yöntemi içindeki karakterleri değiştirmek için kullanılabilir <xref:System.Text.StringBuilder> başka bir nesne belirtilen karakter. Aşağıdaki örnekte **değiştirin** yöntemi aramak için bir <xref:System.Text.StringBuilder> nesnesi tüm örneklerini ünlem işareti karakteri (!) ve bunları soru işareti karakteri (?) ile değiştirin.  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>Bir StringBuilder nesnesini dizeye dönüştürme  
 Dönüştürmeniz gerekir <xref:System.Text.StringBuilder> nesnesini bir <xref:System.String> tarafından temsil edilen bir dizeyi geçirmek önce nesne <xref:System.Text.StringBuilder> nesne içeren bir yöntem için bir <xref:System.String> parametresi veya kullanıcı arabiriminde görüntülenir. Çağırarak bu dönüştürmeyi yapmak <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> yöntemi. Aşağıdaki örnek sayısı <xref:System.Text.StringBuilder> yöntemleri ve çağrıları <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> dizesini görüntülemek için yöntemi.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.StringBuilder?displayProperty=nameWithType>  
- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)  
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
