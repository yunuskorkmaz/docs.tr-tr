---
title: 'Nasıl yapılır: Yeni bir tür (LINQ to XML) proje (C#)'
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 70053a2457005f6751075b33e8e49851d7127446
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486589"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="8c931-102">Nasıl yapılır: Yeni bir tür (LINQ to XML) proje (C#)</span><span class="sxs-lookup"><span data-stu-id="8c931-102">How to: Project a New Type (LINQ to XML) (C#)</span></span>
<span data-ttu-id="8c931-103">Bu bölümdeki diğer örnekler, sonuç olarak döndüren sorgular gösterilmesini <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> , `string`, ve <xref:System.Collections.Generic.IEnumerable%601> , `int`.</span><span class="sxs-lookup"><span data-stu-id="8c931-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="8c931-104">Bunlar ortak sonuç türleri, ancak her senaryo için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="8c931-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="8c931-105">Çoğu durumda sorgularınızın döndürülecek isteyeceksiniz bir <xref:System.Collections.Generic.IEnumerable%601> başka bir tür.</span><span class="sxs-lookup"><span data-stu-id="8c931-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c931-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c931-106">Example</span></span>  
 <span data-ttu-id="8c931-107">Bu örnek nesneleri oluşturmak nasıl gösterir `select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8c931-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="8c931-108">Kod öncelikle bir oluşturucuya sahip yeni bir sınıf tanımlar ve sonra değiştirir `select` deyimi deyim yeni sınıfının yeni bir örneğini olmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="8c931-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="8c931-109">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="8c931-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
class NameQty {  
    public string name;  
    public int qty;  
    public NameQty(string n, int q)  
    {  
        name = n;  
        qty = q;  
    }  
};  
  
class Program {  
    public static void Main() {  
        XElement po = XElement.Load("PurchaseOrder.xml");  
  
        IEnumerable<NameQty> nqList =  
            from n in po.Descendants("Item")  
            select new NameQty(  
                    (string)n.Element("ProductName"),  
                    (int)n.Element("Quantity")  
                );  
  
        foreach (NameQty n in nqList)  
            Console.WriteLine(n.name + ":" + n.qty);  
    }  
}  
```  
  
 <span data-ttu-id="8c931-110">Bu örnekte `M:System.Xml.Linq.XElement.Element` konu başlığı altında tanıtılan yöntemi [nasıl yapılır: Tek bir alt öğe (LINQ to XML) alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8c931-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="8c931-111">Tarafından döndürülen öğe değerlerini almak için atamalar da kullandığı `M:System.Xml.Linq.XElement.Element` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8c931-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="8c931-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8c931-112">This example produces the following output:</span></span>  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  