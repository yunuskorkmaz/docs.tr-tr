---
title: ".NET StringBuilder sınıfını kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3a6c8f6dee9f2a1da6ed4a8219c1b4832464d9aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-stringbuilder-class-in-net"></a>.NET StringBuilder sınıfını kullanma
<xref:System.String> Nesnesidir değişmez. Yöntemlerden birini her kullanışınızda <xref:System.String?displayProperty=nameWithType> sınıfı, oluşturduğunuz yeni bir dize nesnesi bellekte bu yeni nesne için yeni bir ayırma alanı gerektirir. Burada bir dize yinelenen değişiklikleri gerçekleştirmeniz gerekir durumlarda yükü ilişkili yeni bir oluşturma ile <xref:System.String> nesne maliyetli olabilir. <xref:System.Text.StringBuilder?displayProperty=nameWithType> Sınıfı, yeni bir nesne oluşturmadan bir dize değiştirmek istediğinizde kullanılabilir. Örneğin, kullanarak <xref:System.Text.StringBuilder> sınıfı Döngüdeki birlikte birçok dizeleri birleştirme, performansı artırmak.  
  
## <a name="importing-the-systemtext-namespace"></a>System.Text Namespace içeri aktarma  
 <xref:System.Text.StringBuilder> Sınıfı içinde bulunan <xref:System.Text> ad alanı.  Tam olarak nitelenmiş tür adları, kodunuzda sağlar yapmak zorunda kalmamak için aktarabilirsiniz <xref:System.Text> ad alanı:  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>StringBuilder nesnesi örneği  
 Yeni bir örneğini oluşturabilirsiniz <xref:System.Text.StringBuilder> aşağıdaki örnekte gösterildiği gibi değişkeni aşırı yüklü Oluşturucu yöntemlerden biri ile başlatma tarafından sınıfı.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Kapasite ve uzunluğu ayarlama  
 Ancak <xref:System.Text.StringBuilder> onu yalıtan, dizedeki karakter sayısını genişletmek izin veren dinamik bir nesnedir içerebileceğinden karakter sayısı için bir değer belirtebilirsiniz. Bu değer nesnesinin kapasite olarak adlandırılır ve dize uzunluğu ile karıştırılmamalıdır, geçerli <xref:System.Text.StringBuilder> tutar. Örneğin, yeni bir örneğini oluşturabilirsiniz <xref:System.Text.StringBuilder> dize uzunluğu 5 ve "Hello" sınıfıyla belirtin nesnesi 25 en fazla kapasiteye sahiptir. Değiştirdiğinizde <xref:System.Text.StringBuilder>, kapasite sınırına kadar bu boyutu kendisi için yeniden tahsis değil. Bu durumda, yeni alan otomatik olarak ayrılır ve kapasite iki katına. Kapasitesini belirtin <xref:System.Text.StringBuilder> aşırı yüklü oluşturucular birini kullanarak sınıfı. Aşağıdaki örnek belirleyen `MyStringBuilder` nesne en fazla 25 alanları için genişletilebilir.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 Ayrıca, okuma/yazma kullanabilirsiniz <xref:System.Text.StringBuilder.Capacity%2A> nesneniz en büyük uzunluğu ayarlamak için özellik. Aşağıdaki örnek kullanır **kapasite** en fazla nesne uzunluğu tanımlamak için özellik.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 <xref:System.Text.StringBuilder.EnsureCapacity%2A> Yöntemi, geçerli kapasitesini denetlemek için kullanılabilir **StringBuilder**. Kapasite geçirilen değerinden büyükse, hiçbir değişiklik yapıldığında; Ancak, kapasite geçirilen değerinden küçükse, Geçerli kapasitenin geçirilen değerle eşleşecek şekilde değiştirilir.  
  
 <xref:System.Text.StringBuilder.Length%2A> Özelliği de görüntülenebilir veya ayarlayın. Ayarlarsanız **uzunluğu** özelliğini değerinden daha büyük bir değere **kapasite** özelliği, **kapasite** özelliği otomatik olarak aynı değeri olarakdeğiştirildi **Uzunluğu** özelliği. Ayarı **uzunluğu** özelliğini geçerli içinde dize uzunluğu'dan küçük bir değere **StringBuilder** dize kısaltır.  
  
