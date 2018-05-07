---
title: İç birleştirmeler gerçekleştirme
description: İç birleştirmeler gerçekleştirme.
ms.date: 12/1/2016
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
ms.openlocfilehash: 9d372579e3c32964c588b6387b6d4e97f632a21f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="perform-inner-joins"></a>İç birleştirmeler gerçekleştirme

İlişkisel veritabanı bakımından, bir *INNER JOIN* her hangi ilk koleksiyon öğesinde bir sonuç kümesi ikinci koleksiyon eşleşen her öğe için bir kez görünür üretir. Bir öğenin ilk koleksiyonda eşleşen bir öğe varsa sonuç kümesinde görünmez. <xref:System.Linq.Enumerable.Join%2A> Tarafından çağrılır yöntemi `join` yan tümcesinde C# ' ta, bir iç birleştirme uygular.  
  
 Bu konuda, bir iç birleştirme dört çeşidi gerçekleştirme gösterir:  
  
-   İki veri kaynaklarından basit bir anahtarı temel öğeleri karşılık gelen basit bir iç birleştirme.  
  
-   İki veri kaynaklarından öğeleri karşılık gelen bir iç birleştirme temel alarak bir *bileşik* anahtarı. Birden fazla değerini oluşan bir anahtardır, bileşik bir anahtar, birden fazla özelliğe dayalı öğeleri ilişkilendirmenize olanak sağlar.  
  
-   A *birden fazla birleşim* hangi art arda birleştirme işlemleri birbirlerine eklenir.  
  
-   Bir iç birleştirme group JOIN kullanılarak uygulanır.  
  
## <a name="example"></a>Örnek  
  
## <a name="simple-key-join-example"></a>Basit anahtar birleşim örneği  
 Aşağıdaki örnekte, iki tür, kullanıcı tanımlı nesneler içeren iki koleksiyonları oluşturur `Person` ve `Pet`. Sorgu kullanan `join` yan tümcesinde eşleştirmek için C# `Person` nesnelerini `Pet` özelliği nesneleri `Owner` olan `Person`. `select` Yan tümcesinde C# elde edilen nesnelerdeki nasıl görüneceğine tanımlar. Bu örnekte, elde edilen nesnelerdeki sahibinin adı ve Evcil hayvanınızın adı oluşan anonim türleridir.  
  
 [!code-csharp[CsLINQProgJoining#1](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]  
  
 Unutmayın `Person` nesnesindeki `LastName` "Huff" sonuç olduğundan kümesine görünmez olan hiçbir `Pet` olan nesneyi `Pet.Owner` eşit `Person`.  
  
## <a name="example"></a>Örnek  
  
## <a name="composite-key-join-example"></a>Bileşik anahtar birleşim örneği  
 Öğeleri tek bir özelliğe dayalı bağıntı yerine birden çok özelliğe göre öğeleri karşılaştırmak için bileşik bir anahtar kullanabilirsiniz. Bunu yapmak için karşılaştırmak istediğiniz özelliklerini oluşur anonim bir tür dönmek her bir koleksiyon için anahtar Seçici işlevi belirtin. Özellikler etiket, bunlar aynı etiketi her anahtarın anonim türünde olması gerekir. Özellikleri de aynı sırada yer almalıdır.  
  
 Aşağıdaki örnek, bir listesini kullanır `Employee` nesneleri ve listesini `Student` hangi çalışanların de Öğrenciler belirlemek için nesneleri. Bu tür hem de bir `FirstName` ve `LastName` türündeki özelliği <xref:System.String>. Her listenin öğelerini birleştirme anahtarları oluşturmak işlevler oluşan anonim bir tür döndürür `FirstName` ve `LastName` her öğenin özelliklerini. Birleştirme işlemi bu bileşik anahtarlar eşitliği karşılaştırır ve ad ve Soyadı eşleştiği her listeden nesneleri çiftlerini döndürür.  
  
 [!code-csharp[CsLINQProgJoining#2](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]  
  
## <a name="example"></a>Örnek  
  
## <a name="multiple-join-example"></a>Birden fazla birleşim örneği  
 Birleştirme işlemleri herhangi bir sayıda birden fazla birleşim gerçekleştirmek için birbirlerine eklenmiş. Her `join` yan tümcesinde C# karşılık gelen bir belirtilen veri kaynağı önceki birleştirme sonuçlarını.  
  
 Aşağıdaki örnek, üç koleksiyonları oluşturur: listesini `Person` nesneleri, listesini `Cat` nesneleri ve listesini `Dog` nesneleri.  
  
 İlk `join` kişiler ve temel kediler yan tümcesinde C# ile eşleşen bir `Person` nesne eşleşen `Cat.Owner`. İçeren anonim türleri dizisi döndürür `Person` nesne ve `Cat.Name`.  
  
 İkinci `join` yan tümcesinde C# ile ilk birleşimi tarafından döndürülen anonim türler karşılık gelen `Dog` köpekler, sağlanan listesi nesneleri temel oluşan bir bileşik anahtarı `Owner` türünde özellik `Person`ve ilk harfi hayvan kişinin adı. İçeren anonim türleri dizisi döndürür `Cat.Name` ve `Dog.Name` her eşleşen çifti özelliklerinden. Bu bir iç birleştirme olduğundan, yalnızca bir eşleşme ikinci veri kaynağına sahip ilk veri kaynağı nesneden döndürülür.  
  
 [!code-csharp[CsLINQProgJoining#3](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]  
  
## <a name="example"></a>Örnek  
  
## <a name="inner-join-by-using-grouped-join-example"></a>Gruplandırılmış birleşim örneği kullanarak iç birleştirme  
 Aşağıdaki örnekte bir grup birleştirme kullanarak bir iç birleştirme uygulama gösterilmektedir.  
  
 İçinde `query1`, listesini `Person` nesneleri Grup katılmış listesine `Pet` nesneleri temel alarak `Person` eşleşen `Pet.Owner` özelliği. Group JOIN olduğu her grubu oluşur Ara gruplarının bir koleksiyon oluşturur bir `Person` nesne ve eşleşen bir dizi `Pet` nesneleri.  
  
 İkinci bir ekleyerek `from` bu sırası sıralarının sorgu yan tümcesini birleştirilmiş (ya da düzleştirilmiş) bir uzun dizi. Son dizi öğelerin türü tarafından belirtilen `select` yan tümcesi. Bu örnekte, oluşan anonim bir tür türüdür `Person.FirstName` ve `Pet.Name` her eşleşen çifti için özellikler.  
  
 Sonucu `query1` kullanarak alındıktan sonuç kümesi eşdeğerdir `join` yan tümcesi olmadan `into` bir iç birleştirme gerçekleştirmek için yan tümcesi. `query2` Değişkeni eşdeğer bu sorguyu gösterir.  
  
 [!code-csharp[CsLINQProgJoining#4](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [Gruplanmış birleşimler gerçekleştirme](perform-grouped-joins.md)  
 [Sol dış birleştirmeler gerçekleştirme](perform-left-outer-joins.md)  
 [Anonim türler](../programming-guide/classes-and-structs/anonymous-types.md)  
 
