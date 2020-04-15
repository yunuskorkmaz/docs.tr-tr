---
title: LINQ Sorgularına Giriş (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: 5a9d97ff14f087ddfc55986bf77f18492cbf8a04
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389588"
---
# <a name="introduction-to-linq-queries-c"></a>LINQ Sorgularına Giriş (C#)
*Sorgu,* veri kaynağından veri alabilecek bir ifadedir. Sorgular genellikle özel bir sorgu dilinde ifade edilir. İlişkisel veritabanları için SQL ve XML için XQuery gibi çeşitli veri kaynakları türleri için zaman içinde farklı diller geliştirilmiştir. Bu nedenle, geliştiriciler, desteklemeleri gereken her veri kaynağı veya veri biçimi türü için yeni bir sorgu dili öğrenmek zorunda kaldıklarını. LINQ, çeşitli veri kaynakları ve biçimleri arasında verilerle çalışmak için tutarlı bir model sunarak bu durumu basitleştirir. LINQ sorgusunda, her zaman nesnelerle çalışırsınız. XML belgelerinde, SQL veritabanlarında, ADO.NET Datasets'teki verileri ve linq sağlayıcısının kullanılabildiği diğer biçimlerde verileri sorgulamak ve dönüştürmek için aynı temel kodlama desenlerini kullanırsınız.  
  
## <a name="three-parts-of-a-query-operation"></a>Bir Sorgu İşleminin Üç Bölümü  
 Tüm LINQ sorgu işlemleri üç farklı eylemden oluşur:  
  
1. Veri kaynağını edinin.  
  
2. Sorguyu oluşturun.  
  
3. Sorguyu çalıştırın.  
  
 Aşağıdaki örnek, sorgu işleminin üç bölümünün kaynak koduyla nasıl ifade edilir olduğunu gösterir. Örnek, kolaylık sağlamak için veri kaynağı olarak bir tamsayı dizisi kullanır; ancak, aynı kavramlar diğer veri kaynakları için de geçerlidir. Bu örnek, bu konunun geri kalanı boyunca atıfta bulunulan.  
  
 [!code-csharp[CsLINQGettingStarted#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#1)]  
  
 Aşağıdaki resimde tam sorgu işlemi gösterilmektedir. LINQ'da, sorgunun yürütülmesi sorgunun kendisinden farklıdır. Başka bir deyişle, yalnızca bir sorgu değişkeni oluşturarak herhangi bir veri almadım.  
  
 ![Tam LINQ sorgu işleminin diyagramı.](./media/introduction-to-linq-queries/linq-query-complete-operation.png)  
  
## <a name="the-data-source"></a>Veri Kaynağı  
 Önceki örnekte, veri kaynağı bir dizi olduğundan, genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi örtülü olarak destekler. Bu gerçek, LINQ ile sorgulanabileceği anlamına gelir. Sorgu bir `foreach` deyimde yürütülür ve `foreach` gerektirir <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601>. Genel olarak <xref:System.Collections.Generic.IEnumerable%601> desteklenen türler veya türemiş <xref:System.Linq.IQueryable%601> arabirim, *sorgulanabilir türler*olarak adlandırılır.  
  
 Linq veri kaynağı olarak hizmet vermek için sorgulanabilir bir tür, hiçbir değişiklik veya özel işlem gerektirmez. Kaynak veriler sorgulanabilir bir tür olarak bellekte zaten yoksa, LINQ sağlayıcısı nın bunu bu şekilde temsil etmesi gerekir. Örneğin, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir XML belgesini sorgulanabilir <xref:System.Xml.Linq.XElement> bir türe yükler:  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 Ile, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]ilk tasarım zamanında bir nesne-ilişkisel eşleme oluşturmak ya el ile ya da [Visual Studio SQL Tools LINQ](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)kullanarak. Sorgularınızı nesnelere karşı yazarsınız ve çalışma [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zamanında veritabanıyla iletişimi işler. Aşağıdaki örnekte, `Customers` veritabanında belirli bir tablo temsil eder ve <xref:System.Linq.IQueryable%601>sorgu sonucunun <xref:System.Collections.Generic.IEnumerable%601>türü, .  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Belirli veri kaynakları türleri hakkında daha fazla bilgi için çeşitli LINQ sağlayıcılarının belgelerine bakın. Ancak, temel kural çok basittir: BIR LINQ veri kaynağı <xref:System.Collections.Generic.IEnumerable%601> genel arabirimi destekleyen herhangi bir nesne veya ondan devralan bir arabirimdir.  
  
> [!NOTE]
> Genel <xref:System.Collections.IEnumerable> olmayan <xref:System.Collections.ArrayList> arabirimi destekleyen türler linq veri kaynağı olarak da kullanılabilir. Daha fazla bilgi için [LINQ (C#) ile ArrayList nasıl sorgulanır.](./how-to-query-an-arraylist-with-linq.md)  
  
## <a name="the-query"></a><a name="query"></a>Sorgu  
 Sorgu, veri kaynağından veya kaynaklarından hangi bilgilerin alınca alınacak belirtin. İsteğe bağlı olarak, bir sorgu, bu bilgilerin döndürülmeden önce nasıl sıralanmalı, gruplandırılmalı ve şekillendirilmesi gerektiğini de belirtir. Sorgu, sorgu değişkeninde depolanır ve sorgu ifadesiyle başolarak başolarak başlanır. Sorgu yazmayı kolaylaştırmak için C# yeni sorgu sözdizimini tanıttı.  
  
 Önceki örnekteki sorgu, tüm çift sayıları sonda dizisinden döndürür. Sorgu ifadesi üç yan `from`tümce içerir: , `where` ve `select`. (SQL'e aşinaysanız, yan tümcelerin sıralanmasının SQL'deki sıralamadan geri çevrildiğini fark etmişsinizdir.) Yan `from` tümce veri kaynağını belirtir, `where` yan tümce filtreyi uygular ve `select` yan tümce döndürülen öğelerin türünü belirtir. Bunlar ve diğer sorgu yan tümceleri [Dil Tümleşik Sorgusu (LINQ)](../../../linq/index.md) bölümünde ayrıntılı olarak ele alınmıştır. Şimdilik önemli olan nokta, LINQ'da sorgu değişkeninin kendisinin hiçbir işlem yapıp veri döndürmememasıdır. Yalnızca sorgu daha sonraki bir noktada yürütüldüğünde sonuçları oluşturmak için gereken bilgileri depolar. Sorguların arka planda nasıl oluşturulduruştöleri hakkında daha fazla bilgi [için, Bkz. Standart Sorgu Operatörleri Genel Bakış (C#)](./standard-query-operators-overview.md).  
  
> [!NOTE]
> Sorgular, yöntem sözdizimi kullanılarak da ifade edilebilir. Daha fazla bilgi için [LINQ'da Sorgu Sözdizimi ve Yöntem Sözdizimi'ne](./query-syntax-and-method-syntax-in-linq.md)bakın.  
  
## <a name="query-execution"></a>Sorgu Yürütme  
  
### <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Daha önce belirtildiği gibi, sorgu değişkeninin kendisi yalnızca sorgu komutlarını depolar. Sorgunun gerçek yürütülmesi, bir `foreach` deyimdeki sorgu değişkeni üzerinde yineleyene kadar ertelenir. Bu kavram ertelenmiş *yürütme* olarak adlandırılır ve aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 İfade, `foreach` sorgu sonuçlarının alındığı yerdir. Örneğin, önceki sorguda, yineleme değişkeni `num` döndürülen sıradaki her değeri (birer birer) tutar.  
  
 Sorgu değişkeninin kendisi sorgu sonuçlarını hiçbir zaman tutamadığı için, sorguyu istediğiniz sıklıkta yürütebilirsiniz. Örneğin, ayrı bir uygulama tarafından sürekli olarak güncelleştirilen bir veritabanınız olabilir. Uygulamanızda, en son verileri alan bir sorgu oluşturabilir ve her seferinde farklı sonuçlar almak için bunu bir aralıkta tekrar tekrar yürütebilirsiniz.  
  
### <a name="forcing-immediate-execution"></a>Hemen Yürütmeyi Zorlama  
 Bir dizi kaynak öğesi üzerinde toplama işlevleri gerçekleştiren sorguların öncelikle bu öğeler üzerinde yinelemesi gerekir. Bu tür sorgulara `Count` `Max`örnek `Average`olarak `First`, , , ve . Sorgunun kendisi `foreach` bir sonucu döndürmek için `foreach` kullanması gerektiğinden, bunlar açık bir ifade olmadan yürütülür. Ayrıca, bu tür sorguların `IEnumerable` bir koleksiyon değil, tek bir değer döndürdüğüne de dikkat edin. Aşağıdaki sorgu, kaynak dizideki çift sayıların sayısını döndürür:  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 Herhangi bir sorgunun hemen yürütülmesini zorlamak ve sonuçlarını <xref:System.Linq.Enumerable.ToList%2A> <xref:System.Linq.Enumerable.ToArray%2A> önbelleğe almak için, veya yöntemleri arayabilirsiniz.  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 Ayrıca, sorgu ifadesinden `foreach` hemen sonra döngüyü koyarak yürütmeyi zorlayabilirsiniz. Ancak, `ToList` arayarak `ToArray` veya aynı zamanda tek bir toplama nesnesi tüm verileri önbellek.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#'de LINQ'e Başlarken](index.md)
- [Walkthrough: C'de Sorgu Yazma #](./walkthrough-writing-queries-linq.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../../linq/index.md)
- [foreach, in](../../../language-reference/keywords/foreach-in.md)
- [Sorgu Anahtar Kelimeleri (LINQ)](../../../language-reference/keywords/query-keywords.md)
