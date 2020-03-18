---
title: Karışık Bildirimkod-Zorunlu Kod Hataları (LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 76a9bb5abf6ce2700a2a0698ebc109f65e2b7eb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168355"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a>Karışık Bildirim kodu/Zorunlu Kod Hataları (LINQ - XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]doğrudan bir XML ağacını değiştirmenize olanak tanıyan çeşitli yöntemler içerir. Öğeler ekleyebilir, öğeleri silebilir, öğenin içeriğini değiştirebilir, öznitelikler ekleyebilirsiniz ve benzeri şeyler yapabilirsiniz. Bu programlama [arabirimi, XML Ağaçlarını Değiştirme (LINQ - XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)olarak tanımlanır. Eksenlerden <xref:System.Xml.Linq.XContainer.Elements%2A>birini yinelerseniz ve eksen boyunca yinelerken XML ağacını değiştiriyorsanız, bazı garip hatalarla başa çıkabilirsiniz.  
  
 Bu sorun bazen "Cadılar Bayramı Sorunu" olarak bilinir.  
  
## <a name="definition-of-the-problem"></a>Sorunun Tanımı  
 LinQ kullanarak bir koleksiyon aracılığıyla yineleyen bazı kodlar yazdığınızda, kodbildirimel bir biçimde yazarsınız. Bu daha çok *ne* istediğinizi açıklamaya benzer, daha çok *nasıl* yapmak istediğinizi. Eğer kod yazarsanız 1) ilk öğealır, 2) bazı koşullar için test, 3) değiştirir ve 4) listeye geri koyar, o zaman bu zorunlu kod olacaktır. Bilgisayara yapılmasını istediğin şeyi *nasıl* yapacağını söylüyorsun.  
  
 Bu kod stillerini aynı işlemde karıştırmak sorunlara yol açar. Aşağıdaki topluluklara bir göz atın:  
  
 Içinde üç öğe (a, b ve c) bulunan bağlantılı bir listenizle varsayalım:  
  
 `a -> b -> c`  
  
 Şimdi, üç yeni öğe (a', b', ve c') ekleyerek bağlantılı listede taşımak istediğinizi varsayalım. Ortaya çıkan bağlantılı listenin şuna benzemesini istiyorsunuz:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Bu nedenle, liste boyunca yineleyen bir kod yazarsınız ve her öğe için hemen sonra yeni bir öğe eklersiniz. Ne olur, kodunuzu ilk `a` öğeyi görmek `a'` ve ondan sonra eklemek olmasıdır. Şimdi, kodunuz listedeki bir sonraki düğüme `a'`geçecek, şimdi! Bu mutlu listeye yeni bir öğe `a''`ekler.  
  
 Bunu gerçek dünyada nasıl çözersin? Orijinal bağlantılı listenin bir kopyasını oluşturup tamamen yeni bir liste oluşturabilirsiniz. Veya tamamen zorunlu kod yazıyorsanız, ilk öğeyi bulabilir, yeni öğeyi ekleyebilir ve bağlı listede iki kez ilerleyerek eklediğiniz öğenin üzerinde ilerleyebilirsiniz.  
  
## <a name="adding-while-iterating"></a>Yinelerken Ekleme  
 Örneğin, bir ağaçtaki her öğe için yinelenen bir öğe oluşturmak istediğiniz bazı kodlar yazmak istediğinizi varsayalım:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 Bu kod sonsuz bir döngüye girer. İfade `foreach` `Elements()` eksen üzerinden yineler ve `doc` öğeye yeni öğeler ekler. Sadece ekleyen öğeler aracılığıyla da yineler. Ve döngünün her yinelemeile yeni nesneler ayırdığı için, sonunda kullanılabilir tüm belleği tüketir.  
  
 Aşağıdaki <xref:System.Linq.Enumerable.ToList%2A> gibi, standart sorgu işleci kullanarak koleksiyonu belleğe çekerek bu sorunu çözebilirsiniz:  
  
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
  
 Şimdi kod çalışıyor. Ortaya çıkan XML ağacı aşağıdaki gibidir:  
  
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
 Belirli bir düzeydeki tüm düğümleri silmek istiyorsanız, aşağıdaki gibi kod yazmak isteyebilirsiniz:  
  
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
  
 Ancak, bu ne istediğinizi yapmaz. Bu durumda, ilk öğeyi kaldırdıktan sonra, A, kökte bulunan XML ağacından kaldırılır ve yineleyen öğeler yöntemindeki kod sonraki öğeyi bulamaz.  
  
 Önceki kod aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 Çözüm yine aşağıdaki <xref:System.Linq.Enumerable.ToList%2A> gibi, koleksiyonu hayata getirmek için aramaktır:  
  
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
  
## <a name="why-cant-linq-automatically-handle-this"></a>LINQ Neden Bunu Otomatik Olarak İşletemez?  
 Bir yaklaşım her zaman yerine tembel değerlendirme yapıyor bellek her şeyi getirmek olacaktır. Ancak, performans ve bellek kullanımı açısından çok pahalı olacaktır. Aslında, LINQ ve (LINQ XML için) bu yaklaşımı almak olsaydı, gerçek dünya durumlarda başarısız olur.  
  
 Başka bir olası yaklaşım LINQ içine işlem sözdizimi çeşit koymak ve derleyici kodu analiz etmek ve belirli bir koleksiyon gerçekleştirilmesi için gerekli olup olmadığını belirlemek için girişimi olacaktır. Ancak, yan etkileri olan tüm kodu belirlemeye çalışmak inanılmaz derecede karmaşıktır. Aşağıdaki kodu inceleyin:  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 Bu tür analiz kodu yöntemleri TestSomeCondition ve DoMyProjection ve bu yöntemler in called tüm yöntemleri, herhangi bir kod yan etkileri olup olmadığını belirlemek için analiz etmek gerekir. Ama analiz kodu sadece yan etkileri olan herhangi bir kod aramak olamazdı. Bu durumda alt öğeleri `root` üzerinde yan etkileri vardı sadece kod için seçmek gerekir.  
  
 LINQ xml için böyle bir analiz yapmaya çalışmaz.  
  
 Bu sorunlardan kaçınmak size kalmış.  
  
## <a name="guidance"></a>Rehber  
 İlk olarak, bildirimsel ve zorunlu kodu karıştırmayın.  
  
 Koleksiyonlarınızın anlambilimini ve XML ağacını değiştiren yöntemlerin anlambilimini tam olarak biliyor olsanız bile, bu sorun kategorilerinden kaçınan bazı akıllı kodlar yazarsanız, kodunuzu gelecekte diğer geliştiriciler tarafından muhafaza edilmesi gerekir ve bu konularda o kadar açık olmayabilir. Bildirimsel ve zorunlu kodlama stillerini karıştırırsanız, kodunuz daha kırılgan olacaktır.  
  
 Bu sorunların önlenebilecek şekilde bir koleksiyonu somutlaştıran bir kod yazarsanız, bakım programcılarının sorunu anlaması için bunu kodunuzda uygun açıklamalarla not edin.  
  
 İkinci olarak, performans ve diğer hususlar izin verirse, yalnızca bildirim kodu kullanın. Varolan XML ağacınızı değiştirmeyin. Yeni bir tane oluşturun.  
  
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