## <a name="modifying-the-stringbuilder-string"></a>StringBuilder dize değiştirme  
 Aşağıdaki tabloda içeriğini değiştirmek için kullanabileceğiniz yöntemleri listelenmiştir bir **StringBuilder**.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Bilgi geçerli sonuna ekler **StringBuilder**.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Biçimlendirilmiş metin dizesiyle geçirilen bir biçim belirticisi yerini alır.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Bir dize veya nesne geçerli belirtilen dizine ekler **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Geçerli belirtilen sayıda karakteri kaldırır **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Belirtilen dizindeki belirtilen bir karakterin yerini alır.|  
  
### <a name="append"></a>ekleme  
 **Append** yöntemi, geçerli tarafından temsil edilen bir dize sonu metin ya da bir nesnenin dize gösterimini eklemek için kullanılabilir **StringBuilder**. Aşağıdaki örnek başlatır bir **StringBuilder** "Hello World" ve sonra bazı metinleri nesne sonuna ekler. Alan gerektiğinde otomatik olarak ayrılır.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>AppendFormat  
 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> Yöntemi sonuna metin ekler <xref:System.Text.StringBuilder> nesnesi. Bileşik biçimlendirme özelliğini destekler (daha fazla bilgi için bkz: [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)) çağırarak <xref:System.IFormattable> nesne ya da Biçimlendirilecek nesneleri uygulamasıdır. Bu nedenle, sayısal, tarih ve saat ile numaralandırma değerleri, sayısal için özel biçim dizeleri ve tarih ve saat değerleri için standart biçim dizeleri ve özel türleri için tanımlanan biçim dizeleri kabul eder. (Biçimlendirme hakkında daha fazla bilgi için bkz: [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md).) Değişkenleri biçimini özelleştirmek ve bu değer eklemek için bu yöntemi kullanabilirsiniz bir <xref:System.Text.StringBuilder>. Aşağıdaki örnek kullanır <xref:System.Text.StringBuilder.AppendFormat%2A> bir tamsayı değeri yerleştirmek için yöntemini biçimlendirilmiş sonunda para birimi değeri olarak bir <xref:System.Text.StringBuilder> nesnesi.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Ekleme  
 <xref:System.Text.StringBuilder.Insert%2A> Yöntemi ekler bir dize veya nesne geçerli belirtilen konumda <xref:System.Text.StringBuilder> nesnesi. Aşağıdaki örnek, bir sözcük altıncı konumunu eklemek için bu yöntemi kullanır. bir <xref:System.Text.StringBuilder> nesnesi.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>Kaldır  
 Kullanabileceğiniz **kaldırmak** belirtilen sayıda karakteri geçerli kaldırmak için yöntemi <xref:System.Text.StringBuilder> sıfır tabanlı bir belirtilen dizinden başlayarak nesne. Aşağıdaki örnek kullanır **kaldırmak** kısaltmak için yöntemi bir <xref:System.Text.StringBuilder> nesnesi.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>Değiştir  
 **Değiştir** yöntemi içindeki karakterleri değiştirmek için kullanılabilir <xref:System.Text.StringBuilder> başka bir nesneyle belirtilen karakter. Aşağıdaki örnek kullanır **Değiştir** aramak için yöntemi bir <xref:System.Text.StringBuilder> nesnesi için tüm örneklerini ünlem işareti karakteri (!) ve soru işareti (?) karakteri ile değiştirin.  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>StringBuilder nesnesi bir dizeye dönüştürme  
 Dönüştürmeniz gerekir <xref:System.Text.StringBuilder> nesnesine bir <xref:System.String> tarafından temsil edilen bir dizeyi geçirmek önce nesne <xref:System.Text.StringBuilder> içeren bir yöntem nesnesine bir <xref:System.String> parametresi veya kullanıcı arabiriminde görüntülenir. Bu dönüştürme musunuz <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> yöntemi. Aşağıdaki örnek bir dizi çağırır <xref:System.Text.StringBuilder> yöntemleri ve çağrıları <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> dize görüntülenecek yöntemi.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Text.StringBuilder?displayProperty=nameWithType>  
 [Temel dize işlemleri](../../../docs/standard/base-types/basic-string-operations.md)  
 [Biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md)
