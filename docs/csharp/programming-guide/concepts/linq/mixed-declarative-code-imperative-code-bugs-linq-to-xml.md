---
title: Karma bildirime dayalı kod-zorunlu kod hataları (LINQ to XML)C#()
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 30760999a264c81e16104c0c9b112d442ce66121
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591630"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a>Karma bildirime dayalı kod/zorunlu kod hataları (LINQ to XML)C#()
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]bir XML ağacını doğrudan değiştirmenize olanak sağlayan çeşitli yöntemler içerir. Öğe ekleyebilir, öğeleri silebilir, bir öğenin içeriğini değiştirebilir, öznitelik ekleyebilir ve benzerlerini yapabilirsiniz. Bu programlama arabirimi, [XML ağaçlarını (LINQ to XML)C#() değiştirme](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)konusunda açıklanmaktadır. Ve gibi eksenlerden <xref:System.Xml.Linq.XContainer.Elements%2A>birini yinelemenize sahipseniz ve eksen boyunca yineleme yaparken xml ağacını değiştiriyorsanız, bazı garip hatalara sahip olabilirsiniz.  
  
 Bu sorun bazen "Cadılar Bayramı sorunu" olarak bilinir.  
  
## <a name="definition-of-the-problem"></a>Sorunun tanımı  
 Bir koleksiyon aracılığıyla yinelenen LINQ kullanarak bazı kodlar yazdığınızda, bildirime dayalı bir stilde kod yazıyor demektir. İstediğiniz *şeyi* açıklamak, bunun yerine *nasıl* yapılacağını öğrenmek için daha fazla oturum vardır. 1\) ilk öğeyi alan bir kod yazarsanız, 2) onu bir koşul için sınar, 3) onu değiştirir ve 4) listeye geri koyar, bu da zorunlu kod olacaktır. Bilgisayara ne yapılacağını istediğinizi söyleirsiniz.  
  
 Bu kod stillerinin aynı işlemde karıştırılması, sorunlara yol gösterir. Aşağıdakileri göz önünde bulundurun:  
  
 İçinde üç öğe (a, b ve c) içeren bağlı bir listeniz olduğunu varsayalım:  
  
 `a -> b -> c`  
  
 Şimdi, bağlantılı liste içinde, üç yeni öğe (', b ' ve c ') ekleyerek geçiş yapmak istediğinizi varsayalım. Elde edilen bağlantılı listenin şuna benzer görünmesini istiyorsunuz:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Bu nedenle, liste boyunca yinelenen kod yazdığınızda ve her öğe için, hemen sonrasında yeni bir öğe ekler. Ne olacağı, kodunuzun `a` öğeyi ilk göreceği ve sonra ekleneceği `a'` şeydir. Şimdi, kodunuz listede `a'`bir sonraki düğüme geçmeyecektir. Bu, `a''`listeye yeni bir öğe ekler.  
  
 Bunu gerçek dünyada nasıl çözirsiniz? Ayrıca, özgün bağlantılı listenin bir kopyasını oluşturabilir ve tamamen yeni bir liste oluşturabilirsiniz. Ya da yalnızca zorunlu kod yazıyorsanız, ilk öğeyi bulabilir, yeni öğeyi ekleyebilir ve ardından bağlantılı listede iki kez ilerledikten sonra yeni eklediğiniz öğeden ilerleyebilirsiniz.  
  
## <a name="adding-while-iterating"></a>Yineleme sırasında ekleme  
 Örneğin, bir ağaçtaki her öğe için bir kod yazmak istediğinizi, yinelenen bir öğe oluşturmak istediğinizi varsayalım:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 Bu kod sonsuz bir döngüye girer. İfade, `doc` öğesine yeni öğeler `Elements()` ekleyerek eksen boyunca yinelenir. `foreach` Aynı zamanda, yeni eklenen öğeler aracılığıyla yineleme sona erer. Ayrıca, döngünün her tekrarında yeni nesneler ayırdığından, son olarak tüm kullanılabilir belleği tüketir.  
  
 Aşağıdaki gibi <xref:System.Linq.Enumerable.ToList%2A> standart sorgu işlecini kullanarak koleksiyonu belleğe çekerek bu sorunu çözebilirsiniz:  
  
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
  
 Kod artık işe yarar. Elde edilen XML ağacı aşağıda verilmiştir:  
  
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
 Tüm düğümleri belirli bir düzeyde silmek isterseniz, aşağıdaki gibi bir kod yazmayı düşünebilirsiniz:  
  
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
  
 Ancak, bu, istediğiniz şeyi yapmaz. Bu durumda, ilk öğesini kaldırıldıktan sonra, bir, kök içinde yer alan XML ağacından kaldırılır ve yineleme yapan öğeler yöntemindeki kod bir sonraki öğeyi bulamaz.  
  
 Yukarıdaki kod aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 Bu çözüm, koleksiyonu aşağıda gösterildiği <xref:System.Linq.Enumerable.ToList%2A> gibi yeniden gerçekleştirmek için çağrmaktır:  
  
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
  
 Bu, aşağıdaki çıktıyı üretir:  
  
```xml  
<Root />  
```  
  
 Alternatif olarak, üst öğeyi çağırarak <xref:System.Xml.Linq.XElement.RemoveAll%2A> yinelemeyi tamamen ortadan kaldırabilirsiniz:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a>LINQ neden bunu otomatik olarak Işleyemiyor?  
 Tek bir yaklaşım, her şeyi yavaş değerlendirme yapmak yerine her zaman belleğe getirmek olacaktır. Ancak, performans ve bellek kullanımı bakımından çok pahalıdır. Aslında, LINQ ve (LINQ to XML) bu yaklaşıma ulaşacaksa, gerçek dünyada durumlarda başarısız olur.  
  
 Başka bir olası yaklaşım, bazı işlem söz dizimine LINQ 'a yerleştirilecek ve derleyicinin kodu analiz etmeyi denemesini ve belirli bir koleksiyonun gerçekleştirilip gerçekleştirilmeyeceğini belirleyebilmesini sağlar. Ancak, yan etkileri olan tüm kodları belirleme girişimi inanılmaz karmaşıktır. Aşağıdaki kodu göz önünde bulundurun:  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 Bu tür analiz kodu, herhangi bir kodun yan etkilere sahip olup olmadığını anlamak için TestSomeCondition ve DoMyProjection yöntemlerini ve bu yöntemlerin çağırdığı tüm yöntemleri analiz etmeniz gerekir. Ancak, analiz kodu yalnızca yan etkileri olan herhangi bir koda bakamadı. Bu durumda yalnızca alt öğelerinde `root` yan etkileri olan kod için seçim yapması gerekir.  
  
 LINQ to XML böyle bir analiz yapmayı denemez.  
  
 Bu sorunlardan kaçınmak sizin için.  
  
## <a name="guidance"></a>Kılavuz  
 İlk olarak, bildirim temelli ve kesinlik temelli kodu karıştırmayın.  
  
 Koleksiyonlarınızın semantiğini ve xml ağacını değiştiren yöntemlerin semantiğini bildiğiniz halde, bu sorun kategorilerini engelleyen bazı zekice kodu yazarsanız, kodunuzun gelecekte diğer geliştiriciler tarafından tutulması gerekir , ve sorunlar üzerinde açık olmayabilir. Bildirime dayalı ve kesinlik temelli kodlama stillerini karıştırırsanız, kodunuz daha Brittle olacaktır.  
  
 Bu sorunların kaçınılması için bir koleksiyonu üreten bir kod yazarsanız, bakım programcılarının sorunu anlayabilmesi için kodunuzda uygun olan açıklamalara göz önünde bulabilirsiniz.  
  
 İkincisi, performans ve diğer hususlar izin veriyor ise yalnızca bildirim temelli kod kullanın. Mevcut XML ağacınızı değiştirmeyin. Yeni bir tane oluşturun.  
  
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
 