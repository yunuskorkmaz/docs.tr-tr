---
title: Bildirim temelli kod-kesinlik temelli kod hataları (LINQ to XML) karışık (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 56d8140613f3dae7f99c1374634dbd8bdf094a7c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400062"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a>Bildirim temelli kod/kesinliği kod hataları karışımı (LINQ to XML) karışık (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir XML ağacı doğrudan değiştirmenize olanak tanıyan çeşitli yöntemler içerir. Öğeleri ekleyebilir, öğeleri silin, bir öğenin içeriğini değiştirme, öznitelikleri ekleme ve benzeri. Bu programlama arabirimi açıklanan [XML ağaçlarını değiştirme (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md). Bir eksen gibi yineleme, <xref:System.Xml.Linq.XContainer.Elements%2A>ve eksen yineleme gibi XML ağacı değiştirmekte olduğunuz, garip bazı hatalarla kalabilirsiniz.  
  
 Bu sorun, bazen "Cadılar Bayramı sorunu" adı verilir.  
  
## <a name="definition-of-the-problem"></a>Sorun tanımı  
 Bir koleksiyonda tekrarlanan LINQ kullanarak biraz kod yazdığınızda, bildirim temelli bir stilde kodu yazıyorsunuz. Daha fazla açıklayan yakındır *ne* istediğiniz, bunun yerine, *nasıl* bitti almak istediğiniz. (1) ilk öğeyi alır bir kod yazarsanız, bu kesinlik temelli kod şu şekilde olacaktır (2) testler bazı koşullar için 3) bunu değiştirir ve 4) bunu koyar listesine yedekleyin. Bilgisayar söylüyoruz *nasıl* bitti istediğiniz yapmak için.  
  
 Kod aynı işlemde bu stiller karıştırma ne sorunlar müşteri adayları olur. Aşağıdakileri göz önünde bulundurun:  
  
 Üç öğe ile bağlı bir liste içinde olduğunu varsayalım (a, b ve c):  
  
 `a -> b -> c`  
  
 Şimdi, bağlantılı listesinde taşımak üç yeni öğeler eklemek istediğiniz varsayalım (bir ', b' ve c'). Sonuçta elde edilen bağlantılı liste gibi görünecek şekilde istediğiniz:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Bu nedenle listesinde ve her öğe için yineler kod yazma yeni bir öğeyi sağ sonra ekler. Kodunuzu ilk Seti görecek olmasıdır ne `a` öğesi ve ekleme `a'` sonraki. Artık, kodunuz artık listesinde sonraki düğüme taşır `a'`! Sonsuza dek listesine yeni bir öğe ekler `a''`.  
  
 Nasıl, bu gerçek dünyada ister misiniz? İyi özgün bağlantılı listesinin bir kopyasını alın ve tamamen yeni bir liste oluşturun. Veya ilk öğeyi bulabileceğiniz tamamen kesinlik temelli kod yazıyorsanız yeni öğe ekleme ve eklediğiniz öğenin ilerledikten iki kez bağlantılı listesinde ilerleyin.  
  
## <a name="adding-while-iterating"></a>Yineleme sırasında ekleme  
 Örneğin, yinelenen bir öğe oluşturmak istediğiniz bir ağacında her bir öğe için kod yazmak istediğiniz varsayalım:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 Bu kod bir sonsuz döngüye giriyor. `foreach` Deyimi yinelenir aracılığıyla `Elements()` yeni öğeleri eklemek, eksen `doc` öğesi. Ayrıca yeni eklediğiniz öğeleri boyunca yineleme yukarı sona erer. Ve bir döngünün her yinelemesinden ile yeni nesneleri ayırdığından, sonunda tüm kullanılabilir bellek tüketir.  
  
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
  
 Artık kod çalışır. Sonuçta elde edilen XML ağacı aşağıda verilmiştir:  
  
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
  
## <a name="deleting-while-iterating"></a>Yineleme sırasında siliniyor  
 Belirli bir düzeyde tüm düğümleri silmek istiyorsanız, aşağıdaki gibi bir kod yazmak için fikri size cazip olabilir:  
  
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
  
 Ancak, bunu istediğiniz yapmaz. Bu durumda, ilk öğe, A kaldırdıktan sonra kök dizininde bulunan XML ağacı kaldırılır ve sonraki öğeye yineleme yapmak öğeleri yöntemi kodunda bulunamıyor.  
  
 Yukarıdaki kod aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 Çözümü yeniden çağırmaktır <xref:System.Linq.Enumerable.ToList%2A> koleksiyonun şu şekilde gerçekleştirmek için:  
  
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
  
 Alternatif olarak, yineleme tamamen çağırarak ortadan kaldırabileceğiniz <xref:System.Xml.Linq.XElement.RemoveAll%2A> üst öğesindeki:  
  
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
 Her zaman her şeyi belleğe geç değerlendirme yapmak yerine getirmek için bir yaklaşım olacaktır. Ancak, performans ve bellek kullanım açısından çok pahalı olacaktı. Aslında, bu yaklaşımı benimsemeye LINQ ve (LINQ to XML) olsaydı, gerçek dünyadaki koşullarda başarısız olur.  
  
 Başka bir olası bir yaklaşım işlem söz dizimi LINQ çeşit yerleştirin ve kodu analiz edin ve herhangi belirli bir koleksiyon gerçekleştirilmesi gerekli olmadığını belirlemek için derleyici denemesi sahip olacaktır. Ancak, yan etkisi olmadığı tüm kodu belirlenmeye çalışılırken son derece karmaşık olur. Aşağıdaki kodu göz önünde bulundurun:  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 Analiz kodların TestSomeCondition ve DoMyProjection yöntemleri ve herhangi bir kod yan etkilere sahip olduğu belirlemek için bu yöntemi çağıran tüm yöntemleri analiz etmeniz gerekir. Ancak, yan etkileri olan herhangi bir kod için Kod Analizi yalnızca aranamadı. Alt öğeleri üzerinde yan etkileri olan kod için seçilecek gerekir `root` böyle bir durumda.  
  
 Bu tür bir analiz yapmak LINQ to XML denemez.  
  
 Bu, bu sorunları önlemek için size bağlıdır.  
  
## <a name="guidance"></a>Kılavuz  
 İlk olarak, bildirim temelli ve kesinlik temelli kod karıştırmayın.  
  
 Tam olarak koleksiyonlarınız semantiği ve sorunların bu kategorileri engelleyen akıllı kod yazma, XML ağacı değiştirme yöntemleri semantiği bilmeniz bile kodunuzun diğer geliştiriciler tarafından gelecekte saklanması gerekir , ve bunlar üzerinde sorunları olabildiğince açık olmayabilir. Bildirim temelli ve buyurgan stilleri kodlama karıştırmak, kodunuzu daha kırılır olacaktır.  
  
 Bir koleksiyon gerçekleştiren ve böylece bu sorunlardan kaçınılması kod yazma, bakım programcılar sorunu anlamanız, açıklamalar, kodunuzdaki uygun şekilde ile unutmayın.  
  
 İkinci olarak, performans ve diğer önemli noktalar izin verirseniz, yalnızca bildirim temelli bir kod kullanın. Var olan XML ağacınızı değiştirmeyin. Yeni bir tane oluşturun.  
  
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

- [Gelişmiş LINQ to XML programlama (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
