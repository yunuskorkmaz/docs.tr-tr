---
title: "Bildirim temelli kod kesinliği kod hataları (LINQ-XML) karma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d5d50b5444a9aca429eb5ddb682cd23c468a1e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a>Bildirim temelli kod/kesinliği kod hataları (LINQ-XML) karma (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]bir XML ağacı doğrudan değiştirmenize izin çeşitli yöntemler içerir. Öğeler ekleme, öğeleri silin, bir öğenin içeriğini değiştirme, öznitelikler eklemek ve benzeri. Bu programlama arabirimi açıklanan [XML ağaçlarını değiştirme (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md). Eksenleri, biri aracılığıyla gibi yineleme varsa <xref:System.Xml.Linq.XContainer.Elements%2A>ve eksen yineleme olarak XML ağaç değiştiriyorsunuz, bazı garip hatalarla düşebilir.  
  
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
  
 Bu kod sonsuz döngüye girer. `foreach` Deyimi tekrarlanan aracılığıyla `Elements()` eksen için yeni öğe eklemek, `doc` öğesi. Ayrıca aracılığıyla yeni eklenen öğelerin yineleme yukarı sona erer. Ve yeni nesneler her döngü ile ayırdığından, sonunda tüm kullanılabilir bellek tüketir.  
  
 Bellek kullanarak koleksiyon çekerek bu sorunu düzeltebilirsiniz <xref:System.Linq.Enumerable.ToList%2A> aşağıdaki gibi standart sorgu işleci:  
  
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
  
 Ancak, bunu istediğinizi yapmaz. Bu durumda, ilk öğe, A kaldırdıktan sonra kökünde bulunan XML ağacından kaldırıldı ve yineleme yaptığını öğeleri yöntemi kodda sonraki öğesi bulunamıyor.  
  
 Önceki kod şu çıkışı üretir:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 Çözümü yeniden çağırmaktır <xref:System.Linq.Enumerable.ToList%2A> koleksiyonu gibi gerçekleştirmeye için:  
  
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
  
 Bu şu çıkışı üretir:  
  
```xml  
<Root />  
```  
  
 Alternatif olarak, yineleme tamamen çağırarak ortadan kaldırabileceğiniz <xref:System.Xml.Linq.XElement.RemoveAll%2A> üst öğede:  
  
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
  
## <a name="why-cant-linq-automatically-handle-this"></a>Neden LINQ otomatik olarak bu işleyemiyor?  
 Bir yaklaşım, her zaman her şeyi belleğe geç değerlendirme yapmak yerine getirmek için olacaktır. Ancak, performans ve bellek kullanımı açısından çok pahalı olacaktır. Aslında, bu yaklaşımı benimsemeye LINQ ve (LINQ-XML) olsaydı, gerçek durumlarda başarısız olur.  
  
 Başka bir olası yaklaşım işlem sözdizimi LINQ çeşit koyun ve kod çözümlemek ve belirli bir koleksiyon gerçekleştirilmesi gerekli olmadığını belirlemek için derleyici girişimi sahip olacaktır. Ancak, yan etkileri olan tüm kodu belirlenmeye çalışılırken son derece karmaşıktır. Aşağıdaki kod göz önünde bulundurun:  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 Bu tür Analiz kodu TestSomeCondition ve DoMyProjection yöntemleri ve herhangi bir kod yan etkileri sahip belirlemek için bu yöntem çağrılır tüm yöntemleri çözümlemek gerekir. Ancak yan etkileri olan herhangi bir kod için Kod Analizine yalnızca aranamadı. İçin alt öğelerde yan etkileri olan kodu seçmeniz gerekir `root` bu durumda.  
  
 LINQ-XML gibi bir analiz yapma denemez.  
  
 Bu sorunları önlemek için size bağlıdır.  
  
## <a name="guidance"></a>Kılavuz  
 İlk olarak, bildirim temelli ve kesinlik temelli kodu karışık kullanmayın.  
  
 Tam olarak koleksiyonlarınızı semantiği ve bu kategoriler sorunları önler akıllı biraz kod yazarsanız XML ağaç değiştirme yöntemleri semantiği bildiğiniz olsa bile, kodunuzu diğer geliştiriciler tarafından gelecekte saklanması gerekir , ve bunların sorunlarını olabildiğince açık olmayabilir. Bildirim temelli ve kesinlik temelli stilleri kodlama karıştırmak, kodunuzu daha kırılır olacaktır.  
  
 Bir koleksiyon gerçeğe ve böylece bu sorunlardan kaçınılması kodu yazarsanız, böylece bakım programcıları sorunu anlayabileceği, kodunuzda uygun şekilde yorumlarla unutmayın.  
  
 İkinci olarak, performans ve diğer konular için izin verirseniz, yalnızca bildirim temelli kodunu kullanın. Varolan bir XML ağacında değiştirmeyin. Yeni bir tane oluşturun.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş LINQ-XML programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
