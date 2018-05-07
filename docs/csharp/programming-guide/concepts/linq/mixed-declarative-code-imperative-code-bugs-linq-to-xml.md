---
title: Bildirim temelli kod kesinliği kod hataları (LINQ-XML) karma (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: efc58aac69c53cda724e5fe348560a99311e8d4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a>Bildirim temelli kod/kesinliği kod hataları (LINQ-XML) karma (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir XML ağacı doğrudan değiştirmenize izin çeşitli yöntemler içerir. Öğeler ekleme, öğeleri silin, bir öğenin içeriğini değiştirme, öznitelikler eklemek ve benzeri. Bu programlama arabirimi açıklanan [XML ağaçlarını değiştirme (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md). Eksenleri, biri aracılığıyla gibi yineleme varsa <xref:System.Xml.Linq.XContainer.Elements%2A>ve eksen yineleme olarak XML ağaç değiştiriyorsunuz, bazı garip hatalarla düşebilir.  
  
 Bu sorun, bazen "Cadılar sorunun" adı verilir.  
  
## <a name="definition-of-the-problem"></a>Sorun tanımı  
 Bir toplulukta tekrarlanan LINQ kullanarak biraz kod yazarken, bildirim temelli stilde kodu yazıyor. Açıklayan benzer daha fazla *ne* istediğiniz, bunun yerine, *nasıl* onu bitti almak istediğiniz. 1) ilk öğesi alır kod yazın, sonra da bu kesinlik temelli kodu olacaktır 2) testleri belli bir koşul için 3) değiştirdiği ve 4) yerleştirir listesine yedekleyin. Bilgisayar söylemiş olursunuz *nasıl* yapılmasını istediğinizi yapmak için.  
  
 Kod aynı işlemde bu stiller karıştırma ne sorunları müşteri adayları olur. Aşağıdakileri göz önünde bulundurun:  
  
 Üç öğeleri ile bağlantılı bir liste içinde olduğunu varsayalım (a, b ve c):  
  
 `a -> b -> c`  
  
 Şimdi, bağlantılı liste taşımak üç yeni öğeler eklemek istediğinizi varsayalım (bir ', b' ve c'). Şuna için sonuçta elde edilen bağlantılı liste istediğiniz:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Bu nedenle listesi kullanılarak ve her öğe için tekrarlanan kod yazma yeni öğeyi sağ sonra ekler. Kodunuzu ilk göreceği gerçekleşir `a` öğesi ve INSERT `a'` sonraki. Şimdi, kodunuzu artık listesindeki bir sonraki düğüme taşır `a'`! Sonsuza dek listesine yeni bir öğe ekler `a''`.  
  
 Nasıl, bu gerçek dünyada ister misiniz? İyi, özgün bağlantılı listesinin bir kopyasını alın ve tamamen yeni bir liste oluşturur. Veya ilk öğe bulabileceğiniz tamamen kesinlik temelli kod yazıyorsanız, yeni öğe eklemek ve yeni eklediğiniz öğenin üzerine ilerledikten iki kez bağlantılı listesinde ilerleyin.  
  
## <a name="adding-while-iterating"></a>Yineleme sırasında ekleme  
 Örneğin, yinelenen bir öğe oluşturmak istediğiniz bir ağacında her öğe için biraz kod yazmaya istediğinizi varsayalım:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 Bu kod sonsuz döngüye girer. `foreach` Deyimi tekrarlanan aracılığıyla `Elements()` eksen için yeni öğe eklemek, `doc` öğesi. Ayrıca aracılığıyla yeni eklenen öğelerin yineleme yukarı sona erer. Ve yeni nesneler her döngü ile ayırdığından, sonunda tüm kullanılabilir bellek tüketir.  
  
 Bellek kullanarak koleksiyon çekerek bu sorunu düzeltebilirsiniz <xref:System.Linq.Enumerable.ToList%2A> aşağıdaki gibi standart sorgu işleci:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    root.Add(new XElement(e.Name, (string)e));  
Console.WriteLine(root);  
```  
  
 Şimdi kodu çalışır. Sonuçta elde edilen XML ağaç aşağıda verilmiştir:  
  
```xml  
<Root>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
## <a name="deleting-while-iterating"></a>Yineleme sırasında silme  
 Belirli bir düzeyde tüm düğümleri silmek istiyorsanız, aşağıdaki gibi bir kod yazmak için isteği olabilir:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 Ancak, bunu istediğinizi yapmaz. Bu durumda, ilk öğe, A kaldırdıktan sonra kökünde bulunan XML ağacından kaldırıldı ve yineleme yaptığını öğeleri yöntemi kodda sonraki öğesi bulunamıyor.  
  
 Önceki kod şu çıkışı üretir:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 Çözümü yeniden çağırmaktır <xref:System.Linq.Enumerable.ToList%2A> koleksiyonu gibi gerçekleştirmeye için:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 Bu şu çıkışı üretir:  
  
```xml  
<Root />  
```  
  
 Alternatif olarak, yineleme tamamen çağırarak ortadan kaldırabileceğiniz <xref:System.Xml.Linq.XElement.RemoveAll%2A> üst öğede:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a>Neden LINQ otomatik olarak bu işleyemiyor?  
 Bir yaklaşım, her zaman her şeyi belleğe geç değerlendirme yapmak yerine getirmek için olacaktır. Ancak, performans ve bellek kullanımı açısından çok pahalı olacaktır. Aslında, bu yaklaşımı benimsemeye LINQ ve (LINQ-XML) olsaydı, gerçek durumlarda başarısız olur.  
  
 Başka bir olası yaklaşım işlem sözdizimi LINQ çeşit koyun ve kod çözümlemek ve belirli bir koleksiyon gerçekleştirilmesi gerekli olmadığını belirlemek için derleyici girişimi sahip olacaktır. Ancak, yan etkileri olan tüm kodu belirlenmeye çalışılırken son derece karmaşıktır. Aşağıdaki kod göz önünde bulundurun:  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 Bu tür Analiz kodu TestSomeCondition ve DoMyProjection yöntemleri ve herhangi bir kod yan etkileri sahip belirlemek için bu yöntem çağrılır tüm yöntemleri çözümlemek gerekir. Ancak yan etkileri olan herhangi bir kod için Kod Analizine yalnızca aranamadı. İçin alt öğelerde yan etkileri olan kodu seçmeniz gerekir `root` bu durumda.  
  
 LINQ-XML gibi bir analiz yapma denemez.  
  
 Bu sorunları önlemek için size bağlıdır.  
  
## <a name="guidance"></a>Kılavuz  
 İlk olarak, bildirim temelli ve kesinlik temelli kodu karışık kullanmayın.  
  
 Tam olarak koleksiyonlarınızı semantiği ve bu kategoriler sorunları önler akıllı biraz kod yazarsanız XML ağaç değiştirme yöntemleri semantiği bildiğiniz olsa bile, kodunuzu diğer geliştiriciler tarafından gelecekte saklanması gerekir , ve bunların sorunlarını olabildiğince açık olmayabilir. Bildirim temelli ve kesinlik temelli stilleri kodlama karıştırmak, kodunuzu daha kırılır olacaktır.  
  
 Bir koleksiyon gerçeğe ve böylece bu sorunlardan kaçınılması kodu yazarsanız, böylece bakım programcıları sorunu anlayabileceği, kodunuzda uygun şekilde yorumlarla unutmayın.  
  
 İkinci olarak, performans ve diğer konular için izin verirseniz, yalnızca bildirim temelli kodunu kullanın. Varolan bir XML ağacında değiştirmeyin. Yeni bir tane oluşturun.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
XElement newRoot = new XElement("Root",  
    root.Elements(),  
    root.Elements()  
);  
Console.WriteLine(newRoot);  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş LINQ-XML programlama (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
