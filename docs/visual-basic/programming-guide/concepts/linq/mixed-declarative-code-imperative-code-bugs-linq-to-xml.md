---
title: Bildirim Temelli-Kesinlik Temelli Kod Hataları Karışımı (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
ms.openlocfilehash: e5526a64805b19ea293d3ef28636738923d03662
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84361079"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a>Karma bildirime dayalı kod/zorunlu kod hataları (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]bir XML ağacını doğrudan değiştirmenize olanak sağlayan çeşitli yöntemler içerir. Öğe ekleyebilir, öğeleri silebilir, bir öğenin içeriğini değiştirebilir, öznitelik ekleyebilir ve benzerlerini yapabilirsiniz. Bu programlama arabirimi, [XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md)bölümünde açıklanmaktadır. Ve gibi eksenlerden birini yinelemenize sahipseniz <xref:System.Xml.Linq.XContainer.Elements%2A> ve eksen boyunca yineleme yaparken xml ağacını değiştiriyorsanız, bazı garip hatalara sahip olabilirsiniz.  
  
 Bu sorun bazen "Cadılar Bayramı sorunu" olarak bilinir.  
  
## <a name="definition-of-the-problem"></a>Sorunun tanımı  
 Bir koleksiyon aracılığıyla yinelenen LINQ kullanarak bazı kodlar yazdığınızda, bildirime dayalı bir stilde kod yazıyor demektir. İstediğiniz *şeyi* açıklamak, bunun yerine *nasıl* yapılacağını öğrenmek için daha fazla oturum vardır. 1) ilk öğeyi alan bir kod yazarsanız, 2) onu bir koşul için sınar, 3) onu değiştirir ve 4) listeye geri koyar, bu da zorunlu kod olacaktır. *Bilgisayara ne yapılacağını istediğinizi* söyleirsiniz.  
  
 Bu kod stillerinin aynı işlemde karıştırılması, sorunlara yol gösterir. Aşağıdaki topluluklara bir göz atın:  
  
 İçinde üç öğe (a, b ve c) içeren bağlı bir listeniz olduğunu varsayalım:  
  
 `a -> b -> c`  
  
 Şimdi, bağlantılı liste içinde, üç yeni öğe (', b ' ve c ') ekleyerek geçiş yapmak istediğinizi varsayalım. Elde edilen bağlantılı listenin şuna benzer görünmesini istiyorsunuz:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Bu nedenle, liste boyunca yinelenen kod yazdığınızda ve her öğe için, hemen sonrasında yeni bir öğe ekler. Ne olacağı, kodunuzun öğeyi ilk göreceği `a` ve sonra ekleneceği şeydir `a'` . Şimdi, kodunuz listede bir sonraki düğüme geçmeyecektir. `a'` Bu, listeye yeni bir öğe ekler `a''` .  
  
 Bunu gerçek dünyada nasıl çözirsiniz? Ayrıca, özgün bağlantılı listenin bir kopyasını oluşturabilir ve tamamen yeni bir liste oluşturabilirsiniz. Ya da yalnızca zorunlu kod yazıyorsanız, ilk öğeyi bulabilir, yeni öğeyi ekleyebilir ve ardından bağlantılı listede iki kez ilerledikten sonra yeni eklediğiniz öğeden ilerleyebilirsiniz.  
  
## <a name="adding-while-iterating"></a>Yineleme sırasında ekleme  
 Örneğin, bir ağaçtaki her öğe için bir kod yazmak istediğinizi, yinelenen bir öğe oluşturmak istediğinizi varsayalım:  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements()  
    root.Add(New XElement(e.Name, e.Value))  
Next  
```  
  
 Bu kod sonsuz bir döngüye girer. `foreach`İfade, `Elements()` öğesine yeni öğeler ekleyerek eksen boyunca yinelenir `doc` . Aynı zamanda, yeni eklenen öğeler aracılığıyla yineleme sona erer. Ayrıca, döngünün her tekrarında yeni nesneler ayırdığından, son olarak tüm kullanılabilir belleği tüketir.  
  
 Aşağıdaki gibi standart sorgu işlecini kullanarak koleksiyonu belleğe çekerek bu sorunu çözebilirsiniz <xref:System.Linq.Enumerable.ToList%2A> :  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements().ToList()  
    root.Add(New XElement(e.Name, e.Value))  
Next  
Console.WriteLine(root)  
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
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements()  
    e.Remove()  
Next  
Console.WriteLine(root)  
```  
  
 Ancak, bu, istediğiniz şeyi yapmaz. Bu durumda, ilk öğesini kaldırıldıktan sonra, bir, kök içinde yer alan XML ağacından kaldırılır ve yineleme yapan öğeler yöntemindeki kod bir sonraki öğeyi bulamaz.  
  
 Yukarıdaki kod aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 Bu çözüm, <xref:System.Linq.Enumerable.ToList%2A> koleksiyonu aşağıda gösterildiği gibi yeniden gerçekleştirmek için çağrmaktır:  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements().ToList()  
    e.Remove()  
Next  
Console.WriteLine(root)  
```  
  
 Bu, aşağıdaki çıktıyı üretir:  
  
```xml  
<Root />  
```  
  
 Alternatif olarak, üst öğeyi çağırarak yinelemeyi tamamen ortadan kaldırabilirsiniz <xref:System.Xml.Linq.XElement.RemoveAll%2A> :  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
root.RemoveAll()  
Console.WriteLine(root)  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a>LINQ neden bunu otomatik olarak Işleyemiyor?  
 Tek bir yaklaşım, her şeyi yavaş değerlendirme yapmak yerine her zaman belleğe getirmek olacaktır. Ancak, performans ve bellek kullanımı bakımından çok pahalıdır. Aslında, LINQ ve (LINQ to XML) bu yaklaşıma ulaşacaksa, gerçek dünyada durumlarda başarısız olur.  
  
 Başka bir olası yaklaşım, bazı işlem söz dizimine LINQ 'a yerleştirilecek ve derleyicinin kodu analiz etmeyi denemesini ve belirli bir koleksiyonun gerçekleştirilip gerçekleştirilmeyeceğini belirleyebilmesini sağlar. Ancak, yan etkileri olan tüm kodları belirleme girişimi inanılmaz karmaşıktır. Aşağıdaki kodu inceleyin:  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 Bu tür analiz kodu, herhangi bir kodun yan etkilere sahip olup olmadığını anlamak için TestSomeCondition ve DoMyProjection yöntemlerini ve bu yöntemlerin çağırdığı tüm yöntemleri analiz etmeniz gerekir. Ancak, analiz kodu yalnızca yan etkileri olan herhangi bir koda bakamadı. Bu durumda yalnızca alt öğelerinde yan etkileri olan kod için seçim yapması gerekir `root` .  
  
 LINQ to XML böyle bir analiz yapmayı denemez.  
  
 Bu sorunlardan kaçınmak sizin için.  
  
## <a name="guidance"></a>Rehber  
 İlk olarak, bildirim temelli ve kesinlik temelli kodu karıştırmayın.  
  
 Koleksiyonlarınızın semantiğini ve xml ağacını değiştiren yöntemlerin semantiğini bildiğiniz halde, bu sorun kategorilerini engelleyen bazı zekice kodu yazarsanız, kodunuzun gelecekte diğer geliştiriciler tarafından tutulması gerekir ve sorunlar üzerinde net bir şekilde bulunmayabilir. Bildirime dayalı ve kesinlik temelli kodlama stillerini karıştırırsanız, kodunuz daha Brittle olacaktır.  
  
 Bu sorunların kaçınılması için bir koleksiyonu üreten bir kod yazarsanız, bakım programcılarının sorunu anlayabilmesi için kodunuzda uygun olan açıklamalara göz önünde bulabilirsiniz.  
  
 İkincisi, performans ve diğer hususlar izin veriyor ise yalnızca bildirim temelli kod kullanın. Mevcut XML ağacınızı değiştirmeyin. Yeni bir tane oluşturun.  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
Dim newRoot As XElement = New XElement("Root", _  
    root.Elements(), root.Elements())  
Console.WriteLine(newRoot)  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş LINQ to XML Programlama (Visual Basic)](advanced-linq-to-xml-programming.md)
